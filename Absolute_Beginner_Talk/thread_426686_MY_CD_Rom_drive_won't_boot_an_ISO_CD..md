---
title: "MY CD Rom drive won't boot an ISO CD."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-28
**Problem**:
I am trying to boot a LiveCD ISO to look at Linux Puppy. Just interested in seeing what it has to offer.

When I do a cold or warm boot with the LiveCD inserted in the CD Rom bay, the drive light will light but nothing happens. After a moment, GRUB comes up on screen.

**Inquiry**:
How can I make my CD Rom drive bootable again? I started having this problem several days back. I can get Window's programs to work. I can't get Linux programs to work.
Note:
I downloaded: puppyoffice203ce.iso
I used GnomeBaker to burn the ISO to CD at 2X speed.

**Three Questions**:
1. Is there a way to format a CD from GnomeBaker to clear the CD of its contents? I see where you can format a DVD using GnomeBaker. Do I use that to format a CD?
2. I can't get "Erase CD" in GnomeBaker to work either. Do you expect a bad CD-R/RW player or a bad CD disk? They are new CDs. I also tried several Live CDs.   Unused. It is also a R/W CD.
3. What is the Terminal command to md5sum the ISO? I thought I knew it. So far, I've not been able to get it to work. The file is on my desktop. I first do a cd Desktop.

**Summation**:
I hope that I have asked the right questions.
Any suggestions will be appreciated.
kh

---

### Post by taurus on 2007-04-28
Did you look in the BIOS to make sure you have CD-ROM as the first option in the boot loader?  Also, did you burn that ISO file as an image file, NOT a data file.  On other words, if you look at the contend of the CD and you see one large file, then you have burnt it wrong.

And if you burnt it to a CD-R, then there is nothing else you can do about the CD since it's not a writable.  Therefore, if you want to write on it again, you need to use CD-RW.

---

### Post by kittyhawk63 on 2007-04-28
> **taurus said:**
> Did you look in the BIOS to make sure you have CD-ROM as the first option in the boot loader?  Also, did you burn that ISO file as an image file, NOT a data file.  On other words, if you look at the contend of the CD and you see one large file, then you have burnt it wrong.
And if you burnt it to a CD-R, then there is nothing else you can do about the CD since it's not a writable.  Therefore, if you want to write on it again, you need to use CD-RW.

I burned the "image."
I have the CD Rom set up as "first" to boot.
I mentioned that this is a "CD R/W" disk.
Thanks for your reply.

By the way, Nautilus doesn't recognize that I have a disk in the drive.
kh

---

### Post by taurus on 2007-04-28
Have you tried that CD with another computer to see if it's bootable?  Otherwise, look at the CD to see if you see a bunch of files and directories.

---

### Post by kittyhawk63 on 2007-04-28
> **taurus said:**
> Have you tried that CD with another computer to see if it's bootable?  Otherwise, look at the CD to see if you see a bunch of files and directories.

I have two CD Rom drives. It won't boot on either. Maybe the burn was bad. So, I have been trying to get another burn. No success. It may be Linux. I will go into WinXP and do a burn there and see what happens. That is what I have had to do before. It seems that Linux may not like my CD Rom players. Is that possible?
kh

---

### Post by taurus on 2007-04-28
I've never used GnomeBaker since I always use k3b if I want to burn something.  I assume you don't have another computer to test the CD to see if it is bootable?

---

### Post by SoloSalsa on 2007-04-28
> **kittyhawk63 said:**
> I can get Window's programs to work. I can't get Linux programs to work.
So, you **are** able to burn properly from Windows, but **not** from Ubuntu?  Or does the CD not work, no matter how you burn it?
If the CD does not boot, no matter where or how you write it, then the BIOS was likely reset.  Ask us how to fix that.
Or, if you happen to have Windows left, and give up writing, and your machine has decent specifications, you might like to try Puppy as a virtual machine.  I know where you can get a virtual machine of Puppy Linux free, and all in less than 100 MiB.  I run it from a flash drive on all the Windows machines at school.

---

### Post by kittyhawk63 on 2007-04-28
My neighbor across the street has a CD Rom player. I can test the LiveCD on his machine. Yes, I can burn without any problems in Windows. That burns me. lol. I know BIOS is OK. I checked it repeatedly yesterday. Yes give me the URL of the Puppy you referred to.
I will try the burner you suggested Taurus.
Thanks guys.
I hope I covered everything.
kh

---

### Post by osxdude on 2007-04-28
Have you tried redownloading the ISO? Maybe it was a bad download.

---

### Post by SoloSalsa on 2007-04-28
> **kittyhawk63 said:**
> It seems that Linux may not like my CD Rom players. Is that possible?
Yes.  It is somewhat uncommon, but sometimes drives have nasty firmware that is undocumented.  Or, Feisty may have automatically incorrectly set up your drives.  Or you might need drivers for the chipset.  This actually happened to me once, and only the primary channel worked.  The board used software raid, so the chipset only worked properly for Windows.  I no longer have it.

I realize from your signature that the virtual pc will not work too well.  But you could try it.  Moka5 makes a free 'live pc' manager based on VMWare.  Get it here: [http://www.moka5.com/products/getstarted.html](http://www.moka5.com/products/getstarted.html).  Then, get the Puppy image here: [http://www.moka5.com/node/763](http://www.moka5.com/node/763).

---

### Post by kittyhawk63 on 2007-04-28
> **osxdude said:**
> Have you tried redownloading the ISO? Maybe it was a bad download.

Yes, I did. I was trying to run md5 on it. Couldn't get it to work. It worked yesterday when I tried it on Feisty.
kh

---

### Post by kittyhawk63 on 2007-04-28
> **SoloSalsa said:**
> Yes.  It is somewhat uncommon, but sometimes drives have nasty firmware that is undocumented.  Or, Feisty may have automatically incorrectly set up your drives.  Or you might need drivers for the chipset.  This actually happened to me once, and only the primary channel worked.  The board used software raid, so the chipset only worked properly for Windows.  I no longer have it.
And never mind my mention of running Puppy inside Windows.  I realize, from your signature, that it will not work too well.

Oh!
OK!
Done!
kh

---

### Post by kittyhawk63 on 2007-04-28
OK. Here is something k3b gave me. See attachment.

BTW, I don't think I have mounted these Rom drives. What kind of data do I use on a CD to have Nautilus mount the drives?
Sorry that I had not mentioned this earlier. 
kh

---

### Post by kittyhawk63 on 2007-04-28
BTW, I don't think I have mounted these Rom drives. What kind of data do I use on a CD to have Nautilus mount the drives?
Sorry that I had not mentioned this earlier. I just thought of it.
kh

---

### Post by taurus on 2007-04-28
If you don't plan to burn mp3 using k3b, then don't worry about that message.

By the way, to run the checksum.

```
md5sum filename.iso
```

---

### Post by SoloSalsa on 2007-04-28
But hey, that is really uncommon.  Most drives work!  To begin troubleshooting, you should look up your drive models.  And, I edited my post, just in case you want to try the virtual machine, get the installer here: [http://www.moka5.com/products/getstarted.html](http://www.moka5.com/products/getstarted.html).  Then, get the Puppy image here: [http://www.moka5.com/node/763](http://www.moka5.com/node/763).

---

### Post by kittyhawk63 on 2007-04-28
Taurus,
I have had Feisty running for the past eight hours. I have never had it to run over 15 minutes until this without a screen freeze or black screen. I finally got the xorg.conf set up right.
kh

---

### Post by kittyhawk63 on 2007-04-28
Repeat of question.
What kind of CD do I need to insert that will get Nautilus to mount my CD Rom drives. I had forgot to say they were still unmounted. I had forgot this altogether. Sorry for all this. This may be my problem.
kh

---

### Post by kittyhawk63 on 2007-04-28
Have I been abandoned? Just when it was getting interesting.

I have been able to get my standard CD Rom drive to mount using the Dapper LiveCD. I still have been unable to get the CD-R/RW drive to mount using the same LiveCD. Crazy.

Any suggestions?
kh

---

### Post by SoloSalsa on 2007-04-29
Sorry, I did not abandon you, but I do not know how to help.  I use Xubuntu, on an old laptop, with no writing ability.  So I never had to face this.  However, it does mount ROM/R/RW properly.  Try looking up your drive models, someone might have a similar problem.  The search engine in my signature is pretty good...

---

