---
title: "No sound for non administrator users"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by mmasroorali on 2008-03-20
I am facing a strange problem that the non administrator users do not have any sound. This  is what I have tried so far,

         1. PCM is not muted in alsamixer.
         2. All these users belong to the audio group.
         3. In System -> Sound -> Preferences all these users can play the Test tunes, and these are heard.
        4. Sound is not muted for these users.
        5. I have even tried creating fresh users.

---

### Post by p_quarles on 2008-03-20
New users don't automatically become part of the appropriate groups for all system functionality. To enable full sound, you would run this:
```
sudo adduser *username* audio
```
Upon that user's next login, it will have access to audio.

---

### Post by mmasroorali on 2008-03-20
I have been a Sun user from 1991 to 1997, and a Fedora user from 1997 to 2008. Recently I switched to Ubuntu for its ease of software maintenance.

What you are suggesting is somewhat difficult for me to comprehend.
 
I have four users in my machine masroor (administrator), rafid, hamin, lipi.

As you can see,

root@rafid-hamin:/home/masroor# cat /etc/group

gives,
.....
audio:x:29:masroor,lipi,pulse,rafid,hamin
.....

Also, 

root@rafid-hamin:/home/masroor# groups rafid

gives, 
rafid : rafid adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse

So there is no need to add this user to the audio group.

Even if I try this command, 
root@rafid-hamin:/home/masroor# adduser rafid audio

I get,
The user `rafid' is already a member of `audio'.



As I try things a number of times, I find a strange revelation. The first user logging after a reboot gets sound in all applications.

Say I boot the machine and then rafid (non administrator) logs in. This user gets all the sounds including the login drum bit.

After rafid logs out, masroor (administrator) logs in. No sound!!!.

The test tunes in System -> Preference -> Sound works for ALL the users.

Now say the machine is rebooted and masroor (administrator) logs in first. Then this users gets the sole agency of sounds.

Strange, but this is what is happening.

I would appreciate any input.

---

