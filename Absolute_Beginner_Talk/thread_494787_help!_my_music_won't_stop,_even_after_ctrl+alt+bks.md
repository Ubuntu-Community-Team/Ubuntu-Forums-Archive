---
title: "help! my music won't stop, even after ctrl+alt+bkspc!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by jamesey on 2007-07-07
I woke up, booted my machine, I downloaded an MP3, saved it to desktop, and played it through Totem. When it was done, I closed totem, but about 5 seconds after closing, the music started playing again. I liked the song, so I thought, "what the heck" and let it play again. Well after the replay, it didn't stop. It started again, and repeated for about 20 minutes until I decided to restart Gnome. Somehow the song kept playing through the text interface of the restart, through the login screen, and up through now as I type. How do I kill the music?

---

### Post by Inxsible on 2007-07-07
I have had the same problem, but not with Totem.

If I use VLC to play my mp3, it doesnt stop even if i kill VLC and I have to restart my X to stop the music.

Of course, i used VLC because I was busy editing tags in Rhythmbox for the songs and so used another player.

i havent used VLC after that to play Mp3s ....so havent seen it after that.

---

### Post by arsenic23 on 2007-07-07
The GUI to kill running prosseses can be found under System/Administration/System Monitor.

You can also type 'killall prosess_name' into the terminal.  killall totem would prolly fix your issue.

---

### Post by greg_g on 2007-07-07
I had a similar issue yesterday.

Try System -> Administration -> System Monitor.  Under the Processes tab, look for a process called ALSA or something similar.  Kill it.  Don't worry, it should come back after you start another song.

And, if that doesn't work, restart the computer to fix it, but that is a dirty fix I know.

EDIT: If you haven't done this yet, use chessercizes  commands instead which actually stop and start ALSA.  But if those don't work, use mine.

---

### Post by Inxsible on 2007-07-07
Again, the question being....why does it happen in the first place ?

---

### Post by seshomaru samma on 2007-07-07
i guess you could go
```
ap aux | grep totem
```
you will get an output like this :
```
sesho      9910  0.0  0.1   2884   748 pts/1    R+   21:41   0:00 totem
```
look for the pid number (in my case :9910)
and go 
```
kill 9910
```
(replace 9910 with whatever your output is)

---

### Post by greg_g on 2007-07-07
> **Inxsible said:**
> Again, the question being....why does it happen in the first place ?

I'm guessing it is a bad exit by totem.  Totem being closed but not killing all of its processes correctly.

---

### Post by Inxsible on 2007-07-07
it says :
```
bash: ap: command not found
```

---

### Post by Inxsible on 2007-07-07
> **greg_g said:**
> I'm guessing it is a bad exit by totem.  Totem being closed but not killing all of its processes correctly.
Right, is there a way we can ensure that all the child processes started by an app, are killed when the app is killed ?

---

### Post by greg_g on 2007-07-07
> **Inxsible said:**
> Right, is there a way we can ensure that all the child processes started by an app, are killed when the app is killed ?

Well, yeah, by closing it correctly.  That is the job of the application and the kernel.  Sometimes it just doesn't work as planned and something is left behind.  Nothing you can do to prevent it other than pray/chant/rub stones each time you close an application.

Sorry that doesn't answer your question, but sometimes mistakes are a part of life.

---

### Post by chessercizes on 2007-07-07
Hey.

Umm, i dont know if this will work or not but you could try re-starting alsa by:

> sudo /etc/init.d/alsa-utils stop

and then

> sudo /etc/init.d/alsa-utils start

good luck with your problem and hope this helps

---

### Post by Inxsible on 2007-07-07
> **greg_g said:**
> Well, yeah, by closing it correctly.  That is the job of the application and the kernel.  Sometimes it just doesn't work as planned and something is left behind.  Nothing you can do to prevent it other than pray/chant/rub stones each time you close an application.

Sorry that doesn't answer your question, but sometimes mistakes are a part of life.

OK. I was just wondering if it can be avoided. But like I said, I hardly use VLC for mp3. so its not like its a critical issue for me.

BTW...I have never seen VLC do that for my video files....probably because I run only 1 at a time...whereas in mp3 i am mostly running a big playlist.

---

### Post by greg_g on 2007-07-07
> **Inxsible said:**
> OK. I was just wondering if it can be avoided. But like I said, I hardly use VLC for mp3. so its not like its a critical issue for me.

BTW...I have never seen VLC do that for my video files....probably because I run only 1 at a time...whereas in mp3 i am mostly running a big playlist.

Yeah, I have actually only experienced it with audio also.  I think it would just be harder for a video to show up if it is playing again, it needs a screen and all that.  But audio just gets fed to the sound card which takes it from there.

My problem yesterday was that my startup sound, the sound that plays when the login screen comes up, kept repeating quickly.  I didn't even notice for about 30 minutes because my speakers were off, but I noticed when I wanted to watch a video.  Since I wasn't sure what to look for I just killed ALSA and restarted X.

Anyways..

Hope the original poster is having good luck,

greg

---

### Post by Inxsible on 2007-07-07
I just tried it again, for the heck of it...and it happens everytime with VLC.

---

### Post by Inxsible on 2007-07-07
> **chessercizes said:**
> Hey.

Umm, i dont know if this will work or not but you could try re-starting alsa by:



and then



good luck with your problem and hope this helps

When I do what you suggested, it does stop the sound. but the moment i start the alsa again, the songs continue. Looks like we have to restart the X to get away with it.

---

### Post by Inxsible on 2007-07-07
I did a ```
top
``` and then found the PID of the vlc process. Seems like, while playing mp3, on killing the GUI of vlc, it doesnt kill a process called wxvlc.

After looking up the PID of it, I simply killed it using

```
kill 20107
``` replace 20107 with whatever the PID is for you.
That seems like a better solution than re starting X ...to me atleast

---

