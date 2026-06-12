---
title: "Partitouns with out a live CD"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by bobandirus on 2007-09-04
I have been trying to make a partition to install ubuntu on, but all partition managers need a live cd, which is a prob, as i used our last one to put ubuntu on, is there any way to make a partition without needing a CD?

---

### Post by Vadi on 2007-09-04
"need a live cd, which is a prob, as i used our last one to put ubuntu on"

If I understand you right... you can LiveCD's as many times as you want. They don't "expire" or "get used up" at all.

---

### Post by jw5801 on 2007-09-04
I think he means that he used his last blank CD to put the Ubuntu LiveCD on.
And the Ubuntu LiveCD has GParted on it, which is the Gnome Partition Manager which you should be able to use to repartition your drive. You may want to kill the gnome-volume-manager so that it doesn't try to automount your partitions while you're modifying them.
If you find another blank CD then try out the GParted LiveCD (see the link in my sig.). It's the most up-to-date version of GParted you'll find and will save you alot of hassle.
Finally you should be able to partition during the install process, what is the problem with doing it that way?

---

### Post by bobandirus on 2007-09-04
didnt know you could partition with the install :P i was doing this so i had somewhere to install to hehe sorry

---

### Post by bobandirus on 2007-09-04
Just a thought, how do you get the Partition bit on the Ubuntu CD to work, with out Ubuntu trying to install? Or does it load up all by itself?
Sorry if this is a silly question, but I just want to make shure, before I install Ubuntu propally.

---

### Post by Obor on 2007-09-04
don't know if I got you question right

If you have the Ubuntu Live CD and you boot up from it (choose the "try OR install" option), it will give you a working Ubuntu running from the cd (without installing anything on your HD) once you have a running ubuntu live session you can find the partitioner somewhere in the system menu or you can click on Instal Ubuntu and partition during install.

hope this answered your question

Edit: you can watch video about setting up dual boot with ubuntu on [this page]("http://www.robdian.co.uk/content/view/20/50/"). I think it would clear up few of your questions (its done with older ubuntu version but most things still apply).

---

### Post by jw5801 on 2007-09-04
Sure, I always prefer to partition manually anyway, seems less risky to me :p

Open up a terminal in your LiveCD (Applications > Accessories > Terminal) and type: ```
sudo killall gnome-volume-manager
gksu gparted
```
As I mentioned before you need to stop the gnome-volume-manager process else it will automount whatever partition you're trying to edit, which is bad.

...and just for terminal background information:
sudo = run the succeeding command with root privelages
killall = kill the following process
gksu = graphical sudo: this should be used for any command that starts a graphical app
gparted = the gnome partition editor (which obviously needs to be run with root permissions).

---

### Post by bobandirus on 2007-09-04
Ahh yea it does :) thank you :)

---

### Post by jw5801 on 2007-09-04
No probs! :)

---

### Post by johnbull on 2007-09-04
Wish I'd found this yesterday when I was having the same problems as bobandirus. I, too, was eventually led to gparted (thanks, Forum) and got the partioning sorted. But now on boot I get the chance to choose 3 Ubuntu starts plus the Winows XP. I take it this is a result of not killing the gnome volume manager. and my ham fisted attmpts at partioning.
Any way of getting rid of the surplus starters??

---

### Post by Vadi on 2007-09-04
I think your 3 ubuntu starts are normal though.

If I'm right, the first one is to boot ubuntu normally, the second is to boot ubuntu in recovery mode (use that when you fked up), and the third is memtest, which tests your RAM.

if you want though, you can edit your menu.lst and commend out (put the # symbols at the beginning of the line) the other two boot options.

---

### Post by jw5801 on 2007-09-04
Yeah those 3 are meant to be there. It'll be a normal boot, safe/recovery mode and memtest.
You can remove them if you want but I'd recommend leaving them there just in case you ever need to get into safe mode.
If you want to remove them, you need to open up your grub menu.lst (just a text file):
```
gksu gedit /boot/grub/menu.lst
```then you should see a few entries like this:
[quote=menu.lst]title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=803ab468-dd4c-4afe-bbab-494bb6425500 ro single
initrd          /boot/initrd.img-2.6.20-15-generic[/quote]so just comment out the entries you don't want, like this:
```
#title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.20-15-generic #root=UUID=803ab468-dd4c-4afe-bbab-494bb6425500 ro single
#initrd          /boot/initrd.img-2.6.20-15-generic
```

---

