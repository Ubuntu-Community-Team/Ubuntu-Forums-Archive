---
title: "Help! How do I change from XFree86 to Xorg?"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by [Cyanide] on 2005-08-05
I have no idea what I did lol and now my XServer doesn't work.

I think it's because I'm running XFree86 now instead of XOrg.

When I try to do sudo dpkg-reconfigure xserver-xorg it tells me it's broken or not fully installed.

So I'm stuck at the command line interface and I don't know how to configure my wireless to grab updates/packages...

Any ideas anyone?

---

### Post by DJ_Max on 2005-08-05
Are you using Hoary? If so, how did you get XFree86, it comes with Xorg? If you're using Warty, you wanna upgrade to Hoary.

---

### Post by [Cyanide] on 2005-08-05
[QUOTE=DJ_Max]Are you using Hoary? If so, how did you get XFree86, it comes with Xorg? If you're using Warty, you wanna upgrade to Hoary.[/QUOTE]

I'm using Hoary, like I said I have no idea what I did...

---

### Post by KingBahamut on 2005-08-05
[QUOTE='[Cyanide]']I'm using Hoary, like I said I have no idea what I did...[/QUOTE]
 Lol...sounds vaguely like a little misplaced synaptic fanagaling. 

Youll need to remove the XFree86 Packages, and reinstall Xorg , then reconfigure. 

If you have to do this from CLI, because your Xserver is failing then.......phew, roll up your sleeves. Try to do a 

apt-get remove xserver-xfree86
apt-get install xserver-xorg

Purely guessing of course that you installed the xserver-xfree86 package by mistake or some sort as that.

---

