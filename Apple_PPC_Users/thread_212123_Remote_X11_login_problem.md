---
title: "Remote X11 login problem"
date: 2006-07-09
forum: Apple PPC Users
---

### Post by Johnny1975 on 2006-07-09
Hi everybody !

I'm just installed Ubuntu 6.06 LTS to my shiny G4 1.25GHz Mac mini.
I want to use to share my external USB HDD, internet sharing and terminal services. Everything works well except remote X11 login. 
I logged in from my desktop pc (P4 2.4GHz) with a Slackware 10.1 (Xorg 6.8.2)
and after a 10-20 seconds the X server crash with:

Fatal server error:
Caught signal 11. Server aborting

Same thing happans on my Intel PIII laptop with the same Slack distro installed. It seems that something not compatible between the two X implementation.

Can anybody help me ?

Thanks
Janos Suranyi

---

### Post by Johnny1975 on 2006-07-10
Additional info:

I tried a same Ubuntu but X86-version. I try to login to mac mini with a remote X11 login, the effect is same. 
Maybe this is an endianess bug in one of X-libray ?

---

### Post by rasec on 2006-07-10
So you're trying to get XDMCP working? I just tried connecting to my powerbook running kdm from a debian machine and the only problems that I ran into were XDMCP being disable by default in kdm and Xaccess file being too strict by preventing any remote hosts from logging in. I pretty sure that gdm disables XDMCP by default too but I forgot how to enable it. I'm sure that if you search the forums for "xdmcp gdm" you'll come up with something. 

Another thing to check is your firewall. If you have a firewall on your mini make sure that you open up udp port 177 and tcp port 6000 and you should be set.

---

### Post by APU on 2006-07-10
You could also try to forward X11 over an SSH connection. Although you might not need the extra security this offers in a home environment it is quite convinient to have and normally works without hassle. Just add the -X option to the ssh command when you connect to the Mac mini from another Box should do the trick.

APU

---

