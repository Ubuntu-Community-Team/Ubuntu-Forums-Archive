---
title: "Downloaded gnome-ppp now what?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-09
Hi I downloaded gnome-ppp as I am trying to set up an internet connection on another machine. I put it on a usb drive that I got today and put it on the desktop of the machine I am setting up the connection on. Where do I put it(in what folder) and how do I get it to install?

---

### Post by taurus on 2007-02-09
What format is it in?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by rapattack1 on 2007-02-09
deb

---

### Post by taurus on 2007-02-09
```
sudo dpkg -i **filename.deb**
```

---

### Post by rapattack1 on 2007-02-09
Oops ha ha I just read that in the link you sent and did it. OK I opened gnomeppp and was hoping that it would detect the modem since I haven't had much luck with anything else....MMMMmmm no luck with this either.

---

### Post by taurus on 2007-02-09
Maybe a reboot!

---

### Post by rapattack1 on 2007-02-09
OK:popcorn:

---

### Post by rapattack1 on 2007-02-09
MMMmmm now there is another problem. Wow I am a true beginner. I noticed straight away after the reboot that there was a little orange box in the top right hand corner next to the speaker icon. It has a light in it I guess. Anyway I clicked it and a window pops up titled "software updates" Keep your system up-to-date. Then the is a smaller window on top of that saying "software index is broken..............." I think this has to do with "audacity" that I tried to install after gnomeppp.

---

### Post by taurus on 2007-02-09
Run these two commands from a terminal and see what happens.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by rapattack1 on 2007-02-09
OK got a wholelot of err lines with urls and at the end got: Reading package lists....Done 
then I typed the 2nd command and I got -command not found

---

### Post by taurus on 2007-02-09
Can you post the whole error message from this command?

```
sudo aptitude update
```
Also, what does your /etc/apt/sources.list look like?

```
cat /etc/apt/sources.list
```

---

### Post by rapattack1 on 2007-02-10
Attached is a txt file of what you asked me to do.

---

### Post by rapattack1 on 2007-02-10
Well I have gnomeppp installed on my laptop too. Just wish I could get the modem to talk to both machines. It talks to this one, why not them?
:confused:

---

### Post by rapattack1 on 2007-02-16
just thought i'd let you know that i got gnome ppp installed on the laptop and i am on the net due to a gift of a pcmcia modem. it works really well on this old laptop. getting on the net on the desktop is another matter.

---

