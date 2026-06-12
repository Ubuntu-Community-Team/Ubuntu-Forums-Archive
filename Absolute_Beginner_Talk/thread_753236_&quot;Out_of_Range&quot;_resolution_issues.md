---
title: "&quot;Out of Range&quot; resolution issues"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by dfthompson on 2008-04-12
First of all I am new to ubuntu and struggle with the basics. I have a Dell dimension 9100, ATI X1650 pro, and a Chimei 22" Widescreen monitor. I am having real troubles getting a good resolution and keeping it. I have manged to get the display set up well by tweeking the settings, but whenever I turn off the cpu, it comes back up at low resolution. I unfortunatly can't remember how I got it set up right each time this happens. When I go to "screens and graphics" and play with the settings, I usually get "out of range" on any of the higher settings. I have tried to find posts that help, and I have run some suggest command lines, but I'm lost for understanding the problem or the solution.

---

### Post by twist2b on 2008-04-12
I'm sorry, you did NOT give the resolution you want.
ALSO you did not give good specs like which graphics card you have, or which distro. I'm guessing you have gusty.

What you can do, go into recovery mode and type this:

dpkg-reconfigure xserver-xorg
close to the end it has resolution choices. choose the one you want and others.
once you choose it basicly configures for you.

Good luck and tell me how it goes. 
You might also have a driver issue. If you have nvidia I can help you out more.

---

### Post by dfthompson on 2008-04-12
The monitor supports 1680x1050, the card is a Diamond Viper ATI Radeon X1650Pro PCI E 512MB.

---

### Post by dfthompson on 2008-04-12
Oh yea, it is Gutsy. Thanks

---

### Post by LaRoza on 2008-04-12
> **dfthompson said:**
> The monitor supports 1680x1050, the card is a Diamond Viper ATI Radeon X1650Pro PCI E 512MB.

Do you have the drivers installed for that?

---

### Post by ubuntu-freak on 2008-04-12
> **twist2b said:**
> I'm sorry, you did NOT give the resolution you want.
ALSO you did not give good specs like which graphics card you have, or which distro.

 
The resolution he wants isn't that important to us, also, he did say what graphics device he has and beneath his bean count it states he is using Gutsy. 
 
dfthompson, 
 
Just incase you're not completely sure what to do, navigate to Applications>Accessories>Terminal and paste this command into it:
 
**sudo dpkg-reconfigure -phigh xserver-xorg** 

Then choose your prefered resolution when it asks. If that doesn't work, reboot and do the same but in recovery mode. 
 
Nathan

---

### Post by twist2b on 2008-04-12
actually it did matter considering it could be a driver issue.

Tell me how my steps work out. Its ATI driver so the only advice I can give is something that works perfectly for most people:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
install the envy and run it. It works perfectly. Then you can re-configure the resolution.

I'm interested how that works because I do not get to help people with ATI graphic cards that often.

---

### Post by dfthompson on 2008-04-12
Sweet!!!!!!!!!!!!!
The Envy worked like a champ, resolution is perfect now. Thanks.

Now (again I'm a newbie) how can I keep it that way when I reboot in the future? Will what I've done this time stay?

---

### Post by ubuntu-freak on 2008-04-12
> **dfthompson said:**
> Sweet!!!!!!!!!!!!!
The Envy worked like a champ, resolution is perfect now. Thanks.

Now (again I'm a newbie) how can I keep it that way when I reboot in the future? Will what I've done this time stay?

 
 Reboot as much as you want, it should stick. When you decide to install Hardy, do a fresh install, then install the new Envy, as the Hardy version will handle upgrades and new kernels better (says so on the Envy website anyway). 

I'm surprised Ubuntu didn't offer to install the drivers though, then you would just have to use that reconfigure command to set your resolution.
 
Nathan

---

### Post by VipeR_11 on 2008-04-15
I have the same problem + i can't use desktop effects :-[

After few months i tried to install again ubuntu 7.10
I install envy, download/install/configured everything for me and then i needed to reboot.
I did and.....no signal :-[

what should i do now? Is thre any way of reseting the system instead of installing it again?

i use ubuntu 7.10 and my card is ATI X1650 pro
according to envy the drivers it installed were the latest and compatible with my card!

---

### Post by ubuntu-freak on 2008-04-15
> **VipeR_11 said:**
> I have the same problem + i can't use desktop effects :-[

After few months i tried to install again ubuntu 7.10
I install envy, download/install/configured everything for me and then i needed to reboot.
I did and.....no signal :-[

what should i do now? Is thre any way of reseting the system instead of installing it again?

i use ubuntu 7.10 and my card is ATI X1650 pro
according to envy the drivers it installed were the latest and compatible with my card!

 
Boot into recovery mode and type this command:
 
**sudo dpkg-reconfigure -phigh xserver-xorg** 

Then select the right resolution and refresh rate (should be auto-detected really). Reboot with ctrl+alt+del.
 
Nathan

---

### Post by VipeR_11 on 2008-04-15
> **reassuringlyoffensive said:**
> Boot into recovery mode and type this command:
 
**sudo dpkg-reconfigure -phigh xserver-xorg** 

Then select the right resolution and refresh rate (should be auto-detected really). Reboot with ctrl+alt+del.
 
Nathan

Thank you, i'll do it right now!!

One more question if you know plz.

When trying to install a driver with envy do we need to have the restricted drivers activated or not?
does it make any diference? I think i have them on when I install the driver via envy.

---

### Post by ubuntu-freak on 2008-04-15
> **VipeR_11 said:**
> Thank you, i'll do it right now!!

One more question if you know plz.

When trying to install a driver with envy do we need to have the restricted drivers activated or not?
does it make any diference? I think i have them on when I install the driver via envy.

 
It's safe to leave it on. Strange that it didn't offer to install the ATI driver for you.
 
Nathan

---

### Post by dfthompson on 2008-04-18
Remember, this advise is from a newbie....

When I would get my machine so screwed up changing the display settings, that I couldn't get a good boot, I would boot in safe mode and run this line at the prompt:

sudo dpkg-reconfigure xserver-xorg

It will run you through a list of settings to reset things. I was told to accept all the defaults.

Basically it would reset your display to minimal standards and allow you to get back up and running.

---

### Post by ubuntu-freak on 2008-04-18
Yeah, but that command won't work in Hardy I'm afraid. 
 
Nathan 
 
P.S. Not too sure what to use in text-mode with Hardy, but in desktop-mode you can run "gksudo displayconfig-gtk" in Ubuntu/Xubuntu and "gksudo displayconfig" in Kubuntu.

---

