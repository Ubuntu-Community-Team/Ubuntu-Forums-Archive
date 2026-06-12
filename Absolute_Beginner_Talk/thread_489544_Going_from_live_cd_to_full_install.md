---
title: "Going from live cd to full install?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by brattonr on 2007-07-01
Ok, I have been having an issue installing Ubuntu (server) on my PC.

P4 3.2
2 gig ram
2 SATA 160g hd
Intel PERL mb
Intel 10/100 Pro NIC
ATI X1600 AGP 512 Mb
Sound Blaster Live Gold (or something, I forget)

I created a live CD and that seems to work fine.  I also have booted Knoppix (have used it for a while with file recovery for SATA drives and Windows NTFS file systems) and Slackware.  

All of these work well.  With the Ubuntu actual install I get everything auto-detected and the install finished without errors.  Then on reboot the system locks up at (after?) :

"* Running local boot scripts (/etc/rc.local)"

I've read the beginners sticky post about the Xxxx ATI cards.  But what is messing me up is that the live cd's all work.

Any suggestions?

---

### Post by brattonr on 2007-07-01
Recovery mode works, and I get to a prompt.  The only thing I noted during boot up was:

/dev/sda1: Superblock last mount time is in the future.  FIXED

Other than that everything loaded ok, after the initial file checking since the system did not boot up, or shut down normally.

So, if I can get to the recovery "console" prompt, what do I need to change in the etc/rc.local file to make it boot?  

I'd really like to give the LAMP a try, since setting up MySQL, PHP, and everything separately is time consuming.

/cheers

---

