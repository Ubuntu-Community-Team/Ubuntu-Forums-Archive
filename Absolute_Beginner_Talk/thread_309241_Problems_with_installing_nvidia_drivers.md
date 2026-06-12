---
title: "Problems with installing nvidia drivers"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-11-29
Hello im having problems installing nvidia drivers with ubuntu 6.10 25/10/2006 release. I have installed it many times before with dapper 6.06 and early test versions with the 6.10 and never had any problems. I followed the guide at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

First i choose linux-restricted-modules-k7 then i choose nvidia-glx, then i install it then i use the command 
sudo nvidia-glx-config enable 
[SIZE=4]then [/SIZE][B]Ctrl-Alt-Backspace 

[SIZE=1]this have always worked but this time i get this after i used the glx-config enable command.

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.[/SIZE]

[/B]

---

### Post by KingBahamut on 2006-11-29
actually I think that glx-config is deprecated. I think the actual command is sudo nvidia-xconfig , then restart X.

---

### Post by hikitsu4 on 2006-11-29
> **KingBahamut said:**
> actually I think that glx-config is deprecated. I think the actual command is sudo nvidia-xconfig , then restart X.

sudo nvidia-xconfig worked perfectly, thank you.

---

