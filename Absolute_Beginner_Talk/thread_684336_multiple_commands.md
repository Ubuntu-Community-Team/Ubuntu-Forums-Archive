---
title: "multiple commands"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by kevmore on 2008-02-01
when i see this

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

do I have to type them one at a time and hit enter each time, or what?
I know it's probably a pretty stupid question but the instructions said to follow the method exactly so I want to make damn sure.

I just want to stare at my computer like a moron and watch my desktop spin on a cube.
Why is that so hard????

---

### Post by emarkd on 2008-02-01
You do them one at a time, from the terminal.  Applications > Accessories > Terminal and go at it.

Did the restricted drivers manager not work for you?

---

### Post by PeterJS on 2008-02-01
Pro tip: don't type stuff out, that's what copy and paste is for.

People like to give command line advice because it's real easy to copy and paste, instead of having to worry about clicking and typing stuff.

---

### Post by kevmore on 2008-02-03
but I can't cut the whole thing and paste it, right?

---

### Post by kevmore on 2008-02-03
The restricted drivers did not work for me.

---

### Post by leader303 on 2008-02-03
commands can be connected with ```
&&
``` between them.

---

### Post by ~LoKe on 2008-02-03
=)
```
sudo apt-get update && sudo apt-get install linux-restricted-modules-generic restricted-manager xorg-driver-fglrx && sudo depmod -a
```

---

### Post by TheBoat on 2008-02-03
You can also separate commands with a semicolon.

```
;
```

---

### Post by Dr Small on 2008-02-03
Just copy & paste this :)
```
sudo apt-get update ; sudo apt-get install linux-restricted-modules-generic restricted-manager ; sudo apt-get install xorg-driver-fglrx ; sudo depmod -a
```

---

### Post by kevmore on 2008-02-03
cool thanks

---

### Post by Roger Cook on 2008-02-03
If you will put Tomboy notes into the taskbar. Then you can just copy and paste  most all Apt-Get commands to terminal just changing rhe name at the end. I have about 25 Apt-Get and that covers most averything that is needed.

---

### Post by Dr Small on 2008-02-03
> **Roger Cook said:**
> If you will put Tomboy notes into the taskbar. Then you can just copy and paste  most all Apt-Get commands to terminal just changing rhe name at the end. I have about 25 Apt-Get and that covers most averything that is needed.
When I grew up with Ubuntu, they never had tomboy notes :p
But that sounds like a good idea ;)

---

### Post by kevmore on 2008-02-03
does klipper do the same thing?

---

