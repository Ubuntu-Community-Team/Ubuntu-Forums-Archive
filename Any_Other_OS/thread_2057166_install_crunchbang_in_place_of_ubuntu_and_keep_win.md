---
title: "install crunchbang in place of ubuntu and keep windows dual boot"
date: 2012-09-13
forum: Any Other OS
---

### Post by samuelbirkett on 2012-09-13
I currently have ubuntu 12.04 LTS 32bit installed alongside windows 7 64bit

[http://bayimg.com/jaCLKAAEc]("http://image.bayimg.com/jaclkaaec.jpg") (copy and paste, don't click)

my disk[500gb] has 3 partitions the first being ubuntu 2nd windows and 3rd linux swap.

I want to install crunchbang(based on debian) instead of ubuntu. but still keep my windows install, and preferably grub. note I'm using a laptop with no optical drive.

what I'm looking for is some links to point me in the right direction..
maybe a guide on how to config grub after install another linux distro?
idk.. I'm lost in the situation.

thank you in advance.

---

### Post by nothingspecial on 2012-09-13
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by mike555 on 2012-09-13
As long as you did a real install ( not wubi ) you can just install to the partition that has Ubuntu now, the installer will erase Ubuntu and replace it and update grub .
 if you don't have a cd drive you will need to burn the .iso to USB using startup disc creator  or similar program, then start your laptop by the USB ,by pushing the right function key while starting ( mine is F12 )

---

### Post by mips on 2012-09-13
> **mike555 said:**
> As long as you did a real install ( not wubi ) you can just install to the partition that has Ubuntu now, the installer will erase Ubuntu and replace it and update grub .
 if you don't have a cd drive you will need to burn the .iso to USB using startup disc creator  or similar program, then start your laptop by the USB ,by pushing the right function key while starting ( mine is F12 )

This ^^

There's also a new crunchbang release coming out in november I think so if you are feeling adventures you can try their new testing release CrunchBang 11 "Waldorf"

---

### Post by snowpine on 2012-09-13
You can also

```
sudo apt-get install openbox
```

and get basically the same thing as CrunchBang on your Ubuntu, except with longer-term support (12.04 will be supported through April 2017) and a bigger community.

---

### Post by critin on 2012-09-13
> **samuelbirkett said:**
> I currently have ubuntu 12.04 LTS 32bit installed alongside windows 7 64bit

[http://bayimg.com/jaCLKAAEc]("http://image.bayimg.com/jaclkaaec.jpg") (copy and paste, don't click)

my disk[500gb] has 3 partitions the first being ubuntu 2nd windows and 3rd linux swap.

I want to install crunchbang(based on debian) instead of ubuntu. but still keep my windows install, and preferably grub. note I'm using a laptop with no optical drive.

what I'm looking for is some links to point me in the right direction..
maybe a guide on how to config grub after install another linux distro?
idk.. I'm lost in the situation.

thank you in advance.

Download the iso to your computer.  Download unetbootin (find it with google),  Insert a usb flash stick into computer.  Run unetbootin and browse for diskimage --ISO from there.  Choose the iso and it will show on unetbootin, click OK and wait for it to finish.  Safely remove the usb, or if you're already at the computer you want to install it on, just click BOOT.  If not, boot it from the other computer.  You will need to know which key to push to boot from usb or cd, but you already know that.

Be sure you know the partition number of ubuntu so you won't accidently write over Windows.  

You can install to the same partition and it will replace grub by default.  All you have to do is choose the partition and follow instructions from there.

---

### Post by samuelbirkett on 2012-09-18
Thanks for all the replies. I will try install openbox in ubuntu as suggested and If I don't get the same feel as I do in crunch-bang than maybe I'll try installing the other distro.
Will post results later.

---

### Post by mips on 2012-09-18
> **samuelbirkett said:**
> Thanks for all the replies. I will try install openbox in ubuntu as suggested and **If I don't get the same feel as I do in crunch-bang** than maybe I'll try installing the other distro.
Will post results later.

I doubt you would as it loads a boatload of stuff as part of the standard install. If you want the same feel then do a netinstall and only add what you need.

---

