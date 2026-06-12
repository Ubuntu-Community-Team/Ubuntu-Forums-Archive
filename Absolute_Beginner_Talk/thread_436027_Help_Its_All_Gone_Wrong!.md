---
title: "Help Its All Gone Wrong?!?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-05-07
I've just tried installing Ubuntu 7.04 and I got this horrible screen that went a command login and I don't know anything about linux so can someone help Ive got a ATI Radeon Xpress 200M card and thats the problem but I dont get how to fix it.

It says [here]("http://ubuntuforums.org/showthread.php?t=414194") but I dont get what any of that means.

Please give a step by step guide!
Thanks
:confused:

---

### Post by fakie_flip on 2007-05-07
Use the Restricted Drivers Manager. It is made for beginners and very easy to use. At the top click on System, then Administration, then Restricted Drivers Manager.

---

### Post by fakie_flip on 2007-05-07
What did you do before your computer got messed up? Did you follow that guide, and then it was messed up? If so, you could restore your backed up xorg.conf, and you should have graphics again.

---

### Post by SamTyson92 on 2007-05-07
I installed then re-booted like it said then it came up.

So I dont have any back up of any kind.

---

### Post by Sef on 2007-05-10
> I've just tried installing Ubuntu 7.04 and I got this horrible screen that went a command login and I don't know anything about linux so can someone help Ive got a ATI Radeon Xpress 200M card and thats the problem but I dont get how to fix it.

It says here but I dont get what any of that means.

Please give a step by step guide!
Thanks

Can you to the command line by ctrl + alt + F1?   If you can, then type or copy and paste these commands (from [URL="http://ubuntuforums.org/showthread.php?t=414194"] 'Installing Ubuntu 7.04: ATI X**** Cards'/URL]. 

1) ```
sudo apt-get update
```

2) ```
sudo apt-get dist-upgrade
```

3) ```
sudo apt-get install xorg-driver-fglrx
```

4) ```
sudo depmod -a
```

5) ```
sudo aticonfig --initial
```

6) ```
sudo aticonfig --overlay-type=Xv
```

7) ```
sudo shutdown -r now
```

---

### Post by fakie_flip on 2007-05-10
> **SamTyson92 said:**
> I installed then re-booted like it said then it came up.

So I dont have any back up of any kind.

Maybe you have a backup and you don't know it. The Nvidia driver installer automatically creates a backup. Maybe the ATI one does too. You can find out though.

```
ls /etc/X11
```

---

