---
title: "no sound macbook 3,1 with hardy 8.04"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by mkgkg on 2008-05-01
hi,i installed the new hardy version. before i was using the beta one and audio was ok.
now i installed the 8.04 and the audio doesn't work. i added the follow line in /etc/modprobe.d/options:

[PHP]
options snd_hda_intel model =mbp3[/PHP]

after reboot if i try to click the button of the sound i have this error:
No volume control Gstreamer plugins and/or devices found.

so, i go to System->Preferences->Audio and i if click Test i have this error with all the sound playback possible configuration like Autodetect,alsa,oss,pulseaudio:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument


i have macbook santarosa 3,1 version.

any idea to solve the bug?:confused:

---

### Post by MTZeon on 2008-05-01
This should be added to /etc/modprobe.d/alsa-base and not options :)

options snd_hda_intel model=mbp3

Reboot and you should have your sound back (it worked for me, macbook 2008)

---

### Post by kingducttape on 2008-05-02
Same issue as above.  Tried the fix but it didn't work.  Sound worked fine on Gutsy, then broke when I upgraded, decided randomly to work a day later, and now stopped again.  Any help would be excellent...

MacBook Pro Santa Rosa 2.4GHz, Ubuntu 8.04.

---

### Post by d0b33 on 2008-05-02
*bump*

I'm having this problem too, any fix found yet?

This fix wont work for me.

---

### Post by cyberdork33 on 2008-05-02
there are several options you can try:
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Crackling_Sound_on_the_left_Channel](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Crackling_Sound_on_the_left_Channel)

---

### Post by d0b33 on 2008-05-03
OK I got it to work!

Edit:
fix on next page

---

### Post by mkgkg on 2008-05-03
can you say which packet did u download?but did u have  before this your packets-download  my same problem for audio?

---

### Post by d0b33 on 2008-05-03
Edit:

No need to do this, fix on next page

> **mkgkg said:**
> can you say which packet did u download?but did u have  before this your packets-download  my same problem for audio?

Well I had a clean install of hardy so I got no error messages, I just had no sound.

I cant remember all the packages I'll have to check.

Just do a search for pulse then alsa, then arts in the package manager and install all the related packages.

---

### Post by mkgkg on 2008-05-03
what did u mean whit arts?

---

### Post by d0b33 on 2008-05-03
Edit:

No need to do this, fix on next page

> **mkgkg said:**
> what did u mean whit arts?

I installed the aRts sound server control tool.


BTW I noticed that I had a redlight in my headphone port so I launched alsamixer (the gui version "gamix") and ticked the playback button for IEC958 and the light stopped glowing so I fixed that too.

---

### Post by eddied on 2008-05-03
This worked perfectly on my Macbook 2.4 Santa Rosa:
[http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/]("http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/")

---

### Post by d0b33 on 2008-05-03
> **eddied said:**
> This worked perfectly on my Macbook 2.4 Santa Rosa:
[http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/]("http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/")

Thanks good tip I'll try it out now since I'm doing a clean install.

Edit:

It worked! 

no need to install unnecessary packages

now why I never noticed that...

---

### Post by cyberdork33 on 2008-05-03
I added this info to the wiki page.

---

### Post by mkgkg on 2008-05-04
it doesnt work for me. i'added the follow line in /etc/modprobe/options:

[HTML]options snd_hda_intel model=mbp3[/HTML]

i rebooted, and the i have the same problem. if i click with right click on volume icon i have:
[HTML]
No volume control Gstreamer plugins and/or devices found.
[/HTML]

if i go on System, preferences,audio and i click on test, i have
[HTML]
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument[/HTML]



i have macbook santa rosa v3,1.

---

### Post by d0b33 on 2008-05-04
> **mkgkg said:**
> it doesnt work for me. i'added the follow line in /etc/modprobe/options:

[HTML]options snd_hda_intel model=mbp3[/HTML]

i rebooted, and the i have the same problem. if i click with right click on volume icon i have:
[HTML]
No volume control Gstreamer plugins and/or devices found.
[/HTML]

if i go on System, preferences,audio and i click on test, i have
[HTML]
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument[/HTML]



i have macbook santa rosa v3,1.

I would try a clean install of hardy personally, make sure it's not the RC because I have the same macbook and not having any problems.

---

### Post by mkgkg on 2008-05-04
i reinstalled 2 day ago..i ll do again also because on beta version i hadnt problems.

---

### Post by mkgkg on 2008-05-04
but i think is not a problem of reinstallation.

---

### Post by d0b33 on 2008-05-04
Ok, but you should check the md5 of your ubuntu iso you downloaded maybe its a RC?

---

### Post by MTZeon on 2008-05-04
> **mkgkg said:**
> it doesnt work for me. i'added the follow line in /etc/modprobe/options:

[HTML]options snd_hda_intel model=mbp3[/HTML]



This should go into /etc/modprobe.d/alsa-base !

---

### Post by d0b33 on 2008-05-04
> **MTZeon said:**
> This should go into /etc/modprobe.d/alsa-base !

Tried that and it never worked, when I put it under options I got a "switches" tab under volume control which I used to enable speaker output.

Edit:

Tested it again and both work (options and alsa-base)

---

### Post by m84 on 2008-05-04
I can confirm that putting *options snd_hda_intel model=mbp3* in either  /etc/modprobe.d/alsa-base or /etc/modprobe/options works on my macbook 4,1.

However, the sound from the internal speakers is really bad. Only the higher frequencies work, and it is very quiet. Maxing out PCM, Front and master volumes creates very harsh sound. Sound from the output jack is perfect.

Can anyone else confirm this? If anyone knows how to fix this it would be great as this is the last issue i need to fix before i can use ubuntu as my primary os.

Thanks

---

### Post by magik_ocean on 2008-05-05
> **m84 said:**
> Can anyone else confirm this? If anyone knows how to fix this it would be great as this is the last issue i need to fix before i can use ubuntu as my primary os.

Thanks

I can confirm this, the sound from speakers is VERY bad.

---

### Post by h_c on 2008-05-06
I did the following procedure and the sound is working fine on Macbook v3.1 with Ubuntu 8.04.

Add
options snd_hda_intel model=mbp3
to /etc/modprobe.d/alsa-base.

Install build-essential package.

Download alsa-driver-1.0.16 from [http://www.alsa-project.org](http://www.alsa-project.org).
./configure
make
sudo make install

---

### Post by mkgkg on 2008-05-06
yes..i can confirm..with the newest driver the audio is really better..thanks!:popcorn:

---

### Post by m84 on 2008-05-06
Yup, it increases the volume to a usable level. It doesn't provide the same level of sound quality as 0SX... I think I read somewhere that 0SX provides some sort of post processing to make the sound, well less like a tinny pair of laptop speakers, so that might explain difference.

Thanks

---

### Post by Officer Dibble on 2008-05-17
I've tried adding the afore mentioned line to 'Options' but it won't allow me to save it, I'm told I don't have permission. :(

I also visited the website for the updates ALSA driver, which do I go for, please?

Many thanks for any advice. :)

---

### Post by cyberdork33 on 2008-05-17
> **Officer Dibble said:**
> I've tried adding the afore mentioned line to 'Options' but it won't allow me to save it, I'm told I don't have permission. :(
you have to use sudo....

```
sudo gedit /etc/modprobe.d/alsa-bas
```This will be the case for pretty much all config files outside your home directory.

---

### Post by cyrano_says on 2008-05-18
> **cyberdork33 said:**
> you have to use sudo....

```
sudo gedit /etc/modprobe.d/alsa-bas
```This will be the case for pretty much all config files outside your home directory.



I can also confirm that the process brings the sound volumes to audible levels.

Thx.

---

### Post by vanakush on 2008-05-23
> **h_c said:**
> I did the following procedure and the sound is working fine on Macbook v3.1 with Ubuntu 8.04.

Add
options snd_hda_intel model=mbp3
to /etc/modprobe.d/alsa-base.

Install build-essential package.

Download alsa-driver-1.0.16 from [http://www.alsa-project.org](http://www.alsa-project.org).
./configure
make
sudo make install
 
hi 
first of all thanks for this post 
--->im using MacBook4,1 MODEL (MB403LL/A) and everything is working except sound, as i always use a live cd (ubuntu 8.04) i can't reboot to check if sound is working or not after installing updates and alsa-driver-1.0.16. By your given method i was able to install the alsa successfully but pls tell me is there any way to enable sound without reboot
i have also found this link [http://mailman.alsa-project.org/pipermail/alsa-devel/2008-January/005163.html]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-January/005163.html")to fix this problem as my hardware is **_0x106B00A1_** but i don't know how to and where to apply this patch. pls help

i used this method to install the driver

(Added
options snd_hda_intel model=mbp3
to /etc/modprobe.d/alsa-base.) then

1. sudo apt-get update
2. sudo apt-get upgrade
3. sudo apt-get install build-essential
4. cd  '/home/ubuntu/Desktop/alsa-driver-1.0.16'  <-------- extracted package location.
5. ./configure
6. make
7. sudo make install.

is there any way to fix the ubuntu live cd with latest alsa driver?

---

### Post by clebio on 2008-11-04
> **h_c said:**
> I did the following procedure and the sound is working fine on Macbook v3.1 with Ubuntu 8.04.

Add
options snd_hda_intel model=mbp3
to /etc/modprobe.d/alsa-base.

Install build-essential package.

Download alsa-driver-1.0.16 from [http://www.alsa-project.org](http://www.alsa-project.org).
./configure
make
sudo make install

This does not work for me. I'm on a MacBook Pro (5,1) and installed alsa-driver-1.0.18, since it was the current version at alsa-project.org.

I know that sound from the speakers is not working on the unibody Macbook Pros. Should we address this here, or in a new post? I cannot find any  existing posts that address what appears to be a major problem.

---

### Post by cyberdork33 on 2008-11-04
> **clebio said:**
> I know that sound from the speakers is not working on the unibody Macbook Pros. Should we address this here, or in a new post? I cannot find any  existing posts that address what appears to be a major problem.

A new post would be best.

---

### Post by calebio on 2008-11-04
> **clebio said:**
> I know that sound from the speakers is not working on the unibody Macbook Pros. Should we address this here, or in a new post? I cannot find any  existing posts that address what appears to be a major problem.

This is me. I guess i have two accounts.... quite by accident. It won't happen again!

---

### Post by calebio on 2008-11-04
> **cyberdork33 said:**
> A new post would be best.

It's _[here]("http://ubuntuforums.org/showthread.php?p=6107567")_.

---

### Post by cyberdork33 on 2008-11-04
> **calebio said:**
> This is me. I guess i have two accounts.... quite by accident. I won't happen again!

You should make a post in the Forum Feedback & Help forum to have an admin remove your other account as you are only allowed to have one.

---

