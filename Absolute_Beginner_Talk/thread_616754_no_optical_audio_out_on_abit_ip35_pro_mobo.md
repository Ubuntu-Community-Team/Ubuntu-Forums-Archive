---
title: "no optical audio out on abit ip35 pro mobo"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2007-11-18
just set up new speaker system on my pc......i have a abit ip35 pro mobo with optical out and have it run to my receiver.....however i have no audio at all in gutsy....and i have no idea how to set it up to use optical...i do however have sound in windows....any help is greatly appreciated....

---

### Post by Beaucephus on 2007-11-18
For anyone to help they will need to know what Chipset your sound card is (Even if on the mobo).  There are configuration files that need to be updated to enable extra features.  Find out what chipset you have and then search for that specifically.

---

### Post by swp6499 on 2007-11-18
reatek hd audio...is that what you need?

---

### Post by Beaucephus on 2007-11-18
That is more relevant than your motherboard for searching.  Try searching for that plus "optical"

---

### Post by swp6499 on 2007-11-18
i have searched and thats why i then posted...i cannot find out how to use optical...would digital coaxial work easier....im not worried if its optical or coaxial as long as it works...any help is greatly appreciated i will gladly provide any config files needed if someone will help

---

### Post by Beaucephus on 2007-11-19
Did you see [this one?]("http://ubuntuforums.org/showthread.php?t=616845&highlight=HDA")  It doesnt reference optical specifically but this procedure may work.  

This command will help you find the chipset...sorry I couldnt remember earlier.
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by crazedgremlin on 2007-11-25
hey, I'm thinking about buying this motherboard.  does regular (not optical) audio work in ubuntu?

---

### Post by cromb on 2008-03-25
yes

---

