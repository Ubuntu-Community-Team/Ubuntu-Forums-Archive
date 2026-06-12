---
title: "graphics card issues"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Phone33 on 2007-03-04
first im sorry if this stuff is a repost

this is my first day w/ ubuntu so go easy on me =)
first thing i want to do is get rid of my password for my log in screen, is there any way to do that

second thing i want to do is to get this [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)
but i dont know what to do with this step 
Add key
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

i tried skipping it and i get this error on the next step
W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
W: You may want to run apt-get update to correct these problems

i have no idea what to do, also
i have a dual monitor set up for and Nvidia FX quadro 1400 and i think i updated my graphics driver, i get that Nvidia logo at start up but i still cant use my second monitor. im new to this  so i have no idea where to go to enable the second monitor

thanks ana look forward to my ubuntu experince

---

### Post by toasterofirony on 2007-03-04
Follow the instruction!

You need the key to verify the repo. Just type what you're told to into the terminal :)

---

### Post by rsambuca on 2007-03-04
Sorry about Toasterofirony's post - it obviously wasn't very helpful.  I think most people on these forums are more apt to help you in a postive fashion.  Anyways...

Welcome to ubuntu!

To get automatic login, from the top menu bar, click Administration -> Login Window.  Enter your password when prompted.  In the Login Window Preferences, click on the Security tab.  Check the box that says "Enable Automatic Login" and select your user name in the drop down menu and then close.

The wget... command gives you access to the repository (the server with the files you need).  To enter that command, open a terminal from the Main Menu -> Accessories -> Terminal
At the prompt, enter the entire command in the terminal and press enter.  It is easiest to just copy and paste the entire row.

Then carry on with the instructions.

Good luck and feel free to ask more questions.

---

### Post by toasterofirony on 2007-03-04
I was /trying/ to be helpful. Following the instructions to any walk-through is pretty darn important.

---

### Post by Phone33 on 2007-03-05
so i tried it from the top and i got this error now 

chris@chris-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:5315): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
chris@chris-desktop:~$ 
 
it still brings up the file im supossed to edit so i just kept going i did these steps 
    * Add the following line at the end of this file (x86 and amd64): 

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

however when i get here 
    * Add key 

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
 my terminal no longer has the 
chris@chris-desktop:~$ prompt so i restart my terminal and do the wget step, it sas ok i save and close the file then when i try to do 

sudo apt-get update

i get this error again

W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
W: You may want to run apt-get update to correct these problems
 
any ideas?

---

### Post by rsambuca on 2007-03-05
A couple of things.  > my terminal no longer has the
chris@chris-desktop:~$ prompt  Are you saving the sources.list after you make the changes and closing the window?  That should bring your terminal prompt back.

I am not sure where that repositiory that you don't have access to is from.  Could you please post your /etc/apt/sources.list here.

And don't worry about that GnomeUI Warning.  It is a bug but doesn't affect anything.

---

### Post by Phone33 on 2007-03-05
where do i get my /etc/apt/sources.list here?

---

### Post by rsambuca on 2007-03-05
You can enter the command ```
gksudo gedit /etc/apt/sources.list
```, then copy and paste the file here.

---

### Post by Phone33 on 2007-03-06
deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev

---

