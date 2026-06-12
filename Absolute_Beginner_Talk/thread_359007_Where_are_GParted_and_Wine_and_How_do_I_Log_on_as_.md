---
title: "Where are GParted and Wine and How do I Log on as root?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by rtX on 2007-02-11
Just installed ubuntu on a machine that used to have WinXP on it.  The computer has two smallish HDD's.  I don't think ubuntu has formatted one of them (the second) and I cannot find a graphical partitioning tool anywhere in the menu system.  I read that ubuntu used Gparted to partition on install.  How do I go about invoking it?

Also, how do I log on as root?  When I try as the person who installed it, it says my password is wrong.  If I use the name that I enetered when installing ubuntu, I do not seem to have admin rights (at least when I run a newly installed qtparted).

I also want to have a play around with Wine which I have installed, but cannot see how to invoke?

I really like what I see with ubuntu.

TIA,
rtX

---

### Post by jpeddicord on 2007-02-11
**Gparted:**
This is only available on the Live CD. You can install it from the repositories, but it will not be of much use since the hard drive has to be off (essentially) to change the partitions. Your best bet is to boot up the Ubuntu CD and use GParted from there.

**Wine:**
You can run wine by using the following in the terminal:
```
wine program.exe
```
You can also open the wine configuration editor by using the winecfg command.
Another way to invoke wine is to just double-click on an EXE file, and it should open with wine. Restart your PC after you install wine if it doesn't work on the first try.

**Root:**
Do **not**, not, not, login as root. Any commands you need to do while being root should be prefixed with sudo (if in the terminal) or gksu (if in an application launcher). For example, to open a file manager as root, press Alt+F2 and type:```
gksu nautilus
```

Hope that answerers your questions!

Jacob

---

### Post by rtX on 2007-02-11
> **jacobmp92 said:**
> **Gparted:**
Hope that answerers your questions!


Many thanks - it does.  At the risk of being stupid - how do I open a terminal window?  I have played with Linux before and have always had a menu item that does this and was always able to logon as root, too.  I want to use ubuntu for real and so I shall be more careful than I have when playing before.

rtX

---

### Post by TwistesdTexan on 2007-02-11
Click on <Applications> then <Accessories> then <Terminal>

---

### Post by tedrogers on 2007-02-13
You can also use the root terminal to perform admin tasks...but be careful as you can totally bork your system with a few keystrokes.  With great power comes great responsibility...just do your research and think before you type of press enter!

You may need to enable the icon with MENU LAYOUT (see System > Preferences > Menu Layout), then go to the SYSTEM TOOLS section and check next to ROOT TERMINAL. It should then appear in your Applications > System Tools menu.

If it doesn't show straight away then either restart X (CTRL+ALT+DEL) or run this in a normal terminal.

```
killall gnome-panel
```

This will rebuild the menu's for you and it should appear.

Hope this helps....but please be careful with the root terminal!

On another note, I know there is little point in having gparted installed within ubuntu, unless like me, you have other disks that aren't always mounted that you can work on....but it is also useful just to get some statistical info about your disks, i.e. their size, mount points and so forth.

---

