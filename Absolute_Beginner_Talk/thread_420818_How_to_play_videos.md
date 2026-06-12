---
title: "How to play videos?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Drewski on 2007-04-24
Ok, so I've got my network setup, and I've transferred some videos over to my Ubuntu machine.
I've got an AVI and an OGM, but neither will play properly in Totem. With the AVI I get an error telling me I don't have the codec, and for the OGM it seems to play but I get no video, except for a strange light show.

What could be the problem?

---

### Post by aidanr on 2007-04-24
have you followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=413624")?

---

### Post by Drewski on 2007-04-24
I suppose I should have been more specific; I'm running Dapper Drake not Feisty Fawn.
I did try those same steps, but in the app list I only see "GStreamer extra plugins" and "GStreamer ffmpeg video plugin", I see no extra plugins for AAC, XviD, etc.
And yes, I have Show unsupported applications checked.

---

### Post by gilforsyth on 2007-04-24
Also, just personal preference here, you can try using VLC.  

You can either use Synaptic Package Manager or open a terminal and type
```
sudo aptitude install vlc
```
and enter your password when prompted.

---

### Post by aidanr on 2007-04-24
have you enabled multiverse and universe in software sources (or syanptic)

and also added the medibuntu repo

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

edit:// actually just follow ubuntu27's link

---

### Post by ubuntu27 on 2007-04-24
> **Drewski said:**
> I suppose I should have been more specific; I'm running Dapper Drake not Feisty Fawn.


Here is a guide for installing Codecs for Dapper, Edgy and feisty:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


Note: Dapper Drake is Ubuntu 6.06


After you install those codecs, I recommend you to use "xine-ui" for video player.

```
sudo apt-get install xine-ui

```

This is almost off-topic but. After You're are done with everything, take a look at [How to install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

I just want you to know that even though people provide you answer with Terminal command, it is *not* the only way to install programs. It is just that it is *easier* for us to provide commands than writing LONG paragraph explaining the details like  click here, and there, click that, do that, en then this and that. A single command will do it all. Much faster no hassle. :)

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Drewski on 2007-04-24
Hey thanks for all your help guys, it worked! \\:D/

> **ubuntu27 said:**
> I just want you to know that even though people provide you answer with Terminal command, it is *not* the only way to install programs. It is just that it is *easier* for us to provide commands than writing LONG paragraph explaining the details like  click here, and there, click that, do that, en then this and that. A single command will do it all. Much faster no hassle. :)

Yes I understand that, and in some ways I prefer the command-line method, because I think that will help me gain an understanding of the under-the-hood operations of Linux instead of solely relying on the GUI to do everything for me.

On a slightly different note, if I'm in a terminal, and I'm in a directory that has the media file I want to play, how can I "run" that file from that directory? I'm used to Windows, where I just type the filename and the appropriate associated application will open it. Is this possible on *nix systems?

---

### Post by aidanr on 2007-04-24
usually just put the name of the program you want to play it in before the filename, for example

mplayer file.avi
totem file.avi

---

### Post by jfinkels on 2007-04-24
For more help on usage of commands, type in the name of the command followed by --help, or type in "man" followed by the name of the command:
```

mplayer --help
man mplayer

```

---

