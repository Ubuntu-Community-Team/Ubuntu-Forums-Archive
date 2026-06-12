---
title: "How to install VNC Server in Ubuntu"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by shiyasvp on 2007-06-02
Dear friends

How to install VNC Server service in ubuntu 7.04, is it possible to access ubuntu system via vnc service from any windows pc?. also how to setup remote desktop connection in ubuntu 7.04 .  from an ubuntu pc i can connect to windows pcs via remote desktop ?.  can i get the configuration details of above mentioned things

---

### Post by Gagle on 2007-06-02
> **shiyasvp said:**
> Dear friends

How to install VNC Server service in ubuntu 7.04 

For one thing, in an ad hoc windows network, a vnc server can be easily setup in Feisty by going to
System->Preferences->Remote Desktop . From then, use (type in terminal..) the simple command listed in the setup window to connect another Ubuntu computer on the network .  
To connect from a Windows box, use a vnc client. You  could also use Putty("linux emulator") by I would go with the vnc application directly (tightVnc for instance.)

hope it helps 

gagle

---

### Post by information_entropy on 2007-06-02
I use tightvnc client for windows or ultravnc client for widows to access the VNC server on my Ubuntu boxes.  This post is proof that it works.  I am using it right now.

---

### Post by Gagle on 2007-06-02
Just keep in mind things  will go quite smoothly if your network uses DHCP adressing and there isn't any huge firewall protecting the network. If so, you might need to forward ports etc.
If you want to remotely control / log in using vnc on a computer that doesn't "live" in your network, a computer at  a friend's house, your computer at home that you want to access from work fo example, you will need a tad more configurations.
Note that Beryl manager and vnc don't go well together.   In fact you may want to stop Beryl * on the computer that serves as a vnc server*.

---

### Post by Gagle on 2007-06-02
Another note :  It's a little "bug" I encountered that I want to share.

You will see, if you login remotely using anither Ubuntu box,that the command you need to issue at the terminal identifies your vnc server by the name of the computer, not it's internal IP adress.
Sometimes, it wouldn't work.  I had to put my network IP instead.
Example:  My vnc server has an internal IP of 192.168.0.101 and the Remote Desktop configuration told me to issue this command to login from another computer :
```
 vncviewer gagle-desktop:0 
```

Sometimes, I needed to write : ```
  vncviewer 192.18.0.101:0   
``` instead.

gagle

---

