---
title: "videos on text mode"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by zourcast on 2006-03-26
Is it possible to watch videos on **text mode**. If so, how can I do that?

---

### Post by dermotti on 2006-03-26
Whats text mode? You mean from command line without an Xserver up?

---

### Post by zourcast on 2006-03-26
I read somewhere that caca drivers would work, so I wrote this in the command line
 
```
mplayer -vo caca videoname.mov
```
 
The result was interesting, but somawhat useless.
I took this screenshot in graphic mode, but in text mode it is just like this too.
 
[[IMG]http://img46.imageshack.us/img46/8015/screenshot2aq.th.png[/IMG]](http://img46.imageshack.us/my.php?image=screenshot2aq.png)

---

### Post by zourcast on 2006-03-26
[QUOTE=dermotti]Whats text mode? You mean from command line without an Xserver up?[/QUOTE]

Yes.

---

### Post by dermotti on 2006-03-26
I do not belive that is possible (other than the above method). You need to have X up.

I mean you could just install Xorg by  itself and not run KDE or GNOME, and when you **startx** you are presented with just a console. From there you can type mplayer

---

### Post by dermotti on 2006-03-26
[QUOTE=zourcast]I read somewhere that caca drivers would work, so I wrote this in the command line
 
```
mplayer -vo caca videoname.mov
```
 
The result was interesting, but somawhat useless.
I took this screenshot in graphic mode, but in text mode it is just like this too.
 
[[IMG]http://img46.imageshack.us/img46/8015/screenshot2aq.th.png[/IMG]](http://img46.imageshack.us/my.php?image=screenshot2aq.png)[/QUOTE]


Lol is that MR. Smith from the matrix or a porno? lol i can't tell

---

### Post by piedamaro on 2006-03-26
It is possible, you need the svga video output from mplayer.

---

### Post by zourcast on 2006-03-26
[QUOTE=dermotti]Lol is that MR. Smith from the matrix or a porno? lol i can't tell[/QUOTE]

None of them.

That's Kiefer Sutherland in Sentinel (2006).

Thanks for the replies.

---

### Post by zourcast on 2006-03-26
I've tried using svga as output device.

The movie starts without errors, the sound is fine, but the monitor shuts down. After the movie ends, the monitor turns on again.

My graphic board is a ATI Radeon 7000 (VE).

What could be the reason for that hapening.

---

### Post by zourcast on 2006-03-26
I managed to get it playing videos in the console.

I used  cvidix codec, and it plays fine.

There is one problem tough. The movie plays behind the leters. Other than that. It is perfect.

---

### Post by zourcast on 2006-03-26
[QUOTE=zourcast]There is one problem tough. The movie plays behind the leters.[/QUOTE]

Problem solved.

Used the program "screen" to send the video to a new terminal, getting only a litle text in the left upper corner, nothing inportant.

If somebody knows a better way to play videos in text mode, let me know.

---

### Post by zourcast on 2006-03-26
I managed another way to avoyd having the letters covering the movie.

Changed fs to yes, in the file /etc/mplayer/mplayer.config.

Now it is just perfect.

Thanks to those who helped me.

---

