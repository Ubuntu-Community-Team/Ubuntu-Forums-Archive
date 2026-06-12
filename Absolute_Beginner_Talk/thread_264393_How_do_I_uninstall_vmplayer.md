---
title: "How do I uninstall vmplayer"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-24
I need to reinstall vmplayer, but I was told to uninstall first. It doesn't show up in add/remove. So, how do I do this?
Larry

---

### Post by pdub on 2006-09-24
Open terminal and type:

sudo apt-get remove vmware-player

sudo apt-get install vmware-player

---

### Post by HareBall on 2006-09-24
> **pdub said:**
> Open terminal and type:

sudo apt-get remove vmware-player

sudo apt-get install vmware-player

Thank You,
Larry

---

### Post by HareBall on 2006-09-24
> **pdub said:**
> Open terminal and type:

sudo apt-get remove vmware-player

sudo apt-get install vmware-player

OK, I uninstalled and reinstalled. Then I got an error message saying:
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
What next, after I try to uninstall and reinstall again?

---

### Post by pdub on 2006-09-24
What Kernel version are you running? To check, type:

uname -r

Also, check that your kernel headers match your kernel version.

Type:

ls -al /usr/src/linux

Make sure that the symbolic link for **/usr/src/linux** points to **/usr/src/linux-headers-'your kernel version from uname -a'**

Did you get any errors when reinstalling vmware-player?

---

### Post by HareBall on 2006-09-24
> **pdub said:**
> What Kernel version are you running? To check, type:

uname -r

Also, check that your kernel headers match your kernel version.

Type:

ls -al /usr/src/linux

Make sure that the symbolic link for **/usr/src/linux** points to **/usr/src/linux-headers-'your kernel version from uname -a'**

Did you get any errors when reinstalling vmware-player?

The errors are listed above. They were the same both times I uninstalled and reinstalled.
Kernal is 2.6.15-27-386
And I got this when I did the second thing you asked me to do:
larry@larry-desktop:~$ ls -al /usr/src/linux
ls: /usr/src/linux: No such file or directory
As a side note: I went to play a game earlier and one of the games I had tried to install earlier was there and working, so maybe I don't have a problem with vmware after all. I still have sound problems(no sound), but that is anothere thread.
Larry

---

### Post by pdub on 2006-09-24
Has vmware-player ever worked on this system? Did you upgrade the kernel since it was installed? Vmware is fussy about kernel versions.

If vmware-player worked previously then try booting with the older kernel. You probably have multiple choices during boot. i.e. 

Ubuntu, kernel 2.6.15-26-386

Ubuntu, kernel 2.6.15-25-386

Otherwise, you can install kernel headers and then attempt to re-install vmware-player. I am running the same kernel as you and player works fine.

Follow these instructions to install the headers

[B]sudo apt-get install linux-headers-2.6.15-27-386 -y

sudo ln -s /usr/src/linux /usr/src/linux-headers-2.6.15-27-386[/B]

Then try to uninstall and reinstall vmware-player again.

---

### Post by HareBall on 2006-09-24
> **pdub said:**
> Has vmware-player ever worked on this system? Did you upgrade the kernel since it was installed? Vmware is fussy about kernel versions.

If vmware-player worked previously then try booting with the older kernel. You probably have multiple choices during boot. i.e. 

Ubuntu, kernel 2.6.15-26-386

Ubuntu, kernel 2.6.15-25-386

Otherwise, you can install kernel headers and then attempt to re-install vmware-player. I am running the same kernel as you and player works fine.

Follow these instructions to install the headers

[B]sudo apt-get install linux-headers-2.6.15-27-386 -y

sudo ln -s /usr/src/linux /usr/src/linux-headers-2.6.15-27-386[/B]

Then try to uninstall and reinstall vmware-player again.


It's kinda funny, it seems to be working fine, it just gives error messages every time I use it. So far most everything I have installed with it is installed.
Guess that's all that matters in the end, huh.
Larry

---

### Post by pdub on 2006-09-24
I am running vmware player 1.0.1 build-19317 and I don't get any errors. 

As long as it works for you, then I guess problem solved.

If you are still having problems then you might want to start another thread.

Have a good night!

---

### Post by grizz_granlien on 2006-10-09
I tryied VMplayer don't like it I like VMServer it runs faster I find it loads windows XP Faster and it runs nice as well..

when the kernal changes in Ubuntu you need to fix the VMware to tell it the new kernal her is how you do it
 
type
uname -r

and write down answer then type
sudo aptitude install linux-headers-answer

when done type
sudo /usr/bin/vmware-config.pl

this will work all the time and it will ask you questions just hit enter a lot and it will work when it is done okay... Hope that works for you in the future or anyone els that needs this help I recived this info from someone els on here before and it helped me...

>>>---> Grizz <---<<< e-mail [email]wgranlien@shaw.ca[/email] or [email]grizz@grizzsden.com[/email] or .ca

bye

---

