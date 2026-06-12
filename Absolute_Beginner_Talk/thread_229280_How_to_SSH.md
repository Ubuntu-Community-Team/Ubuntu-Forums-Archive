---
title: "How to SSH"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by James_N on 2006-08-04
Hi

Ive had ubuntu installed for a few weeks and its fantastic. I have VMware working, and have VNC working internally but cant get it working externally.

Now i understand SSH is another way i can access my home computer from work?

How do i go about using SSH? do i need anything special? do i get a GUI to use? as this would be easier to use at work :)

Thanks :)

---

### Post by MrHorus on 2006-08-04
> **James_N said:**
> 
How do i go about using SSH? do i need anything special? do i get a GUI to use? as this would be easier to use at work :)

Thanks :)

You need an SSH client.

For Windows I recommend PuTTY, a graphical-based client.

This will open up a text based, encrypted command shell to your machine so you will obv need to open up a port on your firewall and this should normally be the standard port for SSH, 22.

---

### Post by James_N on 2006-08-04
Thanks :) How do i go about setting up my ubuntu machine for SSH? or is it already set up out of the box?

---

### Post by Tomosaur on 2006-08-04
You need to have the ssh daemon running on your machine. Here's a page about SSH from the Ubuntu Wiki:

[SSH Server](http://ubuntuguide.org/wiki/Dapper#SSH_Server)

You can always try the remote desktop.

---

### Post by patrick295767 on 2006-08-04
> **James_N said:**
> Hi

Ive had ubuntu installed for a few weeks and its fantastic. I have VMware working, and have VNC working internally but cant get it working externally.

Now i understand SSH is another way i can access my home computer from work?

How do i go about using SSH? do i need anything special? do i get a GUI to use? as this would be easier to use at work :)

Thanks :)
For gui:
VNC is usually recommanded & cool.   
XDMCP enabled from your gdm is also one possibility for gettnig gui.[http://www.faqs.org/docs/Linux-HOWTO/XDMCP-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/XDMCP-HOWTO.html)
> Using XDMCP is inherently insecure, therefore, most of the distributions shipped as it's XDMCP default turned off. 

---

### Post by James_N on 2006-08-04
> **Tomosaur said:**
> You need to have the ssh daemon running on your machine. Here's a page about SSH from the Ubuntu Wiki:

[SSH Server](http://ubuntuguide.org/wiki/Dapper#SSH_Server)

You can always try the remote desktop.


Thanks, ive installed SSH And got it working, but when logging in, is there no GUI available? Im not quite that good in the terminal yet :(

---

### Post by James_N on 2006-08-04
> **patrick295767 said:**
> For gui:
VNC is usually recommanded & cool.   


VNC is installed but i cant get it working externally for some reason. It works internally and ive forwarded all the ports so im not sure whats a miss.

On the machine from work im typing: [http://81.108.208.162:5901](http://81.108.208.162:5901) 
 
( 5901 being the port VNC is running on (i think)) but i just get the error:

> RFB 003.008

I dont know what this means :(

[http://81.108.208.162:1/](http://81.108.208.162:1/) brings this up in firefox:

> This address uses a network port which is normally used for purposes other than Web browsing. Firefox has cancelled the request for your protection.

---

### Post by Tomosaur on 2006-08-04
SSH = Secure **Shell** login. No GUI I'm afraid :P Some SSH Clients allow X-Forwarding. Putty is, I think, one of these, so you may want to look into that.

---

### Post by James_N on 2006-08-04
> **Tomosaur said:**
> SSH = Secure **Shell** login. No GUI I'm afraid :P Some SSH Clients allow X-Forwarding. Putty is, I think, one of these, so you may want to look into that.

Thanks for that. In that case, for now i need to try and get VNC working externally. Can anyone help me with that please? :)

---

### Post by James_N on 2006-08-04
hmm seems to work with a VNC Viewer instead of firefox.

Thanks

---

