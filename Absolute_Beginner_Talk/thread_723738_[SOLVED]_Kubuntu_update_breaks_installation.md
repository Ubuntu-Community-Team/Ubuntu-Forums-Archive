---
title: "[SOLVED] Kubuntu update breaks installation"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2008-03-13
Hello.  Last week I decided to ditch my dual boot.  My dual boot was with MS Windows and Ubuntu but I have loved Amarok since I saw it.  Problem was that it didn't work with Ubuntu for some reason.  I used Rythmbox (the default) in the mean time which wasn't bad.  For my clean install I decided to go with Kubuntu just to see if Amarok would play OK on a Kubuntu install and because I use some KDE native apps.  Installation went OK (Kubuntu 7.10), updated the Nvidia drivers and then did the upgrade.  Since the updates are approximately 250 MBs, I left the update running overnight.  In the morning, there is a message box saying taht not all updates were installed (in the background window I can see that the update appears to have stopped while updating the headers).  Upon rebooting, the system is inoperative, The system loads and the loading bar fills completely.  Then the screen goes black and if I touch the keyboard I get into a text login.  I enter my username and password and get to a prompt.  At that point, I reach the extent of my knowledge.  Searching this forum haven't turned information (at least in my view) to solve my problem.  Right now I have reinstalled again and am afraid of updating my system.  Any pointers on what might be wrong?  I observed that there was something wrong with libc6 but is related to 8.04.

---

### Post by Rocket2DMn on 2008-03-13
Sounds like you need to reconfigure X - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
Updating kernel stuff can screw up the nvidia drivers, so you will need to reinstall the restricted drivers.

---

### Post by notbitmonk on 2008-03-13
Thanks.  I'll try it tonight and will post results tomorrow.

---

### Post by notbitmonk on 2008-03-14
Haven't rebooted the computer yet.  The error message was as follows:
[INDENT]There was an error commiting changes.  Possibly there was a problem downloading some packages or the commit would break packages.[/INDENT]
On the background, the bar was processing linux-image-2.6.22-14-generic...  I tried running the updater again and selected show details.  The last line read:
[INDENT]Error encountered while processing
/var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb[/INDENT]
Is there something I can do before I reboot and try Rocket2DMn suggestion?

---

### Post by notbitmonk on 2008-03-14
Well, reboot worked OK.  Tried to continue installation and reached 58% when it stopped because there were too many dpkg error due to missing dependencies.  Will try rebooting again and continue installation.

---

### Post by Rocket2DMn on 2008-03-14
Try
```
sudo apt-get clean
rm /var/cache/apt/archives/*.deb
sudo apt-get update
sudo apt-get upgrade
```
If that doesn't work, please copy and paste all the output here.

---

### Post by notbitmonk on 2008-03-14
Rocket2DMn: saw your post just now, after giving up on Kubuntu and going for plain Ubuntu to try installing kubuntu-desktop after finishing the upgrades.  my computer upgraded succesfully however the question that I have now is, if I change to Kubuntu, will it require to download as many upgrades (249MB)?  This Ubuntu install already downloaded as many upgrades and everything went fine.

---

### Post by tyler_roach on 2008-03-14
if you install kubuntu vi apt:

sudo apt-get install kubuntu-desktop

it will automatically fetch the most recent packages (which will be about 250 mb) so there wil be no need to upgrade anything.

---

### Post by Rocket2DMn on 2008-03-14
with kubuntu-desktop, you have Kubuntu, all it really is is Ubuntu with KDE.  You do not need to reinstall anything.

---

### Post by notbitmonk on 2008-03-14
I understand that all the buntus are equal except for the display manager and bundled apps.  I was thinking that by removing the gnome-desktop, I will get rid of the Ubuntu flavor and keep what would be a clean Kubuntu. When I searched in Synaptic, there was no gnome-desktop.  Of the installed packages, there was gnome-desktop-data and libgnome-desktop-2.  Will I be OK if I remove gnome-desktop-data?

---

### Post by Rocket2DMn on 2008-03-14
Here's how to get a "pure Kubuntu" setup - [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
See the part called "Remove Ubuntu" :)

---

### Post by notbitmonk on 2008-03-14
Thanks for all your help.  Does it matter that I installed Ubuntu and then added Kubuntu?  Will the code in the section "Remove Ubuntu" work in this instance?

---

### Post by Rocket2DMn on 2008-03-14
Yes, that is the purpose of that removal stuff - to get rid of Gnome and the stuff it comes with and leave you with KDE only.

---

### Post by notbitmonk on 2008-03-14
I believe that after all this I can mark the post as [SOLVED] even though I didn't find out what went wrong or how to fix it. If you have the same problem, what we did here is only a workaround.  Although installation was more convoluted than I expected, anyone trying to do what I did will need to follow the next steps:
[LIST=1]
[*]Install Ubuntu (I was using 7.10 supplied in a DVD from the book Ubuntu 7.10 Linux Unleashed)
[*]Update the installation
[*]Install your printers.  Mine was an Epson Stylus CX7400 which was installed automatically however the scanner wasn't working meaning that I will resolve the issue later by installing sane-backends, trying to compile the sane-backends from source or trying the epson avasys drivers.
[*]Install kubuntu-desktop following the code from Psychocats "sudo aptitude update && sudo aptitude install kubuntu-desktop" or by using Synaptic
[*]Select KDM as your default desktop manager
[*]Reboot or log out.  Select KDE as your session (located after you click on the bottom left image of the login screen)
[*]Follow the instructions at [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[/LIST]
And there you have it.

---

