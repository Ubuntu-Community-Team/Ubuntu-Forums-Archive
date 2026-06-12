---
title: "Screen Recording With Beryl?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-11
Is there any programs out there that can record your screen, such as 

RecordMyScreen?


That work with Beryl?  I'd love to get something to work with it.

---

### Post by bone43 on 2007-06-11
> **LollYouSuckZor said:**
> Is there any programs out there that can record your screen, such as 

RecordMyScreen?


That work with Beryl?  I'd love to get something to work with it.


Do you want a screen shot or are you talking about video?

A screen shot is Applications> Accessories> Take Screenshot.

---

### Post by LollYouSuckZor on 2007-06-11
Im talking about Video, Screenshots are obvious.  Im looking for Video recording.

---

### Post by bone43 on 2007-06-11
> **LollYouSuckZor said:**
> Im talking about Video, Screenshots are obvious.  Im looking for Video recording.

Theres a Plugin for beryl called Vidcap some what hard to get working from what i under stand but have not tried it.

[http://ubuntuforums.org/showthread.php?t=461567](http://ubuntuforums.org/showthread.php?t=461567)

Good luck let us know if you get it working! :)

---

### Post by LollYouSuckZor on 2007-06-11
Aww.  Well this is about my ninth fresh install... Might as well not make it the tenth =[

---

### Post by loell on 2007-06-11
```
sudo apt-get install recordmydesktop
``` :popcorn:

---

### Post by dustigroove on 2007-06-11
[FONT=Arial][SIZE=2][COLOR=Black]Try [gtk-recordmydesktop]("http://packages.ubuntu.com/feisty/graphics/gtk-recordmydesktop"), I am using Beryl and it seems to record just fine.

**EDIT**: Appears that I type to slow... #-o

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by LollYouSuckZor on 2007-06-11
> **loell said:**
> ```
sudo apt-get install recordmydesktop
``` :popcorn:

I've done that, and yet there is no little icon, I was using KDE before, and it ran fine.  But now it wont? After ive installed Fiesty + beryl?



[PS: sudo apt-get install gtk-recordmydesktop gave me this code]
```

nic@Nic-Pwnz:~$ sudo apt-get install gtk-recordmydesktop
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nic@Nic-Pwnz:~$ 

```

---

### Post by Inxsible on 2007-06-11
> **LollYouSuckZor said:**
> I've done that, and yet there is no little icon, I was using KDE before, and it ran fine.  But now it wont? After ive installed Fiesty + beryl?



[PS: sudo apt-get install gtk-recordmydesktop gave me this code]
```

nic@Nic-Pwnz:~$ sudo apt-get install gtk-recordmydesktop
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nic@Nic-Pwnz:~$ 

```

Do you have Synaptic or Add/Remove open ?

Close them and then try again !

---

### Post by loell on 2007-06-11
either adept or synaptic is running, when you invoked the command. you can exit them. before invoking the command.

---

### Post by LollYouSuckZor on 2007-06-11
> **Inxsible said:**
> Do you have Synaptic or Add/Remove open ?

Close them and then try again !

```

nic@Nic-Pwnz:~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1024    Height:768
Adjusted recording window is set to:
X:0   Y:0    Width:1024    Height:768
Your window manager appears to be beryl


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Opened PCM device hw:0,0
Recording on device hw:0,0 is set to:
2 channels at 22050Hz
Buffer size set to 4096 frames.
Capturing!

```

Apparently it works, and I get a bit of lag.. so it is recording, but it never saves, I have nothing on my toolbar to stop the recording, i just have to close the terminal to stop it.

Any suggestions?

[Two inches to giving up.]

---

### Post by Chris S. on 2007-06-11
A little red circle will appear in the notification area on your panel (maybe you need to add a notification area to a panel, I don't know).  While it is recording the red circle becomes a white square.  Click on it to stop recording.

You don't see either of those things on your panel?

---

### Post by loell on 2007-06-11
if you ran , gtk-recordmydesktop, you'll have the stop icon on your tray, click on it and the recording will stop,

otherwise just press ctl + c in the command line version, to stop.

the file will be saved on ```
/home/you_username
```/ , the file name is ```
out.ogg
```

---

### Post by LollYouSuckZor on 2007-06-11
> **loell said:**
> if you ran , gtk-recordmydesktop, you'll have the stop icon on your tray, click on it and the recording will stop,

the file will be saved on ```
/home/you_username
```/ , the file name is ```
out.ogg
```
```

nic@Nic-Pwnz:~$ gtk-recordmydesktop
bash: gtk-recordmydesktop: command not found
nic@Nic-Pwnz:~$ 

```

---

### Post by LollYouSuckZor on 2007-06-11
> **loell said:**
> if you ran , gtk-recordmydesktop, you'll have the stop icon on your tray, click on it and the recording will stop,

otherwise just press ctl + c in the command line version, to stop.

the file will be saved on ```
/home/you_username
```/ , the file name is ```
out.ogg
```


Hahah, Thanks, Thanks to Synaptic also ;)

I got it working.
 Much appreciated!

---

### Post by Chris S. on 2007-06-11
try "gtk-recordMyDesktop", case sensitive.  That's capital M and D.

---

### Post by loell on 2007-06-11
seems like you've only installed recordmydesktop

install the the gtk front-end by..
```
sudo apt-get gtk-recordmydesktop
```


edit..  ah, ok, you already got it working :)

---

