---
title: "No line-in recording"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Naegling23 on 2006-09-14
I do not have any line-in recording, How can I "enable" this?  There is no option for line-in in my mixer (kmix).

---

### Post by Skia_42 on 2006-09-14
Do you have a physical line-in jack on your computer? Or do you just need to figure out how to specify it as the audio source for recording?

---

### Post by Naegling23 on 2006-09-14
the jack is there, I just need to specify it for recording

---

### Post by Naegling23 on 2006-09-14
so doing some research online shows me that this might be a problem with (k)ubuntu.  Is this true?  Is it mythtv or kubuntu?

---

### Post by Naegling23 on 2006-09-14
nevermind, solved my problem.  line in works like a charm under windows.

Im very quickly getting sick of this linux thing.

---

### Post by srt4play on 2006-09-14
Use what you want, no need to get sick about it.

---

### Post by Drakkor on 2006-09-14
I use Ubuntu with the alsa mixer, no problems with line-in

---

### Post by Naegling23 on 2006-09-15
sorry everyone, I was just very frustrated last night.  I have been working on getting sound working correctly in both mplayer, and mythtv for about a month now.  After another night of not making any progress, I was just venting.

Its still not working, I'm just going to have to learn to live with it.

---

### Post by xyz on 2006-09-15
> **Drakkor said:**
> I use Ubuntu with the alsa mixer, no problems with line-in
I second Drakkor!
Are you familiar with Application> Sound Video > Volume Controle?
Once open,fiddle with Edit > Preferences to add options!
Also run:
```
alsamixer
```
in a console and use left/right arrows to check/select appropriate levels and proper functioning.

---

### Post by Drakkor on 2006-09-15
Hey,Naegling23
With Kmix,have you tried the second tab called "Input" ? From what I see and have just proved it works flawlessly even in Unbuntu(gnome) and there's no less than 3  line inputs ! Don't know what the "LiveDrives" are about,but the regular "Line"
input works with my tvcard,it goes from the tv card into "line in" on the sound card. Just make sure the green light is on at the top so as it's not muted. Check out the screenshot !

---

### Post by xyz on 2006-09-15
Hi Drakkor,
Have you heard of **tkmixer**? Any good or useful here? Thnx.

---

### Post by Drakkor on 2006-09-15
Dunno,xyz,never tried it.
Actually I *was* using the Alsa mixer, but after downloading and trying Kmix,this morning, I actually like it better than Alsa !  :p

---

### Post by Naegling23 on 2006-09-15
Ive been using kmix, and therin lies the problem.  Under the input tab, there just isnt any line in.  There is one for output, but nothing to be able to record from it.

---

### Post by Drakkor on 2006-09-15
Maybe your sound card doesn't support line in recording ??
Wait a minute if it has a line in jack it should ! 
Is there anyway to set preferences to show line in  on the mixer ?

---

