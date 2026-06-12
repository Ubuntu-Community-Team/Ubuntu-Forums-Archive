---
title: "PowerPC Utilities"
date: 2008-03-31
forum: Apple PPC Users
---

### Post by deamon_knight on 2008-03-31
I'm looking for testing utilities compatable with PowerPCs. Memtest86+ dosen't work. Memtester also is for x86 based systems. Is there a Memtest like utility for Macs?

-Thanks

---

### Post by slacka-vt on 2008-03-31
I'm not sure if there is Linux software to test memory on a PPC but
Every Mac comes with a "Apple Hardware Test" cd which tests CPU, Memory, VRAM, etc.
There is also "Tech Tool" which is software that includes a bootable DVD that tests all the fore-mentioned hardware as well as a bunch of great Disk Utilities.

~s

---

### Post by stream303 on 2008-03-31
Just a quick warning here - if you are running OS8, OS9 etc, and try to use one of these utilities which are based on OSX, and boot it, it may prompt you that you need to upgrade your firmware - and then you're hosed after backing out of it, rendering your display nonfunctional.  Don't clear your pram if you do!

[http://www.macosxhints.com/article.php?story=20050218164736471](http://www.macosxhints.com/article.php?story=20050218164736471)

So be careful and check beforehand which OS it is designed for before putting it into your drive....

Here is a good link for firmware updates if you want to do it...

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

---

### Post by deamon_knight on 2008-04-03
The Problem with The Apple Hardware test and Service Diagnostics is that they suck, they regularly miss failing components. I found a .deb package of memtester for PPC but it says that I need lib6c, but synaptic says that package and the dev package is already installed.

---

