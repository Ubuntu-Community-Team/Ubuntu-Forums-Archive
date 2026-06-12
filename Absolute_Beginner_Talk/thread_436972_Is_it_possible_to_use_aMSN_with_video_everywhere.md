---
title: "Is it possible to use aMSN with video everywhere??"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-08
Hi,

I'm trying to setup aMSN with video support in Feisty. However I get a message telling me that probably my firewall/router prevents me from sending/receiving video and that I should alter the firewall/router settings. I have no firewall but I'm behind a router....as most people. OK I can probably open some ports on my router (don't know which one and how) but I have a more general question here. I use Ubuntu on my laptop and when travelling I need to be able to connect to Wifi and start aMSN with video. Now obviously it seems that I'll have to open ports on all routers I will be connected??? No problem if they are mine but what about connecting to a public wifi router or a router at someone else's place??? I cannot alter the settings of these router so does it mean no aMSN with video then??

With Windows there is no problem connecting with a video in MSN. It never asks to open ports on my router....

So is aMSN a real possibility to do videoconference on the go???

---

### Post by davahmet on 2007-05-08
The difference you are seeing is that Windows does not enable a firewall by default.  With Ubuntu, your Linux firewall is enabled as the default behavior.  This is simply the cost of better security, but it's not an obstace.

You will most likely need to open the ports in your Linux firewall.  Probably the easiest way will be to install Firestarter from the repositories as a graphic firewall configuration tool.  If you know the ports aMSN uses, then you should be able to open these ports through Firestarter.

Hope this helps.

---

### Post by kilou on 2007-05-08
Oh I see, Linux comes with a builtin firewall as default and firestarter is just the configuration tool for that firewall? I thought Linux didn't have any firewall and that to have one I needed to install Firestarter...

So I installed Firestarter and first tried to stop the firewall but this didn't help: I still get the message in aMsm! What's wrong?

---

### Post by kilou on 2007-06-01
The problem seems to be the firewall in the router probably. But I cannot change that since I don't have access to the configuration of the router I connect to :( This is a major problem because with a laptop and when you connect to "foreign" routers that you cannot configure aMSN simply won't work with the camera........pretty bad for a solution that is supposed to keep people in touch everywhere :(

MSN or Skype in Windows just work right off the box and you never need to configure the router to allow such programs to work. Another reason for me not to throw away XP!!

---

