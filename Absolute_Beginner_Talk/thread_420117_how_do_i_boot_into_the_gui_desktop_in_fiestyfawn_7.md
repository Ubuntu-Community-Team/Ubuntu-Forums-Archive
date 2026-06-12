---
title: "how do i boot into the gui desktop in fiestyfawn 7.04 server?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by darkwarrior on 2007-04-23
Hi all I recently installed fiestyfawn 7.04 , installation went well however being new to linux i am stumped as to how to boot into the desktop, do i have to install additional software to do this?thanks for any help!

I created a root as well as a local user and added that user to a admin group which enables me to login as user@ubunto with administrator credentials....the machine is a p3 1ghz 256mb ram and a compaq 18ghz scsi hd, adaptec 2940 ultra scsi card, 52x cdrom.

the installation manual tells me how to install the desktop but not how to start it..any help would be much appreciated!! :confused:

---

### Post by Rinzwind on 2007-04-23
Server doesn't come with a desktop.

But if you want gnome:
sudo apt-get ubuntu-desktop
And if it's KDE
sudo apt-get kubuntu-desktop

and it'll install your GUI.

If you allready did this type
startx
from the commandline to get into your GUI 
OR check your 7th screen with: control-alt-F7

---

### Post by Jussi Kukkonen on 2007-04-23
> the installation manual tells me how to install the desktop but not how to start it

Please link to any instructions you refer to, we can't know what manuals you may be following...

I believe installing ubuntu-desktop should make your machine close to a desktop install that should boot straight into gdm -- I'm not sure if that's what you want?

EDIT: Rinzwinds commands are missing the actual command, should be:
```
sudo apt-get *install* ubuntu-desktop
```

---

### Post by darkwarrior on 2007-04-23
[FONT="Verdana"]Hi Jussi Kukkonen, hi Rinzwind  thanks for all your speedy response!, the instructions i made reference to is included with the fiestyfawn server 7.04  ISO image under doc it addresses all  installation issues that one may encounter as a new ubuntu user.

I am still searching for a user manual to get me started, still looking![/FONT]

---

### Post by rich.bradshaw on 2007-04-23
If you are new to Linux then you may find the normal desktop CD easier to get used to... Installing ubuntu-desktop as mentioned above will get you closer to this way of doing things.

What are you thinking of using the server for?

---

### Post by annda on 2007-04-23
here is a very good guide:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

also, i'm not sure about feisty, but in edgy i had to install gdm as well if i wanted to boot straight into X, without the startx command - actually a better idea for a server setup with GUI.

---

### Post by Rinzwind on 2007-04-23
Oops sorry for the mistake!!!
I am such a n00b >:)

---

### Post by darkwarrior on 2007-04-23
HI annda hi rrich bradshaw! to answer rich i use windows server 2000/2003 extensively as well as do design work with visual web developer and sql server 2000/2005, for years friends have told me about linux so i decided to download and try ubuntu!, i tried SUSE linux 10 but somehow the dvd kept getting currupted :c( during downloads  a good friend suggested UBUNTU and so far i like the interfaces i so far seen.

The community spirit is excelent and i really feel gratified at the overwelming responses!!! i am vey impressed!

---

