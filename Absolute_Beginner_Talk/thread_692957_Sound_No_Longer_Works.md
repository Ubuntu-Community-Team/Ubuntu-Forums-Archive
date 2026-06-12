---
title: "Sound No Longer Works"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by BigRon on 2008-02-10
Hello Again, 

When I first installed Ubuntu 6.10 the sound worked perfectly, could listen to CDs etc easily, however I couldn't get on the internet (I had one of those awkward modems).

A friend came round and got me online, but now since getting the modem to work I haven't heard one sound from the PC. Even the little jingle when you start up/shut down is gone. 

Before you ask, the volume slider in the top right hand corner is at max and is definately NOT on mute (I read someone made that mistake earlier). 

I am thinking that maybe my friend did something in the terminal to silence the pc while he was working but I don't know what on earth that could have been. It's a mystery. At first I thought it could be the speakers but I plugged in my headphones and they don't work either.

I'm a beginner so I don't know how to check which soundcard I have or if it is operational.

Any ideas ladies and gentlemen?

Any help on this one would be much appreciated because I miss being able to listen to tunes and videos etc on the PC.

---

### Post by eggdeng on 2008-02-10
To identify your card
```
aplay -l
```
(That's lowercase L)
One way to check if it is working is to play an mp3 in something like xine or audacity where you get  a visual representation of the sound.

---

### Post by BigRon on 2008-02-13
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is the result of typing in aplay -l , The sound worked really well until recently which is weird. I was listening to cds on the day of install and now the pc is completely silent. It's odd, I can't think what could have happened between now and then. It's baffling.

I typed in alsamixer and it indicated that the master sound is on and at max level. Any help on this would be fantastic. :confused:

---

### Post by Redptc on 2008-02-13
Did you right click on the sound icon to bring up ' open sound control'. I find I frequently have to move both the 'master' and 'PCM' controls in order to restore the sound.

If this brings the sound back, there is a process which makes you card the default and this may bring things back to normal. 

:redface:  [COLOR="Red"]Redptc[/COLOR]

---

### Post by mmb1 on 2008-02-13
Could you post your alsamixer output here please?

---

### Post by reehan10 on 2008-02-13
Hi there...
go to sound icon on the panel and right click and select 'open volume control'
there from edit>preferences select surround as well as pcm...then click ok..and then raise both the sludebars to the max...;-)

---

### Post by Redptc on 2008-02-13
> **reehan10 said:**
> Hi there...
go to sound icon on the panel and right click and select 'open volume control'
there from edit>preferences select surround as well as pcm...then click ok..and then raise both the sludebars to the max...;-)

I don't come up with 'Surround' ?  using 7.10  :confused: (not my thread but trying to sort ongoing problems myself)


[COLOR="Red"]Redptc[/COLOR]

---

### Post by BigRon on 2008-02-13
Thankyou all very much for taking the time to help me out with that. :guitar:  

I'm now listening to a bit of James Brown thanks to you!

I hope that one day I see this question come up again and I can help someone out.

---

### Post by littletinman on 2008-02-13
I'm having sound issues with no output. how do i get to alsa output?

---

### Post by Redptc on 2008-02-13
Glad your sound is back!

What was the thing that made it work? Do you think it is permanent, ie does it come back on every time you re-boot?

I'm asking because mine is a periodic thing, in that it works fine for a while but will suddenly stop working. It will then come back again. It seems that Ubuntu will forget about it on reboot but, inexplicably, after a few re-boots, it will start again.

I suggest you see how it goes for a week or so and, if all is well, mark this thread as solved.

---

### Post by Redptc on 2008-02-13
> **littletinman said:**
> I'm having sound issues with no output. how do i get to alsa output?

Do the same as indicated in the previous threads and advise of any results.

---

### Post by littletinman on 2008-02-13
here's what the alsa- thing does 

 **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


All visual audio things work. There's no input and no output (mic/speakers/headphones) it's all nothing. Help?

---

### Post by Redptc on 2008-02-13
> **littletinman said:**
> here's what the alsa- thing does 

 **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


All visual audio things work. There's no input and no output (mic/speakers/headphones) it's all nothing. Help?

Do you get the sound icon in the 'panel'?

Are you able to right-click and get 'open-sound-control'?

If so you should get a panel indicating your sound controls!

---

### Post by littletinman on 2008-02-13
it says open-volume-control

---

### Post by Redptc on 2008-02-13
When you open volume control, move the master and pcm button, then return it to the max. Then go somewhere and see if you have sound.

---

### Post by littletinman on 2008-02-13
I have no sound at all!!!!! nothing. just silence. How do i see if there's an output in the terminal?

---

### Post by Redptc on 2008-02-14
Have a look at this to see if it helps!  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by BigRon on 2008-02-15
Upping the pcm level in alsamixer, compared with edit preferences and allowing sound in the ubunmtu sound settings fixed the problem for me. I have not used my home pc since this issue was fixed but at least I know what to do if it happens again. 

I will let you know if ubuntu remembers or not.

Thanks again to all for the helpful advice.

---

