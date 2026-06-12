---
title: "WiFi list of available wireless networks"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ZeframCochrane on 2007-05-26
Hello everyone!

I'm a complete Ubuntu & Linux newbie, and have a question that may seem really elementary for some of you, but please bear with me :-)

I was recently introduced to Ubuntu by a friend, and fascinated by how it looks & feels, I gave it a look on LiveCD. Until now i was accustomed to using (please don't freak out by reading the name) ol'd heavy 'n slow Windows XP, and i usually wardrived a WiFi network near my home. So what i did was look at the list of "Available Wireless Connections" in the Wireless Zero Configuration interface and select the one i usually use.

Now, i have run the LiveCD, and my Broadcom wireless card gets recognized ok, so all i need now is to connect to the WiFi connection.
Where is the available connection list in Ubuntu? Or, bettert still *IS* there such a list? where do i look for available wireless connections in Ubuntu?

Thanks a lot.

---

### Post by Ek0nomik on 2007-05-26
I believe all you need is the network manager.

```
sudo aptitude install network-manager
```

Then if you right click on the panel, you should be able to add it to your panel and see the list.

---

### Post by kevinlyfellow on 2007-05-26
If your using fiesty, click the connection icon in the upper right hand corner near the time and date... a picture says a thousand words.

---

### Post by amaroKer on 2007-05-26
The network manager applet should be loaded by default.  It is sitting in the Notification Area (system tray).  To enable the drop-down list of available wireless networks, click on the icon and go into Manual Configuration.  Ensure that your device is enabled, and under Properties, enable "roaming mode".  The checkmark indicating that your device is working in the first screen will turn into a bar.  You should then find that when you click on the network manager applet, there is a list of networks there.  If you need a static IP address, turn of roaming mode, and select your network from the list in "properties".  Hope this helps!

---

### Post by ugm6hr on 2007-05-26
Unfortunately, there may be an issue for your Broadcom Wireless card.  If the above advise doesn't work, the following thread was started by someone in your position too.  Follow his/her train of thought and the advice given (there are a few links to solutions):

[http://ubuntuforums.org/showthread.php?t=454103](http://ubuntuforums.org/showthread.php?t=454103)

Good luck.

---

