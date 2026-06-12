---
title: "Total Beginner Info"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by bman on 2006-02-23
I'v used Linux before, thought I knew enough, so trying it again. I wan't to get good at it so I'm asking this. Can sombody post a link, or give information on the basics, like how the filesystem is different to windows, how to install, uninstall programs, orgaization, etc etc.

I haven't seemed to find anything like this on the forums.

Thanks

---

### Post by Squatpuke on 2006-02-23
I'll second that as a Linux Newbie.

---

### Post by bman on 2006-02-23
You know in Windows, you can go to Program Files (mostly) and find all your installed programs, open up the folders and there is everything needed for that program. Is there somewhere like that for Linux, or explain otherwise.

---

### Post by bman on 2006-02-23
I just also relised, I don't have permission to install anything to the drive /

how do I changed this, also how to I create folders.

---

### Post by mr_mop on 2006-02-23
[QUOTE=bman]You know in Windows, you can go to Program Files (mostly) and find all your installed programs, open up the folders and there is everything needed for that program. Is there somewhere like that for Linux, or explain otherwise.[/QUOTE]

There is a tool called synaptic that does a similar job

---

### Post by bman on 2006-02-23
Dosen't that just show what you have installed, not able to go into folder and such.

---

### Post by bman on 2006-02-23
I think I can learn and adjust to this file system and things, I think my only problem right now is I have no permission to do anything. Everything I try to install open, rename etc says "you dont have permission"

Why is this, I'm the administrator?

---

### Post by nocturn on 2006-02-23
Linux and Unix use a very different model for the filesystem.  But keep in mind that everything is managed by the package management system, so you can easily find out where all files for a particular program are stored.

Some basics

/bin and /usr/bin contains executable files.  /sbin and /usr/sbin contain executable files that are restricted, mainly for root only.
/lib and /usr/lib contain libraries (like dll's).

Configuration files is stored in /etc and personal data is always stored in a home directory under /home.

For more details, you can check out the Filesystem Hierarchy Standard here:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by nocturn on 2006-02-23
[QUOTE=bman]Dosen't that just show what you have installed, not able to go into folder and such.[/QUOTE]

Synaptic allows you to manipulate your installed programs and install new ones and updates.

Just go in there an search for a program that you haven't got installed yet (let's say k3b - a CD/DVD burning tool -).  Mark it for installation and apply.

You will notice that synaptic automatically selects packages that k3b depends on.

---

### Post by nocturn on 2006-02-23
[QUOTE=bman]I think I can learn and adjust to this file system and things, I think my only problem right now is I have no permission to do anything. Everything I try to install open, rename etc says "you dont have permission"

Why is this, I'm the administrator?[/QUOTE]

How are you trying to install things?

---

### Post by bman on 2006-02-23
Thanks that will most definintly help me, but my biggest problem right now I think, it the whole permissions thing stated above.

---

### Post by bman on 2006-02-23
through the console, right now I'm trying to update firefox, and nothing is working, command dosent work, or you dont have permission etc

---

### Post by Bartender on 2006-02-23
nocturn -
How come everything's (I'm referring to the link that you included on file permissions) in these endless "one page" formats?  It'd be much less wasteful if they were in .pdf so I could manually print all the even pages first, then flip the paper over and print the odd's...

---

### Post by Iowan on 2006-02-23
[QUOTE=bman]I just also relised, I don't have permission to install anything to the drive /

how do I changed this, also how to I create folders.[/QUOTE]I'm no expert, but most permissions-related problem stem from needing to be **root**. In Ubuntu, the **sudo** command is used.  For example: from a terminal, type **sudo mkdir /mydir [enter]** You'll be asked for a password... that'd be the one you used to log onto the system.  That should create the directory named **mydir** on the root ( / ) directory.  As mentioned, I'm no expert... without trying it, I can't say for sure if typing **ls / [enter]** will list the root directory and show you the new "folder"... if you must **sudo ls / [enter]**, or if it's **ls / -a** or **ls -a /**.

---

### Post by bman on 2006-02-23
Seems like sudu dosent work at all, when I tryed installing WINE, and other things, it just dosent work, says bad command or something.

---

### Post by Bartender on 2006-02-23
Iowan - 
I was thinking the same thing.  bman mentions prior experience w/ Linux, and the sudo model seems to trip people up who are accustomed to different rules.

Doesn't fstab show what his permissions are?  Should we ask him to post if he can?

---

### Post by Iowan on 2006-02-23
[QUOTE=Bartender]nocturn -
How come everything's in these endless "one page" formats? [/QUOTE]
Probably a carryover from the "old" UNIX.  BUT... I can view **man** pages from a command prompt - .pdf's are a li'l tougher.

---

### Post by bman on 2006-02-23
how do I run fstab?

---

### Post by Bartender on 2006-02-23
bman -
this from the Wiki -

[https://wiki.ubuntu.com/FilePermissions?highlight=%28permissions%29](https://wiki.ubuntu.com/FilePermissions?highlight=%28permissions%29)

It's not very self-explanatory but you should be able to try some of the commands and see if you get similar results.

---

### Post by bman on 2006-02-23
I read it, don't really understand what to input into the terminal....to change permissions...

---

### Post by Bartender on 2006-02-23
bman -
I hope I'm not just making things worse.  I know very little about Ubuntu.  What happens when you type 

sudo gedit /etc/fstab

into a terminal?  Just copy/paste that if you want

That's a real basic command for seeing (actually it's probably more accurate to say you'd use this for editing but as long as you just close the terminal when yur done and don't change anything we'll be OK) the drives that Ubuntu recognizes.  The funny little string of text after the drives tells something about permissions, but I'm not good enuf to say what those are without doing a little homework.  I'm grasping at straws and there are probly better ways of seeing your permissions...

---

### Post by Bartender on 2006-02-23
bman -
I searched "permissions".  A lot of posts, some seem like they might be applicable to you.  Here's one -

[http://www.ubuntuforums.org/showthread.php?t=134388&highlight=permissions](http://www.ubuntuforums.org/showthread.php?t=134388&highlight=permissions)

I notice right at the end alan.mckinnon lists some man files - man files have always been about worthless for me but maybe you'll find more helpful.  Can you get to the man files?

---

### Post by bman on 2006-02-23
Just got to school, yes I'm only 17.....I'll be sure to check those things out when I get home, and let you know.

Thanks

---

### Post by bman on 2006-02-23
When I typed that code into the terminal, I got this...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by saads on 2006-02-23
If you go to System -> Administration -> Package Manager  then you should be prompted for a password.  Put in your login password and the package manager should open.  From there you can install and remove anything on your system.  A more user-friendly app for this is under Applications -> Add/Remove.  Although that doesn't have all of the programs that you can get in Synaptic.  However to start off it should be sufficient.

I noticed earlier that you were using the command 'sudu' and you got a unrecognized command error.  The proper command is 'sudo'.

---

### Post by bman on 2006-02-23
Thanks, but we figured this out already, I need to fix my permissions.

---

### Post by aysiu on 2006-02-23
[QUOTE=bman]I'v used Linux before, thought I knew enough, so trying it again. I wan't to get good at it so I'm asking this. Can sombody post a link, or give information on the basics, like how the filesystem is different to windows, how to install, uninstall programs, orgaization, etc etc.

I haven't seemed to find anything like this on the forums.[/QUOTE] I wrote a PDF just for users like you. It covers all the basics about Ubuntu specifically and Linux in general (filesystem, permissions, how to install, what an ISO is, etc.): [http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

---

### Post by bman on 2006-02-23
If I go into the properties of a folder I need, it says "I'm not the owner, you do not have permission to change this"...wtf, I am the owner...I don't get it..

---

### Post by aysiu on 2006-02-23
[QUOTE=bman]If I go into the properties of a folder I need, it says "I'm not the owner, you do not have permission to change this"...wtf, I am the owner...I don't get it..[/QUOTE] See the third link of my signature.

---

### Post by bman on 2006-02-23
Alright, I followed that....used that command to allow me to change things in /root.....followed the firefox tutorial, moved it into /opt.....nothing happens, still using 1.0.7

---

### Post by aysiu on 2006-02-23
[QUOTE=bman]Alright, I followed that....used that command to allow me to change things in /root.....followed the firefox tutorial, moved it into /opt.....nothing happens, still using 1.0.7[/QUOTE] Oh, it's Firefox you're trying to set up? Sorry to throw another link at you, but I can't explain it better than this: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by bman on 2006-02-23
See...that's what I did....and extracted to that folder.....still using 1.0.7....

so messed up frig

---

### Post by aysiu on 2006-02-23
[QUOTE=bman]See...that's what I did....and extracted to that folder.....still using 1.0.7....

so messed up frig[/QUOTE] This part is supposed to fix that: ```
 # First, /usr/bin/firefox
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
``` See, there's a file in /usr/bin called *firefox*. It's not really a file--it's a pointer to the executable for 1.0.7. The first part renames that pointer to be a file called *firefox.ubuntu*. It then makes a link from your new Firefox (the one in /opt) to be the new *firefox* pointer in /usr/bin.

You can do this graphically, too, if you prefer. Try ```
gksudo nautilus
``` in Gnome

 or ```
kdesu konqueror
``` in KDE. 

Go to the /usr/bin directory. Find the file called *firefox* and rename it *firefox.ubuntu*. Then open a new window (control-N) and go to the /opt/firefox folder and middle-click-drag (in Gnome; in KDE you can just drag) the firefox file to /usr/bin and select **link here**. Close both windows.

---

### Post by Coelocanth on 2006-02-23
Bman, I've got to think there's something you missed or messed up with that tutorial. I installed Firefox just last night, using the tutorial, and it worked perfectly (and I'm a noob at this). Not much help, I know, but perhaps you can go over the steps again and see if there's something you missed. I can't see why it wouldn't work for you.

Good luck.

---

### Post by bman on 2006-02-23
Alright I just followed which was last posted by aysiu.....not sure if it worked properly, but the icon in the taskbar and startmenu, I changed the location of where it opens, and it works now. I have them opening up 1.5.....does this mean I can gointo synaptic and remove 1.0.7?

---

### Post by Coelocanth on 2006-02-23
Congrats!

No, I believe the tutorial says **not** to remove the Ubuntu version.

---

### Post by aysiu on 2006-02-23
[QUOTE=bman]does this mean I can gointo synaptic and remove 1.0.7?[/QUOTE] I wouldn't. Part of the tutorial links the new Firefox to your old Firefox plugins. Unless you're hard-up for hard drive space (what is it--10 MB?), then just leave it.

---

### Post by bman on 2006-02-23
Alright, thank you for all your help...if I run into more problems, I'll be sure to come back and ask!

---

### Post by cjm5229 on 2006-02-23
Here's a good place to start[http://makuchaku.info/amnesty/#]("http://makuchaku.info/amnesty/#")
Changing permissions is not something you really want to get in a hurry to do. After you learn the basics of installing programs and find a situation where you have to change permissions it can be done fairly simply from the commandline or from root Nautilus. To browse your folders, Nautilus can be found under "Places" on your top taskbar. Click on Desktop, Home, or Computer and it will bring up a Nautilus browser. You have default ownership of Home and Desktop. you can install some programs right there and make them run, however you are compromising a lot of security that way. I have found that I can bring up root nautilus make the changes I need to, then just close it without changing permissions. Then when it is closed again everything is back where it should be. Again, though, USE WITH CAUTION!
   Now in the Users Guide, if you just have to change permission study "chown" and "chmod".  Try   ```
gksudo nautilus
```, Then after you have reinstalled Breezy for the third time;) (I think it took me four times) go back and read the guide. Good Luck.\\:D/

---

### Post by dvarsam on 2006-02-23
Under the "Customization Tips & Tricks" Page on this Forum:

Read this Tutorial on how to install & backup programs with Synaptic:

[http://www.ubuntuforum.org/showthread.php?t=134914](http://www.ubuntuforum.org/showthread.php?t=134914)

---

