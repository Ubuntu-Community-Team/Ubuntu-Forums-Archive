---
title: "Installed RealPlayer, worked great.. Rebooted, no audio."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-23
Hi everyone,

I must be missing something. I completely uninstalled all of the sound and video tools except for Gxine, Sound Juicer, and Sound Recorder so that I could eliminate as many variables as I could. I then installed RealPlayer using Synaptic, and after that I installed XMMS Music Player. No problems. I opened a web page that I knew had a couple of different types of media (embedded sound, streaming audio) and RealPlayer worked flawlessly. I was very happy.:D  Then, I thought I has better reboot just to make sure that everything had settled in (so to speak), and when everything was said and done, no audio. I was very sad.:-( 

What the heck am I missing? I have instaled all of the commonly needed plugins and codecs. I have read and followed the Restricted Formats guide.
I have gone here:   [http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+video](http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+video)

and here:   [http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefoz](http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefoz)

I am starting to feel a bit like Sisyphus.

I would really appreciate a pointer in the right direction.

TIA,

Kent

---

### Post by Carbonfish on 2006-08-23
C'mon Boys and Girls, you're smarter than me and you are many! Someone must have some idea what might be going on. 

Single soundcard, recognized by OS, system sound and dvd's etc. work, all of the patches that have been recommended to me have been installed, newest version of alsa-oss installed. :confused: :confused: 

Something is reverting to a default state that doesn't recognize these changes after boot, but I am not smart enough to figure this out by myself. On top of that I have only been using *any* distro of Linux for a total of about 2 weeks, so I am not very high up the learning curve.

Please at least reply and tell me to F$*@ off or something so that I know you're not just rolling your eyes and saying "Oh, it's that guy with the sound problem again."

Thanks,

KC

---

### Post by George_S on 2006-08-23
I am experiencing the exact same thing. However, I did not uninstall anything so far. Here is a solution I found on the Helix community forum:

[https://helixcommunity.org/forum/forum.php?thread_id=2795&forum_id=7](https://helixcommunity.org/forum/forum.php?thread_id=2795&forum_id=7)

My problem is this part, "alsa-oss package on Ubuntu." Where is this "alsa-oss" package? Is it on my computer already or do I need to fetch it from somewhere else?


George

---

### Post by Carbonfish on 2006-08-24
Hi George,

I have not looked at your link yet, but I thought that I would get you on the way with your alsa-oss problem. 

Open a terminal window and type 

sudo apt-get install alsa-oss

After that it should take care of itself.

Thanks for the reply, and I'll look at your "fix".

Kent

---

### Post by George_S on 2006-08-24
Hi Kent,

Thanks for your help. I installed alsa-aoss and the RealPlayer now works from the command line (i.e. sound is working).

However, I am still having issues with modifying the usr/bin/realplay file. I get a warning saying that I don't have proper privileges to change the file.

Is there a way around this warning?

Thanks,

George

---

### Post by Carbonfish on 2006-08-24
Hi George,

Well, I pretty new at this myself, but you should be able to open a terminal again, and type:

sudo gedit /usr/bin/realplay

That will open up a text editor and you can change the offensive line.

Just be careful and make sure that you double check the changes you make before you save them. Then save them and close that window. Exit out of the terminal window. I don't know if you need to restart or not to make these changes effective, but it doesn't hurt anything (unless you have some reason that you don't want to shut down). 

That should do it.

Kent

---

### Post by George_S on 2006-08-24
Hey Kent,

It worked like a charm. Realplayer is humming along as it is supposed to.

Thank you for your help.

George

---

### Post by Carbonfish on 2006-08-24
Your welcome. 

What line did you change in /usr/bin/realplay  ?

I may have to do it tomorrow as I am not where I can test the results tonight.

EDIT: Never mind, I think I see it in the link you posted above.

Thanks, 

Kent

---

### Post by George_S on 2006-08-24
Here is the complete solution, just in case:

This is usually caused by an issue with ALSA and ESD. Try installing the alsa-oss package on Ubuntu and then run "aoss realplay" from the command line instead of "realplay".

If that works, you can update the realplay startup script (usually /usr/bin/realplay) and change the line that says

REALPLAYBIN=$HELIX_LIBS/realplay.bin
to
REALPLAYBIN="/usr/bin/aoss $HELIX_LIBS/realplay.bin"

---

### Post by Carbonfish on 2006-08-24
Okay everybody, George's fix doesn't work for embedded audio streams. RealPlayer opens in a separate player window (the same way that it would if I opened it in the terminal).

So I am back to square one.  ](*,) 

Suggestions anyone?  :biggrin:    Pleeeeze?

Kent

---

### Post by Carbonfish on 2006-08-24
Bump.

---

### Post by Carbonfish on 2006-08-24
I guess that I'll just give up on trying to get RealPlayer to stream audio.

No body seems to know how to address this issue, or if they do they are keeping there mouths shut.

All I want to do is stream from [http://www.allclassical.org](http://www.allclassical.org)  while I'm at work. I didn't really think that was asking too much of an OS. I guess it is.

](*,) ](*,) ](*,) 

I am usually not so negative about things like this, but I have been trying to solve this "little" problem for over a week now, and I feel like I'm on the outside looking in at something others are not having issues with, but I can't figure out.

It's depressing.

Kent

---

### Post by Carbonfish on 2006-08-25
Bump.

Just a quick note. Most all of the other audio that I need works. You Tube, WMV, video streams with audio through gxine, DVD's play through gxine, etc. But I would still really like to stream Real media.

I found one thing that was interesting. When I entered about:plugins in my Firefox address bar, it shows all the installed plugins and the Real media files are associated with gxine, but gxine doesn't open them. 

Any suggestions on how I could fix the association with this MIME type?

Kent

---

### Post by Carbonfish on 2006-08-26
So I guess all this silence means that the only way to fix this is to try another distro or hope that the developers read the forums and wait to see if it works in Edgy??   ](*,) 

I *never* say this, but after dinking with this for over a week, I give up!  

Truly sad.:-? 

Kent

---

### Post by George_S on 2006-09-01
> **Carbonfish said:**
> Okay everybody, George's fix doesn't work for embedded audio streams. RealPlayer opens in a separate player window (the same way that it would if I opened it in the terminal).

So I am back to square one.  ](*,) 

Suggestions anyone?  :biggrin:    Pleeeeze?

Kent

Kent, sorry to hear about your troubles. I am not sure about embedded audio streams. I just tried to find some sites that may have that feature, but could not find any. It's mainly Windows Media. Do you have a specific link?

Also, have you tried to post your questions on the Helix forum directly?

[https://helixcommunity.org/forum/forum.php?forum_id=7](https://helixcommunity.org/forum/forum.php?forum_id=7)

---

### Post by Carbonfish on 2006-09-01
Hi George,

Yeah, try going to    [http://www.allclassical.org](http://www.allclassical.org)   and it has embedded music that plays when the home page opens, which I am pretty sure is java driven (funny how I haven't ever looked at the source code to find out!!  :confused:  ), but at the top of the page you will see a link that says "Listen Online". The crazy thing is that sometimes that embedded music (java type) plays, sometimes not. But the RealPlayer opens when I click on it, it connects and buffers, and then says that it's connected at 45 kB/s and the timer starts... but no output. It worked right after I installed RealPlayer, but after I re-booted it quit and hasn't worked since. Obviously I can re-install RealPlayer everytime I re-boot, and I have tried everything else that has been recommended. Yesterday I even tried to kill the esd (which didn't work), but that's not really a fix anyway because the esd re-loads on restart. Since this is a laptop, I re-boot about 25 times a day so I really need these "fixes" to persist after re-boot.

No, I haven't been to the Helix forumm. Thanks for the link. I'll zoom over there after I check out what's happening here.

Thanks for replying and if you think of anything, or know anybody with any ideas, send them my way. I really don't want to do without until Edgy comes out (if it gets fixed then)..

Thanks again,

Kent

---

