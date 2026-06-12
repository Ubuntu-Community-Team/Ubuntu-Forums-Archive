---
title: "Codecs?"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-04-15
I can't seem to play mp3, wma,wmv & mpeg files.  Amarok, Avidemux & Totem say they can't play files.

Where can I get the codecs from?:???:

---

### Post by Qrk on 2006-04-15
Here is a guide

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

You can also look at automatix on this forum.

---

### Post by scion_cho on 2006-04-16
I've tried installing the packages based from what I've read.

I've entered this command in the root terminal:
[COLOR="Navy"]sudo apt-get install totem-xine[/COLOR]
and these are the messages that surfaced:
[COLOR="Red"]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/COLOR]

What is the problem?  I can't play *.dat files (video files from VCD). Help!

---

### Post by Qrk on 2006-04-16
You can't apt-get from the terminal at the same time you have synaptic or update manager running. 

Considering how long it takes synaptic to start up, I wish you could. VCD should work once you get the codecs following the guide on the wiki page.

---

### Post by seoatway on 2006-04-16
Automatix is by far the best way to go for Codecs (and loads of other stuff as well) Do a search on the forum for the BIG thread regarding Automatix and you'll be sorted. I'm not connected to the project but am a big fan.

Cheers

---

### Post by scion_cho on 2006-04-16
Too bad I am currently using Warty the Warthog; Automatix is unavailable.  I'll try to work around with the codecs.  

I had downloaded VLC player, yet the vcd did not work properly still.  Could it be because my hardware could not support it?  Am using a SIS530 video chipset...

---

### Post by Qrk on 2006-04-16
hmm, try adding these sources to your sources.list

```
sudo gedit /etc/sources.list
```
 
Paste the following at the end:


```
deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
```

Then do a 

```
sudo apt-get update
sudo apt-get install win32codecs gstreamer0.8-plugins 
```

---

