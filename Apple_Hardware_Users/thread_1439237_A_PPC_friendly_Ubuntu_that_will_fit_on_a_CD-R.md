---
title: "A PPC friendly Ubuntu that will fit on a CD-R?"
date: 2010-03-25
forum: Apple Hardware Users
---

### Post by chonald on 2010-03-25
I want to install Ubuntu on a PPC iMac.  It is running 10.2.8.  

I'm looking for a ppc version of Ubuntu that will fit on a CD-R, the iMac has no DVD reader.  Where can I find this?

Also, I'm not sure how to get the iMac to boot from disc.  It doesn't seem to respond to holding 'c'.  Also, when I hold 'option' during boot up it shows me a screen with a picture of a lock, it wants me to fill in a password, but my user's password won't work.

I feel very very stuck.

---

### Post by RedSingularity on 2010-03-25
In response to your PPC question, any ubuntu release will fit on a CD-R.  Not sure how to boot it on a mac though.  Never owned one.

---

### Post by penguirl on 2010-03-26
You can find instructions on how to make a K/Ubuntu 9.10 installation CD here: [http://ubuntuforums.org/showthread.php?t=1335735](http://ubuntuforums.org/showthread.php?t=1335735)

The padlock you are seeing indicates that Open Firmware has a password. If you did not set it, perhaps you can ask the person who you got the machine from. There is a work around if you absolutely cannot get the password but it involves opening up your iMac.

---

### Post by the yawner on 2010-03-26
> **RedSingularity said:**
> In response to your PPC question, any ubuntu release will fit on a CD-R.  Not sure how to boot it on a mac though.  Never owned one.
Uhm... Afaik, recent Ubuntu releases no longer supports PPC architecture.

edit:
Whoops. I stand corrected. It appears penguirl's link has discounted my claim.

---

### Post by penguirl on 2010-03-26
You are half right. PPC support was dropped by the developers, but it is now supported by the community. I don't know who "the community" is but I sure would like to thank them and buy them a little popcorn!

[CENTER]:popcorn:

[/CENTER]

---

### Post by penguirl on 2010-03-26
> **RedSingularity said:**
> In response to your PPC question, any ubuntu release will fit on a CD-R.  Not sure how to boot it on a mac though.  Never owned one.

Actually the Karmic live CD weighs in at about 706MB, you have to strip either the 32 or 64 bit code (whichever you don't need) to get it onto a CD. Or overburn the CD but I don't have any experience with that.

---

### Post by chonald on 2010-03-26
Okay.  I'm a little farther.

I had to reset the firmware password by taking out the RAM and resetting the PRAM (whatever that is).  I was able to boot from a CD by holding down the "option" key while the computer was booting.

I then got stuck on trying to detect the CD-ROM, but found a work around for that.  I was trying to install ubuntu-8.10-alternate-powerpc.iso but got stuck on "select and install software" at 6%.  This is the next work around I have to figure out.  Right now I'm going to download another iso for the heck of it (ubuntu-8.04.01-desktop-powerpc.iso) and see if that works.

Does anyone have any suggestions for getting past this select and install software section of the install?

---

### Post by penguirl on 2010-03-26
Glad to hear you got past the firmware lock. I had a similar problem installing Kubuntu Karmic but Ubuntu Karmic installed just fine. Maybe if you try the other one and if it does work you can change desktops after you are up and running.

---

### Post by DougieFresh4U on 2010-03-26
> **RedSingularity said:**
> In response to your PPC question, any ubuntu release will fit on a CD-R.  Not sure how to boot it on a mac though.  Never owned one.

I am using Ubuntu Karmic on my iMac and it was 708MB download. I used 'overburn'  on my cd writer  and it worked out great.Booted right up to a working desktop.
I have also been trying to find Lucid Desktop download and they all seem to be 705MB download. CD will hold 700MB.

---

### Post by cascade9 on 2010-03-26
A 10MB overburn on a CD is noramlly OK. 

If your worried about it, you can get 800MB CDs.

---

### Post by DougieFresh4U on 2010-03-26
> **cascade9 said:**
> A 10MB overburn on a CD is noramlly OK. 

If your worried about it, you can get 800MB CDs.
Didn't know they made 800MB CD's, thanks.
Karmic cd with the extra 10MB was the first time I booted to working desktop. Have tried the Lucid cd and machine rejects cd after a few minutes. Have tried 3 different cd's

---

### Post by ibuclaw on 2010-03-26
This: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Regards
Iain

---

### Post by mcduck on 2010-03-26
> **penguirl said:**
> Actually the Karmic live CD weighs in at about 706MB, you have to strip either the 32 or 64 bit code (whichever you don't need) to get it onto a CD. Or overburn the CD but I don't have any experience with that.

That's just the old 1000 versus 1024 thing with the file sizes, the images will actually fit just fine on a normal 700MB CD without overburning. :)

For example the 10.04 Beta 1 CD I happened to have on my desktop shows as 707,9MB. After a more precise look it's actually 707854336 bytes, while a normal 700MB/80min CD has a capacity of 737280000 bytes (in the normal Mode 1 format)..

Also, 707854336/1024/1024 = **675,1 MiB**, which is of course less than the 737280000/1024/1024 = **703,1 MiB** size of the CD. :)

---

### Post by chonald on 2010-03-27
i found this, which is at 691MB:
[http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-powerpc.iso)

---

