---
title: "ATI Driver Install Error &quot;Bad Substitution&quot;"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by seuzy13 on 2008-04-17
I have been trying to resolve some white screen problems which appear to be the result of an ATI graphics card. Whenever I try to install the ATI Proprietary Driver, I get the following error

"root@Larry:/home/zee/Desktop# sh ati-driver-installer-8.28.8.run --buildpkg --Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install"

I have tried several different versions and I always get the same result. Anything I'm doing wrong, or any alternatives that are easier to install? This ATI driver issue is giving me quite a headache.

I'm using Gutsy with a 9100 IGP card.

Thank you!

---

### Post by Kemono on 2008-04-17
Is [[COLOR="DarkOrange"]this[/COLOR] ](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually ) the **how to** you followed?

Have you tried to run the commands as a normal user with **sudo**? This is how I installed mine.

---

### Post by seuzy13 on 2008-04-17
I also tried to run the commands with sudo. I got the same error every time every way I tried it.

The guide you linked to said to install necessary tools before building manually. Well, when I try to do this, I put in the commands:
sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms
The second command ends with a message like this: 
"Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter"
In any case, I don't have an Ubuntu CD, and I don't think you're supposed to have one for something like this are you?

---

### Post by Kemono on 2008-04-17
I'm still pretty new to Linux but I think there's something about the name of the installer that the shell doesn't like. Syntax errors usually indicate that something is not spelled correctly. Then again, I could be wrong. An expert should take a look at this. 

Good luck.

---

### Post by Kemono on 2008-04-17
Well, I did use the CD.

---

### Post by seuzy13 on 2008-04-17
Hmm...yeah, I tried renaming the file too and it didn't help any. Maybe I should try the CD? Thanks for your help.

---

### Post by Kemono on 2008-04-17
Have you tried to install them through the **Restricted Drivers Manager**? Usually when you install Ubuntu, there's an icon in the system tray saying that there are proprietary drivers you could install for your graphics card, wireless card, etc. They may not be the newest ones, but I'm sure there wouldn't be much difference. I have to get some sleep now. I'll check on this thread tomorrow.

Good luck.

---

### Post by seuzy13 on 2008-04-17
I had to use the restricted drivers manager for my network card, so I did notice that it was the only thing listed and that there was nothing about my graphics card. 

I'm going to burn the Ubuntu CD, and see if that helps, though. More word on how that turns out later.

---

### Post by seuzy13 on 2008-04-17
Well, I burned the CD and ran the two commands (sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms) successfully. At least, without error messages. But I'm still getting a bad substitution error when I go to build the .run script. 

If this doesn't work out, is there some other driver that supports 9100 IGP? I checked the one I'm currently using. It is an ATI driver, but it does not say that it supports 9100 IGP, so that is obviously the problem.

---

### Post by Kemono on 2008-04-18
You could try to install the drivers in the Synaptic Package Manager. Go to **System>Administration>Synaptic Package Manager** and search for *xorg-driver-fglrx*. It says that it supports 9100 IGP. See if that works.

---

### Post by Kemono on 2008-04-18
Also take a look at [ [COLOR="DarkOrange"]this[/COLOR] ](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html) page. See if that helps. Those are instructions for installing the drivers for your card. [ [COLOR="DarkOrange"]Here[/COLOR] ](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html) are the drivers you need.

I have an ATI Radeon 9600 (or 9550. Or 9500...I'm not really sure. I'm using the 9600 drivers), so the installation method for my card may be different than yours. Well, keep me posted.

---

### Post by seuzy13 on 2008-04-18
It appears that I have the latest version of fglrx installed, but it does not support 9100 IGP. I need to take it back several versions. I don't think there's a way to do that from Synaptic, and none of the .run scripts are working (as previously mentioned). :-/

I'm planning to update to Hardy as soon as it comes out in several days. I doubt that will solve my problem, though...

EDIT--
hmm...yeah, I've seen these pages. The newest version that supports my driver is 8.28.8. After that, none of them do, and I had a later one installed from the get-go it seems. It would be really helpful to find out what version of X.org I am using. How do I figure that out? Also, does Ubuntu use XFree86 or is that something opposite of X.org? Sorry if I sound like a total newbie.

Thanks!

---

### Post by Kemono on 2008-04-18
I'm not sure but I think Gutsy Gibbon is using version 7.3 of xorg. [ [COLOR="DarkOrange"]Here's[/COLOR] ](http://en.wikipedia.org/wiki/XFree86) an article about XFree86. Basically it's an interface like X, I suppose.

I'm sorry I can't be of any help. You should get the staff's attention on this issue. They should know what to do. Like I said, I'm pretty new to Linux too.

Edit:

[ [COLOR="DarkOrange"]Your graphics card doesn't seem to be supported well but it appears to be running under the Radeon free driver.[/COLOR] ](http://ubuntuforums.org/showpost.php?p=2545395&postcount=25) ATI and Linux don't get along too well.

---

### Post by Kemono on 2008-04-18
Yes. Looks like ATI's drivers above version 8.28.8 will not [ [COLOR="DarkOrange"]support[/COLOR] ](http://ubuntuforums.org/showpost.php?p=1585558&postcount=55) your graphics card.

---

### Post by seuzy13 on 2008-04-18
Okay, so how do I get the staff's attention? The only real problem is the "substitution error." Without that, I should be able to get it working...

The X.org version and the article about XFree86 helped as well. Now, I know a little more what I'm looking at when I see the recommended/requirements lists for the drivers.

---

### Post by Kemono on 2008-04-18
I have notified one of the staff members. I also found [ [COLOR="DarkOrange"]this[/COLOR] ](http://ubuntuforums.org/showthread.php?t=610589&highlight=bad+substitution) **how to** that might help you. If you haven't already seen it I mean.

---

### Post by seuzy13 on 2008-04-18
Okay, thanks. So, someone is going to take a look at this thread and reply?

---

### Post by Kemono on 2008-04-19
I have also notified one of the administrators. You have to understand that this is not paid support like in Microsoft. They might be busy and can't reply right away, but I'm sure they will see it soon.

---

### Post by matthew on 2008-04-19
Sorry to be a disappointment, but the forum staff are here to keep the *forums* running. The staff badge doesn't necessarily mean we have any more or less ability to answer specific technical questions and issues.

The best bet is to ask, as you have, and hope. This particular issue is a difficult one because of the closed nature of the fglrx drivers. I know people are working on this, but without access to the code it is hard for developers, etc., to know what to try.

We will just have to wait and see if anyone else chimes in here.

For what it is worth, on my laptop (with an ATI card) I am currently using the default, open drivers with good success. The 3D acceleration isn't adequate for the best games, but they are stable and work well otherwise.

---

### Post by Kemono on 2008-04-19
> **matthew said:**
> Sorry to be a disappointment, but the forum staff are here to keep the *forums* running.

I knew that, but on the off chances I might have been right to think at least one of you would know more than I do on this issue.

**seuzy13**, like **matthew** said, your only option might be using your card with the free drivers that come with Ubuntu. At least until someone more experienced can provide a better solution.

P.S.

ATI was a bad investment for me. I'm using the proprietary drivers from ATI, but not even with them I get the full benefit of compiz.

---

### Post by seuzy13 on 2008-04-19
Thanks for your help!

This is a major disapointment, however, because I was wanting to put my computer on standby at night instead of rebooting all the time. This is a long shot, but my other computer has some kind of intel graphics card. Could I maybe swap it out for this one? The only problem is that it is a desktop card and I'm thinking desktop and laptop graphics cards are different.

---

### Post by Kemono on 2008-04-19
That could be a difficult task because:

1. I've never owned an integrated graphics card but I think changing it is not an option. Don't take my word on it, though. I haven't done any research on integrated graphics cards. Ask your computer vendor to be sure.

2. Yes. I think a desktop and a laptop graphics card are two different things. Some IGPs (Integrated Graphics Processors) run from the Motherboard. That means a whole system change is needed sometimes.

---

### Post by seuzy13 on 2008-04-19
Ouch, you're right. Forgot that it was integrated. Yeah, it's a nearly impossible thing in that case. I figured I was just running the driver install script incorrectly in the first place and there was an easy fix...

Oh well. I'll just hold out until I get a different laptop, but that could be years yet.

---

### Post by Kemono on 2008-04-19
There maybe an easy fix but we can't know that without the source code of the ATI drivers. If your card works fine with the free drivers, stay with them. Learn how stuff works in Ubuntu. GNU/Linux is a very powerful system with many capabilities.

Limited budget, eh? Same thing here. Don't worry though. The hardware gets cheaper and cheaper fast. Even now there are some very cheap laptops that will run GNU/Linux easily if you don't need all the bells and whistles of Compiz Fusion.

Take care and good luck.

---

### Post by Roti on 2008-04-29
Hi!

 You have to modify the symlink of /bin/sh to point to /bin/bash. Now it is pointing to /bin/dash.

Roti

---

