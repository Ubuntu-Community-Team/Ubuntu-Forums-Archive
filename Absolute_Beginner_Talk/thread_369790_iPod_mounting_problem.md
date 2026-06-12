---
title: "iPod mounting problem?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by rover on 2007-02-25
Well, i connect my iPod, mount it in the terminal with 
> pmount -t vfat /dev/sda2 /media/ipod 
sudo eject /dev/sda2

Ok, it normally is mounted but when i go to Amarok it doesn't says there is no Media-Device.
And when i hit connect and put in the two comands that are above in the post then it doesn't find any Media-Device.

Please help? :)

---

### Post by rover on 2007-02-25
Maybe its the wrong command? If so help?

---

### Post by dcj65 on 2007-02-25
Well I'm new to this, so I tried to connect my Ipod through amarok and had the same problem. On the other hand my Ipod works fine with Banshee with no extra work at all.

---

### Post by dcj65 on 2007-02-25
Ok the commands you were using are wrong, go to settings in Amarok and go to config amarok.
then to media devices. then put in the exact name of your ipod and the mount command would be  like this ( this is my setup) mount /home/ken/desktop/ipod and then the eject is the same with eject instead of mount. 


Hope this helps

---

### Post by terdon on 2007-02-25
Why are you ejecting? If you look for the ipod after ejecting it of course it won't be there. Just run the mount command and then use amarok or gtkpod or whatever. Once you are done, then eject it.

---

### Post by dcj65 on 2007-02-25
In the config window of Amarok it asks for a mount command and an eject command, thats why I put that in there. The Ipod mounts as soon as you plug it in, but it is not seen by Amarok till you set it up.

---

