---
title: "nothing"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by alanc on 2007-06-10
:D Hi.   I am trying to instal  ubuntu 5.10 but when i put it in the cd rom nothing appears on screen.
. Can someone please help me to get started.
                                           Regards    alanc:p

---

### Post by johnc4510 on 2007-06-10
If you are trying it after the computer is booted, it won't work that way. You must put it in the cd rom and then boot. If this is not your problem, please give us more info. :)

---

### Post by HotShotDJ on 2007-06-10
> **alanc said:**
>  I have tryed it in IE AND MOZILLA but nothing. Can someone please help me to get started.:confused:  HUH????  I'm not trying to be mean, but ...  HUH???   Try [the documentation]("https://help.ubuntu.com") first and then if something confuses you, by all means come back and ask about it.  But I can't make heads or tails of your current question.

---

### Post by starcraft.man on 2007-06-10
> **alanc said:**
> :D Hi.   I am trying to instal  ubuntu 5.10 but when i put it in the cd rom nothing appears on screen.
       I have tryed it in IE AND MOZILLA but nothing. Can someone please help me to get started.
                                           Regards    alanc:p

Uhhhhhhhhhhhh, you tried a CD in IE and firefox? How did you do that?

I strongly recommend downloading and installing a newer version, i believe 5.10 just hit its end cycle a few weeks ago and thus isn't supported anymore by new updates in repos.

This is [how to burn a new CD]("https://wiki.ubuntu.com/BurningIsoHowto") and [this to install via live cd ]("http://www.psychocats.net/ubuntu/installing")which I assume you'll use. I[ recommend going to Ubuntu site ]("http://www.ubuntu.com/getubuntu/download")and downloading Feisty Fawn desktop CD for x86.

Oh and how to get it to work, I believe your problem lies in the fact that your trying to install it when booted into windows. You need to reboot your machine, push your bios button (esc f10 f12 or whichever) and tell the BIOS to boot from CD.

---

### Post by steveneddy on 2007-06-10
Yeah, try the 7.04 version.

Put the cd in the drive - reboot the machine - follow the instructions.

Easy as that. 

You could experiment with the 5.10 version - but if you are installing, please do use the Feisty 7.04 version.

---

### Post by alanc on 2007-06-12
;)Hi.   I have set my settings to boot from cd. When i boot up i have to go into my computer, to find the drive
     i have to open it, and i get the Ubuntu disc tree, with ubuntu linux open office- and mozilla when i click on ubuntu linux, i get a brief tour i click on the first screen and just get the gold screen, i click on the next screen and opens  theme preferences, then to the bottom where i get hOMEPAGE.
    I can net get a live tour, as it suggests, what can i be doing wrong. Please help.
                                                       Regards   alanc:(

---

### Post by jimrz on 2007-06-12
> **alanc said:**
> ;)Hi.   I have set my settings to boot from cd. When i boot up i have to go into my computer, to find the drive
     i have to open it, and i get the Ubuntu disc tree, with ubuntu linux open office- and mozilla when i click on ubuntu linux, i get a brief tour i click on the first screen and just get the gold screen, i click on the next screen and opens  theme preferences, then to the bottom where i get hOMEPAGE.
    I can net get a live tour, as it suggests, what can i be doing wrong. Please help.
                                                       Regards   alanc:(

sounds like your machine is set to boot to the hard drive first, since you are apparently going into windows. you need to enter setup and change your boot order to where the cd drive is listed before your hdd

---

### Post by alanc on 2007-06-12
> **steveneddy said:**
> Yeah, try the 7.04 version.

Put the cd in the drive - reboot the machine - follow the instructions.

Easy as that. 

You could experiment with the 5.10 version - but if you are installing, please do use the Feisty 7.04 version.
;) Hi.  I have set my bios to boot from cd, but when i boot up i have to go into my computer to click on it to open it. I am running a live cd, but it just comes to the ubuntu disc tree, but everything is still nothing live.
                                                          Regards   alanc:(

---

### Post by drowner on 2007-06-12
> **alanc said:**
> ;) Hi.  I have set my bios to boot from cd, but when i boot up i have to go into my computer to click on it to open it. I am running a live cd, but it just comes to the ubuntu disc tree, but everything is still nothing live.
                                                          Regards   alanc:(

Then, you are not booting from the CD

Put the CD in, and restart your computer.

---

### Post by alanc on 2007-06-12
> **jimrz said:**
> sounds like your machine is set to boot to the hard drive first, since you are apparently going into windows. you need to enter setup and change your boot order to where the cd drive is listed before your hdd

;) Hi.  How to i go about doing that.
              Regards  alanc:(

---

### Post by CautionaryX on 2007-06-12
Alanc, 

Thanks for your interest in Ubuntu. Try hitting  F12 (might need to hit it a few times) immediately after it reboots but before the Windows XP loading screen shows up, most motherboards / laptops are configured to let you select the boot device from a menu upon hitting that key. Select the CD drive with the arrow keys and press Enter (Return).

---

### Post by kyrhash on 2007-06-12
do you know what a BIOS is?  First thing you want to do is boot from a cd, so start out by going to start > Shutdown and then click restart.  The computer should turn off for a sec the second it starts you need to look for a way to enter your BIOS.  If you see the windows logo/login screen then you missed it boot up again.  It is different on every PC you may have to hit delete key, or the Escape key or even the Pause/Break key.  Once you get into the bios look around for the boot order setup or something like that.  Change the setup so that the CD/DVD drive will boot before your hard drive.  Exit and don't forget to save the changes.  Remember where it is so you can turn it back if you need to.

---

### Post by ncappel1 on 2007-06-13
And if you accidentally change a setting you shouldn't have, that is **anything else except for the boot order,** if you can't remember what the setting was at before, exit out of the bios without saving and try again. You don't want to risk hurting anything. 

Nicola

---

### Post by jimrz on 2007-06-13
> **alanc said:**
> ;) Hi.  How to i go about doing that.
              Regards  alanc:(

varies from machine to machine. when you first start the machine you will need to hit a specific key (there may be a prompt on the initial screen telling you which) to "enter setup". some fairly common keys for this are "esc' "F2", "F8" or "F12".

I beleive you said earlier that your's is set to boot from cd. if that is correct and you have been actually boot from other bootable cd's, then the problem is with either the disk or your cd-rom. are you sure that you burned the disk "as an image" and not as a data file (.iso)?

---

### Post by bone43 on 2007-06-13
Not to be rude in any way but maybe you should do some reading at the top of this forum before trying to install Ubuntu.
 First off I would recomend that you figure out how to run the live cd this will not change your computer in any way then once you have done that  maybe try to install Ubuntu but as i said do some reading  first and if you have question post back here.

Good Luck :)

Opps here is the link..

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

---

### Post by alanc on 2007-06-13
;)Hi.  I have got into Bios OK, but for the life of me i cannot the CD drives to be listed above the HDDs.
       I have done what it says to do but it still goes back to the HDDs on the top.When i go into the boot section
      of Bios, there is two HDDs and two CDroms, but when i press the top boot device priority it only shows3
     items, and one is a floppy disk, so as you can see i have just about had it.
                                                 Regards    alanc:(

---

### Post by bone43 on 2007-06-13
You have to save the bios changes before you exit, so make your changes and then save them before you exit.

Usually at the bottom of the screen there is a list of commands that tells you how to move around and save in the bios.

---

### Post by alanc on 2007-06-16
:p Yippee, i have finally got the live cd to run, now all i have to do is to configure how i go about using
     it properly.
                                                          Regards    alanc;)

---

### Post by alanc on 2007-06-16
> **alanc said:**
> :p Yippee, i have finally got the live cd to run, now all i have to do is to configure how i go about using
     it properly.
                                                          Regards    alanc;)

Hi.  I am trying to install a cd of Ubuntu, to another hard drive, but i am getting nothing on the screen again,
      could someone please explain to me, how i go about doing that.
                                                 Regards   alanc

---

