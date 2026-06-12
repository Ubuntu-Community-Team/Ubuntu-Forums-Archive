---
title: "IR Blaster Help"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by awesomo on 2007-08-28
Im having a problem getting my ir blaster to work in linux. Ulitmately I am trying to install myth tv, but  I want to set up my hardware beforehand. I am using this guide [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty), and all goes well until I try to use the blaster to turn on my satellite box; then I get the following error:
```
irsend: command failed: SEND_ONCE blaster POWEROFF
irsend: unknown remote: "blaster"

```

Here is what the blaster remote section of my lircd.conf file:
```
begin remote

  name          blaster
  bits          32

  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
  name POWER
  2148532234
 end raw_codes
end remote

```

I have have tried changing the name of the Power command, but to no avail. So can you guys help out another newb?

---

### Post by awesomo on 2007-08-29
Alright, so that error has mysteriously disappeared, but now I have a new problem. Whenever I run the command ```
irsend SEND_ONCE blaster POWEROFF
``` I get the following error, ```
irsend: could not connect to socket
irsend: Connection refused

```
So I checked all the cables, and everything is connected. Is my irblaster broken or is this a linux issue?

---

