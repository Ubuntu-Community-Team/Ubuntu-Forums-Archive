---
title: "Remote Log In"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by seattle vic on 2007-11-20
I'm fairly new to Linux/Ubuntu, but now have it running on two home computers.  I recently bought a wireless router to accommodate a laptop I have on loan from work.  I can only run XP on that laptop, ie, no dual boot like I have on my other machines.

If I just want to, say sit on my porch and use the laptop to run ubuntu on my other machine, can I do that without running the server version?  I'm thinking that I'd need an x program on windows, like xming, and then connect to the local machine running ubuntu, start a session and have the same resources I'd have if I was on the local machine.

Is that possible?

---

### Post by Pumalite on 2007-11-20
[http://openvpn.net/](http://openvpn.net/)

---

### Post by lintoon on 2007-11-20
You could install vncserver on the Ubuntu box and connect to it using a vnc client on your laptop.  Check out RealVNC client for your laptop.

Another option is to use FreeNX.  The vncserver option is a lot easier to set up though.

---

### Post by Inxsible on 2007-11-20
if you are going to do it only within the local network, then using RDP would be the best bet. All you have to do is switch it on in the ubuntu machine.
System>>Preferences>>Remote Desktop.

answer all the questions there. Make sure you uncheck "Ask for confirmation"  or you will have to come to your ubuntu machine to allow access.

Then you could connect to it using vncviewer or any other vnc client that you want to use.

I give you the above option, because you mentioned using it from within the network.  If you wanted to access your ubuntu machine over the internet, you should do it via SSH since that will be more secure.

---

### Post by robertsaron on 2007-11-20
I am using Kubuntu gutsy gibbons 7.10 where in KDE is System>>Preferences>>Remote Desktop.? On all the posts retards post how to do it in KDE. 

Also Can I connect from win xp RDP to linux? I want to type in the ipaddress like so 192.x.x.x:80 for in the win xp rdp and have it connect to my ******* computer at home. is this possible?

---

### Post by Skip Da Shu on 2007-11-20
> **Inxsible said:**
> if you are going to do it only within the local network, then using RDP would be the best bet. All you have to do is switch it on in the ubuntu machine.
System>>Preferences>>Remote Desktop.

answer all the questions there. Make sure you uncheck "Ask for confirmation"  or you will have to come to your ubuntu machine to allow access.

Then you could connect to it using vncviewer or any other vnc client that you want to use.

I give you the above option, because you mentioned using it from within the network.  If you wanted to access your ubuntu machine over the internet, you should do it via SSH since that will be more secure. 

What is equiv to RDP in Xubuntu... how do I go about setting this up w/o "System>>Preferences>>Remote Desktop"?

---

### Post by Inxsible on 2007-11-21
> **robertsaron said:**
> I am using Kubuntu gutsy gibbons 7.10 where in KDE is System>>Preferences>>Remote Desktop.? On all the posts retards post how to do it in KDE. 

Also Can I connect from win xp RDP to linux? I want to type in the ipaddress like so 192.x.x.x:80 for in the win xp rdp and have it connect to my ******* computer at home. is this possible?you might wanna be careful with that kind of language. No one's asking you to follow the directions. You can if you want to.

and if you think everyone here is a retard, then do your own searching. Do you know what Google is ?

---

### Post by seattle vic on 2007-11-24
Thanks for the replies everyone!  I did some experimenting and was able to connect to one of my machines using both RDP on Ubuntu and a VNC client on my laptop.  Also, just did a SSH login as well, so next I'll learn about setting up an x-window from the laptop.

I do have a problem that maybe somebody could help with.  As I mentioned above, I can connect to only one of the two desktops in my LAN.  They are both running Gutsy and I can ping them both as well, however the older machine can't be reached by either SSH or VNC.   Both have the remote desktop settings identical.  I'm using real vnc and get the message, "unable to connect to host: Connection reset by peer (10054)".  The machine I'm trying to connect to is able to read and write to the internet.

Any suggestions?

---

### Post by daflame on 2007-11-29
> **seattle vic said:**
> Thanks for the replies everyone!  I did some experimenting and was able to connect to one of my machines using both RDP on Ubuntu and a VNC client on my laptop.  Also, just did a SSH login as well, so next I'll learn about setting up an x-window from the laptop.

I do have a problem that maybe somebody could help with.  As I mentioned above, I can connect to only one of the two desktops in my LAN.  They are both running Gutsy and I can ping them both as well, however the older machine can't be reached by either SSH or VNC.   Both have the remote desktop settings identical.  I'm using real vnc and get the message, "unable to connect to host: Connection reset by peer (10054)".  The machine I'm trying to connect to is able to read and write to the internet.

Any suggestions?

Although I'm not quite sure about connection reset by peer issues I can offer an alternative that is better.  FreeNX uses SSH to tunnel the X desktop protocol.  If you want packages go here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

