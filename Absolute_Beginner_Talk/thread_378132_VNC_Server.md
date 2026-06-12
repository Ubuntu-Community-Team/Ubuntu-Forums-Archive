---
title: "VNC Server"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2007-03-06
I want to set up a vnc server on my linux like I have on my windows computer, but I am finding it is much harder on linux.  Is there a good program like TightVNC for linux (I know they have one but it doesn't work well).  Thanks

:guitar:

---

### Post by kvonb on 2007-03-06
Menu->System->Preferences->Remote Desktop

Click on "Allow others to view your desktop,  Allow others to control, Require users to enter a password - type in a password, then click on OK.

From the remote computer connect to your.computers.ip:5900

---

### Post by maniacmusician on 2007-03-06
Well, I see a "tightvncserver" package in the repos.

I'm not really familiar with VNC, but I remember that there is a page in the Ubuntu wiki with excellent instructions for getting it set up, so try and find that.

---

### Post by gravz84 on 2007-03-08
I also wanted to know how to do this.. UBUNTU 6.10 EDGY, WIndows xp
On the ubuntu system I've already changed the preferences to allow control..that was the simple part.
Is that a built in vnc server?
Now I want to connect to the "built in vnc server" from a windows machine. In VNC viewer I type the ip:5900 but it says connection refused:10060.
Can anyone tell why this is? and can the port used to connect can be changed? 
I tried to test the port 5900 using telnet "o Ip 5900" and i dont get a reply..


[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html]("http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html")
--same instructions here..but instead of ip::5900 it says ip:0 I tried that too..

--------------------------------------------------------------------------------

Menu->System->Preferences->Remote Desktop

Click on "Allow others to view your desktop, Allow others to control, Require users to enter a password - type in a password, then click on OK.

---

### Post by Matt1632 on 2007-03-08
Just go to add or remove applications and install krfb, that what I use.

---

### Post by Scorpuk on 2007-03-08
to connect to the remote desktop with VNC you need to type in the following:



```
linux.boxes.IP.address:0

ie

192.168.1.1:0
```


I believe :0 implies connect to "active desktop". :-)

---

### Post by gravz84 on 2007-03-09
What is krfb?? We are talking here about connecting remotely from Windows to Ubuntu!! krdc/krfb do that?

u mean ip address:0 rite.. I had tried that.
I now realize that the ip was dynamic and had changed, maybe because of that the vnc couldn't connect. So i made it static now.hopefully it will work now.

"linux.boxes.IP.address:0

ie

192.168.1.1:0"

---

### Post by Ek0nomik on 2007-03-09
What kvonb suggested is the easiest/quickest way of getting a remote desktop to work on Ubuntu.

---

### Post by scxtt on 2007-03-09
krfb (in KDE) or "Remote Desktop" (i think that's the name in Gnome) are "current session" sharing apps (so you can connect to :0 [which is essentially "your monitor"] - port 5900) ... i.e. if you're not logged in, they don't work (w/ the exception of x11vnc) ...

my recommendation would be to:

1. #prompt> sudo aptitude install tightvnc
2. #prompt> vncpasswd  # enter your password for VNC connections
3. #prompt> vncserver -geometry 1280x1024 -depth 24 # this will start a VNC server (:1) that you can connect to ...
4. on the "remote machine" using a VNC viewer type **vncviewer <ip address>:1** - which will differ if you're on your network or connecting from the outside:

example:
internal> vncviewer 192.168.1.100:1
externa> vncviewer my.dns.name:1 (which will forward to port 5901 on the box running the server, make sure your router is aware) ...

---

### Post by HereInOz on 2007-03-09
Don't forget that you will need to open port 5900 in the IPtables firewall on the Ubuntu machine.

---

### Post by enopepsoo on 2007-03-09
awesome thread.  I found another thread that had a much worse method for setting up a vnc server, but this is totally easy and awesome.  IN short, it rocks.  It is the Ubuntu way.

---

### Post by Ukr on 2007-08-16
My VNC working well when i home and using the same e-net but from external i have error 10060. I try connect from win2000 to Ubuntu/gnom typing < ip>:0 If any can help plz.

---

### Post by bodhi.zazen on 2007-08-16
VNC is a snap , with some experience I have it up and running with ssh in < 5 min

[list=number]
[*]VNC :

[list][*]x11vnx (share 1 desktop) : x11vnc : [http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

[*]VNC (over ssh, new desktop): 	[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

[*]Reverse VNC (AKA easy router setup) : [http://www.ubuntuforums.org/showthread.php?t=299489](http://www.ubuntuforums.org/showthread.php?t=299489)[/list]

[*]Secure ssh: [list][*][https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
	
[*]See also [denyhosts](http://denyhosts.sourceforge.net/) ~ it is in the repos, but you should read the config file ...[/list]


[*]And, last FreeNx is popular as well ...  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)[/list]

EDIT: LOL I did not notice how old the OP was :)

---

### Post by mattalexx on 2008-07-23
> **kvonb said:**
> Menu->System->Preferences->Remote Desktop

Click on "Allow others to view your desktop,  Allow others to control, Require users to enter a password - type in a password, then click on OK.

From the remote computer connect to your.computers.ip:5900

This works perfectly for me. By default, I was not connecting on port 5900 though. I used "0" and it worked perfectly. Actually Ubuntu will tell you in that dialog what the address is.

---

