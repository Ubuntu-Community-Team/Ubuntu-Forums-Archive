---
title: "Random number generator"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-02-13
Does anyone know how to write a very short script that will generate a number from 0-9?  Or some other way to generate a random number.

---

### Post by flummoxed on 2006-02-13
```
from random import *

# This generate an integer from 0 to 9
myInteger = randint(0, 9)

print myInteger
```

That's a short python file that will do it for ya. Copy that into a text file, and save it with the .py extension, then run it in the terminal by going to its folder and typing

python yourfilename.py

Where yourfilename is what you named it.

---

### Post by Klaidas on 2006-02-13
Pascal code
```

Randomize; // this makes sure you don't get the same number every time
RandomInteger := random(10);  // generates a number [0 - 10]
```

---

