---
title: "[SOLVED] Desktop shortcuts broken after reboot"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by gredawarha on 2008-02-27
Hello all.

I have searched the forum and can find several threads but so far none that have helped me solve my issue.

I am using ubuntu 7.10.

I have a couple of folders in my secondary hard drive that I wish to be able to access by using shortcuts on my desktop.

I have tried right clicking each folder and making a link.

I have also tried the middle button method.

Both work fine initially however once the computer is rebooted the links become broken and no longer work.

Thanks, your time and patience is appreciated.

---

### Post by neurostu on 2008-02-27
It probably has something to do with the way the 2nd drive is being mounted. It could be getting mounted at a different spot everytime you reboot.

---

### Post by DieB on 2008-02-27
is your secondary harddrive built in and has an entry in /etc/fstab ?
cause if not it might be a problem with the automount.

---

### Post by SunnyRabbiera on 2008-02-27
hmm, is the other hard drive plugged in all the time.
There is a way to get mounted hard drives to appear on the desktop:
First on the top panel right click on your main menu bar and choose "edit menus"
now you are in the menu editor go to system tools and click on the box/circle/whatever next to "configuration editor"
this will make the default configuration editor for gnome (your graphic user interface)
once you enable it close off the menu editor
now go back to your applications menu and then go to system tools and click on the configuration editor.
It will open, click on the little arrow next to "apps" and scroll down to "nautilus" and click on its arrow.
next you select desktop, this will allow you to edit the default contents of your desktop.
You can enable a trash can, a computer icon and other stuff so you can have easier access to your stuff.
the one of most importance is the one that says "volumes visible" so that you can get easier access to your drives.
You may want to play around with this part to get your desktop the way you want it

---

### Post by gredawarha on 2008-02-27
Hi guys thanks for the quick response.

This is my fstab I believe:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bc220a8d-0f3c-4761-854d-d4c581299887 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c0731bfa-9a8a-4cab-8f97-a1021f556dfc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Now i'm pretty sure that my second HD is /dev/hdb1 which is not listed in fstab.

Any ideas?

---

### Post by DieB on 2008-02-27
open the file with "sudo gedit /etc/fstab" and add a line like this

/dev/hdb1  [mountpoint]    ext3    defaults        0       2

as mountpoint use any existing folder you want, but remember it should be empty.
I would use something like /home/[user]/extra_hd

hope that helps.

---

### Post by gredawarha on 2008-02-27
So let me get this straight?

I should i type:

/dev/hdb1 /home/andree/extra_hd ext2 defaults 0 2

Noting that I have replaced user with andree and ext3 with ext2.

Am I correct in thinking that I will need to place a folder named extra_hd in my (andree) folder?

Thanks again.

---

### Post by DieB on 2008-02-27
yes that is correct. u have to add that folder to your home/andree/, but you can use whatever name you want instead of extra_hd
after a reboot it should be mounted permanently to that place.

---

### Post by gredawarha on 2008-02-27
Ok thanks again for the help.

I gave it a go but I got the following:

andree@andree-desktop:~$ sudo su
root@andree-desktop:/home/andree# /dev/hdb1 /home/andree/extra_hd ext2 defaults 0 2
bash: /dev/hdb1: Permission denied
root@andree-desktop:/home/andree# 

Any ideas?  It says permission denied, but I made sure I was root?

Also now when I right click the HD it says it is unmounted where as before I did the above it was mounted?

---

### Post by DieB on 2008-02-27
well as i wrote:

> sudo gedit /etc/fstab

if u type that in your terminal a new window should open with the fstab-file inside that enter your line.

if you wanna do it completely in the terminal use nano or vi instead of gedit

hth

---

### Post by gredawarha on 2008-02-27
Apologies my mistake.

Okay

I did

sudo gedit /etc/fstab 

and then added:

/dev/hdb1 /home/andree/extra_hd ext2 defaults 0 2

so my fstab now looks like:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bc220a8d-0f3c-4761-854d-d4c581299887 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c0731bfa-9a8a-4cab-8f97-a1021f556dfc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1 /home/andree/extra_hd ext2 defaults 0 2


However when I go to the extra_dh folder there is nothing there?

Thanks

---

### Post by DieB on 2008-02-27
as I wrote:

> **DieB said:**
> after a reboot it should be mounted permanently to that place.

---

### Post by gredawarha on 2008-02-27
Thanks DieB.

Did a reboot after reading through the thread again apologies.

I went to the extra_hd folder but there was no HD, there was however several folders there that were originaly on the HD.

Is that normal?  I was expecting to find an image of my HD inside the folder and then the contents of my HD inside that?

It all works fine it's just not what I expected coming from a Windows background.

My desktop links are also working fine now after reebooting too!

Many thanks for your help and more importantly your patience!

---

