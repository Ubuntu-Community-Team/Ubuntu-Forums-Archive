---
title: "Accessing your files Remotely"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by olph4rt on 2006-10-11
I have just for the first time left the world of Microsoft for Ubuntu.  After three crashes, the desktop is now operational.  I chose the desktop because the server need is less than the need for office-related programs for my son's school.  I now need advice on how to attain my goal.  My goal is to expose a folder to the internet.  This folder will contain anything, html, pdf, text, jpegs.  I am not picky about the security of this folder.  I am wanting the rest of the system to be unaccessable, even by me if need be.  I have figured out how to get a couple of programs going with the konsole, such as folding@home, but that's about it.  I have an isp that provides a dynamic ip address whenever my router logs off or the power goes out, then my address changes.  I can log into my home network ( a ms-home system) with out any problem with the gui.  I don't know what linux program would be suitable for my task, so I ask your greatly appreciated advice.  I am also new to commanding the system in the konsole, but I am happy to learn!

Thank you!
FAH team 12782 olph4rt,olph4rt_at_work,olph4rt_of_ubuntu (pending)

---

### Post by Marsolin on 2006-10-11
What method do you want to use to access the folder? Or is that part of your question? The program you were using with Windows probably has an equivalent Linux app.

There are quite a few [FTP Servers]("http://linuxappfinder.com/internetandnetworking/servers/ftp") available that you could use.

You could also try [Kpf]("http://linuxappfinder.com/package/kpf"), the KDE public file server.

If all you need to be able to do is just download files and not upload them then you could set up a simple [web server]("http://linuxappfinder.com/internetandnetworking/servers/web") and access any files through a browser. [LightTPD]("http://linuxappfinder.com/package/lighttpd") would be a good option.

---

### Post by Arevos on 2006-10-11
Hm. Are you picky about how you access said folder? Do you want to be able to access via a web browser, or would you be okay with downloading a small client application in order to access it?

Also, you mention you have a router. I suspect this means you are behind a NAT. NAT's allow you to connect out, but will stop attempts to connect in. You can get around this with port forwarding, which most routers have. Check your router manual or configuration to check that you do indeed have a port forwarding option.

---

### Post by olph4rt on 2006-10-11
I would prefer to use only a web browser.
--->This would allow to access on public computers such as an internet cafe.

I use a D-link DI-604.
---> I will look into deatils of nat.

I will look into those links as well!

Thanks!

---

### Post by Arevos on 2006-10-11
Would you want to upload files to your computer, or just to download them?

---

### Post by scot524 on 2006-10-11
Since you do not have a static IP on the WAN side of the router, you might wish to look at dynamic dns -- this will give you a name and everytime the ip changes DNS is updated. I use one from dyndns.org -- it's free although you are sort of restricted on the use of domain name (such as blahblah-home-ip.net or something like that).  You also need to run some software on the server, or if you're lucky the router will do it for you.

---

### Post by olph4rt on 2006-10-11
Arevos--> I want only to view documents, read documents.

Scot524--> Thank you!  I will respond in due time!

---

### Post by olph4rt on 2006-10-16
I have something working! ... now to secure it!
I had a HECK of a learning curve, but have installed and configured apache2, and ddclient. ddclient wouldn't work all the time with the hardware-update method, so I just used the web method, and it seems to be running fine with tests so far.  I just have to read about securing the computer, although I have set up the router hardware to pass only port 80.  
So thank you everyone!

---

