---
title: "Help with &quot;if&quot; (in bash)"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-09-30
I have the following code:

```

x=0
if $x==0 ; then echo asd ; else echo qwe ; fi

```

but resurns

```
bash: 0==0: command not found
```

How can I test for equality here?

---

### Post by Billy_McBong on 2007-09-30
[COLOR="Blue"]```
if [ $x = 0 ] 
```should work[/COLOR]

---

### Post by nick_h on 2007-10-01
or, in case x is null:
```
if [ "$x" = "0" ]
```

---

