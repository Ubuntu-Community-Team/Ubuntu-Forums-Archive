---
title: "Can't get started"
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by suda on 2009-01-02
Hello everybody,

I am new to this.

I have an iBook G3 and iMac G4. I have downloaded the iso for Ubuntu 8.10 and Xubuntu 8.10, but after being burned in disk utility, disk utility cannot verify the burned disk(s).

I now find out that I may have downloaded the wrong versions? (Learned this in the apple users forum--I am now downloading the versions for the PPC). Why can't I use desktop versions from the Ubuntu homepage (if this is the problem)?

If I do not use disk utility but use the traditional burning method, do I need to double click the download and drag and drop the individual items  into the "disc" icon? Or do I just drag the iso? And what exactly is the iso?

I'm not sure these questions are clear. Sorry. This is way over my head. I may just have to stick with Mac if I can't get this part of it. :-)

Thank you for your help.
suda

---

### Post by gettinoriginal on 2009-01-02
I am not a mac user, but I found this, hope it helps:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by suda on 2009-01-02
Thanks! I actually read that page, but I'll go back and reread it. I've read many different messages and visited different help centers--all seemed to say that any of the Linux programs would work as a desktop download. I'm beginning to suspect the Ubuntu/Xubuntu downloads need to be more computer specific. I'm waiting for one that is PPC :Doriented to finish downloading now to see it it works.

---

### Post by gettinoriginal on 2009-01-02
Well, are you burning at the lowest speed possible ??  Many threads mention this. And yes, you want to burn the entire ISO :P

---

### Post by suda on 2009-01-02
> **gettinoriginal said:**
> Well, are you burning at the lowest speed possible ??  Many threads mention this. And yes, you want to burn the entire ISO :P

Well, I am burning at the lowest speed (4X). Do I need to double click the iso and drag and drop the individual contents onto the disc burner or can I just drag and drop the iso in the form it is downloaded?

Are there any Apple people in this Apple forum who might offer help?  I thank you very much Gettinoriginal.

Thanks again.

---

### Post by gettinoriginal on 2009-01-02
drag and drop the ISO as it is downloaded

---

### Post by pxwpxw on 2009-01-02
> **suda said:**
> Well, I am burning at the lowest speed (4X). Do I need to double click the iso and drag and drop the individual contents onto the disc burner or can I just drag and drop the iso in the form it is downloaded?

Are there any Apple people in this Apple forum who might offer help?  I thank you very much Gettinoriginal.

Thanks again.

Disk Utility in MacOSX is very good for burning isos. You just drag the whole iso on to disk util and then burn at lowest speed.
You mus use the ppc version see the sticky for powerpc at the top of the thread.
If you get a bad burn just do another CD, it happens.

---

### Post by suda on 2009-01-02
> **pxwpxw said:**
> Disk Utility in MacOSX is very good for burning isos. You just drag the whole iso on to disk util and then burn at lowest speed.
You mus use the ppc version see the sticky for powerpc at the top of the thread.
If you get a bad burn just do another CD, it happens.
Thanks for getting back. I did as you said, pxwpxw. (I've now gone through 7 CDs-R, burning at slowest speed). Using the PPC version, the fail verification message said "no checksum to verify." How is this possible?

---

### Post by suda on 2009-01-02
> **suda said:**
> Thanks for getting back. I did as you said, pxwpxw. (I've now gone through 7 CDs-R, burning at slowest speed). Using the PPC version, the fail verification message said "no checksum to verify." How is this possible?
Disc Utility now says I now have an Okay volume. Thanks for your help.

---

### Post by pxwpxw on 2009-01-02
Good, please mark thread solved (in tools).

---

### Post by stream303 on 2009-01-03
Just a quick note - there was a bug in certain versions of disk utility where it would fail the verification, but the disk was actually ok.  I'll have to dig up that reference again, as that can sometimes confuse the issue when the problem may be burn speed / media related, and not really the fault of the buggy error-report of disk-utility.

Updates fixed it apparently - it might be mentioned in the ppc "archives" forum.

---

### Post by suda on 2009-01-03
**Oops! NOT solved!** After burning the live CD (disc utility telling me that all volumes checked out and were mountable, even though disc utility also told me the ISO was deficient prior to burning), I was warned that if I proceeded to use the CD, I risked damaging my operating system. Thus the prior message yesterday about the volume being okay.

Problem: I am downloading successfully the ISO for the PPC version of Ubuntu (8.04), but when my disc utility program "verifies" the ISO _prior_ to actual burning, it says "there is no checksum to verify." How is this possible? Anybody out there had this problem and a solution?

Thanks.

---

### Post by suda on 2009-01-03
Somehow missed this message. Many thanks. Really appreciate the info. I'm also trying a download on the other computer, the PPC G3 to see if I get the same results.

---

### Post by suda on 2009-01-03
See last message (I posted twice). Thanks.

---

### Post by mkvnmtr on 2009-01-03
The check sum is on the page where you got your download. I guess you have to check it yourself but I don't know how on the mac. Maybe someone can tell us.

---

### Post by pxwpxw on 2009-01-03
> **suda said:**
> **Oops! NOT solved!** After burning the live CD (disc utility telling me that all volumes checked out and were mountable, even though disc utility also told me the ISO was deficient prior to burning), I was warned that if I proceeded to use the CD, I risked damaging my operating system. Thus the prior message yesterday about the volume being okay.

Problem: I am downloading successfully the ISO for the PPC version of Ubuntu (8.04), but when my disc utility program "verifies" the ISO _prior_ to actual burning, it says "there is no checksum to verify." How is this possible? Anybody out there had this problem and a solution?

Thanks.

You are doing checks that wont work, probably your burned cd is ok.

This is all you need to do.
If you want to see what is in the iso, ignore the warning and open it.
It is just Apple protecting themselves.

I get the warning (see pics below)

If you want to check the downloaded ISO.

```

MD5SUMS file from ubuntu - 
http://cdimage.ubuntu.com/ports/releases/intrepid/release/MD5SUMS
Has sums for all the intrepid  iso's.

http://cdimage.ubuntu.com/ports/releases/8.04/release/MD5SUMS
Has sums for all the hardy isos.

Checking hardy - correct md5sum is
3a4e75264bcfdb1a7ba461c099f0b17c *ubuntu-8.04-server-powerpc.iso

Check the iso in terminal - use the md5 command

mac03:~ pxw$ md5 -r /ubuntu804ppc/ubuntu-8.04-server-powerpc.iso 
3a4e75264bcfdb1a7ba461c099f0b17c /ubuntu804ppc/ubuntu-8.04-server-powerpc.iso

```

Then you burn the iso, Diks Utility does its own checks during the burn.

You cant verify the burned CD in Macosx.

Then restart and boot from the CD, it has an option to do a self check if you want, it is very slow.

---

### Post by suda on 2009-01-04
Thank you for your time and the excellent explanation, but I'm getting a different experience. On my iMac G4, when I burn the CD that I want to install on my iBook G3 (I don't have a burner on the G3), there is an automatic verification process, and it says the burned disc can't be verified. Do you think I should still go ahead and ignore the warnings about potential damage to my OS use the CD?

---

### Post by mkvnmtr on 2009-01-04
I have never seen that kind of warning on my G4. But when we think about it how can software damage a disk? The worst that could happen is you have to reinstall something and reburn.

---

### Post by suda on 2009-01-04
Exactly. That's the conclusion I came to as well. If the Ubuntu install fails, I'll just reboot with Mac OS. Thanks!

---

### Post by pxwpxw on 2009-01-04
> **suda said:**
> Thank you for your time and the excellent explanation, but I'm getting a different experience. On my iMac G4, when I burn the CD that I want to install on my iBook G3 (I don't have a burner on the G3), there is an automatic verification process, and it says the burned disc can't be verified. Do you think I should still go ahead and ignore the warnings about potential damage to my OS use the CD?

Ok, you mean that when Disk Utility is verifying as it finishes, it gives the failed verify?

I would still try the CD in the G3, I have had that happen. It won't damage the G3, if it has really got errors it will just fail to start or hang up during the install - and you can do the CD check step at the start to get a second opinion. I would try them all, you can always abort the install if you want.

---

### Post by suda on 2009-01-04
I did as you suggested and had NO problems with any system failures. Do you think Apple is trying to keep customers from bolting? :-) Ironically, when I finally burned the CDs, I got verifications that they were good. But in the actual booting of the iBook G3 with the verified CD on board, it goes straight to the Mac OS environment. The Ubuntu icon never shows or gives me a choice of operating system. It's as if I'm not even booting. In another thread on this I explained how I was booting--CD in the drive, restart, chime, holding down the C key until I see the Mac icon and still holding down the C key until I see the Ubuntu icon, only it never appears and then I'm back in the Mac OS environemnt. Yikes!

---

### Post by pxwpxw on 2009-01-04
Did you try the Option key?

My only other suggestion is to look at the ubuntu CD in Macosx on the G4 (ignoring warnings), to check that all the expected files are there (see my pictures above), and try all the other CD's in the G3,
or bette still try booting them with the G4.
There are also some problems booting the installer for early G3, IDK about that.

---

### Post by suda on 2009-01-05
[COLOR="Blue"]> **pxwpxw said:**
> You are doing checks that wont work, probably your burned cd is ok.

This is all you need to do.
If you want to see what is in the iso, ignore the warning and open it.
It is just Apple protecting themselves.

I get the warning (see pics below)

If you want to check the downloaded ISO.

```

MD5SUMS file from ubuntu - 
http://cdimage.ubuntu.com/ports/releases/intrepid/release/MD5SUMS
Has sums for all the intrepid  iso's.

http://cdimage.ubuntu.com/ports/releases/8.04/release/MD5SUMS
Has sums for all the hardy isos.

Checking hardy - correct md5sum is
3a4e75264bcfdb1a7ba461c099f0b17c *ubuntu-8.04-server-powerpc.iso

Check the iso in terminal - use the md5 command

mac03:~ pxw$ md5 -r /ubuntu804ppc/ubuntu-8.04-server-powerpc.iso 
3a4e75264bcfdb1a7ba461c099f0b17c /ubuntu804ppc/ubuntu-8.04-server-powerpc.iso

```

Then you burn the iso, Diks Utility does its own checks during the burn.

You cant verify the burned CD in Macosx.

Then restart and boot from the CD, it has an option to do a self check if you want, it is very slow.
[/COLOR]


Sorry to keep on this, but I am so determined to learn about Linux and ubuntu and to try to get a good boot so that I can enjoy this new system like everybody else. I just noticed that the above md5sum is for the server edition. I downloaded the *desktop* CD and when I went to the Web site you gave above, it had a different md5sum for the desktop. That's no problem, but when I opened md5sum.txt in the ISO for ubuntu-8.04.1-desktop-powerpc.iso, there were a ton of different numbers and none that matched the number on the Web site. That number is: 

4ba92bb7a29de088ea881d5d51c2dd34*ubuntu-8.04.1-desktop-powerpc.iso

When I opened the folder in the ISO called "dists" and came to "release," this is what I found: 

MD5Sum:
 a0bd8b1f18373717a64c443abe84c300    10575 main/binary-powerpc/Packages.gz
 8540b6b11f7f324f2909b21de2d81cf9       96 main/binary-powerpc/Release
 b1747fc36f1c57dbcb1bb5ff734b858d    31999 main/binary-powerpc/Packages

As you can see, there is no match for the "4ba..." 

What am I missing here? How do I find the correct match? Is this why I can't get a boot? Thanks.

s.

---

### Post by suda on 2009-01-05
For a change, I'm going to a answer my own question! :-) I just figured out how to use my disc untility to find the md5sum on my mounted ISO. Here is the result for the above inquiry:


	                       Apple_HFS (0): calculated MD5 $C3F57A0B0C416E4209785B882A19D35E
	calculated MD5 $748832A2A76AC2A2FBD4336B8B2BD609
calculated MD5 $748832A2A76AC2A2FBD4336B8B2BD609


It doesn 't appear that I have a match, does it, with the checksum in the link in the previous message. Would this explain why my iBook isn't seeing ubuntu when booting? Now what? Thanks!

---

### Post by pxwpxw on 2009-01-05
> **suda said:**
> For a change, I'm going to a answer my own question! :-) I just figured out how to use my disc untility to find the md5sum on my mounted ISO. Here is the result for the above inquiry:


	                       Apple_HFS (0): calculated MD5 $C3F57A0B0C416E4209785B882A19D35E
	calculated MD5 $748832A2A76AC2A2FBD4336B8B2BD609
calculated MD5 $748832A2A76AC2A2FBD4336B8B2BD609


It doesn 't appear that I have a match, does it, with the checksum in the link in the previous message. Would this explain why my iBook isn't seeing ubuntu when booting? Now what? Thanks!

Hang on, you are completely off course, and I forgot you have 804.1. Let me see if I can find that info, I will get back then.

The only one you need check is the md5 result you get in Macosx terminal for the original downloaded iso - just the one, and that should match the release checksum for your 804.1 desktop.

---

### Post by pxwpxw on 2009-01-05
Right,

The correct md5sum is from here and you have that above (I hope I got your release correct this time ) -

[http://cdimage.ubuntu.com/ports/releases/8.04.1/release/](http://cdimage.ubuntu.com/ports/releases/8.04.1/release/)
[http://cdimage.ubuntu.com/ports/releases/8.04.1/release/MD5SUMS](http://cdimage.ubuntu.com/ports/releases/8.04.1/release/MD5SUMS)

As you found, the desktop - md5sum should be

 4ba92bb7a29de088ea881d5d51c2dd34

 for your downloaded ubuntu-8.04.1-desktop-powerpc.iso

You get your calculated md5sum for your downloaded iso using the macosx terminal.

You do this by typing the command 'md5 -r' and then dragging and dropping the iso into the terminal window which will then show the full path to the iso and save you a lot of typing and trouble. 
Then hit return.
```

  md5 -r /your path to the iso file/ubuntu-8.04.1-desktop-powerpc.iso

```

That is all you need to do to prove the iso as a whole is error free.

This has nothing to do with Disk Utility.

With md5sums, if the first few numbers match, you can bet that the rest will, because 1 bit error will make an enirely different result.

---

### Post by suda on 2009-01-06
Thank you both! I will check on this tomorrorw. ZZZZ time here.

s.

---

