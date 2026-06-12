---
title: "Only distro that works on my computer! :o"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by Nullibist on 2005-11-01
Morning all, from Sydney, well i've just spent 2 days trying to install SUSE (which was the one i really wanted) and after it destroyed my WinXP partition (presumably by messing with the MBR) i had to reconstruct everything, then tried installing on an empty slave drive but no luck there either (sigh)  I think it didnt like my SATA drive and kept trying to install bootloader to it.  Anyway .......

After some searching i came across Ubuntu and it was up and running in the first install!!  Yay.  It can't seem to connect to my wireless network (i have a WinXP main comp. and an Apple iBook, using an Airport Express wireless router) but i guess what i will do is just go back to my WIRED dlink router for this computer (Ubuntu/XP) and connect the Airport Express also to the wired router so it can "broadcast" for the iBook laptop (which i usually use in the bedroom).

Couple of queries re Ubuntu (sorry for the long post) ... i always understood that there was a separate /root user for admin., am i correct to think that Ubuntu asks me for the /root password every time i try to do an "admin" function, even though i'm in regular user mode, and then lets me do it?  Thats what it seems to be doing anyway (?)

Also, how do i get to access my NTFS partitions which have all my music/video files on them?  The help file suggested i need to use a Terminal to copy certain text in to "mount" them, which i sort of understand means make them visible/accessible within Ubuntu (read only).  Unfortunately and inexplicably "Terminal" was not included with the install CD so i have to reconfigure my routers (as above) to get it :)  Perhaps tomorrow.

Thx for any suggestions.

Nullibist
(Danny)

---

### Post by zerhacke on 2005-11-01
[QUOTE=Nullibist]Morning all, from Sydney, well i've just spent 2 days trying to install SUSE (which was the one i really wanted) and after it destroyed my WinXP partition (presumably by messing with the MBR) i had to reconstruct everything, then tried installing on an empty slave drive but no luck there either (sigh)  I think it didnt like my SATA drive and kept trying to install bootloader to it.  Anyway .......[/QUOTE]
Couldn't help you there, sorry.  I'm not a SuSE guy, having never worked with it.  Someone will be along shortly to fill you in on the why and how.

> After some searching i came across Ubuntu and it was up and running in the first install!!  Yay.  It can't seem to connect to my wireless network (i have a WinXP main comp. and an Apple iBook, using an Airport Express wireless router) but i guess what i will do is just go back to my WIRED dlink router for this computer (Ubuntu/XP) and connect the Airport Express also to the wired router so it can "broadcast" for the iBook laptop (which i usually use in the bedroom).
There's an NDIS wrapper available with a little googling.  It -may- get your wireless working.  It may not.  It's worth a shot at least.

> Couple of queries re Ubuntu (sorry for the long post) ... i always understood that there was a separate /root user for admin., am i correct to think that Ubuntu asks me for the /root password every time i try to do an "admin" function, even though i'm in regular user mode, and then lets me do it?  Thats what it seems to be doing anyway (?)
That's pretty much exactly what's happening.  When it's graphically asking for the root password, it's more or less a GUI frontend to "sudo", super user do, or do something as root.  Ubuntu philosophy is to not ever login as root, but sudo to it as needed.

> Also, how do i get to access my NTFS partitions which have all my music/video files on them?  The help file suggested i need to use a Terminal to copy certain text in to "mount" them, which i sort of understand means make them visible/accessible within Ubuntu (read only).  Unfortunately and inexplicably "Terminal" was not included with the install CD so i have to reconfigure my routers (as above) to get it :)  Perhaps tomorrow.
To access an NTFS drive:
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```
Assuming that the NTFS partition is the first partition on the first drive.  This will make the NTFS partition available at /media/windows on your computer.  You will be able to read from it but not save to it.
To get to a terminal, right click the gnome desktop.  It's in the menu.

If you would rather not enter that command in every time you boot Ubuntu, there is a way to make it automount at boot using fstab, but this requires a little bit of mucking with a text editor as root and I'm not sure you would be comfortable with that yet.  If you are, let us know, someone will show you what to do.

---

### Post by Nullibist on 2005-11-01
Thanks for the reponse!  I gave up on wireless for the time being, anyway this main computer sits on the desk all the time so it may as well be wired.  I just connected it all up and we're online with Ubuntu :)  Yes i had seen that info before re the text to allow access to NTFS drives (in the help files somewhere).  Since I now have my internet going (combo wired/wireless), i just tried to install Terminal.  Went to Add Applications, found it, it downloaded and installed fine, and told me it was available in Applications - System tools.  But when i try to run it it fails, saying:  [Error.  Cannot Launch Entry.  Details:  Failed to execute child process "Terminal" (No such file or directory)]  Hmm.  Since i've only had this install up for a day, perhaps i should just reinstall and choose the s/ware packages along the way making sure to get Terminal (?)  Its odd that its not there by default though, since it seems rather important.  Or am i missing something?

---

### Post by pelle.k on 2005-11-01
Are you sure you didn't uninstall terminal or something? It really should be present at a default install. either way, you can get a command prompt/terminal by using alt+f1 alt+f2 and so on...

I like to use nano for files editing. just ctrl+x to quit it, it asks you if you wanna save the changes you've made.

Other things to know is when you are navigating through file system, ls - lists directory, mkdir - make dir (if you want to make a folder to mount stuff in e.g.), the tab button acts as a search/list as win xp does in dos. try writing "/etc/netw" and hit tab it will list, possible matches or if there's only one match it will fill in for you.
"cd /" will place you in the root. "cd .." will back up.

I think you should fiddle a bit more with everything and when you feel more comfortable, then do a clean, fresh install.

---

### Post by matthewv on 2005-11-01
Terminal should be installed by default, in Applications --> Accessories

---

### Post by Mustard on 2005-11-01
Just reading through this thread I noticed that you asked if the 'root password' is entered when you use a sudo command and a password is asked for.  The password it is looking for is your user password.  Your user password will only work, if your user has been given sudo privileges. The root password is disabled in a default install, so basically there is no root password.

In a default install of ubuntu, the first user created is given sudo privileges.  In the expert install of ubuntu, it actually asks you for a root password, then sets up a user at a latter stage of the install process, but that user won't have sudo priviliges straight away.  Sudo privileges will need to be assigned to the user by the root account, using the visudo command (a command that specifically edits the /etc/sudoers file and checks the syntax before it exits).

For a more elaborate explanation of root and sudo try this page in the wiki...

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

For additional help, you have the ubuntu wiki site, which is constantly updated with the most relevant information, and there is also an ubuntu support channel on the irc.freenode.net server in #ubuntu.  I would highly recommend the IRC help, as its where I have learnt the finer points of using ubuntu ie How to not break my system when fiddling with it. :)  Linux is a powerful and very flexible operating system, but that power and flexibility can sometimes backfire on you when you execute a command incorrectly.  The trick is to read first, think carefully second, and thirdly proceed with caution. ;)

---

### Post by Nullibist on 2005-11-02
Yes, just saw it there (under Applications - Accessories), and ran it ... funny though that it was listed as uninstalled under "add applications" and when i installed it from there, it said it could be found under Applications - System Tools.  Hmm.  Anyway, as long as its there...

[QUOTE=matthewv]Terminal should be installed by default, in Applications --> Accessories[/QUOTE]

---

### Post by Nullibist on 2005-11-02
[QUOTE=Mustard]Just reading through this thread I noticed that you asked if the 'root password' is entered when you use a sudo command and a password is asked for.  The password it is looking for is your user password.  Your user password will only work, if your user has been given sudo privileges. The root password is disabled in a default install, so basically there is no root password.

In a default install of ubuntu, the first user created is given sudo privileges.  In the expert install of ubuntu, it actually asks you for a root password, then sets up a user at a latter stage of the install process, but that user won't have sudo priviliges straight away. 
[/QUOTE]

Well i did the 'default' install and it never asked me for a /root passwd and there's only 1 user (me), so i guess *someone* has to be able to do admin. stuff so it allows me to do it with the user passwd.  Certainly i've gone nosing about in configuration settings (without changing anything) and its asked me for the passwd and then allowed me. 

[QUOTE=Mustard]
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")
[/QUOTE]

Bookmarked ... thx.

[QUOTE=Mustard]  The trick is to read first, think carefully second, and thirdly proceed with caution. ;)[/QUOTE]

Sounds reasonable.  The thing i find most unnerving  is all these folders / files with names that mean nothing to me:  var, etc, lib, and so on.  It'll take quite a while to get familiar with it.

---

### Post by pelle.k on 2005-11-03
Trust me, i'm a beginner just as you are - these strange files / folder really do make a LOT of sense when you get used to it. You'll get the feel of it. Usually config files is somewhere in /etc, logs often in /var, your own files in /home (as well as the desktop) and the list goes on... hope you get the picture.

I would say for most everyday tasks you wont have to use the terminal very much, but the same goes for windows as well. The funny thing is linux isn't that complex, but you are so used to the way things are done in windows you get confused with something completely new.

I guess you could say driving a stick-shift car for the first time might not seem as easy as driving an automatic, but man, when you get used to it it's not very hard at all and it has its advantages.

---

