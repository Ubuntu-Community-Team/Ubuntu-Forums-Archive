---
title: "x11 Forward / Sound"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by hyper_ch on 2006-10-05
Hello

I read it's possible by SSH to have an x11 forward and display the gui of a programm on a different machine. I know wonder whether it's also possible to forward the sound then?

**Scenario**
Me --> Amarok addict
Home: Kubuntu Edgy and a nice collection of MP3s
Work: WinXP
Desire: Access my MP3s at home through the "home Amarok interface"

Is this somehow possible?

---

### Post by dmizer on 2006-10-05
ssh with xforwarding will be prohibitively slow even with an extremely high speed connection.

your best bet will be to set up a streaming mp3 server on your home ubuntu machine which will be accessable by your browser at work.

here's a good howto: [http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server](http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server)

won't get you amarok, but it'll get you your music.

---

### Post by hyper_ch on 2006-10-05
Hmmm, I'll have a look at that... thx... does that work for edgy also?

---

### Post by dmizer on 2006-10-06
> **sjau said:**
> Hmmm, I'll have a look at that... thx... does that work for edgy also?
i don't see any reason why not.  it's a web based application so as long as apache and it's ilk can run, the streaming server will be able to work.

---

### Post by hyper_ch on 2006-10-06
Well, right now I have some other issues :)

I can't connect to my computer at home at all. SSH server is installed, the router does port 22 forwarding... but still SSH fails...
Same goes for FTP...it fails...
However the apache that I setup works...

Anyway, thx for the suggestions and I have a look at it as soon as I get ftp and ssh to work properly :)

---

### Post by dmizer on 2006-10-06
can you connect from your local network?  it could be that there's port blocking on your work firewall.

to test if ssh is even working correctly, you can also try connecting directly from the home computer itself:
```
ssh username@localhost
```
if that connects you, and you can't get connected from anywhere else, then there's still either a routing issue or firewall interference.

---

### Post by hyper_ch on 2006-10-06
I will test that on the weekend :)

You konw, it's been like 3 weeks ago since I moved from windows to ubuntu.. now I'm using edgy and (almost) everything runs the same or better than on windows.
However alone I wouldn't have been able to go so far... thx goes to all of you who helped me so much :)

---

