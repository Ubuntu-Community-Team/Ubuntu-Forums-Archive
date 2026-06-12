---
title: "Help Ubuntu boots to prompt."
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by lightaes on 2005-05-26
When I restarted the pc it started booting to the prompt.  It asks me to login and my password but I have no desktop display.  How do I load ubuntu from the prompt.

---

### Post by xmastree on 2005-05-26
login using your usual username and password, then at the prompt type:

startx

That ought to bring up the gnome desktop.

---

### Post by poofyhairguy on 2005-05-26
[QUOTE=lightaes]When I restarted the pc it started booting to the prompt.  It asks me to login and my password but I have no desktop display.  How do I load ubuntu from the prompt.[/QUOTE]

try the command:

startx

---

### Post by orion_114 on 2005-05-26
I have a similar problem. I installed off a warty disk, some of the packages where broken so I then used my hoary disc (which wont boot!) and did a sudo apt-get upgrade. I now can't even run startx! I get the following error: 
-bash: startx: command not found.
It would seem as though I need to re-install x-server. how would I go about doing that from CLI?

---

### Post by Xian on 2005-05-26
[QUOTE=orion_114]It would seem as though I need to re-install x-server. how would I go about doing that from CLI?[/QUOTE]
Just do it from the command line:
```
$ sudo apt-get install xserver-xorg
```

If you just need to reconfigure X then this will do fine:
```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by orion_114 on 2005-05-26
Hey Xian,
I tried both the commands and they seemed to go smoothly.
I still get the same error though when I type startx.  ](*,)

---

### Post by lightaes on 2005-05-26
I tried startx but this boots to a brown colored screen with no icons, or bars.  It's just an empty brown screen.  I do have mouse though.  I can move it around with no problem.

---

### Post by pdk001 on 2005-05-26
now im having same truble like you, i hope this will be sloved for me

---

### Post by pdk001 on 2005-05-26
[QUOTE=Xian]Just do it from the command line:
```
$ sudo apt-get install xserver-xorg
```

If you just need to reconfigure X then this will do fine:
```
$ sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]
thanks a bunch it works fine as well now

---

### Post by lightaes on 2005-05-26
Mine still didnt boot right after using 
sudo apt-get install xserver-xorg:

but when I used :
sudo apt-get install xserver-common xserver-xfree86

I got it going again

Thanks

---

