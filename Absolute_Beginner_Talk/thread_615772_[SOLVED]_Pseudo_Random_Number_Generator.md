---
title: "[SOLVED] Pseudo Random Number Generator"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-11-17
Hello, 

I would like to know if there is any program or script that would generate 100 pseudo random numbers.  Anything would be helpful!

---

### Post by Trzone on 2007-11-17
For my specific purpose, i found a website random.org.  But i would still like to use/ find a program that generates some pseudo random numbers.. any ideas?

---

### Post by eldragon on 2007-11-17
if linux is what you are programing for.
you can read the file /dev/urandom,
it will give you pseudorandom numbers.....

if you want more randomness, you can read /dev/random
but that file might lose entrophy and you could end up with a stuck program.

---

### Post by Trzone on 2007-11-17
Thanks, although im not programing i just needed a few random integers between 0-9 *shrugs*

---

### Post by mali2297 on 2007-11-17
> **Trzone said:**
> Thanks, although im not programing i just needed a few random integers between 0-9 *shrugs*

I haven't found a simple tool for this. But if you're not afraid of bash, you can use the following commands in the terminal.

```

echo $RANDOM

```
will generate a random number between 0 and 32767.

```

echo $[$RANDOM % 10]

```
will give a number between 0 and 9.

```

for i in $(seq 5); do echo $[$RANDOM % 10]; done

```
will give 5 numbers.

If you want to set the seed of the pseudo-random sequence, just start with 
```

RANDOM=1234

```
where 1234 can be any number you want.

---

### Post by Trzone on 2007-11-17
Thank you so much! i'l try it  :)

---

