---
title: "Remote Desktop Connection"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-09-20
On Macs and PCs, there is a function known as RDC that allows you to connect to other computer via the internet. Is there a similar application for Ubuntu? How do I setup, configure, and use it?

---

### Post by kebes on 2007-09-20
There is a facility called "Remote Desktop" (System > Preferences > Remote Desktop). I believe it's installed by default. See here for some help:
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)
[http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/)

However, if you want to get "more sophisticated" you can use SSH for commandline remote access, and then use that to tunnel a VNC session. See this for some help:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Access)

---

### Post by stalker145 on 2007-09-20
> **intense.ego said:**
> On Macs and PCs, there is a function known as RDC that allows you to connect to other computer via the internet. Is there a similar application for Ubuntu? How do I setup, configure, and use it?

It's not on the Applications menu under Internet? Terminal Services I believe it's called.

I have it on my lappy at home and I don't recall having to install it.

---

### Post by Bothered on 2007-09-20
Personally I recommend using FreeNX for this (it's available in the [seveas repository]("https://wiki.ubuntu.com/SeveasPackages")), or NX server from [NoMachine]("http://www.nomachine.com/").

---

### Post by bjmgryphon on 2007-09-20
There are a few applications that will do the trick. The application I use to connect to windoze via RDP, vncviewer and Citrix ICA client (you must enable one of these server clients on the target system) is called Terminal Server Client. Should be part of the default Gnome Ubuntu install. If not, you can add it with Synaptic or from terminal : sudo apt-get tsclient
You'll need the IP of the system listening with RDP, ICA, or VNC. Enter the IP in the "Computer" dialog box.  Enter the "Protocol", "User" and "Password" (set on the target system). You may also have to enter the target "Client Hostname" (computer name) and/or "Domain" (domain or workgroup) if it is behind a firewall. 
Hope this helps.
Cheers.

---

### Post by Chemist on 2007-09-20
just installed freenx it works a treat mate highly recommended

just having a bit of trouble working out how to resume session :)

---

### Post by intense.ego on 2007-09-20
I still have not gotten used to adding repositories, so could someone please give some simple instructions? especially with this repo where there are different servers and dates. I'm trying to install freenx.

---

### Post by funrider on 2007-09-20
> **intense.ego said:**
> I still have not gotten used to adding repositories, so could someone please give some simple instructions? especially with this repo where there are different servers and dates. I'm trying to install freenx.

man, i just checked [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

it is easy, in plain english, with screenshots. stick to it, it is the easiest way.

---

### Post by intense.ego on 2007-09-20
Your suggestions so far only allow me to share my desktop. What about accessing someone elses?

---

### Post by funrider on 2007-09-20
> **intense.ego said:**
> Your suggestions so far only allow me to share my desktop. What about accessing someone elses?

well, someone else has to open the door for you first - means he/she has to set thing up following the guide we provided

---

### Post by intense.ego on 2007-09-20
Lets say I want to connect to a school or work network using a URL?

---

### Post by Bothered on 2007-09-20
The school or work network need to have configured a remote desktop server for you first ("open the door" as mentioned above).

---

### Post by funrider on 2007-09-20
if your school really offer this service, try getting help directly from your school IT department. They might have guideline for it. different organzation has different set up and policy, our generic suggestion might not apply in your case.

---

### Post by jamesrfla on 2007-09-20
I had the same problem setting up Remote Desktop with Ubuntu. Try this link [http://ubuntuforums.org/showthread.php?t=555776](http://ubuntuforums.org/showthread.php?t=555776)

---

