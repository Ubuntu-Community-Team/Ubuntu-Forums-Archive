---
title: "Advice for Home Server Setup with Ubuntu Desktop"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by rphipps1981 on 2006-08-23
Hello all.

I have just recently installed the Ubuntu desktop version onto an old PC and was impressed with the ease in which it was up and running and all the features that it comes with.

I need advice regarding my current home setup - for which I think I need a file server, mail server, maybe print server - I just don't know.

I currently have 2 printers connected to my Wireless Router via Linksys PSUS4.

I have two desktop machines - one running Windows XP with 512mb ram, 2 SATA RAID hard drives (80gb each), AMD Athlon XP (2Ghz)dvdrw. The other has 256mb ram, 5GB hard drive, 1Ghz processor but is runnnig Ubuntu at the moment.

I have two laptops (both over 3 years old)- both running XP (one will be converted to Ubuntu soon).

At present the only broadband wall connection point is in a very unhelpful place so all pcs are connecting wirelessly for internet access & printing.

I am starting to run out of disk space on the 80gb hard drives and am starting to think I need a file server for this. Should i buy a new pc(or server - does it matter?) to setup with Ubuntu desktop (which also acts as the server) for this or should I just be networking and sharing files between them? I am not really comfortable without the GUI that Ubuntu provides with it's destkop version, so am not convinced about setting up the server version - will this matter. (plus I would then like to use the server as a normal pc if possible?)

I also have about 6 email accounts (one hotmail, the others POP3). I would like to receive them all into one inbox. Reply (if possible from the address that I received the email from) but i would like to be able to check all these email accounts from one location when I am not at home. Can I do this? I am assuming the hotmail account will have to be ditched eventually. Is it best to use a paid online mail server company or set up a mail server at home? If so , what do I need for this? I am also currently receiving far too much spam on all the accounts.

Any advice will be more than welcome. I don't know whether I need to buy a new machine, use what I already have, and whether to set up a file server, a mail server (additional or on the same box), a print server (additional or on the same box).

---

### Post by Jussi Kukkonen on 2006-08-23
> Any advice will be more than welcome. I don't know whether I need to buy a new machine, use what I already have, and whether to set up a file server, a mail server (additional or on the same box), a print server (additional or on the same box).

If reliability and not having to fiddle with things constantly is important, I don't think your server should also be a desktop machine (as in constant desktop use). This is just a preference though.

There's definitely no reason to get a new machine if you have any old equipment you can use. Anything that is less than 10 years old is fine, and one machine can easily do everything you mentioned (except maybe the  trickier mail account settings -- I'm not sure they're available at all). 

Setting up a file server is quite easy, especially if you go with NFS. You might not want to do that though, since you have at least one windows machine, I expect samba to be able to handle your printer/file server needs. the wiki has decent how-tos for both nfs and samba. Mail servers tend to be trickier to setup, especially when you start requiring lots of features like spam filtering and secure access from internet -- don't expect any shrink-wrap experience here. I'm not an expert, so someone else has to give some actual recommendations here.

There's no problem using a desktop-version of ubuntu as server, you'll just have a lot of unnecessary cruft running -- this might of course slow things down or make the machine more unstable. 
Something to remember if you decide to set up a server: admining a server remotely is not necessarily only command-line based. You can install and run graphical apps on the server, and have them shown on your desktop machine. See "Forwarding X over SSH".

---

### Post by Iowan on 2006-08-23
[http://howtoforge.com/perfect_setup_ubuntu_6.06]("http://howtoforge.com/perfect_setup_ubuntu_6.06")
Here's a good starting point - there are how-to's on the forum, too.  I have an old 233 MHZ box running as file server.

---

### Post by rphipps1981 on 2006-08-23
With reference to the old computer, surely I would need to buy large hard drives, set up RAID to ensure data is not lost and I always have the worry that the server will break down at any point. Will it also not be too slow being an old machine?

Can anyone confirm whether the desktop version is more unstable than the server version?

I can generally administer the server from its location, it would only be rare occasions to have to do it from another location. 

Do you have any recommendations for email - collecting from six email accounts and replying from one would at least be an option but should this be done by me or should I be paying for this service?

Thanks for the advice so far, it is all helping me understand what I need to do.

---

### Post by Iowan on 2006-08-23
There's an adage that goes something like: "Speed is money - how fast do you want to go?",  and I guess it's all relative.  I also have a '486 acting as a dial-up router (sporting a whopping 200M hard drive).  My network  cards are all 10BaseT.  Setup is generally adequate for _my_ needs, but you may need more.  It's getting harder to find new hard drives <150G. Most of my servers run headless (no monitor/keyboard), I use SSH to connect to them for most of the administrative jobs that need to be done. I haven't built the email server yet - dunno how practical it'd be on a dial-up system.

---

### Post by rphipps1981 on 2006-08-24
So with regards to the use of a file server - I would only need to get one or two large hard drives and thats it?

How slow would it be on a 800MHz machine with 256mb RAM to access compared to say, accessing it on a 3GHZ machine with 512mb RAM or accessing the files locally?

---

### Post by Jussi Kukkonen on 2006-08-25
> **rphipps1981 said:**
> So with regards to the use of a file server - I would only need to get one or two large hard drives and thats it?

How slow would it be on a 800MHz machine with 256mb RAM to access compared to say, accessing it on a 3GHZ machine with 512mb RAM or accessing the files locally?
There should be no real difference (between the 800MHz and 3GHz) in file sharing -- it's really not a cpu-intensive job... The difference between accessing local and remote stuff depends more on the network bandwidth/latency than the server.

---

### Post by FuriousLettuce on 2006-08-25
> **rphipps1981 said:**
> Can anyone confirm whether the desktop version is more unstable than the server version?

The server version and desktop version are no more stable or unstable than each other - they are exactly the same thing, just with different packages installed. For instance, by default the server version doesn't have GDM installed (for GUI) and does have Apache installed. However, the desktop version does have GDM but not Apache. If you wanted to, you could install exactly the same packages on both a server machine and a desktop machine and end up with exactly the same OS - there aren't any fundamental differences (although config files etc are set up slightly differently).

---

### Post by dca on 2006-08-25
Not that this helps, the only thing I've found which could be conjecture because of lack of 'quality' testing...  ubuntu (w/ gui) seemed to run best on PC(s) running at least a PIII 933/1000 MHz CPU w/ at least 256 MB RAM.  The server vers w/o GUI ran fine on an old heap w/ dual 800MHz processors and 256 MB RAM...  That was used as a storage device because rolling that out cost $225 in add'l parts versus $4,500 for a NAS w/ equal HDD space.  All the other lower (Celeron 633, 666, & maybe even lower) worked great w/ Xubuntu...

---

