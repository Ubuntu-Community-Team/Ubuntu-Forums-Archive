---
title: "Ugh, killed my Ubuntu install"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by wrybread on 2006-11-28
Well I screwed up, a little too much tinkering and now I seem to have killed my Ubuntu install. There doesn't seem to be a "recovery install" for Ubuntu so I guess I'm heading to a reinstall from scratch.

It's a shame, because I think all that really happened is Gnome got corrupted, but no matter what I do it won't reinstall. For example running "sudo apt-get install gnome" returns a bunch of errors about incomplete packages, but "sudo apt-get -f install" doesn't fix anything, and trying to install each package fails. I think things are pretty deeply corrupted, for example even trying to download KDE fails. 

Anyway it's not the biggest deal, at this point I sort of welcome things going wrong since I want to learn how to fix them. So I'm wondering: can I just copy my old Home directory over to the new install? I'm guessing no and I'll need to reinstall the programs, but assuming I reinstall the same apps, will copying over that old Home directory restore my old settings?

Or any other tips on transferring settings from one user to another between installations, which is essentially what I'm doing?

Thanks.

ps- if anyone needs to mount your EXT2 or EXT3 partitions from Windows, this freeware Windows program works great:

[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm#Download](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm#Download)

---

### Post by Sef on 2006-11-28
> So I'm wondering: can I just copy my old Home directory over to the new install? 

Are you reinstalling on the same disk?  If so, then as long as you install to your old Ubuntu partition, you should be able to keep your home directory intact, unless it was messed up by whatever screwed up your Ubuntu.  Just don't reformat your home directory.

---

### Post by CaveRat on 2006-11-28
1. Did you create a Home Partition with your first install?

2. Can you see your Home Folder and it's files from Windows?

---

### Post by Kieranties on 2006-11-28
have you tried the following?
```
 sudo apt-get update
sudo apt-get ubuntu-desktop
```

"ubuntu-desktop" is the bit with gnome in.  of course you could try "kubuntu-desktop" and meddle with kde for a bit

---

### Post by wrybread on 2006-11-28
Thanks for the tips, I'll try them when I get home.

But as far as installing to specific partitions, I'm installing using the Ubuntu 6.10 CD, which boots to a live desktop, and then I'm clicking Install on teh desktop. It's really bare bones, doesn't give me options of where to install or anything like that. Is there a way to get more options?

---

