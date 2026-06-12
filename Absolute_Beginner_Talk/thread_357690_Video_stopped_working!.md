---
title: "Video stopped working!"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Magimog on 2007-02-09
I made quite the noob mistake and I selected about 100 video files to play in gxine.  I expected them to go directly into a playlist, but instead it loaded 100 windows! 

Now in doing that my system ground to a complete halt, and I had to do a hard shutdown. Now upon restarting I have no video output! None of the packaged programs will work, but I do retain the audio.

Can anyone help me out with this? I don't want to reinstall because it was a complete HEADACHE to install it in the first place! Thanks guys :(

---

### Post by shareMenaPeace on 2007-02-09
Can you post which player this is and what error message occures when you try to play a video?

---

### Post by RomeReactor on 2007-02-09
Hi. When you say that you have no video output, does that mean that the X server doesn't start and you're dumped to the command line?

---

### Post by Magimog on 2007-02-10
share: gxine, kaffeine. To my knowledge there are no error messages (or at least I dont know how to view error logs or whatnot), I just get audio now.

rome: sorry I wasnt more clear. Its only when playing video. Its just a blank window.

---

### Post by shareMenaPeace on 2007-02-10
Try install another player

```
sudo aptitude install vlc
```

---

### Post by RomeReactor on 2007-02-10
Although i've been told this doesn't work on Kubuntu, maybe you can try to run the programs from the terminal to see if they dump any output related to the problem. Try with

```
locate gxine
```

to see if the program is in /bin, /usr/bin, or /sbin. Then

```
gxine
```

or

```
 /bin/gxine
```

or

```
/usr/bin/gxine
```

When it opens, try to play a file and post the terminal output (if any) here.

---

### Post by Magimog on 2007-02-10
Share: I will try vlc when i can locate it (the was no program that came up when I looked up vlc(

rome: here is the output:

(gxine:5044): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?

---

### Post by RomeReactor on 2007-02-10
Weird. Maybe Lirc got b0rked? Open Adept and search for **liblircclient0** and see if it's correctly installed.

---

### Post by Magimog on 2007-02-10
Adept says its installed correctly. I have no clue what I did :(

It says something about it not running, is it a startup service?

---

### Post by RomeReactor on 2007-02-10
Synaptic has this to say about Lirc:

> This package provides the daemons and some utilities to support infra-red
remote controls under Linux.

The **lircd** is a daemon that implements the comunication between infrared remotes and the applications, so i assume you have a remote control; i don't have a remote, so lirc daemon is not running on my system. If you don't have a remote, you could try uninstalling it and rebooting. My only other suggestion at this point would be reinstalling Gxine and Kaffeine, but you should wait for someone more knowledgeable to reply to this problem. Sorry.

---

### Post by nickoli_02 on 2007-02-10
you could try using aptitude to repair damaged packages from the hard shutdown. Try this

```
sudo aptitude repair gxine
```

Might work, you may also need to repair other packages, though I don't know what would need repairing. Sorry I can't help further

---

