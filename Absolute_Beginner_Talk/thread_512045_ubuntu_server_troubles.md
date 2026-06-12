---
title: "ubuntu server troubles"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-07-28
I am having trouble editing files (vsftpd.conf) all the files I need to edit are only accessable by 
root. I cannot login as root with my password using the Gui or sudo. I added gui becaues I could not get gksudo gedit to work even after installing them. I have changed my group to root, Im getting really lost here. trying to set up a ftp server and having no luck changing the needed files to allow uploads I can login to ftp. how can I change permission to these files tried 
edit - preferences. any help please.

---

### Post by HermanAB on 2007-07-28
There are various ways to do it.

This will run the gedit editor as root:
$ sudo gedit

This should give you a root prompt:
$ sudo su -
(sudo space su space dash)

'Hope that helps!

Herman

---

### Post by bodhi.zazen on 2007-07-28
> **larry Gaminde said:**
> I am having trouble editing files (vsftpd.conf) all the files I need to edit are only accessable by 
root. I cannot login as root with my password using the Gui or sudo. I added gui becaues I could not get gksudo gedit to work even after installing them. I have changed my group to root, Im getting really lost here. trying to set up a ftp server and having no luck changing the needed files to allow uploads I can login to ftp. how can I change permission to these files tried 
edit - preferences. any help please.

Herman AB gave you some good advice.

What gui did you install ?

You open gui apps (as root) with gksu <command>

So, assuming you installed gnome (ubuntu-desktop) and/or gedit :```
gksu gedit </path/to/file
```

In a terminal you become root with 

sudo su

with sudo, gksu, etc you use the same password you use to log into the system.

Useful links :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Server guides :
[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)

---

### Post by larry Gaminde on 2007-07-28
OK 
I tried these processes and got a window I really don't know the path, all I know is 
  etc.vsftpd.conf  not sure what goes in front of that if I goto Places then Computer its under   File Systems two words would this make it 
  File Systems/etc.vsftpd.conf or is there more guess im reading a little dos into this not knowing if two words are ok. What I really need is a Book I have downloaded some info off the internet but I need a book or manual what sugestions do people have.

---

### Post by bodhi.zazen on 2007-07-28
Well, there is plenty of info on the net, in fact follow some of the links in my sig...

You might also like this, although there are others ...

Command line tips:
	[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
	[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)
	[http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)
	[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by larry Gaminde on 2007-07-28
This is what I get


lg@ubuntu:~$ gksu gedit </etc/vsftpd.conf

(gedit:9666): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Warren Watts on 2007-07-28
gksu gedit </etc/vsftpd.conf   <---  wrong
[B]
gksu gedit /etc/vsftpd.conf[/B]  <---  correct

You might try using a CLI (command Line Interface) editor like nano instead of gedit, then you can just enter

sudo nano /etc/vsftpd.conf

---

### Post by larry Gaminde on 2007-07-28
yes yes yes
guess that shows how new I am 
the example showed </ so I used </ 
now I know and that won't happen again

Thanks All

---

### Post by Warren Watts on 2007-07-28
No thanks necessary; that's what this forum is for: :-)

I am far from an expert, but I do have vsftp up and  running on my system, so if you have any vsftp problems, I can probably help you.

A few basic things:

Remember to open port 21 if you are behind a firewall or a router that acts as a firewall

You need to stop and restart vsftp after you make any changes to vsftpd.conf.  I usually use the services GUI tool under System|Administration|Services to do it.

Good luck!

Warren

---

### Post by larry Gaminde on 2007-07-28
Thanks Warren I will try that, I have been rebooting each time. I just new there was a better way just didn't know what it was.

and thanks are necessary
it shows everyones time was worth it to me

---

### Post by larry Gaminde on 2007-07-28
Oh and yes on the port 21 also 80 right now im just using the lan connection, so no outside connects at this point

---

### Post by larry Gaminde on 2007-07-28
Im having one more problem now, I can log in but I cannot transfer files would this be because im in the root directory? if so how do I change this or should I allow transfers to root and how do I allow this.

---

### Post by bodhi.zazen on 2007-07-29
> **larry Gaminde said:**
> Im having one more problem now, I can log in but I cannot transfer files would this be because im in the root directory? if so how do I change this or should I allow transfers to root and how do I allow this.

I am not sure I am following you with your question.

Are you asking about /root (which is root's home directory) or / (the root directory).

What are you trying to do ? Move/copy some files to your ftp shared directory ? Connect from another computer and upload/download ???

See if this link helps at all :

[http://doc.ubuntu.com/ubuntu/serverguide/C/ftp-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/ftp-server.html)

---

### Post by larry Gaminde on 2007-07-29
Yes I had printed that link and all thoes items are uncommented
Im using Ws_ftp and a windows box and it just keeps saying 
553 Could not create file
and I cannot make a directory It will not allow me to write even though I have uncommented
all write and anon write sections

---

