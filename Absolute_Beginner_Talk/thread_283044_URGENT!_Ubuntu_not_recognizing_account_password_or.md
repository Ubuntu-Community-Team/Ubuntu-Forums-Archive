---
title: "URGENT! Ubuntu not recognizing account password or root password!"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-23
I first noticed i couldnt connect to my ubuntu box over sftp today/

now i do "sudo poweroff" and i put in my password and it doesnt work

i go into root

my root password doesnt work.

did i get hacked? please help

---

### Post by chuckyp on 2006-10-23
Make sure your caps lock key is off.  Also are you trying to log in locally or via ssh or some other variant?

---

### Post by aysiu on 2006-10-23
This may help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by sdubois92 on 2006-10-23
my power just went out and it shut off my PC, now i cant log on! argh!

what do i do!

---

### Post by aysiu on 2006-10-23
Is your power off completely now... or did it go out momentarily and now it's back on again?

Can you boot into recovery mode?

Do you have a live CD?

---

### Post by sdubois92 on 2006-10-23
powers back on

im in the login screen

and yes, i have a live cd.

---

### Post by Anonii on 2006-10-23
> **sdubois92 said:**
> powers back on

im in the login screen

and yes, i have a live cd.
Login, try sudoing again. Does it work? How did you "go into root" before?

---

### Post by sdubois92 on 2006-10-23
what do you mean log in? it wont recognize my password

---

### Post by aysiu on 2006-10-23
A live CD is a good to have just in case, but can you boot into recovery mode?

This tutorial on fixing sudo walks you through all the steps:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by brash on 2006-10-23
I was looking at your posting history and noticed you [recently were working to turn your computer into an FTP server]("http://www.ubuntuforums.org/showthread.php?t=281663"). Is it at all possible you might have done something there to give too much access to outside parties?

---

### Post by skymt on 2006-10-23
You should probably reboot into recovery mode (choose it from the grub menu). That gives you a root shell without a password, unless you previously set a root password. Then run this:```
passwd yourusername
<set your password>
reboot
```When it reboots, try to log in with your new password.

---

### Post by sdubois92 on 2006-10-23
im follwing the tutorial, it asks for my root password, but like i said before, it will not recognize it.

---

### Post by sdubois92 on 2006-10-23
yes, i did set a root password before.

---

### Post by aysiu on 2006-10-23
Ah, good point. If you don't set a root password, recovery mode will just go straight to a root prompt. If you set one, you'll be asked for it.

We'll need the live CD, then. You don't happen to have a Knoppix live CD, do you? If you have a Knoppix one, it'll be a bit easier, but if you have only a Ubuntu live CD, we can work with that, too.

---

### Post by sdubois92 on 2006-10-23
i have a ubuntu live cd i got in the mail, thats it.

---

### Post by aysiu on 2006-10-23
Okay. **Slight disclaimer:** I've never done this before, but I'm basing this off these two tutorials:
[http://gentoo-wiki.com/HOWTO_Reset_a_Lost_Root_Password](http://gentoo-wiki.com/HOWTO_Reset_a_Lost_Root_Password)
[http://archive.cert.uni-stuttgart.de/archive/suse/security/2004/07/msg00237.html](http://archive.cert.uni-stuttgart.de/archive/suse/security/2004/07/msg00237.html)

Boot the live CD.

**Find partition information**
In terminal, type ```
sudo fdisk -l
``` That's a lowercase *L* at the end there. This should give you a sense of your partition layout and where your Ubuntu partition is. Let's say, for the sake of this example, it's /dev/hda2.

**Mount partition**
```
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/hda2 /media/recovery
```

**Now we try to recover**
```
chroot /media/recovery /bin/bash
```

**Reset root password**
```
sudo passwd root
```

Reboot and hope for the best!

---

### Post by sdubois92 on 2006-10-23
when i put in the CD i get the screen that lets me choose to install it and run the live CD, theres no partition information. do i select install cd?

---

### Post by Henry Rayker on 2006-10-23
run the live cd, don't install...

---

### Post by sdubois92 on 2006-10-23
couldnt i just install it again, i didnt have any important files saved. i saved eveeything to a network drive just incase something like this happened.

---

### Post by aysiu on 2006-10-23
You shouldn't be able to install anything without first running the CD.

Run the CD... and then **don't** install anything. Just do as I instructed before.

If you're unfamiliar with the terminal, take a look at this:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

---

### Post by sdubois92 on 2006-10-23
how do i get to it, i have a screen up that looks like this

//www.howtoforge.com/images/perfect_setup_ubuntu606/1.png

---

### Post by skymt on 2006-10-23
> **sdubois92 said:**
> how do i get to it, i have a screen up that looks like this

//www.howtoforge.com/images/perfect_setup_ubuntu606/1.png

You probably want "Rescue a broken system". aysiu's instructions assume you have the desktop CD, and you appear to have the server CD. From there it's the same, though.

---

### Post by aysiu on 2006-10-23
> **sdubois92 said:**
> how do i get to it, i have a screen up that looks like this

//www.howtoforge.com/images/perfect_setup_ubuntu606/1.png
That's odd, because when I pop in my Ubuntu CD, I get this screen.

---

### Post by sdubois92 on 2006-10-23
ya i have the desktop version, i just found the picture the looked closest to it

---

### Post by aysiu on 2006-10-23
And I'm saying this is really weird, since the screenshot I posted **is** the desktop version, and it's not just something I found--I created that image from my actual desktop CD.

Mine has the option to "start Ubuntu," not just "install Ubuntu." In any case, you should probably select "install Ubuntu." It's not actually going to ever erase your hard drive without confirmation. If you seem not to boot into a live session and you're immediately asked for your language, then press Control-Alt-Delete and maybe we can think of something else.

---

