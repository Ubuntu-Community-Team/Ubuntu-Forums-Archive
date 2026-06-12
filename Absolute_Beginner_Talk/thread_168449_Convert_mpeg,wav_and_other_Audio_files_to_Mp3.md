---
title: "Convert mpeg,wav and other Audio files to Mp3?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-30
I have an Mp3 player, that only plays Mp3 files. Right now I have some mpeg files I would like to transfer to it. 

How do I convert them to mp3? Is there a program that can convert most audio files to mp3 for me? Maybe available in the apt-get ?

Thanks

---

### Post by croak77 on 2006-04-30
Try soundconverter if you want gtk/gnome or soundkonverter if you use kde.

---

### Post by savas on 2006-04-30
I think mpeg is a vidio format. Do you mean wav or audio cd? If you want to convert wav files to mp3 you can use lame.

---

### Post by Roel Groeneveld on 2006-04-30
There's a package called Sound Converter available from the repositories (the Universe repo to be precise). Look for 'soundconverter' in Synaptic. 

It is recommended that you also install the gstreamer0.8-plugins with it because that enables it to convert to a variety of audio formats. You have to set the format to which Sound Converter needs to convert under Sound Converter's Preferences.

(If you like nautilus plugins, try this: [http://ubuntuforums.org/showthread.php?t=82806](http://ubuntuforums.org/showthread.php?t=82806) )

---

### Post by aktiwers on 2006-04-30
Thanks! This worked.

```
sudo apt-get install soundconverter
``` 
Thanks a lot! :)

---

### Post by dolarsrg on 2006-05-17
Hi!

I'm using Kubuntu Dapper and it's impossible for me to find the soundkonverter package in the repositories. I've enabled all of them and I used to have that program installed in Brezzy.

Does anybody knows where is at the moment?

I'm trying to convert MP3 files to ogg format.

Thanks!

---

### Post by linear on 2006-05-17
packages.ubuntu.com says: it's in Multiverse.

---

