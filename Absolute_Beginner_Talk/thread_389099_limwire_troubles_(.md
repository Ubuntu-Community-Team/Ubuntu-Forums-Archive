---
title: "limwire troubles :("
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-03-20
hello all,

i've been trying to get limewire to run because i love limewire and amule is *i'm gonna go chuck my computer out the nearest window* slow ](*,).

limewire was (i believe) installed succesfully, it shows up in my applications list, but when i click to launch it nothing happens.

yes, i do have java installed correctly (i think)

---

### Post by taurus on 2007-03-20
Can you at least run it from a terminal to see what the error message is?

Applications -> Accessories -> Terminal
```
limewire
```

---

### Post by gameman12 on 2007-03-20
thx for the speedy reply.

here is the output

```
john@john-laptop:~$ limewire
runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")

```

---

### Post by Efwis on 2007-03-20
Use Frostwire, It uses the Limewire system. I believe it is available in the repositories, not sure since I installed it using automatix2.

same speed, and control as Limewire, just a different look and name.

---

### Post by mahiyar on 2007-03-20
This is because of "bash" and "dash" as two cli's, it seems that limewire needs "bash". See this link esp step 4 [http://ubuntuforums.org/showthread.php?t=278134&highlight=limewire+expecting+%7D]("http://ubuntuforums.org/showthread.php?t=278134&highlight=limewire+expecting+%7D")

BTW -- I too am using frostwire, its like limewire pro but free.

---

### Post by mahy on 2007-03-20
```
sudo gedit /usr/bin/limewire
```

and replace the first line with

```
#! /bin/bash
```

---

### Post by gameman12 on 2007-03-20
mahy, i tried ur code, but they were there already.

i have talked to other ppl and they recommended i nix limewire and use froswire.


i'm gonna install frostwire, but need to update java first. thx for the help though

---

