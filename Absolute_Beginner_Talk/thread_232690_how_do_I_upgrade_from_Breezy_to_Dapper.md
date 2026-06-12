---
title: "how do I upgrade from Breezy to Dapper"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by david.holland on 2006-08-09
Is there any way that I can upgrade Ubuntu 5.10 to 6.06 LTS?

I would usually backup all my important files/folders and re-install.  However I have invested alot of time downloading additional packages via 56K modem (still quite common in the UK) and I want to avoid doing this again for reasons that are obvious.

Can I simply upgrade to Dapper using the "shipit" CD I've received or do I need to just bite the bullet, re-install and download all non-distributable packages again?[-o<

---

### Post by david.holland on 2006-08-09
If any one is having the same issue as my first post in this thread then see these links for upgrade help:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Not tried any at time of writing but will update post ..

---

### Post by scxtt on 2006-08-09
didn't look @ your links, but if you have a 6.06 disk and you load it in 5.10 - you should be prompted to upgrade - that might be dependent on if the updater is running, but it's possible anyway ...

---

### Post by dckirba on 2006-08-09
Just a quick question along the same lines: I can't install 6.06 from live CD because of RAM restrictions on my computer at work. And I'm having a real hard time downloading the alternate version because we live in dialup. I do have the install CD for 5.10. I read your links and I think this is possible, but just to confirm, can I install 5.10 and then use the internet to upgrade to Dapper? Will this take forever and what happens if I lose my connection while upgrading because that happens a lot here?

Thanks,
David K

---

### Post by scxtt on 2006-08-09
i definitely would NOT try to upgrade from breezy --> dapper via dialup, esp. if it drops from time to time ... you'd have better luck having someone send you a Alt. 6.06 CD ...

---

### Post by david.holland on 2006-08-09
**I am suffering here with dial-up and upgrading**:-({|= 

When I start Breezy and insert the Dapper CD (the "shipit" CD received from Ubuntu) nothing happens other than a nautilus browser shows the CD contents.  Is there no way that Ubuntu can be upgraded like WinXP is with service pack 2?

I have followed the documentation on links above but this seems to require an internet connection (fast internet connection I would suggest minimum of 256K download speed) as dial up would take an eternity.  This is my original point - I am probably better off backing up my important files and doing a fresh install with Dapper and completely replacing Breezy then downloading all the additional non-distributable packages.

If any one knows how to upgrade without needing to connect to the internet please share your knowledge!!

---

### Post by Sef on 2006-08-09
> This is my original point - I am probably better off backing up my important files and doing a fresh install with Dapper and completely replacing Breezy then downloading all the additional non-distributable packages.

I agree with you that is your best option.

---

### Post by Brunellus on 2006-08-09
backup and re-install is your best choice if you're on dialup.  

If you're comfortable/confident with linux, I'd suggest moving towards a multi-CD distro like Debian, where at least you have the software at hand, rather than having to download it.

---

### Post by davebgimp on 2006-08-09
> **david.holland said:**
> 
If any one knows how to upgrade without needing to connect to the internet please share your knowledge!!

You need to boot from that Dapper CD

Or, you can just update your sources list:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

and then run:
**sudo apt-get update**
**sudo apt-get dist-upgrade**

from the terminal.

But, since you already have a cd, just boot from it.

---

### Post by scxtt on 2006-08-09
i'm guessing that the "feature" which will 'auto-recognize' that an upgrade CD is inserted either isn't running or just isn't setup on your breezy install ... possibly the updater that sits in the system tray is what does it, not sure ... you can also add the CD to your /etc/apt/sources.list and do it that way ... do a **man apt-cdrom** for some more info ...

but i agree that a full install of dapper will server you better than an upgraded breezy ...

---

### Post by xander848 on 2006-08-09
I dont have the link offhand but if you have a friend w/ broadband there are dvds that you can download that have the repository pacages on them. I believe that its not an offcial ubuntu thing but try looking for the link on google. That might help if you do a reinstall for dapper.

---

