---
title: "PPC install - screensaver freezes desktop"
date: 2004-12-17
forum: Apple PPC Users
---

### Post by stynx9000 on 2004-12-17
Hey folks,

Brand new here and brand new to Ubuntu.  So far I'm really enjoying it!  

I've got a brand-spanking new install (4.10 I believe) on my Mac G3 - It's a 450 Mhz ppc with 1 GB of RAM.

Everything seems to be working flawlessly except the screensavers.  When I turn screensavers on (set to the random default selections) they'll activate and after 5-10 minutes of doing there thing the whole system will freeze up.

This also happens when I'm working in the Desktop Preferences-> Screensaver GUI, not just when previewing but when just moving through the GUI.

I thought maybe something had gone wonky on the install so I reinstalled but have the same exact problem.  All updates were automatically applied on install, but other than that it's a vanilla installation.

Any suggestions?

Thanks,
Ben

---

### Post by chascon on 2005-01-06
This is my post that works for me.  You might have to change things (ie, the r128 or ati in /etc/module will have to radeon if you have a radeon card, and the /etx/X11/XF86Config-4 would have to change correspongly in the Diver part) if you do not have the Rage 128 video card, check but you might.  I hope it works for you and I only ask that you get involved in actively reporting the bug to the bug links below as I get the distinct impression this bug is thought to be remote. 



This is what works for me on debian-ppc for my old iMac DV slot loading 400 mhz with a Rage 128 VR. Maybe someone could try this on their iMac if they are at their wits end. Remember ubuntu activiely discourages mixing debian with ubuntu so take responcibility. I'd do this myself if I didn't have my debian-ppc running nicely.

Please post results.

What woud be intersting is if one went to F1 (cntrl-option F1) and as su added
deb [http://people.debian.org/~daenzer/dri-trunk/](http://people.debian.org/~daenzer/dri-trunk/) ./
to the
/etc/apt/sources.list
did a
apt-get update
then uninstalled xserver-xfree86 and installed xserver-xfree86-dri-trunk

-removed rss-glx
-removed xscreensaver-gl
-turn off xscreensaver latter in X
or even remove xsceensaver (there will be a warning about a dep named desktop? but I've been told this is only a place holder so this should be nothing to worry about)
(on debian-ppc make sure you don't have: xscreensaver xscreensaver-nognome xscreensaver-gl)

X Config
then change default depth to 16 in XF86Config
-make sure "Load DRI" is enabled
-maybe make sure r128 is included rather than ati as driver (for the Rage 128 video card)

PS-the default xfree86 in debian-ppc freezes the screen, as does installing xscreensaver xscreensaver-nognome xscreensaver-gl so there seem to be two issues here in debian-ppc at least. Ubuntu dev please take heed and maybe talk to Daenzer (Mr.Cooper?) to ask why he made his branch of xfree86 and how it works. And maybe pick up an old iMac with the said video card. They are cheap.

Oh and panickedthumb, you mind posting your XF86Config file so that we all could benefit from your discover of 1500 fps?

The below is not a bad idea, although I have never noticed a diff doing this:

# sudo nano /etc/modules
if not already present add

uninorth_agp
agpgart
r128

If XF86Config says r128 then this should be r128 else if it says ati, then I imagine this should say ati

followup:

Re: ATi Rage 128 and DRI
I myself reported this bug (Rage 128 freeze when enabling DRI) in bug 4125 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=4125](https://bugzilla.ubuntu.com/show_bug.cgi?id=4125)). You yourself deemed it a duplicate of 2411 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=2411](https://bugzilla.ubuntu.com/show_bug.cgi?id=2411)). It was then reported as fixed in hoary. I dist-upgraded to suffer the system freeze with DRI enabled in hoary.
So no, this problem has been reported ubuntu bugzilla and as my documentation in thos reports show, it is widely reported in other distros. So in answer to the question if there is a problem here, it's self-evident.

I took my own words and installed ubuntu-ppc last night again. I uninstalled xserver-xfree from console and installed xserver-xfree86-dri-trunk after adding the the appropiate source to the sources.list.
Removing xserver-xfree removes ubuntu-desktop, x-window-system-core, xfree86-driver-synaptics, and x-server-xfree86. I also removed xscreensaver, xscreensaver-gl, and rss-glx. I then configured XF86Config-4 to detail Driver r128, and set the default depth to 16. I then added agpgart, uninorth-agp, r128 to /etc/modules and reinstalled x-window-system-core.

The result?
I have X with accel now, glxinfo | grep "direct rendering" puts out "yes" and it hasn't crashed all night.
To be fair, I've gotton accel working without the /etc/modules stuff, but apparently it shoud work better with agpgart, uninorth-agp, r128 added to /etc/modules.

The only issue, if it is one, is that I can't install the recommended libglide2 and drm-trunk-module as they seem to be obseleted or simply not in the repositories I have in sources.list. I know I can get them from the debian-ppc ones but not sure if I should do this (ramifications?). Yes I know libglide2 is old. (Funny thing is that debian-ppc sarge suggests libglide3 not 2 during this process.)

Of course, the other concern is how will this affect an upgrade to hoary. I guess to be on the safe side one could remove xfree86-dri-trunk and then dist-upgrade. Then check thru to see that no undireable packages were installed during the upgrade post-upgrade. I'm sure there is an elegant wa to do this. Please feel free to add.

Chascon

PS-I apprecite your enthusiasm daniel but there is obviously a problem with the Rage 128 VR on mac-ppc. I just happen to be one of the few ppc users that is bothering to report this problem. But this does not mean it doesn't exist as luboshiq himself has reported in this thread. By the sounds of it, he has the same model as mine, " iMac G3 with slot-loading CDRW ... Rage 128", but with the CDRW. This would have been the Grey iMac slot loading from 1999, the step above mine with a CD-RW built in rather than just the CD/DVD reader I got.


PS-
As you might have guessed, this was previously posted under "ATi Rage 128 and DRI".

---

### Post by chascon on 2005-01-06
oh and try not to double post.  Get back with your results.  Particiapte (in this and the reporting of bugs) to make this distro better for "your" hardware.

---

### Post by chascon on 2005-01-07
[http://www.ubuntuforums.org/showthread.php?t=3723&page=3&pp=10&highlight=freeze](http://www.ubuntuforums.org/showthread.php?t=3723&page=3&pp=10&highlight=freeze)

The topic is currently developing in the above thread.

---

