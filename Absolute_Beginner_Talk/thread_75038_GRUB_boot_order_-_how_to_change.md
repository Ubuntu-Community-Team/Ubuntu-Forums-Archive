---
title: "GRUB boot order - how to change?"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by Myydral on 2005-10-13
Hi all. I have just installed Linux for the first time and so far...WOW... I am very impressed.

A question I have at the moment is this - "How do I make Winblows the default operating system in GRUB?"

I have Linux default on my laptop but when I load it onto my main system, I wish it to be Winblows - for the significant other . Until I get Linux doing everything that Windows currently does for me, I still need a Windows box.

I have read the Ubuntuguide, but I can't seem to follow that regarding this matter. Wiki confused me too.

Hopefully help is only a post away....cheers.

---

### Post by adwait on 2005-10-13
Hi!
Ok lets start....
Open up the /boot/grub/menu.lst file using
```
sudo gedit /boot/grub/menu.lst
```

Now, count the seria number of the windows entry. IMPORTANT: Start counting from 0 not 1 (ie: 0 1 2 3.....)

Now find the line
```
default 0
```
Change it to the serial number of the windows partition...
done!

---

### Post by davmac on 2005-10-13
Hi,

It's a fairly easy change. Open up a terminal window and type "sudo cp /boot/grub/menu.lst /boot/menu/grub.backup" to back up the config file and then type "sudo gedit /boot/grub/menu.lst" to edit it.

All of the entries in your grub menu are listed towards the bottom of the file. You can change the order of these.

Alternatively, near the top you'll see a line "default = 0". You can just change this number.

HTH,

---

### Post by katzpiketailes on 2008-07-02
i typed in : sudo gedit /boot/grub/menu.lst

 the menu.1st file opened up but nothing was written on it..so i can't edit anything..

help plss..

---

### Post by don horn on 2008-07-02
Hi
I'm total beginner but same interest and I got as far as seeing the list but tried to alter default from 0 to 4.

Got message 'you do not have the necessary permissions to save the file.'

How do I get the permissionn I need please - remember this is my first go at ubuntu please.

Don Horn

---

### Post by antoz on 2008-07-03
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

The above link has been very helpfull to me for anything about grub give it a go.A

---

### Post by Kevbert on 2008-07-03
The menu.lst is a small L.  When you count the number of entries the count is from 0 and you need to include the line
```
Other operating systems:
```
as an entry.  So if you just have one version of Ubuntu, Windows would be 4 and you'd need to set default to 4.
When you edit the file you need to use 'sudo' to get write permissions for the file.  If you aren't prompted for a password then there's a problem when using sudo.

---

### Post by dnairb on 2008-07-03
> **katzpiketailes said:**
> i typed in : sudo gedit /boot/grub/menu.lst

 the menu.1st file opened up but nothing was written on it..so i can't edit anything..

help plss..

the file is menu.lst (an "ell" not a one)

---

### Post by estyles on 2008-07-03
personally, I create a launcher on my desktop for "sudo nautilus", which will prompt you for a password and then open a window that has root priveleges.  I think it's easier for noobs like me to do things graphically - even editing a text file.  That way you can navigate to /boot/grub and find menu.lst, instead of typing in 'menu.1st' and instead of getting an error, gedit just creates the file.

If you need help on how to create a launcher, I believe this is all there is to it (at work right now on a windows box, so I can't check): Right-click on your desktop and choose Create Launcher.  I don't know if automatically launches the properties box, but if not you should be able to right-click the launcher and edit Properties.  Name it something like "Root Window", and for the command, type in: sudo nautilus

I find that Root Window shortcut to be invaluable.

I was writing a short how-to on how to not only change your default boot, but also how to make it automatically boot from windows->linux and linux->windows.  I have to make some changes to it to plug a security hole, but after that, I'll repost it in Tips and Tutorials.  For what you want, simply setting Windows to be the default, the above posts should be exactly what you need.

---

### Post by Sneaky07 on 2008-07-03
> Hi
I'm total beginner but same interest and I got as far as seeing the list but tried to alter default from 0 to 4.

Got message 'you do not have the necessary permissions to save the file.'

How do I get the permissionn I need please - remember this is my first go at ubuntu please.

Don Horn

In order to have permissions to change your menu.lst (with an L) you have to log in as root.  You should know your root password because you have to make one when you install Ubuntu. In order to log in under root you must first open a terminal and use "su" command.  Then it will ask you for your password which you should know.  After you enter it you will know you are in root because it will have root@.....  After that change to the file directory by using "cd (then the path)".  Once your in the menu.lst directory in the terminal type in "gedit menu.lst" or any other form of text editor equivalence if you don't have gedit installed.  Then you should be able to edit the file and save changes.

In simple terms:
```
su
(Type root password)
cd path_name
gedit menu.lst (or any other file)
```

To Myydral:

At the end of your menu.lst file you should be able to see all of your operating systems with a few lines of code underneath them.  

Example:
Windows
root hd(0,0)
kernel (kernel edition)
etc....

Simplest way to change that it loads up Windows instead of Linux is to cut the Windows portion out and paste it at the top of the list of all of the other operating systems.  It's pretty simple.  So when you reboot Windows will be at the top of the grub list and you can also change the timeout time in your list to add more seconds until it loads the first listed operating system.  Hope this helps!!

---

### Post by dodle on 2008-07-04
I think the simplest way to do this is to download *startupmanager*.

Either use synaptic to get it, or open a terminal and type:
```
sudo apt-get install startupmanager
gksu startupmanager
```

You can choose which operating system you want to be your default on the first tab.

---

### Post by Tonyr63 on 2008-07-04
> **Sneaky07 said:**
> In order to have permissions to change your menu.lst (with an L) you have to log in as root.  You should know your root password because you have to make one when you install Ubuntu. In order to log in under root you must first open a terminal and use "su" command.  Then it will ask you for your password which you should know.  After you enter it you will know you are in root because it will have root@.....  After that change to the file directory by using "cd (then the path)".  Once your in the menu.lst directory in the terminal type in "gedit menu.lst" or any other form of text editor equivalence if you don't have gedit installed.  Then you should be able to edit the file and save changes.

In simple terms:
```
su
(Type root password)
cd path_name
gedit menu.lst (or any other file)
```

To Myydral:

At the end of your menu.lst file you should be able to see all of your operating systems with a few lines of code underneath them.  

Example:
Windows
root hd(0,0)
kernel (kernel edition)
etc....

Simplest way to change that it loads up Windows instead of Linux is to cut the Windows portion out and paste it at the top of the list of all of the other operating systems.  It's pretty simple.  So when you reboot Windows will be at the top of the grub list and you can also change the timeout time in your list to add more seconds until it loads the first listed operating system.  Hope this helps!!

Hi

I installed xunbuntu to a new partition created during the install by manually resizing free space and initially following the install it restarted back to XP as if the install did not happen. I repeated the install a second time and I got a boot munu allowing me to boot into Windows and Xunbuntu.

The problem I found was that when I scroled down the menu to Window XP option I got "Starting ....GROB and nothing.  System hung like a donkey.

I am left with the impression after much correspondance on this and other forums there is diddly sqwat I can do to troubleshoot or get back to my Windows partition.  Lucky there is no important data there however I was really hoping Ubuntu would properly support dual booting, which on testing has proved very problematic.

Partition information:

sudo blkid

/dev/sda1: LABEL="ANNS DATA" UUID="1ECD-2877" TYPE="vfat"
/dev/sdb1: LABEL="DSK_1_1" UUID="B9B9-3C80" TYPE="vfat"
/dev/sdb5: TYPE="swap" UUID="a866c23b-4f66-4d5e-aad8-41f358f74d7c"
/dev/sdb6: UUID="00268405-12ec-4972-80b2-ed392dc20e6c" TYPE="ext2"

ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 120 2008-06-18 05:04 .
drwxr-xr-x 6 root root 120 2008-06-18 05:04 ..
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 00268405-12ec-4972-80b2-ed392dc20e6c -> ../../sdb6
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 1ECD-2877 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 a866c23b-4f66-4d5e-aad8-41f358f74d7c -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 B9B9-3C80 -> ../../sdb1

sudo blkid

/dev/sda1: LABEL="ANNS DATA" UUID="1ECD-2877" TYPE="vfat"
/dev/sdb1: LABEL="DSK_1_1" UUID="B9B9-3C80" TYPE="vfat"
/dev/sdb5: TYPE="swap" UUID="a866c23b-4f66-4d5e-aad8-41f358f74d7c"
/dev/sdb6: UUID="00268405-12ec-4972-80b2-ed392dc20e6c" TYPE="ext2"

I believe the XP boot partition is on sdb1.

The system has a SCSI drive and 2 IDE deives.
"Anns Data is the SCSI drive and XP should be on DSK_1_1.

That's why I thought changing the boot.ini file to hd(0,1) would have worked.

I don't understand why Linux this all my disks are SCSI when I have 2 IDE disks?

I have to question the Ubuntu setup that allows you to resize a partition with windows already installed and yet does not automatically set up a dual boot scenario?

Why does all the documentation suggest that to have a dual boot you have to manually resize and allocate partitions? Surely if people are resizing disks with Windows rather that over writing they have signaled their intention to have a dual boot?

This is a serious design oversight for Ubuntu to not have this partition stuff clear during setup.

---

