---
title: "[SOLVED] LimeWire White Screen"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by DonBucknall on 2007-07-29
Hello,

I have installed LimeWire and when I start it, it comes up with a white screen.
I have compiz-fusion installed aswell and when I disable it LimeWire works.
How do I get round this so LimeWire works under compiz-fusion aswell?

I tried [https://help.ubuntu.com/community/LimeWire](https://help.ubuntu.com/community/LimeWire)

but then I get this:
> $ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading LimeWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct


Does anyone know how to get it working?

Thanks,

Don

---

### Post by DonBucknall on 2007-07-29
I searched the forums before I got this problem, and found one with exactly the same name.
It had a solution in it but I didn't know how to do it.
With a little more research I found out how to do it and I solved the problem.

> Fixed!

it was a problem with java so i looked around

found that i had to tweak it a little so all i did was make a startup script

[QUOTE]#!/bin/bash
cd /usr/lib/LimeWire/
export AWT_TOOLKIT=MToolkit && java -jar LimeWire.jar
made it and saved it as Limewire_fix.sh

and changed the command on the limewire icon done if anyone else needs help hit me up

the fix is for java 6[/QUOTE]

Thanks to Spankymasterc who posted the fix.

Don

---

### Post by JAGGEDSPHERE on 2007-08-11
this one worked for me (tried others too...)
thanks for the fix
7.04. compiz

---

### Post by rne1223 on 2007-08-18
```
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
```


How do I update java to 1.5+?

---

### Post by MenZa on 2007-08-18
I recommend that, instead of using Limewire, you can use Frostwire---an open source client which does the same as Limewire (even uses the same network):

```
sudo aptitude install frostwire
```

---

