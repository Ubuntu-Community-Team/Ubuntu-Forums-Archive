---
title: "Upgrading To Dapper"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-06-06
Hi,

I'm just thinking about upgrading to dapper (I haven't the time to do it beforehand) but the problem is I'm worried about all my personal files.

I don't have another computer of external hard drive that I can transport all my files onto and I was wondering what would happen when I upgrade? 

Will everything be fine?

Also, what happens to all the programs that I have installed? 

Will they continue to work fine or will they all be uninstalled?

Many thanks

---

### Post by glotz on 2006-06-06
There's no guarantees... What kind of partitioning scheme do you have and how full are your disks? Your installed programs will remain. At least mine did...

---

### Post by dueyfinster on 2006-06-06
It depends on what options you choose at the partitioning stage. You could try use a Gmail account and the Gmail Storage extension for firefox to backup files. 

What I'd recommend is booting to the live disc, install gparted, partition your drive and copy over your files (/home directory), then reinstall on the partition where the old files are located. Alternatively you could just upgrade Ubuntu, which can be done by editing  /etc/apt/sources.list (command: sudo gedit /etc/apt/sources.list) and changing every instance of warty/hoary/breezy to dapper, then type (command: sudo apt-get update) and (command: Sudo apt-get upgrade)

Best of Luck!

---

### Post by Dr Von Bon Bon on 2006-06-06
I don't have any partitions, it's just one drive without windows or anything else.

A lot of the files are too big to really put anywhere as they are films and such.

What is the chance that if I upgrade it will be lost?

I was going to just upgrade it though the update manager, not a disc or anything.

---

### Post by Kilz on 2006-06-06
[QUOTE=Dr Von Bon Bon]I don't have any partitions, it's just one drive without windows or anything else.

A lot of the files are too big to really put anywhere as they are films and such.

What is the chance that if I upgrade it will be lost?

I was going to just upgrade it though the update manager, not a disc or anything.[/QUOTE]
It depends on how much customization you did to the present install. The more you changed the greater the chance. Backup what you can just to be safe.

---

### Post by Dr Von Bon Bon on 2006-06-06
I haven't done that much.

I changed the themes around, I've installed some random things but it's not that I'm overly worried about, it's all my documents, music and videos.

---

### Post by aysiu on 2006-06-06
Upgrading will not affect your files.

It might affect a few global settings (preferences for the login screen) but not any of your personal settings.

You may also end up with your X (graphical) server not working, so consider that you may have to do some troubleshooting from the command-line.

But if you do an upgrade (as opposed to a clean reinstall), there's no chance your personal files will be deleted or corrupted.

---

### Post by Dr Von Bon Bon on 2006-06-06
Oh that's a relief.

As long as I can get help for whatever goes wrong that's cool.

---

