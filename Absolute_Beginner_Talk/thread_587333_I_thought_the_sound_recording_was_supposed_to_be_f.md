---
title: "I thought the sound recording was supposed to be fixed in 7.10 :("
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-10-22
Sound recording was broken in Feisty. I have tried every suggestion in this forum with no luck. Neither Sound Recorder or Audacity or any other sound pgm.  will let me record.  I can hear the music/streaming audio I just can't record it. Just gives me a "flat line".  Switching between ALSA and OSS doesn't help...

I have been fighting this issue since 7.04 in April. The pre-release info. said that this would be addressed in 7.10. I need to use this pc for audio recording, & it figures, that is the very thing I am unable to do... I see threads all over the forum about the recording issue. Why is this such a problem with this OS?

 Can anyone help me out with this problem at all? ](*,)

---

### Post by Dr Small on 2007-10-22
I basically want to be able to record streaming audio, or audio that I can hear, the same way, but was never successful myself. I have the same problem, only I am running Feisty ;)

Dr Small

---

### Post by discmaster on 2007-10-22
Check out the poll results in this thread...
[http://ubuntuforums.org/showthread.php?t=102377](http://ubuntuforums.org/showthread.php?t=102377)

57% can't record! What the heck??? This thread is from '05 & the developers still can't get it worked out. :( Why is this so difficult?

---

### Post by discmaster on 2007-10-23
Please help, anyone?!?!? :cry: I want so badly to continue using linux, but without being able to record audio, I guess I will be forced to move back to windows... :(

If anyone is able to help me to avoid going back to "Bill", I would surely appreciate it! I don't have any real ideas on how to fix this, don't even know where to look, other than the volume device settings, etc. Changing the settings seems to do nothing for me.

Not real clear on how to use the JACK, someone suggested that might fix it, I don't know...:(

---

### Post by qix on 2007-10-23
Just a quick note: Tried using ubuntustudio?
[http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by discmaster on 2007-10-23
Yes I am using ubuntu studio now; for some reason, my pc seems "slower" now, & I also still can't record. I am guessing it is a hardware conflict. Nothing will "capture" audio wise... :(

---

### Post by zettberlin on 2007-10-25
What evil Soundchip do you use?

Find out and maybe solve the issue with alsamixer:

# alsamixer
change to the capture-channel with TAB, leave the mixer with ESC. 
What does this show?

---

### Post by Qwerty_ on 2007-10-25
I was able to record streamed stuff. IIRC you have to set the sound recorder to record the mix.

There is a tutorial out there that I stumbled apon whilst trying to record Skype convos.

---

### Post by Drakkor on 2007-10-25
When I upgraded to Gutsy,I got the new Audacity, and now I can record anything that the
computer plays, because now there is an "input", selector , mine, as you can see is set
to "Vol". Hope this helps. I had no "input" selector in Fiesty. Also , if you want to record 
steams,streamtuner is nice !

---

### Post by WIREHEAD on 2007-10-29
Drakkor,

Man , you have no idea how glad I am to hear that there is a solution to this problem  !

Now , if I can upgrade I'll be set.
 ( If anybody has a solution to Wine's server being down and  not being able to upgrade due to failure to retrieve these packages I'm willing to listen )

Thanks !

---

### Post by shirsch on 2007-10-29
Let me chime in with the chorus...  Despite my best efforts, Ubuntu's Audacity just refuses to "see" any form of input regardless of settings.  I'm running Kubuntu 7.10, FWIW.

After spending an entire morning beating my head against the wall, I ripped the packages off and built audacity from their official sources (1.3.3).  After some experimentation with kmix settings, Bingo! It worked.  After having it come to life, I tried going back to the Ubuntu package.  Once again, nothing.

The pulldowns on the Ubuntu version show a variety of possible inputs and outputs, all with zero explanation and all with (apparently) no correlation to anything I see in kmix.  The hand-built sources see only OSS /dev/dsp, but work perfectly.  At the risk of repeating myself, the exact same selection in the Ubuntu package fails to work.  The posting above this one shows a selection called 'Vol' available on the pulldown.  I have no such choice.

Given that I can record with the locally built Audacity, a few more questions:  

- What is the distinction between the input selector pulldown on the main GUI and the ones available for input and output in preferences?

- Why is the level slider on Audacity non-functional?  I have to adjust record level via the 'Line' slider on the kmix 'Output' tab.

- I found it necessary to have the red button underneath 'Capture 0' on the kmix Input tab pressed.  However, the slider above it has no effect and the recording works even when all the way off.

- I am unable to find any block diagram or description regarding what the various kmix settings are actually doing.  Which switches and faders feed which blocks in the audio processing chain?  How can one find out this critical information?

I have to say that audio processing on Linux is really still a mess.  Very disappointing.  It's bad enough that things don't work, but the utter lack of system-level documentation just puts the icing on the cake.

---

### Post by scaglifr on 2007-10-30
I too am stuck on this one,  Have been using audacity to record anything that plays on suse for years, thought I would try ubuntu.  I do have a "vol" selector but despite any settings adjustment in audacity (as supplied with gutsy) I still cannot record.

---

### Post by wolfvorkian1 on 2007-10-30
> **Dr Small said:**
> I basically want to be able to record streaming audio, or audio that I can hear, the same way, but was never successful myself. I have the same problem, only I am running Feisty ;)

Dr Small

You can Doc, read the below. It works, I've used it. 

[http://www.linux.com/articles/43721](http://www.linux.com/articles/43721)

---

### Post by Drakkor on 2007-10-30
As I said before,if you want to record audio streams e.g. internet radio,you can't beat streamtuner along with streamripper,it records via the terminal to a folder in you home folder ! :)

---

### Post by discmaster on 2007-10-30
@ Drakkor,

As per your prev. post (#9) that is very interesting; I have the same vers. as you, & my pgm. does not have that vol. dropdown control. I have checked "view all toolbars", & it is still not there... :confused:

---

### Post by Drakkor on 2007-10-30
Ok, discmaster, what kind of "Record from input" options do you have in the drop-down box of the Sound Recorder program ? Mine is set to "Mix" here:

---

### Post by discmaster on 2007-10-30
I have "digital" & "capture". I have tried each setting. None will record for me.

BTW, what sound card are you using? Onboard or pci card? Also, what mainboard?

---

### Post by Drakkor on 2007-10-30
You're getting where I'm leaning to, it may be a function of your sound card to record "What you hear", I have a Soundblaster Live Card with an Asus mainboard. you could try what I found here: [http://www.forum4designers.com/archive58-2005-3-203737.html](http://www.forum4designers.com/archive58-2005-3-203737.html)

---

### Post by FuturePilot on 2007-10-30
> **Drakkor said:**
> When I upgraded to Gutsy,I got the new Audacity, and now I can record anything that the
computer plays, because now there is an "input", selector , mine, as you can see is set
to "Vol". Hope this helps. I had no "input" selector in Fiesty. Also , if you want to record 
steams,streamtuner is nice !

Yes it did come back! I was also missing it in Feisty. w00t!\\:D/

---

### Post by discmaster on 2007-10-30
I checked out your link; Funny thing is, all items are unmuted my default. I have went through &  muted/unmuted, various settings, did just about every configuration you could imagine, & the closest I got was 1 scratchy record channel in audacity.

This hasn't worked for me in 7.04 or 7.10. I am thinking that another sound card is in order here. I just want to be sure of getting one that I know will work; I don't want to have to experiment w/ a 1/2 dozen cards until I nail it. :popcorn:

---

### Post by Drakkor on 2007-10-30
Yeah,discmaster,don't want to rub it in,but here's the choice for "Record from input" options 
on my Soundblaster Live card.... :)  You should be able to pick one up pretty cheap,they're kinda old,lol !

---

