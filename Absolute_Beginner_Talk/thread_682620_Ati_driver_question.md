---
title: "Ati driver question"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-01-30
I use a ati radeon xpress 200 card and this was installed using the restriced drivers managment.

It came to my attention that ati released drivers for linux. 

I went to their website and when I look at the driver I needed said to download the
 ATI Catalyst™ 8.1 Proprietary Linux x86 Display Driver found on this page:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Is this the same driver ubuntu gutsy installs by default? Or is this a better driver.

With the driver I have now I can use compiz fusion but 3d games don't work. Would this change with that driver? I know the card is 3d capable, I could play half-life 2 on windows.

Thanks.

---

### Post by LostMagix on 2008-01-30
I didnt know there was any other way to use a ATI card, this may be how i could fix my problem....


You may have inadvertently help me fix my issues!!!

---

### Post by billgoldberg on 2008-01-30
I only discoverd this today after reading a post in the community cafe.

---

### Post by luisromangz on 2008-01-30
It's a better driver based in a new codebase, it provides support for AIGLX, and is faster.

---

### Post by billgoldberg on 2008-01-30
Would I need to do anything special to install it or can I just run the installer without risking damage to the system?

---

### Post by LostMagix on 2008-01-30
Before i go and start changing stuff up, does someone just want to check and make sure its not a biger problem then just the driver


[http://ubuntuforums.org/showthread.php?p=4235355#post4235355]("http://ubuntuforums.org/showthread.php?p=4235355#post4235355")

---

### Post by bumanie on 2008-01-30
As you probably know, ati is actually owned by amd. Amd have committed to realeasing drivers under open source. I thought this was not meant to happen until about mid-year, but it looks as though it has started. I would bet that the open source driver on the website will be better than any in fesity and gutsy because when they were released the drivers were still proprietry drivers and would now be a number of months old. Give the new one a try. I think amd have seen merit in open sourse drivers for ati to help boost sales of both vga cards and cpu's. I read they are planning to have all-in-one driver packages for cpu's and graphics cards in the future, with the focus being on better/easier set up and compatability between the two (better profits too).

---

### Post by billgoldberg on 2008-01-30
I'm going to back up some stuff and try the new driver. I'll post back here to tell how it went .

---

### Post by dark_harmonics on 2008-01-30
I would not recommend this for new users. Messing with video drivers has cost me hours and hours of messing with settings. If you update to that driver and use compiz fusion effects, it will turn your direct rendering off and make it indirect (it is exported in the compiz script to make it work). Something the driver doesnt support messes with it. Also if you use a dual -head machine (not big desktop that still works) it wont work anymore. I love my dual-cubed desktop and so I reverted back to the ubuntu stable driver. 

First i curse ati, then I curse myself for diving into the mess and finally i just accept that ubuntu developers really do test their stuff and include the most stable versions in the repos.

Not to say that it isn't faster. It definitely is. 

Hope you have a better experience with this!

---

### Post by LostMagix on 2008-01-30
lolz, how do i know if i have  linux x86 or linux x86_64....

or ether...

---

### Post by p_quarles on 2008-01-30
@LostMagic: Run this command:
```
uname -a
```
The kernel architecture will be included in the output.

---

### Post by LostMagix on 2008-01-30
Thank you!!

---

### Post by dark_harmonics on 2008-01-30
> **LostMagix said:**
> lolz, how do i know if i have  linux x86 or linux x86_64....

or ether...

The driver is the same no matter what you click on there. 

But essentially its just the difference between 64 and 32 bit drivers. Their current package has both in it so it doesnt matter what you pick there. You guys should definately follow a guide to do this. Check out section three on this document:
 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by LostMagix on 2008-01-30
I got this, what does it mean?

Linux LostMagix 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux

---

### Post by LostMagix on 2008-01-30
Ok Thanks...

---

### Post by dark_harmonics on 2008-01-30
Sure no problem.

I just want to reiterate that you should not do this on a computer that you aren't willing to spend some time messing with settings on. The supported ubuntu way is always the easiest. That being said, good luck with your experimentation with this driver!

---

### Post by erfahren on 2008-01-30
its better to create .deb packages so you can more easily revert the changes if needed. see the install wiki:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by bumanie on 2008-01-30
It depends on your cpu. If you know what type of cpu you have and still aren't sure, post the model here and someone will help.

---

### Post by erfahren on 2008-01-30
> **bumanie said:**
> It depends on your cpu. If you know what type of cpu you have and still aren't sure, post the model here and someone will help.
no, it depends on whether you are using 32-bit Ubuntu or 64-bit Ubuntu

---

### Post by dark_harmonics on 2008-01-30
> **bumanie said:**
> It depends on your cpu. If you know what type of cpu you have and still aren't sure, post the model here and someone will help.

Yes you are correct with most things. This package from ATI actually is the same for 64 and 32 bit systems. It supports both. You'll notice if you click the link to the 32 bit its the same as when you click the one for the 64. I know because i recently reinstalled my system to 64 bit and when i went to download the driver it was the exact same. I then used the one I already had to install it.


Edit:  erfahren is more correct. If you have a 64bit processor you could still have 32 bit ubuntu

---

### Post by billgoldberg on 2008-01-30
I installed the driver and well, compiz is reall slow. I just ran the installer.

Now I'm following a guide but I'm stuck here:

Then install the binary drivers:

sudo dpkg -i fglrx-kernel-source_<version>.deb

What do I need to enter in <version>?

the guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)

---

### Post by bumanie on 2008-01-30
Usually you put the name of the package.

---

### Post by billgoldberg on 2008-01-30
what package?

---

### Post by erfahren on 2008-01-30
> **billgoldberg said:**
> I installed the driver and well, compiz is reall slow. I just ran the installer.

Now I'm following a guide but I'm stuck here:

Then install the binary drivers:

sudo dpkg -i fglrx-kernel-source_<version>.deb

What do I need to enter in <version>?

the guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)
the "fglrx-kernel-source_<version>.deb" is just the name of the package you created (like "fglrx-kernel-source_8.452.1-1_i386.deb) 

if you already installed that driver using the installer you'll need to uninstall it first (don't ask me how) - but if you made .deb packages out of it you'd just be installing the driver again but in a different way. (It actually wouldn't be a good idea though.)

---

### Post by LostMagix on 2008-01-30
So under<version> would i put "ATI Technologies Inc RV350 AS [Radeon 9550]"???

---

### Post by LostMagix on 2008-01-30
Im sorry i should have read, I apologize

---

### Post by bumanie on 2008-01-30
Sorry I can't see what you are doing, but usually there will be a name, followed by numbers, followed by.deb
I have never tired an ati card driver install, just generalising re the name and .deb issue, however I must add that I did look at the site you posted and maybe the diver is newer, but that site has been there a long time. As I said originally, i didn't think ati/amd were releasing open source ati drivers until mid-year (and then we will have to see how 'open and free' they are). I think what you are trying to load is probably still a proprietry driver, although the site does say that they now work with open source developers to try to help getting the drivers stable. I'm sorry I can't be more precise.

---

### Post by LostMagix on 2008-01-30
So it should look something like this correct?


sudo dpkg -i fglrx-kernel-source_8.452.1-1_i386.deb

---

### Post by erfahren on 2008-01-30
with the guide I posted earlier all you have to do is copy and paste the commands - its a better guide anyhow
EDIT (repost): [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by billgoldberg on 2008-01-30
the next step in the guide produced and error.

I think i'll pass on that driver.

How would I remove the driver I just installed and reinstall the one gutsy installs by default?

---

### Post by bumanie on 2008-01-30
I bleieve you just have re-enable the restricted driver again and that will override the ati driver. You can also check in synaptic and remove anything you have just installed.

---

### Post by LostMagix on 2008-01-30
It worked PERFECT!!!

Thank you SO MUCH!!!

---

### Post by Michl on 2008-01-30
> **dark_harmonics said:**
> I would not recommend this for new users. Messing with video drivers has cost me hours and hours of messing with settings.

I second that emotion... been there.

---

