---
title: "MPlayer Plugin: Fullscreen?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Inkyskin on 2006-01-28
When watching video clips with the MPlayer plugin for Firefox, if I select fullscreen, it just puts the vid clip against a full screen black background, and keeps the clip at its original size. Is there anyway I can get it to show a true fullscreen like in Win Media Player on XP?

---

### Post by imrumpf on 2006-01-28
```
sudo gedit .mplayer/config
```

and add:

```
zoom=yes
```

---

### Post by Inkyskin on 2006-01-28
Perfect, thanks :)

---

### Post by cvmostert on 2006-02-14
[QUOTE=imrumpf]```
sudo gedit .mplayer/config
```

and add:

```
zoom=yes
```[/QUOTE]

have never seen this command... 

.application/config

does it work with other programs or does it mean something spesific? excuse my ignorance...

thanx in advance!
c

ps. thanx for the info, it worked for me aswell... zooming good now!

---

### Post by imrumpf on 2006-02-14
when you first open the terminal you are in your home folder. What you dont see is a huge collection of installed programs and folders. Go into your home folder with nautilus and hit CTRL + H. You should see all the different program folders now. In case you wanted to make a folder named "mplayer", Ubuntu has the program folder as ".mplayer" to hopefully avoid you not being able to use that folder name: who uses a . at the beginning anyways? there is a config file within .mplayer folder which we are editing.

I am pretty sure this is what is going on. please correct me if I am wrong.

---

### Post by public_void on 2006-02-14
> who uses a . at the beginning anyways?
The . in front of the folder or files will hide it. It would look ugly with all those directories visible, so its hidden.

---

### Post by imrumpf on 2006-02-14
Thanks for correcting me...nifty feature!

---

### Post by totfit on 2006-02-14
I just tried the solution offered and saw no change in MPlayer when I played a video. The zoom still didn't work. Any ideas?

---

### Post by totfit on 2006-02-14
Sorry, I have it now. I edited the first line instead of adding the command below.

Thanks

---

### Post by imrumpf on 2006-02-14
try adding -zoom at the commandline
or change zoom=no to zoom=yes in /etc/mplayer/mplayer.conf

---

### Post by FrankTM on 2006-02-14
[QUOTE=imrumpf]when you first open the terminal you are in your home folder. What you dont see is a huge collection of installed programs and folders. Go into your home folder with nautilus and hit CTRL + H. You should see all the different program folders now. In case you wanted to make a folder named "mplayer", Ubuntu has the program folder as ".mplayer" to hopefully avoid you not being able to use that folder name: who uses a . at the beginning anyways? there is a config file within .mplayer folder which we are editing.

I am pretty sure this is what is going on. please correct me if I am wrong.[/QUOTE]
i didnt know the ctrl + h command
this might be handy sometimes

i always used the location bar (via the "go" menu) or command line

thx mate :)

---

