---
title: "Upgrading Ubuntu WITHOUT internet connection!"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-29
Hi, I'm trying to upgrade my Ubuntu to Dapper/Edgy.

There is a problem though:
The computer that has the old version on it doesn't have a internet connection ( wireless driver missing, tried installing it, didn't work because it says chmod configure though there was no configure file on the CD. )

SO, I have a Dapper live CD. No internet connection.

Changed the repositories to only the cd, did so, keep on getting the message that it couldn't download anything from it, though icon with the name is directly on the desktop.

SO, I tried the live CD, it has to format and won't just upgrade when I click the "install" button.

Anyways, is there any way to upgrade to Dapper using **_ONLY_** the CD ?

---

### Post by Sef on 2006-10-29
> Anyways, is there any way to upgrade to Dapper using ONLY the CD ?

Generally no. You have to finish the upgrade via the internet.  The only way I know of getting around that is having someone send you a disk with other packages that are needed to be upgraded.

---

### Post by Ryupower on 2006-10-29
> **Sef said:**
> Generally no. You have to finish the upgrade via the internet.  The only way I know of getting around that is having someone send you a disk with other packages that are needed to be upgraded.

OK, I'm using a different computer that has a cd burner. So what does this method require me to do? :)

---

### Post by PPAAUULL on 2006-10-29
Can't you upgrade with the Alternative disk without an internet connection?

---

### Post by Sef on 2006-10-29
> Can't you upgrade with the Alternative disk without an internet connection?

That does not have all the packages required to complete an full update.

> So what does this method require me to do?

Here are the [packages]("http://packages.ubuntu.com/"). However, I don't fully know what ones to tell you to download except for the obvious one. (I think it is obvious.)  Someone else will have to tell you what packages to download.

---

### Post by Bartender on 2006-10-29
> **Ryupower said:**
> The computer that has the old version on it doesn't have a internet connection ( wireless driver missing, tried installing it, didn't work because it says chmod configure though there was no configure file on the CD. )
I'm not sure I understand your situation, but can you skip the wireless stuff and just plug into the modem directly?  I guarantee you that doing what you want to do online is going to be much easier than the alternatives, such as trying to build an update CD.    Heck, dragging your PC halfway across town to school, the library, a friend's house, whatever you gotta do, would be easier!

---

### Post by AgenT on 2006-10-29
> **PPAAUULL said:**
> Can't you upgrade with the Alternative disk without an internet connection?
Yes you can and there is even an option called something like "Upgrade" if I remember correctly. The problem being, of course, is that this CD *only* has what you need for a fresh install. This means if you have any other extra packages that you installed, there is a good chance that they will not be upgraded. There is also the chance that you may also end up with package conflicts until you resolve them by installing the needed upgradable packages. There is also the chance that everything will go well. And no one can tell you what packages you need because no one knows what packages you currently have installed.

The Desktop CD (default download) is just for fresh installs and LiveCD usage. For anything else it is no good.

Here is the description of the Alternate CD taken from Ubuntu download page (I have highlighted what is important):
**Alternate install CD**
The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:[LIST]
[*]creating pre-configured OEM systems;
[*]setting up automated deployments;
[*]_***upgrading from older installations without network access;***_
[*]LVM and/or RAID partitioning;
[*]installing GRUB to a location other than the Master Boot Record;
[*]installs on systems with less than about 192MB of RAM.[/LIST]

---

### Post by Ryupower on 2006-10-29
> **AgenT said:**
> Yes you can and there is even an option called something like "Upgrade" if I remember correctly. The problem being, of course, is that this CD *only* has what you need for a fresh install. This means if you have any other extra packages that you installed, there is a good chance that they will not be upgraded. There is also the chance that you may also end up with package conflicts until you resolve them by installing the needed upgradable packages. There is also the chance that everything will go well. And no one can tell you what packages you need because no one knows what packages you currently have installed.

The Desktop CD (default download) is just for fresh installs and LiveCD usage. For anything else it is no good.

Here is the description of the Alternate CD taken from Ubuntu download page (I have highlighted what is important):
**Alternate install CD**
The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:[LIST]
[*]creating pre-configured OEM systems;
[*]setting up automated deployments;
[*]_***upgrading from older installations without network access;***_
[*]LVM and/or RAID partitioning;
[*]installing GRUB to a location other than the Master Boot Record;
[*]installs on systems with less than about 192MB of RAM.[/LIST]

It's OK if the other packages don't get upgraded, it's just the OS I wanna upgrade.
Thank you :)

Thanky you all!

---

### Post by AgenT on 2006-10-29
> **Ryupower said:**
> It's OK if the other packages don't get upgraded, it's just the OS I wanna upgrade.
Thank you :)

Thanky you all!
Good luck with everything! 

If you have questions, just post again with your specific problem. Also, if that problem pertains to some category that is available under the Support category, post there. For example, there is the "Hardware & Laptop" category, the "Netwoking & Wireless" and many more. Posting in a specific category will usually yield best results.

You can also try using [IRC]("https://help.ubuntu.com/community/XChatHowto") for live help. Useful if you need help right away, but sometimes the forum may be a better place.

---

### Post by unlokia on 2006-10-29
Hi there - I shall be happy to supply *ANYONE* within the UK, with ALL needed media for Ubuntu, for the cost of my time plus the cost of the media and postage. This set is:

The Ubuntu Edgy Eft Desktop i386 CD
The Ubuntu Edgy Eft Desktop i386 ALTERNATE CD
The Ubuntu Edgy Eft Desktop i386 DVD

Should you wish to buy these, I can only accept cash or postal orders, but the charge is a very modest £5.

Let me know, should you require this service. It as a great pity for non-broadband Ubuntu users, to miss out on a working system.

Regards, Matt :)

---

### Post by Ryupower on 2006-11-05
Thanks people!
and...PROBLEM SOLVED! ^^

---

### Post by Bartender on 2006-11-05
What'd you do?

---

