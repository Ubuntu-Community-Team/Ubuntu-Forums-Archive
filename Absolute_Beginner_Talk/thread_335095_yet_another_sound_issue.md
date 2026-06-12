---
title: "yet another sound issue"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-01-09
ok i had a the prob with flash just like everyone else. installed swiftfox and plugins got it all good then i updated to flash 9 it was mute again but with video, fixed that now i have no sound at all on the whole system. it just went out one day i turned on the pc. what is wrong???? also how do i play .wma files???? and why wont my m player play mp3's anymore??? why is there such stupid problems with ubuntu???

---

### Post by WiseElben on 2007-01-09
I don't understand how you suddenly can't play MP3's. Try to [install]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") the codec's again. I would suggest that you do not use the 64bit version because it is definitely harder to get stuff working on it. This, of course, would be a last result.

---

### Post by antgul3382 on 2007-01-10
i have no sound at all not just mp3

---

### Post by ComplexNumber on 2007-01-10
there are several things to check: 
1) main menu -> system -> preferences -> sound.
2) volume control and default sound card (see screenshots). check to see if nothing is being muted etc.

---

### Post by antgul3382 on 2007-01-10
My Sound Options Doesnt Look Like That?!?!??!?!

---

### Post by ComplexNumber on 2007-01-10
> **antgul3382 said:**
> My Sound Options Doesnt Look Like That?!?!??!?!
well post a screenshot to show what they look like.

---

### Post by antgul3382 on 2007-01-10
Ok

---

### Post by Eddie Wilson on 2007-01-10
Are you sure its not a hardware problem now?

---

### Post by antgul3382 on 2007-01-10
How Is That Possible??? It Was Working And The Sound Works On Windows Xp Mce

---

### Post by moeFinley on 2007-01-10
The screenshots posted by ComplexNumber are of the volume control.  You can access this by double clicking on the speaker icon next to the date/time (or just above the sexy lady's head).

Make sure you go to Edit -> Preferences and switch on all the relevent controls.

This will show you your installed sound cards.  Check that it's installed or you might have two and it's outputing to the wrong device.

```
aplay -l
```

This will play a sound file to the default device.

```
aplay -D default /path/to/audio/file.wav
```

You can also change 'default' to a sound device listed with the previous command.

If you using ALSA a lot of problems can be sorted by correctly editing your /etc/asound.conf file.  I really don't know why Ubuntu doesn't have a wizard during the install to configure this file!?  On [this page]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound") there is a good example which can be adapted quite quickly.

[Here is a good ALSA troubleshooting guide]("http://alsa.opensrc.org/TroubleShooting")

---

### Post by antgul3382 on 2007-01-10
thanks man some were muted alls well!!!! thanks again i was about to throw the **** out the window~8)

---

### Post by moeFinley on 2007-01-10
Glad I could help.

I remember the when (about eight months ago) the simplest thing seems a complete nightmare because you don't know where to look.  But trust me, just as you've learnt how to do it all in Windows, soon you'll be doing it in Linux.  Then you'll have a free OS for life.

---

### Post by ComplexNumber on 2007-01-10
> **antgul3382 said:**
> thanks man some were muted alls well!!!! thanks again i was about to throw the **** out the window~8)
that happens a lot, and thats what i suspected.

---

### Post by antgul3382 on 2007-01-10
yeah im getting pretty good with it now this is a first in a while......i love linux and i was all about ms stuff, now that ive used ubuntu i refuse to use it aside from certain things i absolutley cant do with ubuntu


thanks again

---

### Post by Eddie Wilson on 2007-01-10
Sorry, I didn't know you had sound in Xp.
Eddie

---

