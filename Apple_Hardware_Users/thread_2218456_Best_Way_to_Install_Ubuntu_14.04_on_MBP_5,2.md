---
title: "Best Way to Install Ubuntu 14.04 on MBP 5,2"
date: 2014-04-20
forum: Apple Hardware Users
---

### Post by swarup on 2014-04-20
I installed Ubuntu 9.04 on my new MBP 5,2 five years ago, and it worked great!  Nonetheless the installation and ensuing struggle to get everything working was so intense that I shied away from doing any newer installations after that. My 9.04 still works wonderfully today and I love it! I do all my work on it-- but now the internet browser is so old that there are problems showing many websites. And I have other such problems due to the age of the software on the OS.

So it is time to go for a new Ubuntu, and specifically a LTS version so once it is installed I won't have to deal with it for another 5 years.

I've been reading about the installation options-- 
1. Some say to use the "64bit" version of 14.04; others say to use the "64bit MAC AMD64" version
2. Some say to use the Bios Emulation style, others say to use utilize the EFI.

I just need a straightforward set of instructions for the 14.04 install, and I'll go with it.

Here is my hardware:
MBP 5,2
Ram 8 GB 1067 DDR3
2.8 Ghz Intel Core 2 Duo
NVIDIA Ge Force 9400M/9600M GT

---

### Post by swarup on 2014-04-21
My thought is to first set up a triple boot OSX/9.04/14.04 in order to test 14.04 and ensure it works properly. That way I won't be left out in the cold. I'll have the 9.04 as a fallback. And once I see 14.04 is working well, then I'll delete 9.04 and  expand the 14.04 partition to take up that space.

[Here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") is the traditional method for installing a dual or triple boot OSX/Ubuntu, or OSX/Win/Ubuntu.

That is the method I used in 2009 to set up my dual boot with OSX/9.04. I've still got it running today. So I already have the setup using rEFIt running on the computer.

Now, the thing is that in the above link, they detail how to do three different setups: (1) make Ubuntu the only OS; (2) set up a dual boot OSX/Ubuntu; (3) set up a triple boot OSX/Win/Ubuntu. 

They don't explain how to set up a triple boot with two linux os's. But if you look at the partitioning diagram they gave for their triple boot OSX/Vista/Ubuntu-- I think if the Vista partition is considered as my 9.04, then I should be able to boot up to the 14.04 livecd, go into gparted, shrink the 9.04 partition, create unallocated space to the right of it, and install 14.04 to the new unallocated space. Do you think that should work?

Now assuming that plan works, one question arises in my mind-- once I'm satisfied with the function of 14.04, and am ready to delete 9.04. Then the new unallocated space where 9.04 was will be to the left of 14.04 and not to the right. As I recall, the partition can be expanded in the rightward direction, but not in the leftward direction. If that is the case, then I may have to delete 14.04 as well and reinstall afresh over the entire space where 9.04 and 14.04 were. But once I got success the first time, I should be able to do it a second time.

My understanding for the above plan, is that I would be using the usual Bios method and not the EFI method, and would therefore use the 14.04 64bit download, and not the 64bit MAC download. Is that correct?

---

### Post by swarup on 2014-04-21
Can anyone explain what is the difference between these two download options for 14.04: 

1. 64-bit PC (AMD64) desktop image 
and 
2. 64-bit Mac (AMD64) desktop image

I have been trying to read up on which of the two should be utilized for a standard install with rEFit, but I could not find information on this. The "64-bit Mac (AMD64) desktop image" option is something new for me-- never seen it before. In the past I used the standard 64-bit PC (AMD64) desktop image.

---

### Post by aradick2 on 2014-04-21
14.04 was incredibly simple to install on my MBP 5,3. In Mac OS I shrinked the size of the OSX partition, leaving empty space for the Ubuntu install. Then I used the standard 64-bit PC desktop image (**I had to boot with the parameter nomodeset) and installed Ubuntu, selecting the option "Install Ubuntu alongside Mac OS." Anything like rEFInd or rEFIt is unnecessary and the only things I had to install in Ubuntu were the wireless drivers and the Nvidia drivers.

---

### Post by swarup on 2014-04-22
That's amazing! It sounds almost too good to be true! I can hardly believe it!
1) For so many years rEFIt was needed. What has changed, to make rEFIt unnecesary?
2) So when you boot the computer now, the first thing which shows up is a GRUB menu?
3) Is 14.04 working well? Are there any other problems or difficulties in how it runs?
4) Where did you get the wireless drivers and the Nvidia drivers?
5) Can I think that if 14.04 installed the way you describe on the MBP 5,3, then it should probably do the same on my MBP 5,2? Is there any reason to think that 5,3 and 5,3 would behave differently with regard to the 14.04 install?

---

### Post by aradick2 on 2014-04-22
> **swarup said:**
> That's amazing! It sounds almost too good to be true! I can hardly believe it!
1) For so many years rEFIt was needed. What has changed, to make rEFIt unnecesary?
2) So when you boot the computer now, the first thing which shows up is a GRUB menu?
3) Is 14.04 working well? Are there any other problems or difficulties in how it runs?
4) Where did you get the wireless drivers and the Nvidia drivers?
5) Can I think that if 14.04 installed the way you describe on the MBP 5,3, then it should probably do the same on my MBP 5,2? Is there any reason to think that 5,3 and 5,3 would behave differently with regard to the 14.04 install?
Just letting you know, I'm no Linux guru or anything, I haven't been using it that long at all.
1) Ubuntu (the Linux kernel itself and GRUB) has much better native EFI support (especially because Windows 8 now uses EFI).
2) Yeah, GRUB comes up. When I want to boot into Mac, I hold the alt key while booting and that brings up the standard Mac boot menu. (Note: for me, my mac thinks there is a windows install for no reason, which shows up here, but clicking on it does not boot anything).
3) 14.04 runs awesomely! It does run hotter than OS X (but barely), but it should run cooler than 9.04 depending on what you've done to make it more efficient. Battery life is very similar to OS X as well. Suspend(sleep) on lid close works now out of the box too.
4) I used the tool within Ubuntu that's called "Additional Drivers", and I installed the proprietary versions of the nvidia and the broadcom drivers.
5) I feel like it will be almost exactly the same, since we both have almost the same proc and definitely the same video cards. (Remember to boot the install cd with nomodeset.)

---

### Post by swarup on 2014-04-22
Sounds very cool. I can hardly think of anything else to ask! Sounds straightforward, basically like a standard install on a PC. I was going to try and do a triple boot with OSX/9.04/14.04 to preserve the 9.04 until getting confirmation that 14.04 is installed and working well. But hearing your experience, it sounds like engaging in the complexity of a triple boot to preserve 9.04 will not be needed. I think I'll just swipe that 9.04 partition clean, format it, and install 14.04 in its place. I will need to remove rEFIt, but I'll google it to find out how this is done (unless you know and it is real easy to write in a quick sentence).

Two quick questions for you:
1) The 14.04 iso download is 964 MB, which will not fit on a CD. So I'll have to make a bootable USB-- assume that is what you did as well?
2) Is the MBP set up to look first for the bootable USB before booting up to the HDD? Or will I have to go into a bios or whatever the MBP has, to change the boot priorities?

---

### Post by aradick2 on 2014-04-22
> **swarup said:**
> Sounds very cool. I can hardly think of anything else to ask! Sounds straightforward, basically like a standard install on a PC. I was going to try and do a triple boot with OSX/9.04/14.04 to preserve the 9.04 until getting confirmation that 14.04 is installed and working well. But hearing your experience, it sounds like engaging in the complexity of a triple boot to preserve 9.04 will not be needed. I think I'll just swipe that 9.04 partition clean, format it, and install 14.04 in its place. I will need to remove rEFIt, but I'll google it to find out how this is done (unless you know and it is real easy to write in a quick sentence).

Two quick questions for you:
1) The 14.04 iso download is 964 MB, which will not fit on a CD. So I'll have to make a bootable USB-- assume that is what you did as well?
2) Is the MBP set up to look first for the bootable USB before booting up to the HDD? Or will I have to go into a bios or whatever the MBP has, to change the boot priorities?
I don't know exactly how to get rid of rEFIt, but I am pretty sure its easy.
1) I used a DVD because I had an extra one lying around.
2) Hold alt when booting, then wait (I had to wait awhile) for the install media to load. Then click on the usb/dvd boot option.

---

### Post by swarup on 2014-04-22
Got it-- thanks. Will let you know how it goes. 
I am in the process now of backing up my evolution mail in a way that the new evo will recognize. I'm going to back it up in a few different formats just to be sure it will transfer smoothly into the new evo, because the evo I've been using is so old. Once the mail backup is done, I'll go ahead and do the 14.04 install.

---

### Post by Rahabib on 2014-04-22
please report how it goes. Since you are using rEFIt already, let me know if it keeps it or if you it replaces it with grub or you have other issues.

---

### Post by monkeybrain20122 on 2014-04-22
> **swarup said:**
> I installed Ubuntu 9.04 on my new MBP 5,2 five years ago, and it worked great!  Nonetheless the installation and ensuing struggle to get everything working was so intense that I shied away from doing any newer installations after that. 

Maybe you won't need to struggle intensely if you keep up yo date. Things get easier and easier. I started with ubuntu 10.04 and it seems like a century ago in terms of the progress they have made. I can't imagine using 9.04 on reasonably up to date hardware and that includes things from 5-6 years ago.

---

### Post by swarup on 2014-04-22
Some are recommending to me to keep my 9.04 and install a triple boot to be safe, in case there are issues with 14.04. On the one hand I was so much looking forward to getting rid of rEFIt and having a clean setup with just OSX and 14.04. But maybe they are right that it would be safer to keep 9.04 and at least just do the initial install as a triple boot. Then if everything looks fine, I can redo the install later, get rid of 9.04 & rEFIt and set up 14.04 this time straight with EFI.

I am still thinking about it, but maybe that is the safer way?

---

### Post by Tom 6 on 2014-04-22
Hi :)  
rEFIt is the Mac boot-loader isn't it?  If so then 9.04 probably doesn't need it if 14.04 doesn't.  The 9.04 only needed the non-Grub one in order to get into the Mac side.  It didn't need it for itself afaik.  The 14.04 'should' (hopefully) magically give you a boot-menu item for 9.04 while it's sorting the one for Mac.  Grub2 has had massive advances in the last 5 years but you cold always ask their devs mailing list.   

Also if you lose your 9.04 in the process then you have ended up in the same place anyway, but with the advantage that you can still see the files on the old 9.04's partition.  All you would be missing is the ability to boot into 9.04 which you don't seem keen about keeping anyway.  So, no harm no foul.  Export from Evo though and maybe export bookmarks from your web-browser too.  

So i was suggesting just doing the straight-forwards 14.04 install and see what you do end up with.  

Errr, have you checked out the thread about "request for Mac testers"?  
Regards from 
Tom :)

---

### Post by swarup on 2014-04-22
I see-- that is something I hadn't thought of. So in a sense I'll have the best of all the worlds-- I'll still have 9.04 in case I need to go back to it, and I'll gain 14.04 to experiment with, and I'll get rid of rEFIt. Sounds great! I've backed up all my stuff from 9.04, as well as exported the mail from evo and backed up my Firefox bookmarks. So the last thing I need to do now is google how to uninstall rEFIt. Then I'll do the install. This is getting exciting!

---

### Post by swarup on 2014-04-22
Quick question: the mountpoint of the 9.04 (ext3) is currently /. The 14.04 will be installed to an ext4 partition, also with mount point of / right?

---

### Post by Tom 6 on 2014-04-22
Hi :)  
Errr, kinda but not really.  There is only ever 1 / and the other will be mounted as something else.  So after grub has found both partitions are bootable (and the Mac one too) it automatically makes a boot-menu for you.  

When you boot into the 14.04 the 9.04 gets mounted as something like 

/media/sda3  

but when you reboot into the 9.04 it becomes the / and the 14.04 becomes something like 

/media/sda5

err, with the extra wrinkle that it doesn't use sdaX in there, it tends to use things like F34h9 or some other incomprehensible thing but you don't usually see that.  Anyway, the main point you were asking about should happen roughly the way you seem to be expecting, hopefully!  (inshalla)
Regards from 
Tom :)

---

### Post by Tom 6 on 2014-04-23
Hi :)  
Ahh, just realised that the installer asks you to set mount points.  The only one(s) to worry about are the ones for the 14.04.  So only set the 1 partition 
/ 
for where it's going to be installed.  Grub will find the older 9.04 without you needing to take any action and without you needing to point to it at all.  It's very clever!  You might also want to have a separate 
/home
partition, especially if you are planning to have quite a large area for Ubuntu.  Normally i'm installing dual-boots to Windows and Windows can't see what's on the Ubuntu side so i keep Ubuntu very small and put all my files on the Windows side.  Even then it's quite handy to have a separate /home partition but for this install it might be a really good idea. 
Regards from 
Tom :)

---

### Post by swarup on 2014-04-25
I did the install yesterday, and everything went incredibly smoothly. I ended up just deleting the old 9.04 ubuntu partition, and installing the newest OSX (Mavericks) and then Ubuntu 14.04 side by side. No rEFIT or anything else needed. Installing Ubuntu on a Mac has become incredibly simple! No difference from installing on a PC now.

(Yes, one does need to set the boot to [nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132") for the livecd, and I had to do it for the first boot into Ubuntu. Once I booted in and installed the NVIDIA driver, it was no longer needed. To install the NVIDIA driver, just type "Additional Drivers" in the dash and the tool will come up right away for installing it.)

---

### Post by Tom 6 on 2014-04-25
Hi :)  
Congrats!! :D  Nicely done! 

It is good to hear, again, that it is getting much easier and is within reach of most normal users.  I know you were over-prepared and maybe didn't even notice some problems but what you have said off-list and on-list gives me much more confidence about the whole thing.  

Many thanks, congrats and regards from 
Tom :)

---

### Post by Rahabib on 2014-04-25
> **swarup said:**
> I did the install yesterday, and everything went incredibly smoothly. I ended up just deleting the old 9.04 ubuntu partition, and installing the newest OSX (Mavericks) and then Ubuntu 14.04 side by side. No rEFIT or anything else needed. Installing Ubuntu on a Mac has become incredibly simple! No difference from installing on a PC now.

(Yes, one does need to set the boot to [nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132") for the livecd, and I had to do it for the first boot into Ubuntu. Once I booted in and installed the NVIDIA driver, it was no longer needed. To install the NVIDIA driver, just type "Additional Drivers" in the dash and the tool will come up right away for installing it.)

Good to hear.  I simply upgraded for now, but I think I am still going  to wipe it clean as I still get phantom messages on shutdown about  applications I removed a long time ago.  Although nautilus is far more  stable than in 13.10.

So does grub now show up to choose your OS?  Grub only shows up for me after rEFIt but it crashes going to OSX.  SO for me to get to OSX I have to use rEFIt.  I am hoping thats because of legacy/pre EFI dependencies still in Grub that will be replaced.

Also, I assume you used Ubuntu MAC 64?

---

### Post by Tom 6 on 2014-04-25
Hi Rahabib :)  
Sounds like you need to post a few threads of your own!  

In Grub do you ever use the 2nd line for Ubuntu, the one that has "Recovery mode" in it's title.  There are all sorts of maintenance tools in there.  I also try running these 5 commands every few months

sudo apt-get check
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get remove

Regards from 
Tom :)

---

### Post by swarup on 2014-04-28
> **Rahabib said:**
> Good to hear.  ... So does grub now show up to choose your OS?  Grub only shows up for me after rEFIt but it crashes going to OSX.  SO for me to get to OSX I have to use rEFIt.  I am hoping thats because of legacy/pre EFI dependencies still in Grub that will be replaced.

Also, I assume you used Ubuntu MAC 64?

Sorry for the delayed reply-- just saw your post.

1. Upon booting, GRUB shows up directly. It is used for going into Ubuntu only. (The OSX option in it does not work.)
2. To boot into OSX, press the "option" key when you turn on the computer, and you'll get a screen giving you three options-- the leftmost option is to boot into OSX. Select that, and it boots perfectly into OSX.
3. So rEFIt is not needed at all.
4. I used the regular 64-bit 14.04 iso. (NOT the MAC 64-bit)

It couldn't be easier now-- no different than installing on a pc. Try it-- it's a breeze!

---

### Post by Rahabib on 2014-04-29
> **Tom 6 said:**
> Hi Rahabib :smile:  
Sounds like you need to post a few threads of your own!  

In Grub do you ever use the 2nd line for Ubuntu, the one that has  "Recovery mode" in it's title.  There are all sorts of maintenance tools  in there.  I also try running these 5 commands every few months

sudo apt-get check
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get remove

Regards from 
Tom :smile:

I am sorry, it was not my intention to hijack the thread. I was simply finding out if the process swarmup had issues since he was going through the same process I was going to.  I run Ubuntu Tweak janitor every few months which I assume is simply running those same commands.  I tested them today and they found nothing.  If I need further assistance on this, Ill be sure to create a new thread (if a search doesn't find a resolution for me).

> **swarup said:**
> Sorry for the delayed reply-- just saw your post.

1. Upon booting, GRUB shows up directly. It is used for going into Ubuntu only. (The OSX option in it does not work.)
2. To boot into OSX, press the "option" key when you turn on the computer, and you'll get a screen giving you three options-- the leftmost option is to boot into OSX. Select that, and it boots perfectly into OSX.
3. So rEFIt is not needed at all.
4. I used the regular 64-bit 14.04 iso. (NOT the MAC 64-bit)

It couldn't be easier now-- no different than installing on a pc. Try it-- it's a breeze!

Thanks.  I am still having issues with online accounts that have been removed in the past but still showing up, and a few other errors, so I think Ill give this a try sometime next week when I have a day to work on this.  I am fairly confident that I can get it up and running without incident.  Thank you for posting your experience, it was very helpful.

---

### Post by swarup on 2014-04-29
You're very welcome. I wish you all the best with your install.
The truly wonderful news is that now Ubuntu is a breeze and a pleasure to install on apple computers. I kept the same 9.04 OS on my MBP for five years due to concern about difficulty with the next installation. And indeed there were always reports over the years on the forums as well as on the official guidlines, as to failures to install or failure of significant components of the OS to function properlly-- sound, overheating, backlit keyboard not working, no wireless-- so many issues used to be there in the past. But now it is clear Canonical and the Ubuntu community have gotten these obstacles worked out. Installation-- at least on the MBP-- is a breeze. :p

---

### Post by blodgy on 2014-05-26
Did you allocate drive space using the installation dvd or the mac disk utility?  Does it make a difference?  Thanks

---

### Post by swarup on 2014-05-28
I used the installation dvd (usb in my case). I heartily recommend using a usb-- it is much faster.

---

### Post by blodgy on 2014-05-29
Thanks for the response.  USB it is.

---

