---
title: "Sound issues which can cause crash in DVD Shrink"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-07
Right now, I'm compressing a DVD to be burned using Wine/DVD Shrink. As far as making an iso and burning it goes, it works, but not without an issue which is 

a) Annoying 
And 
b) is problematic to the point that when I tried to watch a youtube video yesterday, DVD shrink crashed while extracting DVD info. 

I'm almost sure that this problem is related to an error which came up while configuring Wine via "winecfg". I can't get into the audio tab at the moment because dvd shrink is working, but upon entry of cfg I get this:
> ALSA lib pcm_dsnoop.c:559:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory


The symptoms I can describe are (but are not limited to): When unchecking certain options such as enabling or disabling 
French/spanish subtitles, or moving the entire dialogue box, audio (apparently from the movie) will pop in and out very suddently. 

The ultimate though, is when the movie is actually being compressed to an iso file. The popping in/out audio is then constant (until the whole thing is done). It's probably only a quarter second's worth of whatever audio is chosen, so it's really fast popping in and out. 

I"ll post the contents of what happens in cfg when I get into the audio tab after this one is done. But any clues as to what is going on, if anyone knows, would be great. Thanks.

Doug

---

### Post by Sweet Spot on 2006-09-07
And now, "winecfg" crashes when I try to open the Audio tab, and this message is presented : > ALSA lib seq_hw.c:456 ( snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/masterbain/.kde/socket-masterbain-desktop.
can't create mcop directory
 
Obviously not right. 

doug

---

### Post by harlan on 2006-09-07
Try with k9copy,very similar to DVDShrink.It's in the ubuntu repositories.

---

### Post by Sweet Spot on 2006-09-07
Actually, I tried K9 and found it to be *nothing* like DVD shrink, since it doesn't create the right sized file to burn. Didn't like it at all. Besides, I really like DVD shrink, and it does the job very well, I just need this issue to be worked out. So if anybody knows what the problem may be, I'd really appreciate the help. 

Interesting thing is, last week, I was able to get into the audio" tab in Winecfg, but now, it just crashes when I attempt to click it (audio) Always with the same message: > ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/masterbain/.kde/socket-masterbain-desktop.
can't create mcop directory


---

### Post by cre8ivgil on 2006-11-04
I had the same problem with Wine crashing while selecting the Audio Tab. Here is what I did: Run winecfg as a regular user, do not use "sudo winecfg" then select the Audio Tab...it should now open, next make such nothing is checked off by unchecking anything that is checked, then hit apply. You should be okay now as it is not necessary to check an audio option to shrink a movie. I shrink to an ISO Image then burn with K3B without any problems, even the audio is fine.

---

### Post by karhulitos on 2006-11-04
I get the same with or without sudo. I've just shrinked a DVD without any problems. Should I be now concerned about the sound on that shrinked ISO file? Or are we just talking about system sounds while compressing?

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** winecfg.exe: free(): invalid pointer: 0x7c2a2618 ***
```

---

