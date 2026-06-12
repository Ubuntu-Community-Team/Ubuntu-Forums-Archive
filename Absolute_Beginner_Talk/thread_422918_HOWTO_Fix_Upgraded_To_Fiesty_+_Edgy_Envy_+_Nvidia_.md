---
title: "HOWTO: Fix Upgraded To Fiesty + Edgy Envy + Nvidia graphics driver issues"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by slayerboy on 2007-04-25
I've seen posts recently regarding having problems with Nvidia drivers and upgrading to Fiesty and used to use Envy.  I'm not sure if this is a widespread thing, but I posted this in another topic and felt it would be beneficial to post a fix that seems to work, but might break other restricted hardware.  Use at your own risk, and if in doubt post the error you're getting when you try to boot to X with an Nvidia graphics card and/or you don't know which drivers you should be using.

CTRL+ALT+F1 to a terminal screen, then login and type:
```
sudo killall gdm
sudo aptitude search nvidia
```Now when it lists packages with Nvidia in them, you might see some with "i"'s next to them on the left. If there are, type this [COLOR=DarkRed](and only type the red if you don't have anything like wireless cards or anything else configured with the restricted manager)[/COLOR]:

```
sudo aptitude remove <REPLACE PACKAGE NAME HERE> <2ND PACKAGE NAME> <ETC, ETC, ETC>
[COLOR=Red]sudo aptitude remove envy linux-restricted-modules[/COLOR]
```Now change your xorg.conf to change to the NV driver and restart your system.

Now try installing the nvidia-glx-new package, [COLOR=DarkRed]nvidia-glx, or nvidia-glx-legacy depending on which one works, but try in order,[/COLOR] (IRC you can do this from add/remove programs) and then reboot. If you don't see the Nvidia logo when X comes up, edit the xorg.conf and change the driver to Nvidia and it should work.

Good Luck! :KS

---

### Post by five2one on 2007-04-27
thank you!

---

### Post by slayerboy on 2007-04-29
> **five2one said:**
> thank you!
You're welcome!  Glad it worked for you!:KS

---

### Post by Pjotrik on 2007-05-01
Thank you. This is the first guide that I've found that is working, but when I reboot I get the same error with X.

---

### Post by slayerboy on 2007-05-01
> **Pjotrik said:**
> Thank you. This is the first guide that I've found that is working, but when I reboot I get the same error with X.

Which particular Nvidia card are you using?  You'll be surprised what cards are now considered legacy.  Have you tried each different nvidia driver? (nvidia-glx-legacy, nvidia-glx, nvidia-glx-new)  Repeat the steps above to try each one.  One of them should work following these steps.  Also, post your xorg.conf and we might be able to help evaluate that for you as well.

---

### Post by mitanc on 2007-05-01
I installed on Edgy using the envy script.  Like an idiot I upgraded to feisty without removing the envy drivers and X crashed when loaded.  I changed back to the "nv" driver and life is good, but I can't get back to using the nvidia drivers.  I followed the above and purged the nvidia stuff.  I did apt-get for the nvidia-glx, nvidia-glx-new, and nvidia-glx-legacy.  One at a time and in that order, none work and when X tries to start it just says its missing the nvidia.ko module in the kernel.  

Any idead how to fix this?  I think I need to remove what envy did and then reinstall the restricted drivers?  Anyone know how to remove the old envy stuff?

---

### Post by Pjotrik on 2007-05-01
> **slayerboy said:**
> Which particular Nvidia card are you using?  You'll be surprised what cards are now considered legacy.  Have you tried each different nvidia driver? (nvidia-glx-legacy, nvidia-glx, nvidia-glx-new)  Repeat the steps above to try each one.  One of them should work following these steps.  Also, post your xorg.conf and we might be able to help evaluate that for you as well.

I tried all nvidia drivers twice, but it works only with nvidia-glx-new. I have Geforce 6200 and here's my xorg : [http://www.sendspace.com/file/bazwc5](http://www.sendspace.com/file/bazwc5)

---

### Post by staib on 2007-05-01
> **mitanc said:**
> I installed on Edgy using the envy script.  Like an idiot I upgraded to feisty without removing the envy drivers and X crashed when loaded....

I too did this - had used Envy on 6.10 then simply upgraded to 7.04. At first it looked like there was a problem but after re-booting completely it sorted itself out and displayed 7.04 with the previous nvidia settings. 

The only issue I have is that the automatic updates alert 'thinks' there are two updates needed (nvidia-glx and nvidia-glx-dev) but there are errors trying to install these and it just aborts the upgrade.

Is there anything I can do to 'fix' this?

Cheers,

Nick

---

### Post by Splinter on 2007-05-02
> **staib said:**
> I too did this - had used Envy on 6.10 then simply upgraded to 7.04. At first it looked like there was a problem but after re-booting completely it sorted itself out and displayed 7.04 with the previous nvidia settings. 

The only issue I have is that the automatic updates alert 'thinks' there are two updates needed (nvidia-glx and nvidia-glx-dev) but there are errors trying to install these and it just aborts the upgrade.

Is there anything I can do to 'fix' this?

Cheers,

Nick

I have the same problem, nvidia-glx and nvidia-glx-dev can't be installed. I get the following error. If anyone have a solution please reply. I used Envy to install the nVidia drivers in 6.10 (Edgy) and then upgraded to 7.04 (Feisty) today. Everything still works except for these packages not being able to install.

```
E: /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: conflicting packages - not installing nvidia-glx
E: /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing libgl1-mesa-dev
E: /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing mesa-common-dev
```

/Elli

---

### Post by jondecker76 on 2007-05-02
i've had the same problem with every upgrade i've done..  I'll have to give this a try

---

### Post by mitanc on 2007-05-03
I bit the bullet and reinstalled Feisty from scratch.  I have to say everything is working much better than before and the nvidia drivers worked the minute I clicked them on the restricted drivers menu.

Loving ubuntu right now.

---

### Post by Jose Catre-Vandis on 2007-05-20
This thread helped me alot after an Edgy upgrade to Dapper went wrong and i couldn't boot it. So I created a new partition and installed Fiesty. Using Automatix I installed the nvidia drivers. No X! After some fiddling I got GDM up and running but couldn't get twinview working again.

So uninstalled all the nvidia drivers (they were all there!) and reinstalled nvidia-glx. Copied over my twinview settings to xorg.conf and hey presto, all working again.

This was for a Shuttle PC with the Geoforce 4 graphics. Sadly my TV will only cope with 1024 x 768 set for it and my monitor as well. But it works. Also its the first time Automatix has ever let me down.

[edit]

On start up today, X failed, and I had to revert to "nv" to get to GDM, so the search for success continues

[edit 2]

It seems that installing the nvidia drivers through Automatix2 causes problems when trying to use nvidia-glx - you get a mismatch between the driver and the kernel module, caused by Automatix installing "all" the nvidia drivers (legacy and glx-new). I gave up eventually and reinstalled Fiesty, then installed nvidia-glx through synaptic, and applied the right settings in xorg.conf for twinview and all worked fine

---

### Post by Me_Titus on 2007-06-10
Thanks for this help... ;)


MeTitus

---

