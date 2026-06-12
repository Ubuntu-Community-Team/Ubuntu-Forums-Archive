---
title: "usb sound"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by peterpaul on 2007-04-26
usb sound works great:(sometimes).dapper drake

when it works:system>preferences>sound shows default sound card as "USB sound".
all apps. work fine. movie player,xmms,banshee amarok etc
EXCEPT for real player which works ok when playing install cd demonstration files.other mp3 files give error message "Cannot open the audio device. Another application may be using it.".

when it doesnt work:
zilch not even system sounds.system>preferences>sound shows default sound card as VIA 8237.unable to lock sound card to "USB sound".
alsamixer in terminal shows only one channel "PCM". mute/unmute and vol.work ok.

why does sound card switch seemingly randomly??

not only new-bie but confused-bie

may be simple for experienced users.tks

---

### Post by simonn on 2007-04-26
[http://ubuntuforums.org/showthread.php?t=410263](http://ubuntuforums.org/showthread.php?t=410263)

---

### Post by peterpaul on 2007-04-26
tks simon but "$ lsmod | grep snd" gives bash: $:command not found". using dapper drake.
what am i doing wrong?

---

### Post by simonn on 2007-04-26
The $ sign is the prompt. You actually type: lsmod | grep snd

It is common practice to use $ to mean when logged in as a user and # when logged in as root. This is not really neccesary with Ubuntu as you do not log in as root.

---

### Post by peterpaul on 2007-04-27
tks simonn.tried suggestion re.creating a new file with option 0 then1 etc.
have rebooted multiple time and usb sound card seems to be selected correctly.
tks fr the tip but realplayer still does not work.(gnome).(ERROR. SOME OTHER APPLICATION MAY BE USING IT.)could this be a separate issue?

i have kde desktop also and surprise,surprise realplayer works fine with kde but some other  players do not.

   gnome.
                                                         
1. real player   NO  SOUND            (visual OK)  
2. amarok       OK
3. kaffeine       OK
4. xmms         OK
5. banshee      OK
6. rythm box     OK
7. movie player OK

   kde

1.realplayer      OK                           (visual OK)
2.amarok          OK
3.kaffeine         OK
4.rythmbx         OK
5.banshee        NO SOUND
6. movie player NO SOUND       
7.xmms            NO SOUND
can you help?

---

### Post by peterpaul on 2007-04-30
anyone??

---

