---
title: "Can I move complete Ubuntu installation"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by EddieA on 2007-02-08
I have a very small hard drive :(  on which I dual boot XP and  Ubuntu  and I keep running out of space so  I have sent off for a bigger one :)  I have a USB drive for data but do not want to use it for OS. I want to use my old small drive for XP and my new **_big_** drive for Ubuntu. I still need XP for certain apps.

I am a beginner and have set Ubuntu up with Java, wireless and lots of nice stuff with a lot of work and help from many Ubuntu docs and would like to keep all my programs and settings -
 - Can I move my entire Ubuntu setup to the new drive (and leave my old one to XP), without re-installing?
How would I do this?
Any help greatly appreciated.

---

### Post by xpod on 2007-02-08
Im not sure but i  think this might be what your looking for 

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Never used it though so dont know about it

---

### Post by frodon on 2007-02-08
I did that several month ago and it works well but it's not something really easy for a beginner.

Do you have a software to create an image of your windows partition ?
If you don't get one then i will assist you and explain you the steps to follow.

BtW, do you want to keep your old drive with XP and move only the ubuntu partition to the new drive ? if yes i will be easier.

---

### Post by EddieA on 2007-02-08
what quick replies !!

Xpod
Thanks for the link I have followed it to 'systemrescue cd' page  will read them both before proceeding


Frodon 
Do you mean 'partimage' or 'systemrescuecd' or similar?
Yes I was going to leave XP where it was and boot on that drive and just move Ubuntu to new drive. (with lots of lovely room for what is going to be my main OS)

My drive won't arrive for two days so I am going to read the links above and anything you may refer me to in the meantime.
When it does arrive I would be very grateful for your help.
TIA

---

### Post by frodon on 2007-02-08
Ok but i inform you that you won't be able to keep your boot on the windows drive because linux need to be on the boot drive.
In your case you won't need to ghost your windows partition so you can forget my point about ghosting your windows partition.

Tell me when you'll need help, it's too long to explain in one shot and i will need some termnal outputs with your new drive so wihout your drive i can't help you.

Basicaly you will need to make partitions on your new drives then copy your ubuntu partition on it. Once done you will need to modify your fstab, your menu.lst and device.map files then install GRUB on your new drive. And finally enter your BIOS to choose your new drive as boot device on startup.

---

### Post by EddieA on 2007-02-08
Thanks I (sort of) understand so far 
One quick Q:
Will I need then (when I *physically* install the new drive) to make the new hard drive (which will become my new  boot drive) the master or can I set it up as slave?

---

### Post by frodon on 2007-02-08
Good question, i wonder if it's possible to set a slave drive as boot drive.

Anyway put it as slave first to be able to boot as usual and do all the copy, file modifying and GRUB install stuffs, then why not just invert the drives:-k 

In all the cases, listen this advice :
Make sure to have a working ubuntu live CD before doing anything because if we miss one step your computer won't boot and you will need a live CD to ask help in the forum then :). In addition you can also do all the stuff with a live CD in case that your computer don't boot anymore.

---

### Post by EddieA on 2007-02-08
OK thanks good idea re slave/master
Live CD is OK
see you when  I get my new drive.

---

### Post by Bachstelze on 2007-02-08
Since you just want to copy your installation and not make an image of it to restore it later, a low-hassle way is to use GParted's copy-and-paste feature. I did it several times and it worked flawlessly. Of course, you''l then need to edit your GRUB's menu.list and your fstab accordinlgy.

---

### Post by EddieA on 2007-02-08
Thanks for tip - will go with Frodon for this to see his method.

Would like to get more info re gparted cut/paste so I know exactly what it copies.

---

### Post by frodon on 2007-02-08
> **HymnToLife said:**
> Since you just want to copy your installation and not make an image of it to restore it later, a low-hassle way is to use GParted's copy-and-paste feature. I did it several times and it worked flawlessly. Of course, you''l then need to edit your GRUB's menu.list and your fstab accordinlgy.This works only if you transfer the whole instalation to another disk and with the exact same partition names but here EddieA want to keep his windows partition where it is and transfer the ubuntu partition to another disk so in this case it's mandatory to adapt the fstab to give the new partition names, the menu.lst to give the new path of the windows partition and the device.map because there's a new drive.

But on the principle if you buy the same disk and do the same partitions and then just replace one disk by the other then a cut and paste and a GRUB install is all you have to do indeed.

---

### Post by EddieA on 2007-02-13
Frodon - sorry about long delay but I have been having 'interesting times' with my hardware.
I now have new hard-drive installed and configured but my plans have changed.
I have decided that I would use my limited experience to re-install Ubuntu (and try out Kubuntu) and hopefully make a better job of it than I did initially.
Using your post I knew where to look for possible errors and managed to reboot with a new drive, with master/slave combination and Kubuntu - and i managed to resolve a Grub problem with identifying my old Ubuntu install. So I can now transfer any files etc.
I am very happy with the result but I know as I progress I shall be installing again with the benefit of any future experience.
I am now going to install another Edgy or Feisty for  experiments and resize XP partition to fill up old drive.
Thanks again for the tips re which files I may have to edit  which pointed me in the right direction.

---

### Post by frodon on 2007-02-13
I'm glad that you are fine now with your new configuration, now all you have to do is enjoy :)

You're always welcome with your questions :KS

---

### Post by linuxjerk on 2007-04-02
I haven't found a complete copying utility yet. Not one that boot properly anyway.

---

### Post by frodon on 2007-04-02
> **linuxjerk said:**
> I haven't found a complete copying utility yet. Not one that boot properly anyway.This don't exist, you always need some manual operation like BIOS editing, fstab editing and so on.

---

