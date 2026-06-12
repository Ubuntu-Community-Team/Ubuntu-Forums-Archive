---
title: "No sound out of soundcard."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-06-11
Hi, I have an IBM thinkpad
Ubuntu plays the log on sound but then no other sounds can ever be heard. No mp3s, no wav files.. When i click "test" in the sound control panel.. I hear nothing for any of the settings..

Anyone help?:D

EDIT: actually , i can't even hear the system sounds either!

---

### Post by southernman on 2007-06-11
I believe all you'll need to do is go to: Applications > Add/Remove Programs

In the top right corner make sure it shows you, "All avaliable applications"

On the left hand side now select Sound and VIdeo.

In the Application list, scroll down to Gstreamer plugins and choose those you want to use... one or all of them depending on your needs.

Once done with that, click the apply button.

Happy Listening!

Oh btw, you'll get notices about making sure it's legal to use those plugins. If it is legal in your country just keep moving forward. ;)

---

### Post by systemintheglitch on 2007-06-11
Hmmm..
I don't think so..
I allready have the plugins for mp3, yet I cant currently play mp3s.. etc..
I can't hear anything, not even the test sounds.. 
BUT, I can hear the logon sound!

Any help guys?

---

### Post by southernman on 2007-06-11
Sorry, it's been a long day! After re-reading your OP I see that's not what you asked for.

In your sound dialogue box (control panel) What are the options for drivers? ALSA, OSS... or auto.

By chance, does your mobo have onboard sound? if so, what chipset is it? Little info like that supplied in the OP can help.

Do you have a seperate sound card?

Having onboard stuff and a PCI card, can cause conflicts sometime.

---

### Post by systemintheglitch on 2007-06-11
I have onboard sound because it is an IBM laptop.
Everything says autodetect in that panel. But i tried EVERYTHING and nothing works.. I tried selecting OSS, ALSA, etc.. everything.

Also, it has the option to select "Intel ICH6" and "Intel ICH6 -IEC958"
and some other options. like "ESD".. But like I said nothing works.. 
And I had an previous ubuntu version where this worked before I reformatted..

:(

---

### Post by southernman on 2007-06-11
> **systemintheglitch said:**
> I have onboard sound because it is an IBM laptop.
 D 'oh in my best Homer Simpson voice!

The only thing further, I can do is refer you to this:

[https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")


Hope that helps

---

### Post by systemintheglitch on 2007-06-11
None of that worked.
:(

EDIT: and no system sounds work, now that i realize it.

---

### Post by Lord_Alda on 2007-06-11
Mine neither... 
Icpci:
Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by systemintheglitch on 2007-06-12
So noone can help at all?

---

### Post by Paul_world10 on 2007-06-12
at erminal type    lspci 

might have to check alsa mixer stuff also

---

### Post by Lord_Alda on 2007-06-12
Install GNOME ALSA mixer. and play around unmuting everything.. but before that check out... [THIS]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards").

---

