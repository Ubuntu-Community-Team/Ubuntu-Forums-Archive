---
title: "Bluetooth Bug Workaround?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by boardfoot on 2008-04-08
Hi guys,

I tried to get help in the install forum but got nowhere fast. I'm hoping someone who frequents here can help a linux noob get his new laptop to install or even run ubuntu.

I get a "* Starting Bluetooth Service" hang on startup and installation. I can't even use the Live CD (7.10 & 8.04)

I did some digging around and happened upon a hundred year old bug reports on this. Did anyone find a workaround? Is bluetooth going to prevent me from installing ubuntu on my new ferrari?

Launchpad bug # 106977 (among others)

Can someone please help. I can't be seen running Vista... I'll lose my marbles chasing bugs and viruses all day long.

---

### Post by dstew on 2008-04-08
> I get a "* Starting Bluetooth Service" hang on startup and installation. I can't even use the Live CD (7.10 & 8.04)Were you able to install a system? Did you try the Alternate Install CD?

---

### Post by boardfoot on 2008-04-09
I tried every version of ubuntu and even debian.

Seems only Vista runs without a hitch. Worse than this... HP can't even tell me what chipset is in my machine for the ethernet so I cannot even seek out an internet install.

Alternate CDs, safe mode, you name it. I get the same error in the same place. I see that there is a bug posted from a year ago but I have not heard or found any information on a workaround.

I can't install or run any linux OSes so far.

I'm totally bummed.

---

### Post by dstew on 2008-04-10
> Alternate CDs, safe mode, you name it. I get the same error in the same place.Again, are you getting this error from an installed system or from the Live CD? If it is from an installed system that won't boot, you should blacklist the hci_usb driver.

---

### Post by nge on 2008-04-10
have you tried to turn off your bluetooth device before starting the Live CD ?
(maybe you need to do it from BIOS first)

---

### Post by boardfoot on 2008-04-11
Thanks for your attempts.

I cannot boot the Live CD (I've tried 7.10 and 8.04, all burned fine since they work on this system I am using now).

I can't even get to a terminal prompt. It just hangs.

Very frustrating.

---

### Post by dstew on 2008-04-11
Try the Alternate Install CD. It uses a text-based installer that should work. You can get it from the Ubuntu download page, check the box below the Start Download button.

---

### Post by boardfoot on 2008-04-11
Alternate CD does same thing ;(

Anyone know of anyone else in Edmonton, Alberta, Canada who can look into this in person?

I'd pay to avoid Vista... but I must admit I don't ever have these kinds of probs when I try to install a windows based OS. Drivers don't work... no prob the device just won't work... Linux the OS goes to poop. 6 of one... half dozen of the other...

I'm pretty much reserved to Vista at this point. I can't even get any info on the ethernet chipset from HP for my laptop... so finding drivers is stupid regardless. HP just posts the drivers for the card I see... just not any info on them... awesome service from them too.... NOT.

---

### Post by bbmack on 2008-04-12
I have had the same issue with both 7.10 and 8.04.  I am using a dv9736ca.  I installed both versions with the alternate CD.  With 7.10, when it locked up I went to the command line (ctl-alt-f1), logged in and entered &#8220;startx&#8221;.  This brought up X and I was able to go into services (system/administration/services) and disable bluetooth.  

With 8.04 I ended up adding &#8220;exit(0)&#8221; to the beginning of /etc/init.d/bluetooth to stop it from loading.  I could then disable bluetooth in services.  In order to complete the upgrades I commented out the &#8220;exit(0)&#8221; line once bluetooth was disabled and then it continued to work.

Remember this is a workaround, it does not solve the problem.

---

### Post by JimmyBEng on 2008-04-13
> **dstew said:**
> Were you able to install a system? Did you try the Alternate Install CD?

this is the first question to answer.  Have you been able to install at all?

if yes and you have some access to the command line try this

open the blacklist file
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the following to the file
```
## causes error while loading
blacklist bluetooth
```

this will prevent the bluetooth module from loading.  If you are hanging during the install process, i am sure there is an equivalent method (i just don't know it)

Once you get into a position where you are running, you may want to investigate the real reason for the problem.  I saw the same symptom at first on my dv9500, but the problem was with the uvcvideo module.  It was crashing during load and taking down anything connected to USB, including bluetooth.

check that by running dmesg after you start, and look in the output for something like 'MasterAslan' saw in this post :[http://ubuntuforums.org/showpost.php?p=4254811&postcount=352]("http://ubuntuforums.org/showpost.php?p=4254811&postcount=352")

If that turns out to be your problem, my solution is a couple posts later in that same thread.  Short version: blacklist uvcvideo instead of bluetooth.

---

### Post by bbmack on 2008-04-14
> **JimmyBEng said:**
> 
If that turns out to be your problem, my solution is a couple posts later in that same thread.  Short version: blacklist uvcvideo instead of bluetooth.

Thanks, this worked for me.  I blacklisted uvcvideo, then a reboot, then I enabled bluetooth again and did a reboot.  No bluetooth hang.  Now, I don't use bluetooth on this system, but it would seem that if I did, I could.

Back to try it with 8.04...   EDIT:  This worked as well.  Note, this is the beta version.

Thanks again

---

### Post by boardfoot on 2008-04-17
The UVCVIDEO blacklisting solved the problem.

I am eternally in your debt.

I don't have to run that Virus... I mean Vista ;) which leaves me beaming :)

I tried all of the apic workarounds, etc. for days... none helped.

I installed 7.10 fresh and simply edited the blacklist file.

Newbies here is a step by step (I had to take a crash course... which has made me more comfy in my linux backend but was an exercise in frustration for days... maybe I help with the frustration factor with this step-by-step for total newbies...)

Step1. 

Install Gutsy (7.10) with the **ALTERNATE CD**. The Live CD will puke so avoid it.

Step 2.

Install in text mode (first option)

Step 3.

Follow the install instructions and let it do its thing. It will ask you to reboot when it is done.

Step 4.

It will reboot and it will look good until you get hung up on the "* Starting Bluetooth Service "
Now press: **Ctrl + Alt + F2**

You will see a text based login. Enter your login info you setup at install.
You will see a prompt now.
Type the following:

**sudo nano /etc/modprobe.d/blacklist**

You will be prompted for a password... enter it as you setup in install

You will then have a screen with a bunch of settings. press **CTRL + V** to scroll down to the bottom. When you get to the bottom press **Enter** until you have a space in between the last line. Now you must type the following:

[B]# causes error with ricoh 1812 webcam that disables USB
blacklist uvcvideo[/B]

Press **Ctrl + O** (letter) to save file
Press **Enter** to confirm the save
Press **Ctrl + X** to exit Nano

Press **Ctrl + Alt + Delete** to reboot system

You should see the splash bar go all the way to the end and a couple flashes.

Then Ubuntu will cry foul and say that the video driver is not correct.

Press **Continue** to carry on. We'll sort this out later.

You see a login screen and do your thing.

Then when it loads you will be bombarded with update notification and restricted driver notifications.

Ignore the Restricted Drivers portion for now (hit the little x top right of bubble to hush it up.

We want to focus on the OS updates first. Then we'll tackle the video drivers. In my brief experience... do your drivers last and your core updates first. I won't go into why... just trust me.

Update your 500+ updates and let it do it's thing. It'll ask you to reboot and do so.

Then you'll log back in... get that restricted driver notifications again. Now we'll deal with it.

Open it and click on the Nvidia listing and enable it. It'll download the drivers and ask you to restart. Do so.

You come back to the desktop upon reboot but fear not the 640x480 screen res. We have to make some adjustments to the screen and res to line them up higher. (just like windows).

Click on **System > Administration > Screens & Graphics**

You'll see some defaults and 640x480 as your only option.

Click on the **Screen Model** and select the type of monitor and the highest resolution your vid chip supports. Then select the desired resolution below it (doesn't have to be the same... you can select a lower res than max if you so desire). Click OK and it'll tell you you need to log out and back in for the changes to take effect. I suggest rebooting...

Upon reboot, you may find that the screen res is still not quite right. Go back into **System > Administration > Screens & Graphics** and change the resolution to the one you want (not sure why it sometimes doesn't stick, but it should the second time around). It should ask you if the res is good.... select yes if you can see it.

Voila... you're in, you're updated, and you have a screen big enough to view all the progs you need.

You will need to search around for info on getting your other peripherals working and I'll leave that to you.

Hope this helps. Thanks to those who helped me solve this annoyance. This is what the Linux movement is all about and I'm proud to count myself among you.

Now some keywords for searches:

HP
DV9000
DV9808
DV9808CA
DV7000
HPDV9808CA
HP Laptop Bluetooth error
HP Laptop System Hang
HP Laptop LiveCD error

Regards,

Jason

---

