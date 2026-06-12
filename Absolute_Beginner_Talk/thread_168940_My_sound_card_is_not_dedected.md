---
title: "My sound card is not dedected"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Freeman200661 on 2006-05-01
[FONT="Book Antiqua"][FONT="Arial"][COLOR="black"][/COLOR][/FONT][/FONT]Hi every body, I'm a new user of Linux, the sound card is not dedected although it's showed up on the hardware browser, it's (82801DB AC'97 Audio.  If anyone could help that would be highly appreciated.

---

### Post by Sandlst on 2006-05-01
Quick question: how do you know your card was not detected?  Does opening a media player/volume control (Applications/Sound & Video/) give any sort of error msg?  Or is it simply playing files you know are music with no sound coming out?  At first, I thought my soundcard was not detected on Ubuntu, but opening the volume control (double-click volume icon on the top right of your screen in the bar) I was able to open up more volume options under (edit/prefrences)-my volume is controlled by the 'Front' volume control, which was hidden and muted by default.  Also, you could go under (File/Change Device) in volume control to see if more than one mixer is avaliable, and repeat the last sentence.  Hope this helps, post back if you have any problems.

---

### Post by Freeman200661 on 2006-05-01
**Dear Sand**lst,
Thanks for your kind reply, actually I tried to open some media/music, but I got the followiing error message:
Application "gnome-sound-recorder" (process 4412) has crashed
due to a fatal error.
(Aborted)

---

### Post by Sandlst on 2006-05-01
Hmm, does it give you an error message when you try to open volume controls?  Also, could you open a terminal, click (Edit/Profiles) highlight default, hit edit, go to the 'Title and Command' tab, select 'When command exits:' to 'Hold the terminal open' then type ```
gnome-sound-recorder
```And post the error dump here?  This should hopefully give out a more detailed error message.

---

### Post by Freeman200661 on 2006-05-02
T**[B]hank you buddy, after following your instruction, I received the following; **[/B]
(gnome-sound-recorder:3767): GnomeUI-WARNING **: While connecting to session man
ager:
Authentication Rejected, reason : None of the authentication protocols specified
 are supported and host-based authentication failed.
INFO ( 3767: 0) Initializing GStreamer Core Library version 0.6.0
INFO ( 3767: 0) CPU features: (00000000) MMX SSE
registry: loaded user_registry in 0.000192 seconds
          (/root/.gstreamer/registry.xml)
registry: loaded global_registry in 0.106035 seconds
          (/var/cache/gstreamer-0.6/registry.xml)
[root@ldn addel]#

---

