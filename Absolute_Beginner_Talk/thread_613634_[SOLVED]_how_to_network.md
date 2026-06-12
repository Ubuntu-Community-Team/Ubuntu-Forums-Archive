---
title: "[SOLVED] how to network?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-15
hey,

this is a very n00b question :D
how can i listen to music on my vista box from my linux box?  EDIT: ACTUALLY THE OTHER WAY AROUND

I have samba.

sv

---

### Post by hyper_ch on 2007-11-15
Use GnuMP3d

---

### Post by staticvoid on 2007-11-15
thank you hyper_ch I'll check it out. hopefully I can mark this thread as solved when I write my findings :D

sv

---

### Post by bharadwaj on 2007-11-15
staticvoid need to be a bit more specific. Is that you want to share the music files from linux to that of windows or is that you want listen to Mp3s in  linux machine working in vista? since you have already installed samba you would be sharing files by now later install the Realteck driver upgrades in vista. Or is is that you want to listen to music in linux then in gusty add remove programms install Gstreamer extra plugins that will definelty fix the problem.

---

### Post by staticvoid on 2007-11-15
> **staticvoid said:**
> 
how can i listen to music on my vista box from my linux box?


What I meant to say was, if I have music on my bro's HP with vista and I want to play those files on my VAIO with Ubuntu, How can I do that?

I tried GNUMP3d and it looks very cool.
the line in the config file I am suppose to edit that says

root = home/mp3

What do I change that to? How do I get to the vista? or is that the folder on my machine I want to share? I gave it /home/Music, and it said that that did not exist... Anyway, I'll figure it out...

and yea, I have Samba and I can see a bunch of networks, I'm just a little cunfuddled at all the passwords and stuff. It aint simple ;)

sv

---

### Post by maybeway36 on 2007-11-15
I've had success mounting CIFS shares for the shared music and adding it to my Amarok/Rhythmbox library.

---

### Post by staticvoid on 2007-11-15
maybeway36, what is CIFS? and I can use rythmbox to do this?? cool! tell me more :)

sv

*googles....*

EDIT:  Common Internet File System... oh ok. so how can I implement this into rythmbox?

---

### Post by hyper_ch on 2007-11-15
gnump3d is webbased...

this means on the linux box where you have your music you install gnump3d... then you set in the config the path where you have the music files and you also specifiy a port.

then on the other box, you enter the IP address and port of the linux box in the browser, you can then create your playlist and stream it.

---

### Post by staticvoid on 2007-11-16
ok now how do I get to my music on ere from the HP?

  GNUMP3d now serving upon:
    [http://localhost:8888/](http://localhost:8888/)

I typed in that addy and got a "unable to connect" message. humdinger. :)

I might need to change the topic of this thread to something more specific :D

---

### Post by hyper_ch on 2007-11-16
well, you have to enter the right ip of the box with where you have gnump3d installed...

[http://192.168.x.x:8888](http://192.168.x.x:8888)

where the "x" represent the actual server ip.

---

### Post by staticvoid on 2007-11-16
WooHoo!!!   :D Thats Awesome :) this is fun stuff.

thanks. it worked great.

sv

EDIT: so now how do I set a password? I did what the howtoforge tutorial said but it did not work. is there a different way since it is a newer version?

---

### Post by hyper_ch on 2007-11-16
after altering the config file, you'll have to restart gnump3d - otherwise it will not use the new config.

---

### Post by hyper_ch on 2007-11-16
btw, use synaptic, apt-get, aptitude to install gnump3d. It's in the repos.

---

### Post by staticvoid on 2007-11-16
mm, okay. Hey thanx a ton. Hopefully when I retart it it asks for a password and stuff. Although, all my theme editing got updated instantly, whys that?

sv

---

