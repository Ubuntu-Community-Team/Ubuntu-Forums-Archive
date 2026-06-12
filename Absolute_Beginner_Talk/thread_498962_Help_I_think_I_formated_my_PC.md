---
title: "Help I think I formated my PC"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by loomee on 2007-07-12
I installed ubuntu 7.04 and when I ran the installation I clicked on GNOME format then I got an error message so I decided to leave that section and proceed with installation. I was able to install ubunto which I am using right now to write this query. The problem is my windows OS is gone, I can not access it,all I see is disk1 in the desktop with an empty 73GB storage which is the size of my HD. My question is, did I really lose my windows OS and all my files? and is there away to restore or recover my OS and files?

I would appreciate any help.

---

### Post by Cappy on 2007-07-12
testdisk:
```
sudo apt-get install testdisk
```

Then you can run ```
photorec
```
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Anything that has been overwritten will be unrecoverable.
Also, you'll have to recover any files to something other than your hard drive to avoid overwritting other data.
If PhotoRec doesn't work you may look for a commercial solution.

---

### Post by loomee on 2007-07-12
> **Cappy said:**
> testdisk:
```
sudo apt-get install testdisk
```

Then you can run ```
photorec
```
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Anything that has been overwritten will be unrecoverable.
Also, you'll have to recover any files to something other than your hard drive to avoid overwritting other data.
If PhotoRec doesn't work you may look for a commercial solution.

Thank you for your reply, I did what you told me to do and then I typed Photorec and I got a window that said, no harddisk is found, you need to be root to use photorec, how can I go to root, I am very newbie and I installed ubuntu about 6 hours ago.

---

### Post by marsmissionaries on 2007-07-12
sudo photorec

---

### Post by Inxsible on 2007-07-12
Do a ```
sudo photorec
``` EDIT: Too late :rolleyes:

---

### Post by loomee on 2007-07-12
Thank you guys, 

Though it's a bit too complicated for me but I hope  it works, all my company data  resides on the lost OS ..

I ran Photorec and it's telling time  for achievement 3h37min, so I'll have to waint and see

---

### Post by xpod on 2007-07-12
> Though it's a bit too complicated for me but I hope it works, all my company data resides on the lost OS ..

i`m really sorry to hear your woes and i hope you recover your date BUT............

Why the hell did you try messing about with new operating systems you admit you dont understand on a computer with all you companys data on it???????????

Without backing up too it`ll bet????...ARHHHH:lolflag:
I dont backup myself but then i could`nt give too hoots if it all goes pearshaped.

Sorry but i just never ceases to amaze me how many folks try this stuff on important machines only to wipe everything during partitioning.
At least you aint blaming Ubuntu itself as many do.

Good luck regardless

---

### Post by loomee on 2007-07-12
> **xpod said:**
> i`m really sorry to hear your woes and i hope you recover your date BUT............

Why the hell did you try messing about with new operating systems you admit you dont understand on a computer with all you companys data on it???????????

Without backing up too it`ll bet????...ARHHHH:lolflag:
I dont backup myself but then i could`nt give too hoots if it all goes pearshaped.

Sorry but i just never ceases to amaze me how many folks try this stuff on important machines only to wipe everything during partitioning.
At least you aint blaming Ubuntu itself as many do.

Good luck regardless

Well, you're right, I should not play around with fire blind folded, and no, I am not blaming Ubuntu for my own stupid mistake. I guess sometimes we only learn the hard way. But tell me, is there away to retrieve my drives?

Photorec has finished due to limitation of space and I dont want to just restore data where I have no idea where it will reside or if it's going to replace other files.

---

### Post by hyper_ch on 2007-07-12
Hmmm, do you have a second harddrive or can you borrow one?
It is better to not touch the formatted drive because the more you use it, the less likely you can recover anything...

---

### Post by loomee on 2007-07-12
> **hyper_ch said:**
> Hmmm, do you have a second harddrive or can you borrow one?
It is better to not touch the formatted drive because the more you use it, the less likely you can recover anything...

No, actually I am using a laptop, but is there away to uninstall Ubuntu and try fdisk?

---

### Post by dfreer on 2007-07-12
> **hyper_ch said:**
> Hmmm, do you have a second harddrive or can you borrow one?
It is better to not touch the formatted drive because the more you use it, the less likely you can recover anything...

Yep. Your best bet for now is to grab a Linux Live CD, and use that to use the internet while you try to get your data recovered (DON'T INSTALL again, lol). Or another computer.

---

### Post by Cappy on 2007-07-12
You'll need to hook up a external or internal hard drive unless you have a USB disk (or ipod) with enough space.

I've used a program called R-Studio in the past and it worked really well but it costs $$$ =(
Basically if you do need to use another program don't get one that says "Undelete" since you need something with "Recovery" in the name such as "Partition recovery", etc.

Wiping Ubuntu would make your situation worse .. and fdisk isn't going to do crap

You should really get off your partition's Ubuntu though, and use the Live CD Ubuntu to prevent further damage to your files.

---

