---
title: "Weird Sound problem on Core2Duo Macbook (7.10)"
date: 2007-11-12
forum: Apple Intel Users
---

### Post by ml7667 on 2007-11-12
I'm running Gutsy Gibbon on a core2duo macbook. I am having a really weird sound problem. I am getting a fuzzy distorted crackle in the left channel of whatever I'm listening to sound on. I hear it through the internal speakers, through headphones, and through the left speaker of external speakers. Any idea what this could be? I thought for a second that it could be a busted speaker in the internal speakers but then I plugged in headphones and external speakers and I heard the same noise in the left channel of both.

---

### Post by cyberdork33 on 2007-11-12
This sounds very similar to some problems that people were having in feisty. Can you try to:

1. Reboot a couple time and see if it changes. Some people reported that it would only do this ever so often.

2. Try adjusting the Volume level in OSX before booting Ubuntu. Some users found that the static was only heard if the volume level in OSX was at a certain level or higher.

---

### Post by ml7667 on 2007-11-12
I will try rebooting and seeing if it makes a difference.

I actually dont have OSX installed on this macbook anymore, just a complete install of gutsy. This is my first time really delving into linux so I did a fresh install of just ubuntu so I can force myself to learn everything and do everything in linux, haha.

---

### Post by ml7667 on 2007-11-12
So I rebooted and the problem is gone. I've been noticing it off and on so it definitely is based on the boot.

---

### Post by cyberdork33 on 2007-11-12
> **ml7667 said:**
> So I rebooted and the problem is gone. I've been noticing it off and on so it definitely is based on the boot.

I think the best thing is to find a bug report or start a new one.

---

### Post by volanin on 2007-11-13
> **ml7667 said:**
> I'm running Gutsy Gibbon on a core2duo macbook. I am having a really weird sound problem. I am getting a fuzzy distorted crackle in the left channel of whatever I'm listening to sound on. I hear it through the internal speakers, through headphones, and through the left speaker of external speakers. Any idea what this could be? I thought for a second that it could be a busted speaker in the internal speakers but then I plugged in headphones and external speakers and I heard the same noise in the left channel of both.

I have exactly the same problem, and it's already driving me nuts.
I almost went back to the store, to complain, but then I checked in MacOSX and the problem vanished.
Differently from you, I've never booted a single time with the problem solved.
The crackling sound is there EVERYTIME. Always the left channel.

I resorted to lowering the Front Channel in ALSA to 90 (It really means TREBLE)
And lowering the Surround Channel also to 90, just to match. (It really means BASS)

Now the sound is a little lower, and DISGUISES the crackling, but does not get rid of it.
I am using the 2.6.23 kernel from Fedora, so even the new version modules do not fix it.

At least I am glad to know now that this is a linux problem and not my hardware...
Linux always manage to solve these things, even if it takes some time.
File a bug report. I will support you there.
:)

---

### Post by ml7667 on 2007-11-13
Haha, I too am glad I am not alone and it is not a problem with my Macbook. I was worried that i busted the internal speakers in my new macbook!

---

### Post by Amackera on 2007-11-13
I have the same problem. Like volanin I've been mixing the levels to get rid of it, but it's hugely irritating.

---

### Post by volanin on 2007-11-13
I've been searching around the net and reading the kernel docs, and I THINK I found a solution.
I have powered-up the computer only a few times since I did this, but the sound was loud,
very clear and with not crackling at all. So I am posting it here for you to try as well.

Follow these steps:


**1.** Open a terminal.

**2.** Type:
```
$ sudo gedit /etc/modprobe.d/options
```
**3.** Add the following line to the end of the file:
```
options snd-hda-intel model=[MODEL_BELOW] position_fix=2 probe_mask=1
```
**4.** Save the file and type in the terminal:
```
$ sudo update-initramfs -u
```
**5.** Reboot your computer.


You must select the Intel HDA model that corresponds to your computer:

```
intel-mac-v1   : Intel Mac Type 1
intel-mac-v2   : Intel Mac Type 2
intel-mac-v3   : Intel Mac Type 3
intel-mac-v4   : Intel Mac Type 4
intel-mac-v5   : Intel Mac Type 5
macmini        : Intel Mac Mini (equivalent with type 3)
macbook        : Intel Mac Book (eq. type 5)
macbook-pro-v1 : Intel Mac Book Pro 1st generation (eq. type 3)
macbook-pro    : Intel Mac Book Pro 2nd generation (eq. type 3)
imac-intel     : Intel iMac (eq. type 2)
imac-intel-20  : Intel iMac (newer version) (eq. type 3)
```

For example, I have a Macbook 3rd generation, and the only setting that worked was
**model=intel-mac-v3**. All others just gave me NO sound at all, including the apparently
obvious *macbook* and the documented-as-equivalent *macmini* ones.

If nothing works, you can revert this by deleting the line and performing the rest of the steps.


For BEST sound, if the above works, open a terminal and type:
```
$ alsamixer
```

And set the FRONT and SURROUND sliders to their maximum.
It might be necessary to unmute them with the 'M' key.
Press ESC twice to leave the program.
:)


*EDIT:*
It was confirmed by cipher999 that **position_fix=1** works as well.
Thanks!

---

### Post by cipher999 on 2007-11-13
volanin, confirmed !

I have a macbook pro first gen, and I also had the annoying crackling on the left speaker at every boot. Now I only booted twice but I think the problem is gone.

```
options snd-hda-intel position_fix=1
``` did the trick, but position_fix=0 didn't.

I also noticed that ```
options snd-hda-intel model=macbook-pro-v1
``` worked.

This problem has been getting me mad for one year ! This thread also relates to it : [http://ubuntuforums.org/showthread.php?t=371047](http://ubuntuforums.org/showthread.php?t=371047) but doesn't provide a solution that worked for me.

---

### Post by volanin on 2007-11-13
I did a few more tests and updated the instructions above.
Please try them out and report here if these solved the problem for you!
:)

---

### Post by Amackera on 2007-11-14
Confirmed, fix works for me too. I'm using the Macbook v5 setting.

Great work!

---

### Post by frabcus on 2007-11-15
How do I find out which model Macbook I have?

---

### Post by volanin on 2007-11-15
Honestly, I did it partly by guessing:

I know I have a Macbook 3rd generation.
So I firstly tried with model=macbook, and got no sound.
Then I tried with model=intel_mac_v3, and everything was fine!

Later, I also tried with intel_mac_v5 and macmini, just for the sake of it.
But got no sound from any of them either.
:)

---

### Post by Demophobie on 2007-11-21
Hi!

I think i will a macbook 3rd generation next week.

@volanin
Is there anything you could not get to work? What about the apple light?
What hardware is on your macbook? GMA x3100 and a bcm43xx?

thanks :) 
Patrick

---

### Post by kenleycapps on 2007-12-19
Just wanted to throw out there for those who went with a Macbook Core2Duo (white) should note that the intel-mac-v3 works with the code listed. Eliminated the static for me.

---

### Post by hardawayd on 2007-12-20
I have a Macbook Pro lastest version (Santa Rosa). I tried the setting for macbook-pro but no luck. Did anyone find what setting works for the latest Macbook Pro?

---

### Post by Amackera on 2008-01-15
Hey guys, I hate to say it but the problem isn't fixed for me. 
It works after a 2nd boot, but that's irritating.

Has anyone filed an official bug? And how/where would we report it?

---

### Post by cyberdork33 on 2008-01-15
> **Amackera said:**
> Hey guys, I hate to say it but the problem isn't fixed for me. 
It works after a 2nd boot, but that's irritating.

Has anyone filed an official bug? And how/where would we report it?

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by pilotopirx on 2008-01-24
This solved my issue... but not permanently!
If I understand right, this will re-create the sound modules. how do I know for sure that the new ones are being used by the system?  is there a way to load them after boot time, obv. without rebooting?

---

### Post by mabovo on 2008-01-24
I tested with type 5 on MacBook 2nd gen and it works very well. 
I tested with skype test call and sound was very nice than before.
Now I have to set-up microphone.

Thanks.

---

### Post by Amackera on 2008-03-02
Is there a fix for this yet - has anyone had permanent success?

---

### Post by cipher999 on 2008-03-03
I hate to say, but despite I earlier wrote that it was fixed permanently, it is not. It does the work for one reboot or two, but later on this issue comes back.


This is so irritating !

---

### Post by bsantos on 2008-03-16
Are you still having issues? I'm using Hardy and still have this problem with distorted sound on the left channel on a MB C2D 2nd gen. Almost all the times on first boot the issue is present, but gone every time after a suspend to ram. I've taken logs of lsusb and lspci before and after but didn't yet analise them, but I could already see that they differ with a simple diff.

---

### Post by bsantos on 2008-03-20
Hmmmm just ditched a workaround option for the module (position_fix) and now got perfect sound right on first boot... :eek:

If this becomes fixed, the only things missing for it to be perfect are: xrandr working with tv-out, openoffice being usable (weird hangs using menus) and madwifi working after suspend (madwifi is very slow on svn lately, all devs on ath5k?), and the fifo bug getting fixed. It is pretty easy to get it if using various applications using the network a lot (some downloads on firefox, miro downloading videos, some albums from Jamendo on transmission); and weird vt switch issues on intel, display is always messed up on shutdown...

---

### Post by Amackera on 2008-03-21
bsantos, can you please post the details of your workaround? This is exciting! :popcorn:

---

### Post by bsantos on 2008-03-21
I had position_fix=1 as an option for the snd-hda-intel module in /etc/modprobe.d/options, and the sound was always distorted on boot but after a suspend to ram became perfect.
I commented the module options so the module loads without any options (at least defined by me) and the sound was perfect on the next boot and after a suspend to ram.

I'll do a couple of reboots to check if it is solved for good (some people got intermittent boot success). So if you have any manual options for the module to load (like model or position_fix) try to comment them out and let the module load normally.

Let us know how it goes. :)

---

### Post by jettjunker on 2008-04-05
I've tinkered with this for a few hours now, and have yet to get it to boot a single time without this problem... trying variations of what's been suggested and by modifying /etc/modprobe.d/alsa-base similarly as suggested at [http://ubuntuforums.org/archive/index.php/t-221875.html](http://ubuntuforums.org/archive/index.php/t-221875.html) (but using "macmini" as model, of course).  I'm running a brand new mac mini -- is there a new version number like for the macbooks that I should be using?  Any word on an actual fix? .

EDIT: SOLVED! you know, um, relatively... 1.0.16 works great.  Here's what I did:

sudo synaptic #and uninstall the alsa drivers (alsa-base and/or alsa-source)
#undo changes to /etc/modprobe.d/alsa-base
#undo changes to /etc/modprobe.d/options
sudo /etc/init.d/alsa-utils stop
sudo update-initramfs -u
sudo update-modules
#follow inst: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

And, after the reboot everything sounds great!  I'm not really sure if I needed to do each of those steps, but it worked.  Yay!

---

### Post by eltonone on 2008-04-29
Thanks for the information everyone.

I had/have a similar problem with my 2nd Generation Macbook Pro.  Volanin's solution seems to have worked for me so far, but I've only been running with it for a half hour.  Here is what I did: [http://eltonone.com/2008/04/25/noisy-line-out-speaker-left-channel-using-ubuntu-710-and-a-macbook-pro/]("http://eltonone.com/2008/04/25/noisy-line-out-speaker-left-channel-using-ubuntu-710-and-a-macbook-pro/")

I do still have a weird high frequency buzzing/humming noise coming from my left speaker permanently - line in plugged in or not.  Never had it while running OS X and it's similar to the noise you get using the line out of a G4 with mirrored doors which gets faster and louder as your processor runs faster.  I've also had a similar noise from a Motorola V3 mobile phone which had a faulty gain table.  This sound is digital noise modulated by some other electromagnetic interference, so I guess it is aided by lack of propper shielding and/or the gain table for the audio device being somehow not quite right, leading to a poor signal to noise ratio either way.  The fact that on my Macbook Pro the noise is just out of the left speaker must either mean there is poor shielding on that side or the driver is set differently for left and right speakers, which I doubt.

Saying all that, I don't know how to fix this and I may be wrong - I'm only theorizing based on my understanding of digital audio systems and not really on my understanding on how linux is structured.

Anyway, so far things are working with the fix above so thanks again and good luck to everyone else finding a definitive solution.

---

### Post by cyberdork33 on 2008-04-29
Please post in the new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Try this:
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Crackling_Sound_on_the_left_Channel](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Crackling_Sound_on_the_left_Channel)

---

### Post by barnex on 2008-05-20
On my first-gen macbook with Hardy, I got this fixed with position_fix=1. I had first edited /etc/modprobe.d/alsa-base according to the instructions on [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook"). Don't know if that makes a difference, but it worked, finally!

---

### Post by Oscar Pradilla on 2008-07-13
This works for me...
options snd-hda-intel model=intel-mac-v3 position_fix=2 probe_mask=1

Macbook Pro 1st gen

---

