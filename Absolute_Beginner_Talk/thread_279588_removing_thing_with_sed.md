---
title: "removing thing with sed"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2006-10-18
Would someone please tell me the code to remove the last 2 digits of an entry?

Examples of entries:

```
echo warthog12345 | sed <code>
warthog123
```

```
echo hedgehog1234567 | sed <code>
hedgehog12345
```

```
echo badger123456789 | sed <code>
badger1234567
```

The same sed code should work for all 3 above.

Does anyone know the missing code?

---

### Post by Jussi Kukkonen on 2006-10-18
Not the solution you were looking for, but a solution if you're in bash:
```
string="badger123456789"
len=${#string}
echo ${string:0:len-2}
```

---

### Post by Arndt on 2006-10-18
> **newbie22 said:**
> Would someone please tell me the code to remove the last 2 digits of an entry?

Examples of entries:

```
echo warthog12345 | sed <code>
warthog123
```

```
echo hedgehog1234567 | sed <code>
hedgehog12345
```

```
echo badger123456789 | sed <code>
badger1234567
```

The same sed code should work for all 3 above.

Does anyone know the missing code?

Not very hard to do:

```
sed -e 's/[0-9][0-9]$//'

```

Why do you need this?

---

### Post by newbie22 on 2006-10-18
Thanks!

I am trying to write a mathematical script.  The program did not support fractions.  So I had the formula multiplied by 100, and use the above to remove the last 2 digits.

Instead of looking, downloading another program, rewriting the script to correspond to the new program, I just decided to add in the little sed piece.

Thanks again!

---

### Post by Arndt on 2006-10-19
> **newbie22 said:**
> Thanks!

I am trying to write a mathematical script.  The program did not support fractions.  So I had the formula multiplied by 100, and use the above to remove the last 2 digits.

Instead of looking, downloading another program, rewriting the script to correspond to the new program, I just decided to add in the little sed piece.

Thanks again!

You can do this too:

```
$ echo '65537 100 / p' | dc
655

```

---

