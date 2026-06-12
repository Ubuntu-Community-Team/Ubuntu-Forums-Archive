---
title: "How to &quot;&quot;phone&quot;&quot; computer to computer on the network without Internet ?"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-05-17
and if possible from the command line ?
(microphones and speakers available on the hardware of both PC )
  
Is there some possibilities with a kidn of mplayer ... & somethg to make streaming ... 
Or other program ..?
  
Thank you, 

Greetings !

---

### Post by steve.horsley on 2006-05-17
You're going back in history a bit there. People used to use bulletin boards before the internet. You won't be able to do it with speaker and mic, but that's what modems are designed for. And Linux certainly can work this way. You will need to search (google, I guess) for guides on setting up bulletin boards and accessing them.

---

### Post by txinga on 2006-05-18
I'm a little curious on this one too. Could you use something like gaim but just inside your home network?

---

### Post by skinnygmg on 2006-05-18
here's a cross platform network chat app

[http://www.icewalkers.com/Linux/Software/519350/Akeni-LAN-Messenger.html](http://www.icewalkers.com/Linux/Software/519350/Akeni-LAN-Messenger.html)

if you try it, let us know how it goes :-k

---

### Post by patrick295767 on 2006-05-18
[QUOTE=skinnygmg]here's a cross platform network chat app

[http://www.icewalkers.com/Linux/Software/519350/Akeni-LAN-Messenger.html](http://www.icewalkers.com/Linux/Software/519350/Akeni-LAN-Messenger.html)

if you try it, let us know how it goes :-k[/QUOTE]
  
"Akeni LAN messenger is a cross-platform instant messenger client. It is a P2P program that works on your LAN without the need of an Internet connection or a dedicated server. The client has an user interface similar to AIM, ICQ, or MSN Messenger. It supports all the standard IM features such as chat, group conference, presence management, file transfer, and emergency alert/notification. Extra features include contact management and optional tabbed chat sessions."
  
Thank you !!
We are progressing ... 
We have the chat now... 
  
So, how can we have the sound somehow... 
I am sure it s possible to Stream server our /dev/dsp 
  
then we can read it from the other pc via :
mplayer .... IPadressotherpc... 
(with cache)
  
Like to listen radio : 
mplayer -nocache -ao oss  mms://vip9.yacast.fr/encoderfranceinter

Greetz,
Pat'

---

