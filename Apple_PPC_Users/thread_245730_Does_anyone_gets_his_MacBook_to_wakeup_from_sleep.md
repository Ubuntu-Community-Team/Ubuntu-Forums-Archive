---
title: "Does anyone gets his MacBook to wakeup from sleep?"
date: 2006-08-28
forum: Apple PPC Users
---

### Post by Entity on 2006-08-28
Does anyone gets his MacBook (non-pro) to wakeup from sleep in Dapper Drake???

If yes, how did you proceed!?

Mine seems to wake up but the screen remains turned off.

---

### Post by goneskiing on 2006-08-28
Here is what I have found so far (on 15in MacBook Pro)

For AC:
I have set suspend on sleep (in my case 30 mins).  This seems to work fine - I click my mouse and type in my password. and there's my dialogs

For cover close, I chose hibernate - this requires a new boot but upon entering Ubuntu leads back to the main screen - seems to work okay

For battery:
I have suspend on sleep (20 mins) - works okay but computer seems to run during the suspend and uses up lots of battery

For cover close I use suspend and it too resumes immediately but constantly runs and uses up battery - while this works so well on OSX, basically not the right option for Ubuntu.  Plus if I put it in bag (ie leaving cafe to go back to office) the machine gets really hot.  Basically need to shut down when moving.

---

### Post by blot0 on 2006-08-29
i had the same problem with using suspend..
my screen wouldnt come back on after going into suspend mode.

i read the sleep section from [http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)
and the adding exit 0 bit seemed to fix the issue for me.

i guess its kinda a suspend to ram feature, shuts mostly everything off.. but will still drain the battery to keep the data in ram.
but there is an option in power managment, that if the battery gets low it will change to hybernate.

---

### Post by Asgaard on 2006-09-22
that doesn't fix it for me; i've tried a HEAP of stuff and couldn't make it come back from sleep. according to Lortie's page there, all his fixes were merged into Ubuntu and should have been available with the security updates this week and the previous, but still no joy.
i press keys, use the touchpad, press the power buton, nothing brings it back up from sleep. SIGH

also the Gentoo people seem to have the right kernel patches or something cause they report [here](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad_in_X11) that the touchpad works in synaptics mode, including scrolling. i  can't get Xorg to see my touchpad, it keeps saying no touchpad was detected. i've tried every combination of Device and Protocol values in xorg.conf to no avail.

could someone that has these things working, post simple instructions from a fresh install?

---

### Post by stmiller on 2006-09-22
An OLD work-around that fixed it for some ATI video card laptops in the past was to add a line

Option          "AGPMode"               "4"

in /etc/X11/xorg.conf under

Section "Device"


Not sure if that is in there by default with ubuntu.

---

### Post by Asgaard on 2006-09-23
here's some progress i made: i compiled the new 2.6.18 kernel from some days ago with the mactel patchset they mention in the gentoo wiki, and the config they provide. the first difference i noted is it includes a HEAP less modules and stuff so it compiles and boots faster, and it doesn't have that irritating apic kernel panic.
also the synaptics driver finally works and i have scrolling.
i haven't checked out what parts of ubuntu don't find expected kernel features, but i hope i don't find any.

sleep STILL does not work for me but i'm determined to keep trying.

---

### Post by vagabond_gr on 2006-09-24
Asgaard, that's good news. I was planning to do the same after reading the Gentoo page, but I didn't have the time yet. Maybe I'll do it one of these days. Anyway please keep us posted in case of any progress.

Thanks,
Kostas

---

### Post by Asgaard on 2006-09-24
with a dual core processor and that config, compiling is a breeze.
just apply the patches and put the config into place, then set CONCURRENCY_LEVEL=4, then make-kpkg --initrd buildpackage
~6-7min later you have fresh .debs in the parent directory ^__^

---

### Post by Entity on 2006-09-25
> **Asgaard said:**
> with a dual core processor and that config, compiling is a breeze.
just apply the patches and put the config into place, then set CONCURRENCY_LEVEL=4, then make-kpg --initrd buildpackage
~6-7min later you have fresh .debs in the parent directory ^__^

Using which kernel did you do that? 2.6.18 vanilla or Ubuntu's latest kernel (dapper or edgy?)

I was unable to compile on vanilla and edgy's. Maybe you can provide us with the deb packages?

---

### Post by Asgaard on 2006-09-26
the image and headers debs are 9mb, i have nowhere to put them :/

i used vanilla 2.6.18 from kernel.org, blscreen's config from the ubuntu wiki, and all mactel patches except sigmatel (breaks sound)

blscreen's config:
wget -O config-macbook-blscreen [http://omnibus.uni-freiburg.de/~s8rasand/config](http://omnibus.uni-freiburg.de/~s8rasand/config)
cp config-macbook-blscreen <PATH TO KERNEL SOURCES>/.config

mactel patches using subversion:

svn co [https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.18](https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.18) mactel-patches-2.6.18
cd mactel-patches-2.6.18
#remove the sigmatel patch here, i forgot the filename
./apply <PATH TO KERNEL SOURCES>


then cd to the kernel source dir, and do as root:
export CONCURRENCY_LEVEL=4
make-kpkg --initrd buildpackage

i mispelled that last command on my previous post, sorry ^__^

after compiling is done, the .debs are in the kernel source parent directory

see if sleep works for you with that setup, if it does then either i borked my userland while fiddling with it or my macbook straight out hates me :/

note that to get synaptics to work in X, you'll need to load the usbhid module AFTER appletouch, which is the inverse from the default. to fix that, put the following two lines into a file /etc/modprobe.d/touchpad:
options usbhid pb_fnmode=2
install usbhid /sbin/modprobe appletouch && sleep 2 && /sbin/modprobe --ignore-install usbhid $CMDLINE_OPTS



this is pretty much straight out of the gentoo wiki, but still, i hope it clears up things a bit.

---

### Post by auximini on 2006-09-26
I think our Macbooks hate both of us. I followed along with the Gentoo wiki and I'm unable to get sleep to work. Hibernate doesn't even work, however, it works with the stock ubuntu kernel.

I've also tried running an -rc4 kernel with revision 41 from the mactel patches (41 was for -rc4). Still doesn't work, although -rc4 was confirmed in the gentoo wiki.

I'd be happy if I could get hibernate working ... checking out my kernel config now.

---

### Post by auximini on 2006-09-26
Following the instructions at [http://www.suspend2.net](http://www.suspend2.net), I'm able to get the macbook to hibernate now. suspend2 has support for s2ram, but it still doesn't work. For the time being, I'm satisfied with hibernate, although s2ram would be great.

---

