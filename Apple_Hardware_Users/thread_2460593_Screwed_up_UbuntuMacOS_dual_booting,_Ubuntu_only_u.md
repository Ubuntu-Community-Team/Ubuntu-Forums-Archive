---
title: "Screwed up Ubuntu/MacOS dual booting, Ubuntu only uses half of the RAM available"
date: 2021-04-14
forum: Apple Hardware Users
---

### Post by nugget-of-wisdom on 2021-04-14
I fully installed Ubuntu after screwing up dual booting and now Ubuntu only uses half of the RAM available
I was getting tired of Mac OS and wanted to be able to customize it, so I tried dual booting Ubuntu to check it out.
What I did was flash Ubuntu onto my external usb SSD and then installed rEFInd.
After that I restarted my Macbook Air (Mid-2013 running High Sierra) and landed on the rEFInd boot screen and booted Ubuntu.
So far so good. I chose the live Ubuntu version because I didn't want to fully install yet, and it starts running perfectly, I look around, and then restart to go back to the rEFInd boot screen and then boot Mac OS, but it takes me to the OS X Mountain Lion OS X utility screen, so I decided that I screwed it up and went back to fully install Ubuntu.
After installing it, I start Discord and Chromium for YouTube but the fans start going crazy so I looked to see how much memory there was but it only said 2 GB of RAM was available, even though mine has 6 GB of it.
I looked on the internet how to increase the RAM, but couldn't figure it out. Did I set the partition to 2 GB for Ubuntu and now it's stuck with that forever? Or is there a way to maximize ram usage? Thank you in advance!

---

### Post by CelticWarrior on 2021-04-14
Welcome.

First of all, at first glance you're making a huge confusion about RAM (Random Access Memory). It has nothing to do with partitions, it's made of physical modules and when and if it can be increased it is done by adding or replacing those modules.
And fans also have nothing to do with RAM.

---

### Post by nugget-of-wisdom on 2021-04-14
Sorry I'm only really knowledgeable on software, not hardware.

---

### Post by CelticWarrior on 2021-04-14
> **nugget-of-wisdom said:**
> Sorry I'm only really knowledgeable on software, not hardware.
Right... But you should know, at least, the very basics of hardware specifications of the machine where you're running "the software".

How do you know you should have 6GB RAM? Macs of that vintage used to come with 4, 8 or 16GB (upgradable to 64GB). 6GB is a weird number in this context. The typical combos were 2*2, 2*4 and 2*8...

Where did you get the information about Ubuntu using only 2GB?

What exactly are we supposed to see in that huge screenshot? BTW, don't do that! Please use the attachment feature or upload images to an external host and post the links here. The mods don't like huge screenshots.

---

### Post by nugget-of-wisdom on 2021-04-14
You're right, it's 4GB, I thought it was 6GB.

I got the info from GParted

And I'll remove the screenshot

Is it possible to change to Linux Mint?

---

### Post by CelticWarrior on 2021-04-14
> [COLOR=#000000]I got the info from GParted[/COLOR]


No, you didn't.

Again, RAM is NOT drive space or partitions. Gparted reads, shows and allows management of DRIVES, not RAM.

But please do post (as attachment) a screenshoot of Gparted showing the drive were you installed Ubuntu. That, at least, may give a clue about possible problems or issues derived from non-standard installations.
To get the RAM Ubuntu is seeing you can simply open System Settings > About...

---

### Post by howefield on 2021-04-14
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by grahammechanical on 2021-04-14
When considering system memory (RAM) remember that the operating system loads stuff into memory so reducing the amount of RAM available. Then when we open applications each application also puts stuff into memory and so reduces the amount of RAM available. And then some memory (RAM) is kept available as cache memory.

Ubuntu has a GUI utility called System Monitor. It tells me that of the 4 GB of system memory (RAM) 50% is already used and there is 1.8 GiB of RAM set aside as cache memory.  I have open Firefox and a 48 page LibreOffice Writer document.

There are some text based utilities that we load from the command line that give us information about memory usage. It is not so easy to understand the read out.

```
top
```

> [SIZE=2]MiB Mem: 3809.4 total, 272.1 free, 1679.[/SIZE]9 used, 1857.4 buff/cache

The numbers change all the time as the TOP utility is monitoring the system in real time.

Regards

---

### Post by ajgreeny on 2021-04-14
The easiest way to see how much RAM your machine has is to use the terminal command ```
free -mw
``` which give oitput similar to this
```
              total        used        free      shared     buffers       cache   available
Mem:           7878        1050        2099         285         169        4558        6245
Swap:           947          37         909
```
For the size of partitions you would do better to show us the output of ```
sudo fdisk -l
```

---

