---
title: "Upgrading/no backup's"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by ellgor on 2007-07-04
Hi all,

Moved over to Ubuntu and like what I've found, apart from, I currently run Dapper,6.04? and recently upgraded to 6.10? it ran well and for some reason (xservers) decided not to run. No problem I thought, as I'd read that on the grub screen there are previous options to choose from, which I did and found that they had exactly the same thing wrong with them. 
So I started from scratch with the live CD (dapper) and before I start upgrading (third time) would like to know what I'm doing wrong, or not, as the case may be, also, I have one screen resolution to choose from 640x480 whether I want it or not, which I don't (things dont fit in the screen). I've checked the forums and tried a number of tips including downloading envy , all to no avail, any help at all will be greatly appreciated.

Regards, Ellgor.

---

### Post by cleverselfreferentialname on 2007-07-05
I suggest upgrading to Feisty, it's substantially less buggy.

What's your graphics card, first and foremost?

Running:
sudo dpkg-reconfigure xserver-xorg
will allow you to adjust everything appropriately.

---

### Post by moredhel on 2007-07-05
also, what resolution do you normally run at in windows? Remember to put that into what clever said above^

And I would also strongly recommend upgrading to 7.04 (feisty fawn).

If not that stay at 6.06 (dapper drake) as it is a long term support release, where as edgy eft (6.10) has really been supersceded by 7.04 (feisty fawn)

---

### Post by coolen on 2007-07-05
New kernel upgrades will often produce error with the Nvidia drivers. it's a version mismatch, basically. The drivers were built for the older kernel, and the newer one can't load them...thus, when you try to get your X server to use the nvidia driver, blue screen of useful output!
Upgrade to Feisty. Ubuntu provides Nvidia drivers, so they're rolled out at the same time. That, or keep a very close eye on the version numbers.
Of course, this error with the older kernel's just confusing...try Feisty anyway.

---

### Post by ellgor on 2007-07-06
Hi all again,

Thanks for the responses from you, with regard to my graphics card it's a Nvidia GeForce blah-de blah, as somebody mentioned, doing the Xfiles thing, it has been done it has been meshed with Nvidia's drivers and still nothing's changed?
As for upgrading, I've looked at the specs? for and downloading Feisty, now it says there that the Cd you end up with is not bootable and you will have to make a bootable floppy to get it to run, fair enough if you have a floppy drive, which I haven't and I'm not about to cut a hole in my case to fit one in, any suggestions will be more than welcome.
Lastly, the list in the grub menu, is that right they are supposed to be former/previous version's and should be as they were first entered, and not get upgraded adhoc, comments also welcome.

Regards, Ellgor.

---

