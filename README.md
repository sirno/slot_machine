# Slot Machine

![tests](https://github.com/sirno/slot_machine/actions/workflows/tests.yml/badge.svg)

Have you ever found yourself ruminating over which configuration to choose?

Don't choose.

Randomize.

With `slot_machine` you can now sample any configuration.

Can't settle on a background color? Randomize...

Looking for a reasonable model parameter? Randomize...

Don't know what to eat on Sunday? Randomize...

With `slot_machine` your next choice will be one you look forward to.

## Examples

Simply add your favorite samplers to the configuration:

```yaml
chicken_nuggets: !IntegerSample 5..20
price: !UniformSample 9.99..20
```

Specify your dataclass and get rolling:

```python
from dataclasses import dataclass
from slot_machine import SlotsSerializer

@dataclass(slots=True)
class Basket(SlotsSerializer):
    chicken_nuggets: int
    price: float

yaml_file = """
basket:
  chicken_nuggets: !IntegerSample 5..10
  price: !UniformSample 9.99..20
"""

surprise_basket = Basket.from_yaml(yaml_file)

print(surprise_basket)
```
