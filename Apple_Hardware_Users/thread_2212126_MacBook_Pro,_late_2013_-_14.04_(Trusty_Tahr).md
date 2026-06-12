---
title: "MacBook Pro, late 2013 - 14.04 (Trusty Tahr)"
date: 2014-03-19
forum: Apple Hardware Users
---

### Post by karypid on 2014-03-19
Hi,

I recently purchased a late 2013 MacBook Pro and installing 13.10 was a bit of a pain:
[http://askubuntu.com/questions/370583/installing-ubuntu-on-macbook-pro-11-2-11-3](http://askubuntu.com/questions/370583/installing-ubuntu-on-macbook-pro-11-2-11-3)

Does anyone know if the upcoming 14.04 release have the fixes mentioned in the above thread? (efibootmgr when installing boot loader, [FONT=Ubuntu Mono]libata.force=noncq[/FONT] for startup,  sound driver [FONT=Ubuntu Mono]set_gpio_data 1[/FONT], etc)?

The most pain I had was because of [FONT=Ubuntu Mono]libata.force=noncq[/FONT]

I had just finished the install and was running efibootmgr, when I got the "freeze" due to the new SSD in the mac, which basically forced me to have to do an internet recovery (reinstall OS X) and then run the Ubuntu installation again...

With the upcoming 14.04 I was thinking of doing a fresh install, but only if these issues are resolved... Anybody know if this works yet?

---

### Post by bapoumba on 2014-03-19
Thread moved to Apple Users (although I hesitated with Ubuntu +1, but you may get more experienced eyes here).

---

### Post by andy10 on 2014-03-19
I don't know if this will be of any help but... I install both Ubuntu and Xubuntu 14.04 on my mid 2010 MacBook Pro and both ran with out problems. I am now using Xubuntu. I installed using **rEFInd** and placed Grub on the partition with Xubuntu. I fixed the slight heating issue with a cron script I found on-line ([http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/](http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/))  all has been well since. Although, I do not have an SSD drive.

Andy

---

### Post by lael on 2014-03-20
I have a late 2013 Retina MBP.  13.10 is working for me.  I used rEFIt.  I had to disable ncq too.  No iSight support yet. No hotplugging of Thunderbolt Devices.  Audio works, but speakers are missing the bass.  I think I read something about fixes to audio in the 3.13, not sure on the SSD imrprovements or hotplugging thunderbolt devices.

I'm planning on doing a second partition for 14.04 alongside 13.10

---

