---
title: "webcam"
date: 2004-11-09
forum: Apple PPC Users
---

### Post by trash on 2004-11-09
WOW I was so surprised, I pluged in my USB Logitech QuickCam Pro 3000 (AKA Phillips 730), fired up Gnomemeeting went through the set-up and there it was, PERFECT video!! Ubuntu does it again lol! So anybody looking to buy a webcam, i would recommend go Phillips compatible.
The cam I have though has the microphone built in... i know this seems to be an issue and i have search this forum but haven't found a good method yet. if anybody has experienced this situation i'd like to hear about it... i've adjusted everything i have found regarding ALSA but nothin works.

Also I wanna get this(gnomemeeting) working to use the phone capabilities so feedback on that aspect would be great to.

mucho thanks:)

---

### Post by trash on 2004-11-14
I tried the fix below using 'snd-powermac' for my sound module, but nothing changed.
can anybody help?
thanks

**********
In order to fix the problem with the USB webcam microphone, this
has to be added in the modprobe.conf:

alias snd-card-0 <your-sound-module> 
options <your-sound-module> index=0

alias snd-card-1 snd-usb-audio
options snd-usb-audio index=1

this will make the usb microphone come second, thus not
affect the overall sound output of the system.

*****

---

### Post by sumanjay on 2004-11-14
My experiences with the webcam and gnomemeeting were slightly different, but much less successful. While going thru the setup wizard for gnomemeeting, the microphone was correctly detected (as camera), but the camera itself wasn't! So I can use the microphone on the webcam, but I can't get any video input or pictures! Now if only we could graft our experiences together - we'd have a working webcam  ](*,) 

PS - I have a Logitech Messenger webcam with the built in mike. Not much different from the Pro version.

---

### Post by trash on 2004-11-15
hmmmm, yes well in the process of trying to get my mic working i have now knocked out sound for my cd.... grrrr, i'm sure it's a simple fix... but still another to add to the growing list of fixes lol.

I'll get back to ya with any progress i make... i'll keep the cam in mind but since i didn't do anything at all to get it workin I can't even tell ya where to start..... ](*,) ..indeed.

---

### Post by trash on 2004-12-03
can anybody write a howto for this issue??
i've checked out both bug reports which both suggest fixes but neither work..

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=106748#c2&gt;](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=106748#c2&gt;)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1293](https://bugzilla.ubuntu.com/show_bug.cgi?id=1293)

anybody?

this is what i've added to my etc/modprobe.d/aliases...
alias snd-card-0 snd-powermac
options snd-powermac index=0

alias snd-card-1 snd-usb-audio
options snd-usb-audio index=1

sumanjay, you had any luck getting your cam workin?

---

### Post by azelter on 2004-12-03
Hmm, I've also had similar experiences. I have a Logitech QuickCam 4000 Pro. Video works fine in gnomemeeting, but no audio. The correct drivers seem to be loaded when I plug it in, as /var/log/syslog shows:
Dec  2 21:09:29 pohjanakka kernel: usbcore: registered new driver Philips webcam
........... (cut several lines)
Dec  2 21:09:29 pohjanakka kernel: usbcore: registered new driver audio
Dec  2 21:09:29 pohjanakka kernel: drivers/usb/class/audio.c: v1.0.0:USB Audio Class driver
Dec  2 21:09:29 pohjanakka usb.agent[5350]:      pwc: loaded successfully
Dec  2 21:09:29 pohjanakka usb.agent[5352]:      audio: loaded successfully
Dec  2 21:09:29 pohjanakka usb.agent[5352]:      pwc: already loaded
Dec  2 21:09:29 pohjanakka usb.agent[5354]:      pwc: loaded successfully
Dec  2 21:09:30 pohjanakka usb.agent[5352]:      snd-usb-audio: loaded successfully
Dec  2 21:09:30 pohjanakka kernel: usbcore: registered new driver snd-usb-audio
Dec  2 21:09:30 pohjanakka udev[5504]: creating device node '/dev/dsp2'
Dec  2 21:09:30 pohjanakka udev[5505]: creating device node '/dev/mixer2'

Interstingly, the first time I installed ubuntu, I then did an apt-get upgrade plus apt-get dist upgrade to Debian testing and was left with a reasonably functional split-personality Debian/Ubuntu system in which gnomemeeting could use the webcam and built in mic fine. When I decided to reinstall and stick to Ubuntu however, I find I can only use video. If the webcam is pluged in when I boot up, I lood the onboard soundcard (as it makes the primary audio device the webcam), but still can't use the webcam microphone!!! Shame I didn't look at the syslog when it was working...

Ah well.

---

### Post by trash on 2004-12-03
Oh yay! there's hope ! Like you azelter, my syslog looks fine to...

since the bug reports are 'resolved' and seeing as you have had it working before there really is no reason why a good howto doesn't exsist... even the gnomemeeting website states that webcams with mics are supported, but thats as far as they go. 
So I tried installing my ibot firewire cam which just doesn't want to work, and everywhere I look for info a new/different driver or plugin comes up... tres too complicated lol.
I also tried a macally usb mic(without the phillips webcam pluged in) it did light up but would not record.
My usb cam does work very well in gnomemeeting and camstream but not at all in ayttm or xawtv

So anybody out there with the know howto:

firewire webcams
usb webcam/mic
usb mic

howto's needed:)

---

### Post by azelter on 2004-12-14
OK. I got it working now.
To get the audio working you just need to add one line:
audio
to your /etc/hotplug/blacklist file
This prevents the audio driver being loaded by usb.agent so you get :
Dec 14 19:24:21 pohjanakka usb.agent[4725]:      audio: blacklisted
instead of
Dec  2 21:09:29 pohjanakka usb.agent[5352]:      audio: loaded successfully

Then when (later) the snd-usb-audio module is loaded:
Dec  2 21:09:30 pohjanakka usb.agent[5352]:      snd-usb-audio: loaded successfully
It actually works. If the audio module is loaded first (which it is if it isn't blacklisted) then the second module won't work and you therefore don't get audio.
In debian testing the 'audio' module was automatically blacklisted in the /etc/hotplug/blacklist.d/alsa-base file (hence the camera worked for me with that system).  In Ubuntu it is not.
Hope that solves other peoples problems as it did mine.
Cheers

---

### Post by trash on 2004-12-15
Nice goin azelter \\:D/ 

I'm not sure when or why this happened but now when i start 'gnomemeeting -d' from the terminal i get an error 'can't access shared library libpt.so'.. so gnomemeeting won't even open. Strange part is Synaptic tells me libpt is installed, and when i try to upgrade it, it wants to remove gnomemeeting... so i have made the audio change but have yet to be able to test it.

---

### Post by trash on 2005-02-01
Ok back to the cam/gnomemeeting issue...

 $ gnomemeeting -d
gnomemeeting: error while loading shared libraries: libpt.so.1.6.6: cannot open shared object file: No such file or directory


anybody else getting this? the libpt i have installed is libpt.so.1.6.5 and i can't find 1.6.6 anywhere on my system or for download... I did come across a couple of post by somebody else on the gnomemeeting list with 1.6.6 issues but they were unrelated to my problem, as my cam works fine with camstream and their cam didn't work at all. The other poster suggested it was a known problem in Ubuntu(can anybody confirm?)

thanks

---

### Post by khc on 2005-02-01
If you are brave, you can simply symlink libpt.so.1.6.6 to whatever you have. That may or may not work.

---

### Post by trash on 2005-02-01
hehe, that was the first thing i thought about.... so ya went ahead and did it.
now I get:

gnomemeeting -d
gnomemeeting: relocation error: /usr/lib/libopenh323.so.1.13.4: undefined symbol: _ZTI11PASN_Choice

arg!

---

### Post by bedge on 2006-06-25
ohphone: error while loading shared libraries: libpt.so.1.9.2: cannot open shared object file: No such file or directory

so...

0 #> ln -s /usr/lib/libpt.so /usr/lib/libpt.so.1.9.2

Then it starts.

-Bruce

---

