---
title: "MBP 5,5 No Sound with 9.10"
date: 2009-10-04
forum: Apple Hardware Users
---

### Post by Alpha_Cluster on 2009-10-04
So I have tried the fix listed in the [wiki]("https://help.ubuntu.com/community/MacBookPro5-5/Karmic") (whoever made it just copy and pasted from the 9.04 article). This did manage to get the red showing out of my audio jack but nothing more. I got no audio. Also this article is HORRIBLY misleading as NONE of the sound options mentioned in the article after installing the driver. Of course this is I think a horrible pulseaudio issue actually more then a alsa issue but anyone got an idea as to how to get this working? It is rather annoying having everything but sound working.

I am sure this sounds rather rude but I am just bothered by the fact that the article has never been pruned of old information from the looks of it and so in its current form does not help (used to tell you to use sudo make also which is a bad practice and should not be done). I to help figure this out if I can but does anyone here have any advice so I can try something that might fix this issue?

---

### Post by ALLurGroceries on 2009-10-04
> **Alpha_Cluster said:**
> So I have tried the fix listed in the [wiki]("https://help.ubuntu.com/community/MacBookPro5-5/Karmic") (whoever made it just copy and pasted from the 9.04 article). This did manage to get the red showing out of my audio jack but nothing more. I got no audio. Also this article is HORRIBLY misleading as NONE of the sound options mentioned in the article after installing the driver. Of course this is I think a horrible pulseaudio issue actually more then a alsa issue but anyone got an idea as to how to get this working? It is rather annoying having everything but sound working.

I am sure this sounds rather rude but I am just bothered by the fact that the article has never been pruned of old information from the looks of it and so in its current form does not help (used to tell you to use sudo make also which is a bad practice and should not be done). I to help figure this out if I can but does anyone here have any advice so I can try something that might fix this issue?

Have you tried recompiling the latest version of ALSA? Make sure your kernel headers are installed first and I've written directions here:
[http://forum.notebookreview.com/showthread.php?t=418403#sound]("http://forum.notebookreview.com/showthread.php?t=418403#sound")

In your mixer you'll need to unmute Front Speaker, Surround Speaker, and check the Surround Speaker box to enable it.

If sound doesn't work after that you can try forcing the model:
```
sudo echo "options snd-hda-intel model=mbp3" >> /etc/modprobe.d/alsa-base.conf
```

Then force reload ALSA:
```
sudo alsa force-reload
```

Good luck.

---

### Post by Alpha_Cluster on 2009-10-06
I followed your guide and it does not seem to solve the problems. Now I do not even see any hardware listed in the sound preferences.

---

### Post by ALLurGroceries on 2009-10-06
> **Alpha_Cluster said:**
> I followed your guide and it does not seem to solve the problems. Now I do not even see any hardware listed in the sound preferences.

Maybe you encountered errors during compilation or make install. It works perfectly for me.

There's another thread here, maybe try some of their suggestions (although those didn't work for me):
[http://ubuntuforums.org/showthread.php?t=1188849]("http://ubuntuforums.org/showthread.php?t=1188849")

---

### Post by hvthao on 2009-10-06
> **ALLurGroceries said:**
> Maybe you encountered errors during compilation or make install. It works perfectly for me.

There's another thread here, maybe try some of their suggestions (although those didn't work for me):
[http://ubuntuforums.org/showthread.php?t=1188849]("http://ubuntuforums.org/showthread.php?t=1188849")

Did you try on Karmic or Jaunty?

---

### Post by amd-64 on 2009-10-07
If anyone got sound to work in karmic (2.6.31-11 or 12) for a MBP 5-3 or 5-5 please tell me exactly what did you do.

---

### Post by hvthao on 2009-10-08
In Jaunty is no problem, but just got the headphone working in Karmic.

---

### Post by dlenmn on 2009-10-08
My sound didn't work in karmic, but I just tried the instructions on the wiki and it all worked fine (speakers and headphones). I'm using the latest version of everything (did and apt-get update). Not sure what else I can say.

---

### Post by hvthao on 2009-10-08
Ok. It works, but I didn't realize that i have to unmute the front speakers and check the surround speaker in the alsa mixer, which is hidden in karmic. To do that, you just install the gnome alsa mixter (gnome-alsamixer).

---

### Post by Gekkido on 2009-10-09
> **ALLurGroceries said:**
> Maybe you encountered errors during compilation or make install. It works perfectly for me.

There's another thread here, maybe try some of their suggestions (although those didn't work for me):
[http://ubuntuforums.org/showthread.php?t=1188849]("http://ubuntuforums.org/showthread.php?t=1188849")

I followed your instructions and almost blew my speakers on my laptop!

Makes me very happy.

---

### Post by amd-64 on 2009-10-09
I finally got sound to work on Karmic for a MBP5,3 I followed the guide here 

[http://forum.notebookreview.com/showthread.php?t=418403#sound](http://forum.notebookreview.com/showthread.php?t=418403#sound)

Installing gnome-alsamixer was not enough. You need to create /etc/asound.conf if you don't have it. 

```
 
 pcm.out {
        type route
        slave.pcm "hw:0,0";
        slave.channels 6
        ttable {
                0.0 1
                1.1 1
                2.2 1
                3.3 1
                4.4 1
                0.5 0.5
                1.5 0.5
        }
}

pcm.!default {
    type pulse
}

```

I also installed asoundconf-gtk but I am not sure if that was needed.

---

### Post by Cerin on 2009-11-06
I've followed all these instructions on 5.5 with 9.10, but still no sound.

---

