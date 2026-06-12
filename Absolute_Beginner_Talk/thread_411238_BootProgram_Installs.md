---
title: "Boot\Program Installs"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Mike38 on 2007-04-16
Hey all,

  I'm an extreme newbie to Ubuntu, like 2 weeks,  I have 2 problems and 1 question.

The first problem should be solved easy enuff for most of you but I can't figure it out,  I upgraded to windows xp (Partioned HD, That took a week alone!),  And of course when I went to reboot the grub had vanished and windows booted, so for the last three days I've been hunting on how to restore the grub,  Found it here (From a google search),  SSSOOOO I restored grub rebooted and got an Unable to mount HD,  So I looked at what it was trying to do (Edit Command from boot menu)  and it was trying to boot of of HD0,6 and my System was at HD0,5,  So I figured simple enuff I'll just change it and boot,  well it worked,  the problem is,  now everytime I boot up I have to change it,  I looked in the boot directory and cant find the settings there I tried removing the "Quit" in the boot seq. so it would go to save default no go,  anyone know how to set it so it stays???  And I did the "setup (hd0,5)" and all that correctly still doesn't change it tried 3x......

Second Question:  In the time I actually have the system up I've Installed a few programs thru Add\Remove and the SPM and at least 6 or 7 times now I've installed something and the system says it's installed but I can't find it anywhere,  Example I installed Test Disk today from SPM and It is no where on the system that I can find, Applications, System-Preferances\Admin, And the system reported It installed fine.....

And a really newbie question How do I know what version of Ubuntu I'm running bootup says 6.12 but I saw a 7.01 somewhere round here,  and would like to upgrade to that if possble....

    Thanx for any help folks,  I plan On Eventually trying to make this my main operating system,  But I've been on windows since 3.1 so It's kinda hard learning all this new stuff,  Heck just found out today that "Terminal"  was a command line program runner,  Not a "Terminal" to get on tel-Net:D 

Anyway anyhelp,   Thanx\

                                             Mike

---

### Post by mips on 2007-04-16
Will get a better response here, [http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

Maybe ask a mod or staff to move your post for you.

---

### Post by Perfect Storm on 2007-04-16
Moved.

---

### Post by freebird54 on 2007-04-16
Well - we can start by getting it default to boot what you want.  You need to edit the file /boot/grub/menu.lst like so: (   that's LST not 1ST)

```
gksudo gedit /boot/grub/menu.lst
```

change the (hd0,6) to (hd0,5) if that's what's needed, then save and exit. Next boot, should be there.  Here's link with lots of info for you on how grub (and other things) work.  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

When you try to run those programs from terminal do they run?  Many programs end up in your /home/*<yourname>*/progname  directory - so that is the first place to look.  There is an option in the graphic 'explorer' (called Nautilus) to show hidden files (under the view menu) - that may well bring them into sight.  Linux uses any file or dir name that begins with . as a semi-hidden file.

Hope that gets you going - there is LOTS of info out there.  here's another link to useful info  [http://kyle.monoperative.net/cheat.html](http://kyle.monoperative.net/cheat.html)  and don't forget that Firefox has bookmarks to the Ubuntu docs and Wiki for even more stuff.

Enjoy...

---

### Post by Mike38 on 2007-04-19
Ok Thanx alot for the help I'll give it a try now and do some reading in the morning.

---

