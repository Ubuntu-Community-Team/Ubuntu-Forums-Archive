---
title: "remote desktop"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by shinson71 on 2007-03-31
good evening ladies and gents. First of all i am only a couple of days into this and this forum is awesome. I have had so many answers to questions just from reading old posts. 
However, my question for this 15 minutes of the day is: should i be able to log into my ubuntu server using vnc if i am not already logged in. It works like a charm as long as the box is already logged in, but if i reboot or log out and its sitting at a login screen i get a "failed to connect"#-o . Should i be able to initiate a system login , am i missing yet another simple command or is this the way this should work?
Thanks ahead of time. Let the answers begin!

---

### Post by nsilva on 2007-03-31
what you have to look into is that the service you are requesting in this case VNC is still available, even if you log out. (If you reboot keep in mind the service will close, and if it is set to start automatically it will be available after reboot, otherwise it would have to be started manually)

[http://ubuntu-tutorials.blogspot.com/2007/02/sharing-ubuntu-desktop-using-remote.html](http://ubuntu-tutorials.blogspot.com/2007/02/sharing-ubuntu-desktop-using-remote.html)

Take a look to it and let me know of it helps

---

### Post by chamberlain2006 on 2007-03-31
I'm a fan of NX, I personally use NoMachine NX, ([http://www.nomachine.com)](http://www.nomachine.com)).  I use NXserver and I can connect to it from any computer, Windows or otherwise, and it doesn't require me to be logged in in Ubuntu.

---

### Post by shinson71 on 2007-03-31
thank you for the replies, i will have to test the nx server software. Until such time it's good to know i can just lock the station and hook back up with remote desktop instead of dragging a monitor out everytime i need to change something.

---

### Post by nsilva on 2007-04-01
> **shinson71 said:**
> thank you for the replies, i will have to test the nx server software. Until such time it's good to know i can just lock the station and hook back up with remote desktop instead of dragging a monitor out everytime i need to change something.
Keep in mind this post when installing the Freenx server, only version 1.5 worked for me

[http://ubuntuforums.org/showthread.php?t=348175](http://ubuntuforums.org/showthread.php?t=348175)

---

