---
title: "When Dapper Drake is ready for primetime"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-04-17
How will the update work?  Do I have to move all of my data to another drive or partition?  Will it look at my Breezy Badger install and save my preferences?  And most importantlly, how will I install it?  Do I burn an ISO, or will there be an easier route to take.

---

### Post by macdo on 2006-04-17
I think, subject to verification, that you just have to modify your /ect/apt/sources.list, then update and upgrade. That should keep all settings and data. but don't take my word for it!

---

### Post by aysiu on 2006-04-17
This is why it's good to have a separate /home partition--that way, no matter what happens during an upgrade, you can always do a clean reinstall and keep your settings and files intact.

That said, if the upgrade does go as planned, your settings and files will be intact, and even if it messes up, people here will usually help you fix it.

To do a proper upgrade, you would, assuming you have Ubuntu (and not Kubuntu), go to Applications > Accessories > Terminal ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` Then, you would ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_breezy
sudo gedit /etc/apt/sources.list
``` Do a find/replace of the word *dapper* for the word *breezy*. Now, this next step isn't necessary, but I would strongly advise it: Log out, press Control-Alt-F1, log in, and type ```
sudo /etc/init.d/gdm stop
``` Then type ```
sudo apt-get update
sudo apt-get dist-upgrade
sudo /etc/init.d/gdm restart
```

---

### Post by Marquis_de_Carabas on 2006-04-17
I think Dapper is more than ready for the primetime. Obviously your mileage may vary, I take no responsibility for loss of data/sanity etc. but I upgraded a week or so ago - using the same steps as aysiu just recommended - and haven't looked back. I loved Breezy, and I love Dapper even more! :D

---

### Post by nalmeth on 2006-04-17
I also think it's ready for everyday use, and also will not guarantee it ;)
I have heard that there are issues when upgrading to dapper, if you have run a lot from automatix, like firefox 1.5, and stuff like that. 
You may be better off moving your /home to another partition, and installing dapper from the CD.
With your /home on its own partition, you can go either route (apt-get dist-upgrade OR fresh install)

---

### Post by BarFly on 2006-04-17
That was relativelly painless, but leaves me with further questions.  I got command not found when using this sudo /etc/init.d/gdm stop .  As this was the optional step (but stronglly recommended), I skipped it.

I thought I botched the install when I watched the screen rapidlly scroll through text too fast for me to read.  I then hit the power button, thinking everything was fcked.  I booted into Dapper Drake and it told me I had 621 upgrades available!  If you shut down a Windows install, you are sht out of luck, apparantlly that is not the case with Ubuntu.

Ok, my real question is whether it is better to do a clean install for Linux.  I always did that for Windows and this is the first time I did not do a clean install.

---

### Post by BarFly on 2006-04-17
Oh! This is a more important question.  Many noobs like myself would like to know how to move your home directory to a different partition or HDD.  Do you just drag and drop?  I am not that ignorant to cause me to not be able to back-up my home files.  I want to know (and probabally other noobs want to know) how to tell Ubuntu to look for the home directory on a different HDD or partion.

Thanks for all your help!  I have never seen a support board that gives real advice before this!

---

### Post by jimrz on 2006-04-17
In the partitioning section of your new install you will be shown a list of detected partitions, find the one you copied /home to and change what ever it shows for mount point to "/home" but do not have the installer format it.

---

### Post by BarFly on 2006-04-18
Clean install?  Is this the best route to take?  For sure you should do that for Windows, what about Linux?  I am trying to learn how this OS works.

I have Dapper Drake now, but am wondering if  I should have done a clean install.

---

### Post by angkor on 2006-04-18
[QUOTE=BarFly]I have Dapper Drake now, but am wondering if  I should have done a clean install.[/QUOTE]

Does that mean you dist-upgraded from breezy to dapper? If so and everything works it really isn't necessary to do a clean install.

If you installed dapper from one of the flight cd's you will have a clean dapper when it's released by installing the (daily) upgrades that come along.

---

### Post by htinn on 2006-04-18
Doing the dist-upgrade method has pros and cons.

Pros: less downloading (a LOT less uploading if you use bittorrent), less reconfiguring, less remembering what settings/plugins/extensions you like to use

Cons: more likely to toast your system if you get stuck in the middle, your system might not even boot (especially old G4 PPCs) with the new kernel, old applications are more likely to experience "breakage"

---

### Post by BarFly on 2006-04-18
Yup, I upgraded from Breezy to Dapper following the instructions above.  I was concerned that crap from the Breezy install would be left behind.  That is why I asked whether it is best to do a clean install.  That happens when upgrading Windows, I guess it does not happen for Ubuntu.  Most importantlly, I had zero data loss from the home directory.  I think I might be in love with Ubuntu...

/loving Linux more and more every day

---

### Post by BarFly on 2006-04-18
I take back everything I posted.  Dapper Drake told me there were updates available.  I installed them and rebooted, using the instructions.  Uh, I could not boot into anything.  Now I am back using 5.10, and lost all data as I did a fresh install (not really a problem as I back up crucial personal files).  I am not bitter (although a tad pissed off).  Hey, the OS is free.

Geez, now I have to reinstall FF 1.5.02, etc.

---

### Post by aysiu on 2006-04-18
[QUOTE=BarFly]
Geez, now I have to reinstall FF 1.5.02, etc.[/QUOTE] Automatix, my friend.

Or, for just Firefox, [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by angkor on 2006-04-18
[QUOTE=BarFly]I take back everything I posted.  Dapper Drake told me there were updates available.  I installed them and rebooted, using the instructions.  Uh, I could not boot into anything. [/QUOTE]

Well now, that went awry! ;)

Do you remember what caused the boot to bork? I can't imagine it was something you couldn't get fixed by posting here. :)

---

### Post by BarFly on 2006-04-18
Yeah, htinn, Dapper Drake did a number on my box!  Everything is fine now, but that was a serious pain in the butt.

---

### Post by BarFly on 2006-04-18
When booting, I got warnings saying that gtk is not working.  Upon reinstalling 5.10, I got conflicts (imagine that).  That makes sense as I had Dapper Drake installed.

---

### Post by angkor on 2006-04-18
[QUOTE=BarFly]When booting, I got warnings saying that gtk is not working.  Upon reinstalling 5.10, I got conflicts (imagine that).  That makes sense as I had Dapper Drake installed.[/QUOTE]


Oh that's just graphical stuff. You could have fixed that! :);)

---

### Post by BarFly on 2006-04-18
Ok, I learn something everyday.  I could have fixed it instead of reinstalling.  Now I am using Dapper Drake.  For sure I will post on this thread if I have the same boot problem as the the prior install.  Thanks to all for your help.  Now, to shut down and reboot.

---

