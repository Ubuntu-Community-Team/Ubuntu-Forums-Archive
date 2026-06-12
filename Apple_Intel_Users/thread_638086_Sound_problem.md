---
title: "Sound problem"
date: 2007-12-11
forum: Apple Intel Users
---

### Post by dr-jerry-katzman-md on 2007-12-11
Hello my name is Jerry Katzman MD and I have a problem: the sound on my macbook is next to nothing. I have the volume all the way up and have it all the way up under System->Prefs->Sound but I can still barely hear anything. I have no problems under OSX or XP but in linux the sound is very faint. What should I check?

Thank you for your help.

---

### Post by blazercist on 2007-12-11
type alsamixer in console and turn everything all the way up on the playback section. goodluck

---

### Post by cyberdork33 on 2007-12-11
also... what hardware are you on?

---

### Post by sstusick on 2007-12-11
I have this same issue as well. The sound is about 30% what it should be when everything is turned up in alsa mixer. 

Sound Card: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Toshiba Satellite A105-S4004 Laptop

---

### Post by Rog-Mahal on 2007-12-12
Do you have all of the channels enabled (unmuted)? I recompiled my kernel and found that I needed to front, surround and center in order to get full volume.

---

### Post by wigglydiggly on 2007-12-12
I had the same problem with 2nd gen Macbook.  This is what I did

Right click on the speaker Icon and Open Volume Control>Edit>Preferences-- check all box to make visible.  Then under volume control set Master to about 80%, PCM will control volume and the rest all the way to 100% Under switches check Line in as Output Then Options Input source to mic.  You can now close Volume control.  Finally right click again on the specker icon> Preferences and select PCM as device to control. volume

With this setup I have control over volume and the mic works with skype.

Hope this works with you hardware I know sound has been a problem on the Intel macbook for me.

---

### Post by sstusick on 2007-12-14
> **sstusick said:**
> I have this same issue as well. The sound is about 30% what it should be when everything is turned up in alsa mixer. 

Sound Card: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Toshiba Satellite A105-S4004 Laptop
I still have this issue. I used the CLI Alsamixer controls and everything was un-muted. 

I had this same issue with Feisty, but forget what I did to fix it :(

---

