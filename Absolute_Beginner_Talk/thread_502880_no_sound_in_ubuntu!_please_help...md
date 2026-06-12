---
title: "no sound in ubuntu! please help.."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by rustix on 2007-07-17
i have a Compaq C563TU notebook and I installed Ubuntu 7.04. I am new to ubuntu or any version of linux and this is the first time i installed ubuntu. now i've got dual booting (i.e. ubuntu + windows xp sp2).

the prob is in ubuntu there is no sound. the sound card drivers "seems" to have been installed but no sound. why is this? and the first time i ran ubuntu from the live cd there was sound in the sense that i heard the login and logout sounds but after installing it there is no sound at all. not even when i run the live cd. what do i do?

is there any way to uninstall ubuntu??

---

### Post by NilsE on 2007-07-17
Try this and see what happens. If the card is recognized it should activate it.

In a terminal run: 
```
asoundconf list

This should return a list of cards.
```
Then run:
```
asoundconf set-default-card xxxxxxx

Then again with sudo: 

sudo asoundconf set-default-card xxxxxx

Where xxxxxx is the card that showed up in the list command (case sensitive)
```

---

### Post by Earthwormzim on 2007-07-17
When I first installed Ubuntu, I could not get the sound to work either.  After hours and hours of searching the internet for help, I nearly gave up.  I tried just about everything, like configuring the Alsa-Mixer, etc.  But in the end, it turned out to be something far simpler...I have an Audigy card, but perhaps your card will have something simlar.  

As it turns out, all I had to do was double-click the volume bar in the panel, and the "Volume Control: Audigy 1 [SB0090] {Alsa mixer}" window popped up.  On it, there were two tabs; one labeled, "Playback" and the other, "Switches".  On the "Switches" tab there was one check-box that said, "Audigy Analog/Digital Output jack: [ ] " (the brackets represent the check-box).  For some reason, Feisty came with that setting checked by default, which silenced my computer.  So, I unchecked it, and...voila!  SOUND!

I know you don't have the same card or drivers...but who knows, maybe yours will have a similar set of options.

---

### Post by Shin_Gouki2501 on 2007-07-17
Earthworm jim i was battling also quite soem time with a sudden "no" sound i think ur description and solution of the Problem is just what i need i will check it out ASAP!

wbr Shin Gouki

---

### Post by porphiron on 2007-07-17
had exactly the same problem, heres how i solved it, using the volume control taskbar applet->show switches, tick/untick analog/digital output jack,

hope this helps

porph

---

### Post by rustix on 2007-07-17
**@NilsE**

when i entered ```
asoundconf list
``` i got the following in response

```

Names of available sound cards:
Intel

```

after that i entered the following:

```

asoundconf set-default-card Intel
sudo asoundconf set-default-card Intel

```

but still no sound.... any other suggestions pls??


**@Earthwormzim**

Nope. In my "Switches" tab all i have is "LineIn: []", "IEC958: []" and "IntMic: []"

any other suggestion??

I'll be very greatful for any help I could get...

oh and one more thing.. when i typed 

```

lspci | grep Audio

```

I got the following in response:

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

just in case it's of any use..

please guys.. need sound badly..  ](*,)

---

### Post by Earthwormzim on 2007-07-17
> **Shin_Gouki2501 said:**
> Earthworm jim i was battling also quite soem time with a sudden "no" sound i think ur description and solution of the Problem is just what i need i will check it out ASAP!

wbr Shin Gouki

> **porphiron said:**
> had exactly the same problem, heres how i solved it, using the volume control taskbar applet->show switches, tick/untick analog/digital output jack,

hope this helps

porph

I sense a little sarcasm.  I'll be the first to admit that I'm no Linux pro, but, nonetheless, I did have a similar problem, and I thought it *might* be helpful to share my experience with others that were as well.  I hope it helped...but, if not...maybe next time.

---

### Post by Shin_Gouki2501 on 2007-07-18
this is NO joke im also new too linux! heres my thread:
[http://ubuntuforums.org/showthread.php?t=497393](http://ubuntuforums.org/showthread.php?t=497393)

In there i got help for Hardware issues with soundcard, but i guess since it worked once (and the other day i messed arround with the task bar)

It has to be your solution and so im REALLY helpfull , because the things u say "most" people take for common but if ur new to the OS it just CAN happen.

And sadly such thigns are not listed in guides or tutorial , although i think they should !

---

### Post by rustix on 2007-07-18
so doesn't anyone have any suggestions? :(

---

### Post by venoom27 on 2007-07-18
I accidentally deleted my drivers so I was jumping around to different forums and found my info in a number of pklaces but I will try to put it all in here and maybe it can help more people.

1. Go to a shell and type: aplay -l

    * Success - You will get a list of the all the soundcards installed on your system. Your sound just might be muted. See alsamixer section. 
Failure - You will get a message like aplay: device_list:221: no soundcard found... then you will have to move on to step two.

2. Type this into the shell: lspci -v

    * Success - At this point, you should see your sound card listed. This is a positive sign because it means that Ubuntu is detecting the presence of your soundcard, but the drivers are not installed/running. Leave your shell running since you will need it.
    * Failure - If it is not listed, then there are a few things that you can do.
          o If your soundcard is an onboard sound card, then it might be disabled in the system's BIOS. You will have to reboot and hit the key that lets you enter into the BIOS (usually Delete, F2, or F8).
          o If your soundcard is not onboard, make sure that it is properly seated in the PCI slot. If your card is working under Windows then this is not a problem. 

3. Check to see if the ALSA driver for your sound card exists. Go to [*http://www.alsa-project.org/alsa-doc/*](*http://www.alsa-project.org/alsa-doc/*) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

    * Success - You will have found the driver for your soundcard's chipset.
    * Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you,
 

4.    ** Install the required tools**

sudo apt-get install build-essential ncurses-dev gettext

5.** Install your kernel headers**
sudo apt-get install linux-headers-`uname -r`

6.Download the latest version of alsa from [WWW] Alsa project (driver, library, and utils) to a directory (eg. ~/downloads). In the following we assume that the latest version is 1.0.14rc4. Please change this in accordance with the one you downloaded from the Alsa project site.
[_alsa-driver_]("http://www.alsa-project.org/alsa/ftp/driver/")
[_alsa-lib_]("http://www.alsa-project.org/alsa/ftp/lib/")
[_alsa-utils_]("http://www.alsa-project.org/alsa/ftp/utils/")

7.**Setup installation directories**

Now this worked for me after trying many different things. 
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14rc4.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc4.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc4.tar.bz2

8.**Compile and install alsa-driver**
cd alsa-driver-1.0.14rc4
sudo ./configure --with-cards=**<Your Card Name From Step 3>**
sudo make
sudo make install
./snddevices

9**.Compile and install alsa-lib**
cd ../alsa-lib-1.0.14rc4
sudo ./configure
sudo make
sudo make install

10.**Compile and install alsa-utils**
cd ../alsa-utils-1.0.14rc4
sudo ./configure
sudo make
sudo make install

11.**Reboot**
And your audio should work.

This worked for me after trying a number of things. I hope this helps. Also look at some of the links below they may also help you.


info from 
[-http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")
[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]-https://help.ubuntu.com/community/HdaIntelSoundHowto
[/URL][-http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0")

---

### Post by Shin_Gouki2501 on 2007-07-19
oh i forgot tried this?:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by deputyjones on 2007-07-26
> **Earthwormzim said:**
> When I first installed Ubuntu, I could not get the sound to work either.  After hours and hours of searching the internet for help, I nearly gave up.  I tried just about everything, like configuring the Alsa-Mixer, etc.  But in the end, it turned out to be something far simpler...I have an Audigy card, but perhaps your card will have something simlar.  

As it turns out, all I had to do was double-click the volume bar in the panel, and the "Volume Control: Audigy 1 [SB0090] {Alsa mixer}" window popped up.  On it, there were two tabs; one labeled, "Playback" and the other, "Switches".  On the "Switches" tab there was one check-box that said, "Audigy Analog/Digital Output jack: [ ] " (the brackets represent the check-box).  For some reason, Feisty came with that setting checked by default, which silenced my computer.  So, I unchecked it, and...voila!  SOUND!

I know you don't have the same card or drivers...but who knows, maybe yours will have a similar set of options.

That did it for me, thanks!

---

### Post by bribaetz on 2007-07-26
i dont need sound all that bad but it would be nice

---

### Post by funkshun on 2007-07-26
Hey I feel your pain. Cesare Tirabassi hooked me up with this link for the Intel chip set.

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

I followed these directions and was able to get sound. It was smooth process. I just installed ubuntu this last weekend.

---

### Post by Shin_Gouki2501 on 2007-09-16
@Earthwormzim!
u totaly ruels i could it workin finnaly :)

---

### Post by bjstabio on 2007-09-16
I wanted to thank everyone for the help I received.  I had tried everything I could think of to get sound and nothing worked.  Then I found this forum, double-clicked on the speaker, unchecked the switch box, and WOW, I had sound.  Thanks for the help.

---

### Post by Shin_Gouki2501 on 2007-09-17
Yes sometimes tons of FAQs , wikis or manpages help little but with a little help from "human beeings" its kinda easily solved, 
i guess thats why they call ubuntu : Linux for human beeings :)

---

### Post by Darles on 2007-11-02
Cheers guys. 
I stumbled across this thread after having to re-install feisty and experiencing problems with my sound card being recognised. 

It now works thanks to the info found here.

Well done and thanks again!

Darles :guitar:

---

### Post by missmoondog on 2007-11-02
> **Earthwormzim said:**
> When I first installed Ubuntu, I could not get the sound to work either.  After hours and hours of searching the internet for help, I nearly gave up.  I tried just about everything, like configuring the Alsa-Mixer, etc.  But in the end, it turned out to be something far simpler...I have an Audigy card, but perhaps your card will have something simlar.  

As it turns out, all I had to do was double-click the volume bar in the panel, and the "Volume Control: Audigy 1 [SB0090] {Alsa mixer}" window popped up.  On it, there were two tabs; one labeled, "Playback" and the other, "Switches".  On the "Switches" tab there was one check-box that said, "Audigy Analog/Digital Output jack: [ ] " (the brackets represent the check-box).  For some reason, Feisty came with that setting checked by default, which silenced my computer.  So, I unchecked it, and...voila!  SOUND!

I know you don't have the same card or drivers...but who knows, maybe yours will have a similar set of options.
finally!!
what an easy fix. 

thanks

---

