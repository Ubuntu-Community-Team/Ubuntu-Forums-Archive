---
title: "Un-muted in alsamixer but no sound"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by wispygalaxy on 2007-10-20
I have no sound on Ubuntu. I went into alsadisk, and un-muted "Caller I" and "Off-Hook". But it goes back to mute. I did this: (copied from the Comprehensive Sound Problem Solutions Guide)


[COLOR="Green"]Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1.
[/COLOR]

I plugged in zero after "sudo alsactl store". When I open alsamixer, it still says mute for those two!  How do I "save" the settings and get sound?  Thanks for the help!  :-)

---

### Post by Frak on 2007-10-20
What is your sound card.

---

### Post by khughitt on 2007-10-20
what is the output from the command **asoundconf list**?

---

### Post by wispygalaxy on 2007-10-20
> **pwnedd said:**
> what is the output from the command **asoundconf list**?

Names of available sound cards:
Intel


Hope that helps!

---

### Post by Frak on 2007-10-20
This may be throwing a stone into the middle of nowhere, but
run
```
sudo aptitude reinstall alsa
```

I've never experienced issues with Intel before

Also, make sure your sound card isn't disabled in your BIOS

---

### Post by wispygalaxy on 2007-10-20
> **Frak said:**
> This may be throwing a stone into the middle of nowhere, but
run
```
sudo aptitude reinstall alsa
```

I've never experienced issues with Intel before

Also, make sure your sound card isn't disabled in your BIOS

Yep, ran that in Terminal, but no sound.  How do I check my sound card in BIOS?  I'm REALLY new to Linux, as you can see.  :redface:

---

### Post by Frak on 2007-10-20
When your BIOS screen appears press whatever it tells you to go into setup, then go under devices/perephrials/etc. (varies from BIOS to BIOS) then go under your sound card and make sure its enabled, then save and exit.

---

### Post by wispygalaxy on 2007-10-20
> **Frak said:**
> When your BIOS screen appears press whatever it tells you to go into setup, then go under devices/perephrials/etc. (varies from BIOS to BIOS) then go under your sound card and make sure its enabled, then save and exit.

Should I push Del or F2 during bootup?  It doesn't open BIOS for me...

---

### Post by wispygalaxy on 2007-10-20
I opened BIOS finally.  But there was no setup menu, or anything that had to do with the sound card.

---

### Post by GSF1200S on 2007-10-20
Post the results of:

```
lspci
```

Ive never had an issue with audio, so i may not be much help...

---

### Post by wispygalaxy on 2007-10-20
> **GSF1200S said:**
> Post the results of:

```
lspci
```

Ive never had an issue with audio, so i may not be much help...

Yes, it says that my Audio Device is an Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Don't know how to tinker with that, though :(

---

### Post by GSF1200S on 2007-10-20
> **wispygalaxy said:**
> Yes, it says that my Audio Device is an Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Don't know how to tinker with that, though :(

HUh? WEeeeeiiird... this is what my lspci

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


! We have the same thing, but mine works without a hitch.. im almost going to bet its something in your bios- which bios do you have (phoenix, dell, etc).

Ill check out sound drivers for that, but that card is supported out of the box on gutsy. You either had bad luck and it got messed up, or your BIOS is preventing it from working.

---

### Post by wispygalaxy on 2007-10-21
> **GSF1200S said:**
> HUh? WEeeeeiiird... this is what my lspci

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


! We have the same thing, but mine works without a hitch.. im almost going to bet its something in your bios- which bios do you have (phoenix, dell, etc).

Ill check out sound drivers for that, but that card is supported out of the box on gutsy. You either had bad luck and it got messed up, or your BIOS is preventing it from working.

Funny thing is that with my BIOS, I can't find the spot where the sound card is.  I guess there is a problem in BIOS.  I have a Toshiba laptop called Satellite A205-S4607 System Unit.  Is there a problem with Aslamixer, since whenever I go into it, it says it's muted.  But I can't keep it unmuted.

---

### Post by GSF1200S on 2007-10-21
What happens if you type alsamixer in a terminal. I cant really tell what you are talking about with alsa mixer..

Type alsamixer in a terminal, take a screenshot and attach it to a post here. At least then I can see what you are talking about.

**EDIT** You prolly have a phoenix bios like I do.. they are notorious for sucking as it pertains to giving user options...

---

### Post by wispygalaxy on 2007-10-21
> **GSF1200S said:**
> What happens if you type alsamixer in a terminal. I cant really tell what you are talking about with alsa mixer..

Type alsamixer in a terminal, take a screenshot and attach it to a post here. At least then I can see what you are talking about.

**EDIT** You prolly have a phoenix bios like I do.. they are notorious for sucking as it pertains to giving user options...

Ok, I have the screenshot in the attachment.  I can't really interpret it LOL.  Sorry, ignore that box in the middle of the screen.

EDIT: I unmute the two columns, but they keep going back to mute.

---

### Post by GSF1200S on 2007-10-21
First off, turn master all the way up (use your keyboard controls while the terminal is up)

**EDIT** This is what mine looks like- its weird its so different-

---

### Post by wispygalaxy on 2007-10-21
> **GSF1200S said:**
> First off, turn master all the way up (use your keyboard controls while the terminal is up)

**EDIT** This is what mine looks like- its weird its so different-

Alright, I did that.  Should I unmute?

EDIT:  Maybe I should upgrade alsamixer?

---

### Post by GSF1200S on 2007-10-21
Yeah.. but where are you muting exactly?? 

Check out this thread... 

[http://ubuntuforums.org/showthread.php?p=3587127#post3587127](http://ubuntuforums.org/showthread.php?p=3587127#post3587127)

Make sure the master channel is set to "Master"- 

I wish a sound vet would come along because im running out of ideas... you can post a pic of *where* youre unmuting, and tell us *what* you are unmuting.

If i cant give you an answer, bump this thread tomorrow so that someone else can try...

---

### Post by wispygalaxy on 2007-10-21
I'm testing the sound in "sound preferences".  Should it take a long time?

---

### Post by GSF1200S on 2007-10-21
> **wispygalaxy said:**
> I'm testing the sound in "sound preferences".  Should it take a long time?

It shouldnt, but Ive never done it. I dont think that will help, though.

Im going to attach the attachment submitted by another forum guy. See at the bottom where it talks about "Default Mixer Tracks?"

Make sure that "Master" is selected- if PCM is selected, Mute will not toggle. 

Im going to throw the towel here.. if the default mixer tracks doesnt help you, well have to hope someone else comes along. This community is the best, and help should arrive soon. 

Issues come and get fixed by this community.. welcome to Ubuntu (sorry about Vista)

---

### Post by wispygalaxy on 2007-10-21
Thanks, pal, but I'm going to stop for now.  I will visit my college tech center soon, so I guess things will be ok.  Thank you very much for helping me.  I'm glad I got Ubuntu, freezes less often than Vista.  See you around!  :)

---

### Post by GSF1200S on 2007-10-21
Yup yup.. defintely call toshiba and get them to send you a disk.. I dont think the tech center will be able to help.

---

### Post by Frak on 2007-10-21
> **wispygalaxy said:**
> Yes, it says that my Audio Device is an Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Don't know how to tinker with that, though :(
Weird that's my card also :confused:

Call Toshiba for the Disc also.

---

### Post by wispygalaxy on 2007-10-21
Thanks GSF1200S and Frak.  :-)  I think I have the disc at home, and I will look for it.  That is probably what caused all of this.

---

### Post by adamorjames on 2007-10-21
I have a Toshiba laptop A105 S4284 with an HDA Intel in it. On Gutsy, I got my sound to go from barely audible to working great by using the kernel that I think came with Tribe 5, 2.6.22.10. I think it is a kernel problem :). 

I wouldn't suggest installing a new Alsa because I had a bad experience with that. Use it as a last resort I say. :lol:

---

### Post by wispygalaxy on 2007-10-21
Thanks for the response, adamorjames.  But I'm going to a tech support center tomorrow.  I'm scared to do anything now since this sound problem is so strange.  Thanks anyway!  :-)

---

### Post by adamorjames on 2007-10-21
> **wispygalaxy said:**
> Thanks for the response, adamorjames.  But I'm going to a tech support center tomorrow.  I'm scared to do anything now since this sound problem is so strange.  Thanks anyway!  :-)

Welcome! Good luck wispygalaxy :D

---

