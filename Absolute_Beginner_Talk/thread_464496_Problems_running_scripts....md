---
title: "Problems running scripts..."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Memory.Dump on 2007-06-04
ok so I want to run a stript that was written by somebody very smart on these forums I copied it into a file and saved it as lotrolauncher

here is a listing of the directory and the commands I've attempted I am not srue what I'm doing wrong?

```
memorydump@memorydump-desktop:~/Desktop$ cd Games
memorydump@memorydump-desktop:~/Desktop/Games$ ls
Dungeon Siege 2.desktop  PlaneShift Client.desktop   UrbanTerror40_full.zip
et.desktop               PlaneShift Setup.desktop    urlencode.sh
lotrolauncher            PlaneShift Updater.desktop  Warcraft III.desktop
memorydump@memorydump-desktop:~/Desktop/Games$ lotrolauncher
bash: lotrolauncher: command not found
memorydump@memorydump-desktop:~/Desktop/Games$ ./lotrolauncher
bash: ./lotrolauncher: Permission denied
memorydump@memorydump-desktop:~/Desktop/Games$ sudo ./lotrolauncher
sudo: ./lotrolauncher: command not found
memorydump@memorydump-desktop:~/Desktop/Games$ 

```

---

### Post by pbw on 2007-06-04
Don't know what the script is, but it sounds like all you need to do is change ownership and make it executable.

sudo chown memorydump.users lotrolauncher

chmod +x lotrolauncher

And you should be good to go.

---

### Post by dbott67 on 2007-06-04
Assuming that you've set the script executable, the problem may be 64-bit vs. 32 architecture. Are you running 64-bit? If so, this is from another thread I posted in a few months ago.**  Tintazul** provides the answer at the bottom:

> **dbott67 said:**
> Well, how's this for irony?  I was googling for "folding at home dash bash linux" and got this hit:
[http://ubuntuforums.org/archive/index.php/t-314483.html](http://ubuntuforums.org/archive/index.php/t-314483.html)

Heck, I was evening trying to help the guy (I don't remember doing it though!).  Anyhow, here's what he did to fix it:

> [COLOR=Blue][B][I]Tintazul
December 11th, 2006, 06:24 PM[/I][/B][/COLOR]

Thanks, Dave! Your solution didn't solve the problem, but after much fussing and trying and searching the net, [COLOR=Red]here's the answer - since my architecture is 64-bit, I have to install the 32-bit compatibility library ia32-libs[/COLOR]. It's now working fine! The solution was found on this thread of the Folding Community forum: 64 Bit Linux Needs 32 bit compatibility libraries? [YES] ([http://forum.folding-community.org/viewtopic.php?t=17223](http://forum.folding-community.org/viewtopic.php?t=17223))

The deanhopkins guy who started this thread had the same architecture upgrade, but I don't have MSN to let him know of the solution. He might have figured it out by now.

:D Thank you very much! You've helped someone who's not only fairly new to Linux, but also a virgin in terms of x64 architecture.

-Dave

---

