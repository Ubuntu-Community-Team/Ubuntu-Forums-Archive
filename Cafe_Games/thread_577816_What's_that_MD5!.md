---
title: "What's that MD5!"
date: 2007-10-16
forum: Cafe Games
---

### Post by LaRoza on 2007-10-16
The game is simple, give an MD5 Checksum, and have the next person give the original content, ie, word, file, etc. Only post if you correctly answer the previous one.

3e25960a79dbc69b674cd4ec67a72c62

---

### Post by LaRoza on 2007-10-16
Two hours and no takers? It was a joke by the way :D

(It was "Hello world", in case you were wondering)

---

### Post by InsertNameHere on 2007-10-16
1d41c853af58d3a7ae54990ce29417d8

---

### Post by FuturePilot on 2007-10-17
How do you do this?

---

### Post by Vicfred on 2007-10-17
hmm you can do it with an implementation on lots of programming languages hmm or you can use an online generator... the only way i know to de-crypt md5 is throught rainbow tables... and its pretty fast when you got the tables but generate the tables may be toooo slow on a single pc tho...this is what i know maybe theres more ways to decrypt it

@InsertNameHere

its "ubuntu" hmm my turn?

2ecca0f10025449158f294ac358d345e

---

### Post by LaRoza on 2007-10-17
To use Python (installed on Ubuntu, available for most OS's including Windows) see my wiki if you don't have it.

Type "python" in a terminal, you will get an interactive session.

Type "import md5"

Now, use:

```

print md5.md5(string)

```

I used "print md5.md5("Hello world")

---

### Post by FuturePilot on 2007-10-17
```
>>> print md5.md5("Hello World")
<md5 HASH object @ 0xb7dc9b80>
>>> 

```
Did I do this right?:confused:

---

### Post by LaRoza on 2007-10-18
> **FuturePilot said:**
> ```
>>> print md5.md5("Hello World")
<md5 HASH object @ 0xb7dc9b80>
>>> 

```
Did I do this right?:confused:

Sorry, I made an error

>>> import md5
>>> m = md5.new()
>>> m.update("Hello world")
>>> m.hexdigest()

---

### Post by FuturePilot on 2007-10-18
> **LaRoza said:**
> Sorry, I made an error

>>> import md5
>>> m = md5.new()
>>> m.update("Hello world")
>>> m.hexdigest()

There we go.
```
'3e25960a79dbc69b674cd4ec67a72c62'

```

---

### Post by Vicfred on 2007-10-19
> **FuturePilot said:**
> There we go.
```
'3e25960a79dbc69b674cd4ec67a72c62'

```

its "hello world", my turn

'f8e3bfa0d2f3d1d1bf33e9b80f11d752'

---

### Post by PCaddicted on 2011-07-13
I don't know.
8g8g09fyguf99n8g98ye56r

---

