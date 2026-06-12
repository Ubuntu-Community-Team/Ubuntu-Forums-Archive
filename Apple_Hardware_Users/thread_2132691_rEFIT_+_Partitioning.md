---
title: "rEFIT + Partitioning"
date: 2013-04-05
forum: Apple Hardware Users
---

### Post by d4m1r on 2013-04-05
Hey guys, need some advice from some of you OS X experts....Basically, I  want to run a triple boot setup (OS X, Windows 7, and linux). To do so,  I know I need to partition my HDD and that is my 1st question. I  currently only have 1 partition and OS X is installed on it, what built  in app can I use to divide up my 1 internal HDD into 3 parts?

So, after getting my partitions up, should I install rEFIT or Windows 7  first via Bootcamp Assistant? Basically, I am going to guess the path  will look something like the below but I don't know how rEFIT fits in  given Windows 7 usually installs its own boot manager (MBR) and so does  linux (GRUB)....

OSX->partition disk in 3 pieces->install rEFIT->install windows 7->install linux

And then at boot, rEFIT would display everytime and I could pick into which OS to go into, correct? Thanks in advance guys!

---

### Post by este.el.paz on 2013-04-06
> **d4m1r said:**
> Hey guys, need some advice from some of you OS X experts....Basically, I  want to run a triple boot setup (OS X, Windows 7, and linux). To do so,  I know I need to partition my HDD and that is my 1st question. I  currently only have 1 partition and OS X is installed on it, what built  in app can I use to divide up my 1 internal HDD into 3 parts?

OSX->partition disk in 3 pieces->install rEFIT->install windows 7->install linux

And then at boot, rEFIT would display everytime and I could pick into which OS to go into, correct? Thanks in advance guys!

@d4:

I have answered a few people about this almost exact question a few times, so you might find it if you look.  I used the approach described by "rodbooks" to set up a dual boot system, you could google that for more details.  rEFIt is something that "synchronizes" the different partitions, so that they work, there is also rEFInd, which is newer.  Rodbooks suggests using bootcamp to cut up the disc, but I found that once you go that way it can't be changed; I set up two partitions but now I wanted three, but BC has locked the disc--I'll have erase everything and start over if I want 3.  I saw other people saying they used DU to set up their partitions; rEFIt can be installed before that into the OSX system; then perhaps Windows; then install Linux--from OSX DU the space for Linux could be set as "free space" . . . and then choose "install Linux into largest free space" . . . .  Then, BEFORE booting the linux install, reboot into rEFIt and tab through to the (can't remember) the "terminal" lookiing icon and select "synchronize partitions" and let it do its thing.  Then you should be able to reboot into Linux . . . the Ubuntu flavors seem to install pretty cleanly.  The only issue with the "triple boot" thing is that the linux system sets up at least three partitions itself (hoome, swap, boot), and sometimes the more partition thing is supposed to maybe be a problem.  You could always run Windows in Parallels or VMFusionware and just install Linux in another partition, or even run everything in Virtual from OSX?

e.e.p.

---

### Post by d4m1r on 2013-04-07
For anyone else interested, I was successfully able to triple boot my 2012 13" MBP with OS X 10.8.3, Windows 7 x64, and Ubuntu 12.04.02 x64 using the  below linked guides. It was fairly tricky and especially time consuming but it does work! Now with reFIT, I get a prompt and can boot into either three OS's :)

[http://www.lifehacker.com.au/2010/05/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/](http://www.lifehacker.com.au/2010/05/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/)

[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)

Note: I installed both Windows 7 and Ubuntu via MBR and NOT EFI. Possibly might work under EFI as well but I haven't personally tried it. Went with MBR for simplicity but I don't know if installing them via MBR and not EFI has any benefits **or** downsides for that matter....

---

