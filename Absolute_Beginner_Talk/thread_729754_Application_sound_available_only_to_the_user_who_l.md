---
title: "Application sound available only to the user who logs in first after a boot."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by mmasroorali on 2008-03-20
It is strange but this happens in my computer, the first user logging
in after a reboot gets sound in all applications.

Say I boot the machine and then userone (non administrator) logs in. This user gets all the application sounds.

After userone logs out, computerowner (administrator) logs in. No sound!!!.

The test tunes in System -> Preference -> Sound works for ALL the users.

Now say the machine is rebooted and computerowner (administrator) logs in first. Then this user gets the sole agency of sounds.

Strange, but this is what is happening.

I have four users in my machine computerowner (administrator), userone,
 usertwo, userthree (names changed for better readability).

All of them belong to the audio group.

As you can see,

# cat /etc/group

gives,
.....
audio:x:29:computerowner,userthree,pulse,userone,usertwo
.....

Also, 

# groups userone

gives, 
userone : userone adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse

I do not find a clue how to solve this problem.

I would appreciate any input.

---

### Post by leroyc on 2008-03-20
Strange problem indeed.

I advise you to check the problem step by step. 

First, check the ownership of the devices:

```
ls -la /dev/snd
```

This way you will see which user and which group are set for the devices. I had some rough moments configuring my sound.

It is always advised to rebuild your ALSA driver, just in case it does not support the system.

As for the sound, there is no reason to be unavailable for the root user.

---

### Post by mmasroorali on 2008-03-20
Thanks for your post, here is the output.

# ls -l /dev/snd
total 0
crw-rw---- 1 root audio 116, 10 2008-03-20 17:22 controlC0
crw-rw---- 1 root audio 116,  9 2008-03-20 17:22 pcmC0D0c
crw-rw---- 1 root audio 116,  8 2008-03-20 17:22 pcmC0D0p
crw-rw---- 1 root audio 116,  7 2008-03-20 17:22 pcmC0D1c
crw-rw---- 1 root audio 116,  6 2008-03-20 17:22 pcmC0D2c
crw-rw---- 1 root audio 116,  5 2008-03-20 17:22 pcmC0D3c
crw-rw---- 1 root audio 116,  4 2008-03-20 17:22 pcmC0D4p
crw-rw---- 1 root audio 116,  3 2008-03-20 17:22 seq
crw-rw---- 1 root audio 116,  2 2008-03-20 17:22 timer


Just to reiterate, the test tunes in System->Preference->Sound work for ALL.

---

