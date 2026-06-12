---
title: "Alsa, oss what's what?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-01-15
I'm kind of confused with audio... I have only one audio card... integrated one... but in the mix I see actualy two devices (that both control the same hardware together)... RealtekALC883 (OSS Mixer) and HDA Nvidia (ALSA mixer) why is that?
Also the gnomemeeting (ekiga) had some troubles when I had nvidia selected... but other that that was just Default....

Somebody explain?

---

### Post by kane77 on 2007-01-15
in ekiga I get this error: 
```
An error occured while trying to play audio to the soundcard for the audio reception. Please check that your soundcard is not busy and that your driver supports full-duplex.
The audio reception has been disabled.
```

what can I do??

---

### Post by xpod on 2007-01-15
Have you tried playing around with the options in Sys>pref>sound??
Or checking the alsamixer settings by typing alsamixer in the terminal or right clicking your volume icon for sound prefs and making sure nothings muted etc

I believe alsa is what you want but Im not too sure myself so mabey this might have something of use??

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

---

### Post by kane77 on 2007-01-15
now I lost sound! :(
it's not muted... I checked everything... the music seems as if it's playing but no sound :(

what do I do??

---

### Post by ComplexNumber on 2007-01-15
OSS is the old(and largely defunct) sound driver, i'm  led to believe.

i had the "no sound" problem recently, but it was random (sometimes when i logged in, i would have sound. sometimes not). 



are there any sounds that play? for example, in my case, i could play mp3's, but various audio applications would be silent.

---

### Post by zellis on 2007-01-15
Linux's inner workings actually includes two different systems for playing sound. The older one is called OSS and is limited in its ability to play sound from more than one application at a time, but supports older soundcards very well. The newer one is called Alsa, is more sophisticated (can play sound from multiple sources) and can support some newer soundcards that OSS can't, but is less well developed.

Not sure what would make your sound go away after fiddling with them. Ummm....check that the master volume isn't set at 0?

---

### Post by xpod on 2007-01-15
I got a built in realtek ac97 audio chip  and it all worked great out the box......I did have issues with initial flash sound in dapper but it was fixed with some line of code.
I have had my sound become muted on occasion too but that was easily fixed via alsamixer

I dont have dapper just now and cant quite recall if the sound utility in that was the same as the one here in edgy....I`m sure i had to use the "multimedia system selector" in dapper for the same options i can access via "sound" here in edgy:-k 

You could change from alsa to oss etc and do basic sound tests with it.

---

### Post by kane77 on 2007-01-15
> **xpod said:**
> You could change from alsa to oss etc and do basic sound tests with it.
hmm.. how do I do it though...

on my setup it seems that both the oss and alsa work together (obviously in some conspiracy)... Both sliders work together independently so I can lower/increase the volume with 3 different sliders... (pcm, master on alsa and volume on oss..) I'd be glad to only have alsa.. but how do I do it?

---

### Post by ComplexNumber on 2007-01-15
> hmm.. how do I do it though...go to main menu -> system -> preferences -> sound. by default, you'll se that they are all on 'autodetect'. change it to alsa.



do you have the volume control applet on your panel? if not, right click on the panel, select 'add to panel', select 'volume control'. if so, right click on it, select 'preferences'. what does it give as your default sound card? now close that.
then right click on the applet again, select 'open volume control', select 'File' in the menu, then select 'change device'. select the alsa version.
it may need a reboot for the changes to be set up, but i can't confirm that.

---

### Post by kane77 on 2007-01-15
> **ComplexNumber said:**
> go to main menu -> system -> preferences -> sound. by default, you'll se that they are all on 'autodetect'. change it to alsa.

err... the choice is greyed out.... :(

---

### Post by ComplexNumber on 2007-01-15
> **kane77 said:**
> err... the choice is greyed out.... :(
in that case, fire up your terminal and type in 'gnome-sound-properties'. tel me what happens and if it shows any errors.

---

### Post by kane77 on 2007-01-15
> **ComplexNumber said:**
> in that case, fire up your terminal and type in 'gnome-sound-properties'. tel me what happens and if it shows any errors.

well it starts the sound management, I may have said it wrong... I ran that before, only the dialog for selecting defauld sound card is greyed out... Some other way to switch only to alsa...

the error I get when I recieve call on my ekiga is about card not being able to work in full-duplex... but I'm sure it is...

---

### Post by ComplexNumber on 2007-01-15
when you select 'sound' from the system menu, what does it give as your default card (see screenshot)?

---

### Post by kane77 on 2007-01-16
> **ComplexNumber said:**
> when you select 'sound' from the system menu, what does it give as your default card (see screenshot)?
 
it looks like this...  I'm starting to think though that it's a network problem (with ekiga) Irecently found out that it works fine when I connect to second computer's ip...

---

### Post by ComplexNumber on 2007-01-16
> **kane77 said:**
> it looks like this... I'm starting to think though that it's a network problem (with ekiga) Irecently found out that it works fine when I connect to second computer's ip...
i don't think its a network problem when your default sound card is greyed out like that.
i don't think you have the right drivers.
[here]("http://ubuntuforums.org/showthread.php?t=205449") and [here]("http://alsa.opensrc.org/TroubleShooting") may help you out. also i would probably be inclined to disable(in the bios) your inbuilt sound card.

---

