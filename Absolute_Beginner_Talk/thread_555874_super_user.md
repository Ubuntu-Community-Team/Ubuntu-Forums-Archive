---
title: "super user"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by htdjose on 2007-09-20
how do you know if your logged in as superuser, i didnt make any other accounts, only the main one i log into.. am i logging in as superuser
?
=swoop=
p.s. why is it bad to log in as super user?

---

### Post by swisscow on 2007-09-20
No, your not. But if you type ```
whomai 
```into a terminal it will tell you who you are!

Good thing not being logged in as super user - then you can't screw things up, add viruses etc.

---

### Post by Ant_Merlin on 2007-09-20
Hi, in ubuntu the first login is as a user in the administrator group. this means you are a normal use but you are able to use the sudo command (Super User DO), you have also a full list in the system and programs menus.
hope this helps

---

### Post by JReagan1990 on 2007-09-20
Ubuntu does not come with a super user profile.  Logging in as a super user is not necessarily a bad thing, but it does leave you open to security and mistakes, as it gives you all the power to delete important files, etc.

Ubuntu keeps the super user password for a short while, just to keep you from having to retype it in.  It will then drop the password, and ask for it again, after 15 min. or so.

---

### Post by Calash on 2007-09-20
To give "Super User" privileges (also called root privileges) to an application in the terminal you can type sudo before the command.  This will prompt you for your password, but then execute with full root privileges.

Ubuntu does have a root account, but it is disabled by default.  It is a very good idea not to enable it, as you open the potential for security risks when using root.  Any application run with root privileges can alter any part of the OS, damaging files or planting viruses.

---

### Post by htdjose on 2007-09-20
okay thanks, i understand now..super user can f me over, cool stuff, thanks, another quick question...i dont know what i did, on my desktop theres one of my hard drives on there, os( i think its the vista hard drive) im not sure what i did, what do i do to fix it, unmount it? i just dont want it on the desktop anymore...any help would be greatly appreciated
=swoop=

---

### Post by Ant_Merlin on 2007-09-20
Hi the hard drive on desktop just means you have accessed it recently, unmount it and it will go away from desktop till needed again. When you put CD/DVD`s in you will see then there too.

---

### Post by RedSquirrel on 2007-09-20
This is a helpful document for learning about sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by htdjose on 2007-09-20
okay, thanks
=swoop=

---

### Post by anemptygun on 2007-09-20
superuser=root

---

### Post by bigboy_pdb on 2007-09-20
htdjose, what swisscow mentioned can be helpful for seeing which user you are. There was a typo in the response though. The command is "whoami" (and not "whomai"). Typing this in the terminal will show you which user you are. If you type "sudo whoami" it will state that you're executing the command as root.

Regarding removing file system icons (in your case the one for the Windows partition) from your desktop, you can do the one of the following:

_**Don't show any file systems on desktop but keep the volume mounted**_
If you don't want to see the file system on your desktop, but you still want it mounted (perhaps because you frequently access the contents of the file system), you can use GNOME Configuration Editor to keep file systems that are mounted from being shown on the desktop.

**NOTE:** Other file systems such as USB drives or CD-ROMs will no longer appear on the desktop when you do this.

You can add an icon to launch the configuration editor to your tool bar by right clicking on Applications/Places/System and selecting "Edit Menus", going to "System Tools", and clicking the check box beside "Configuration Editor". Then you can access it by going to Applications -> System Tools -> Configuration Editor.

Alternately, you could run it from the terminal or by using the "Run Application" window using the command "gconf-editor" (press ALT-F2 to open the "Run Application Window").

Once you're in the Configuration Editor go to "/apps/nautilus/desktop" and then uncheck the check box beside "volumes_visible". Icons for mounted file systems will no longer show up on your computer.

There are also options for adding home, computer, documents, trash, and network icons to your desktop there.

_**Show drives on desktop but don't mount volume when Ubuntu starts**_
If you don't want the drive to be mounted when your computer starts but you want to see icons on the desktop for other file systems (such as USB drives or CD-ROMs when they are inserted into the tower), you can simply comment out the line for that file system in the file "/etc/fstab".

**NOTE:** You will have to mount the file system to see its contents (double clicking its icon in the nautilus file manager will do this). If you don't access the file system very often then this isn't an issue.

To do this, do the following. In the terminal or the "Run Application Window" type "gksudo gedit /etc/fstab". Write a "#" character at the beginning of the line that corresponds with the file system that you don't want to see on the desktop. This will keep it from mounting when Linux starts up and as a result it won't show up on the desktop.

If you don't know what file system it is then you can use the command "mount" (in the terminal) to see which drives are mounted. Windows partitions have a type of VFAT or NTFS and their devices are usually "/dev/sda1" or "/dev/hda1" (since Windows is usually on the first hard drive on the first partition).

The line under "# /dev/sda1" or "# /dev/hda1" and that has the words "ntfs" or "vfat" in it is most likely the line that you'll want to write a "#" character at the front of (in the "fstab" file).

After you've done this, you can restart your computer to check if it worked.

---

