---
title: "rescue cd"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-02-03
Dear friends, would you kindly tell me how to make a rescue boot cd for ubuntu?
I may have to reinstall winXP or install red hat for some purpose; but I am afraid it would really erase the master boot record.
Kindly advise.

---

### Post by sauravbhaumik on 2007-02-03
Dear friends, would you kindly tell me how to make a rescue boot cd for ubuntu?
I may have to reinstall winXP or install red hat for some purpose; but I am afraid it would really erase the master boot record.
Kindly advise.

---

### Post by bodhi.zazen on 2007-02-03
If you install redhat it will (should) recognize Ubuntu if you install grub to the MBR as you install ...

If you install windows you will need to restore grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Some like supergrub: 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by mikewhatever on 2007-02-03
Perhaps [this one]("http://www.sysresccd.org/Main_Page")
I downloaded it, but never had to use, so check the FAQs and features first.

If you just want something to recover Ubuntu after reinstalling Windows, read [ HERE](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by pseudonym on 2007-02-03
I find [this Rescue CD]("http://www.sysresccd.org/Main_Page") very useful for things like this. It inluceds loads of other handy tools as well.

---

### Post by sauravbhaumik on 2007-02-03
> **bodhi.zazen said:**
> If you install redhat it will (should) recognize Ubuntu if you install grub to the MBR as you install ...

If you install windows you will need to restore grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Some like supergrub: 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

But actually, Red Hat did not recognize ubuntu; and after red hat installation, I found only red hat and windows in my system; though I am sure ubuntu was there - but I could not access ubuntu.

Is there anything I could have done without reinstalling ubuntu?
Supergrub seems to be good, but how can it restore ubuntu if red hat is installed?

---

### Post by bodhi.zazen on 2007-02-04
No big deal ;)

boot to Red hat

mount your Ubuntu partition to say /media/ubuntu

In Red hat open a terminal and as root (su or sudo) open /boot/grub/menu.lst for editing

Now open /media/ubuntu/boot/grub/menu.lst

Copy the Ubuntu stanza to Red hat, but lets use chainloader, so edit your Ubuntu stanza to :

> title Ubuntu
Root (hdx,y)
savedefault
chainloader +1
boot

I do not know your ubuntu partition so you will need to fill in (hdx,y) with say (hd0,1) or whatever is appropriate for Ubuntu.

The advantage of chainloader is it passes booting from fedora to your Ubuntu partition. When you boot you will thus get 2 boot (grub) screens, first from Red Hat, second from Ubuntu.

This will be useful when you upgrade your ubuntu kernel you will not have to edit /bot/grub/menu.lst in Red hat (manually).

Whe disadvantage is well 2 grub screens on boot.

You can fix this.

Boot Ubutnu.

Again open (Ubuntu) /boot/grub/menu.lst and change default to 0 and timeout to 0. Now you well rapidly boot Ubuntu from the red had menu.

In Ubuntu:
>  timeout   0
default   0You will find these lines near the top of (Ubuntu) /boot/grub/menu.lst

HTH

---

### Post by sauravbhaumik on 2007-02-04
But it doesn't open in even Ubuntu```
saurav@saurav-desktop:~$ sudo su
root@saurav-desktop:/home/saurav# /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied

```

---

### Post by bodhi.zazen on 2007-02-04
> **sauravbhaumik said:**
> But it doesn't open in even Ubuntu```
saurav@saurav-desktop:~$ sudo su
root@saurav-desktop:/home/saurav# /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied

```

LOL :lol:

You need to specify an editor, nano ? vim ? gedit ?

```
sudo su
**nano**  -B /boot/grub/menu.lst
```

With nano, the -B flag (option) automatically makes a backup ;)

for gedit use gksudo :```
saurav@saurav-desktop:~$gksudo /boot/grub/menu.lst
```
Note: gksudo is issued as a user not root ;)

---

### Post by Mr.Auer on 2008-01-31
gksudo means GTK Sudo = a graphical dialog for asking your password. So running something "gksu command" or "gksudo command" is the same as running "sudo command", except with gksu or gksudo it will pop up a dialog box asking for your password.

---

### Post by seventhc on 2008-01-31
> With nano, the -B flag (option) automatically makes a backup :wink: I like that, is there an option in vim or gedit that does that too???

---

### Post by Sukarn on 2008-01-31
> **Mr.Auer said:**
> gksudo means GTK Sudo = a graphical dialog for asking your password. So running something "gksu command" or "gksudo command" is the same as running "sudo command", except with gksu or gksudo it will pop up a dialog box asking for your password.

There are other differences, like where the settings  for the application are stored (which account's home directory is treated as home directory in that application)

AFAIK, running an application with gksudo makes that application treat /root as its home directory, and running it with sudo makes that application treat ~/ (/home/username) as its home directory.

---

### Post by bodhi.zazen on 2008-01-31
> **seventhc said:**
> I like that, is there an option in vim or gedit that does that too???

Yes, gedit does this automatically I believe, saving to <file>~

For vim , you need to install vim-full, then :

[http://vim.sourceforge.net/tips/tip.php?tip_id=892](http://vim.sourceforge.net/tips/tip.php?tip_id=892)

---

### Post by seventhc on 2008-01-31
Thanks:) I have vim-full, so I'll just have to add to my vimrc. :)

---

