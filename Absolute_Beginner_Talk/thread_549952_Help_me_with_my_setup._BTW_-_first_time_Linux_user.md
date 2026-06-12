---
title: "Help me with my setup. BTW - first time Linux user."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by simonduz on 2007-09-13
Here's my situation.  I work in a corporate M$ world and support M$ servers.  At home I like simplicity.  I am on a mission to build a media server/file server/firewall server, and by Christmas I need 3 desktop computers (1 for each of my children).  I desperately want to use Linux for all.  But I have some requirements.
[LIST]
[*]I need the server to perform media streaming, file server functions with security, print server, firewall for my children's browsing, remote access for my home network, and it needs to play well with my Windows machines for work.
[*]The workstations may be a bit trickier.  I would like use a pre-built image for each child's computer so that they can boot using the network, use the image on the file server, and use only what I provide but they would able create and save files, and internet favorites.
[/LIST]
So I ask, am I in over my head?  Keep in mind that I have never used Linux and I am trying to choose the best distro for the ease of building this infrastructure and it's administration.
Thanks in advance.

---

### Post by overdrank on 2007-09-13
> **simonduz said:**
> Here's my situation.  I work in a corporate M$ world and support M$ servers.  At home I like simplicity.  I am on a mission to build a media server/file server/firewall server, and by Christmas I need 3 desktop computers (1 for each of my children).  I desperately want to use Linux for all.  But I have some requirements.
[LIST]
[*]I need the server to perform media streaming, file server functions with security, print server, firewall for my children's browsing, remote access for my home network, and it needs to play well with my Windows machines for work.
[*]The workstations may be a bit trickier.  I would like use a pre-built image for each child's computer so that they can boot using the network, use the image on the file server, and use only what I provide but they would able create and save files, and internet favorites.
[/LIST]
So I ask, am I in over my head?  Keep in mind that I have never used Linux and I am trying to choose the best distro for the ease of building this infrastructure and it's administration.
Thanks in advance.

Hi maybe this link will be of some help
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
Good luck and welcome!

---

### Post by simonduz on 2007-09-13
Thanks for the link.   It helps a little.
So what's up with the funny names like Fiesty Fawn, Dapper Drake, etc?  Are these nicknames given to the versions of Ubuntu or is there more to it.  
The link gives great details for command line setup but what about GUI administration for Firewall, SAMBA, etc?  This is probably the one part of Linux that I am cautious of as a newbie, especially if I need to make a quick change and don't want to Google for the correct Linux shell command.
Any others with thoughts on my setup?

---

### Post by overdrank on 2007-09-13
> **simonduz said:**
> Thanks for the link.   It helps a little.
So what's up with the funny names like Fiesty Fawn, Dapper Drake, etc?  Are these nicknames given to the versions of Ubuntu or is there more to it.  
The link gives great details for command line setup but what about GUI administration for Firewall, SAMBA, etc?  This is probably the one part of Linux that I am cautious of as a newbie, especially if I need to make a quick change and don't want to Google for the correct Linux shell command.
Any others with thoughts on my setup?

Ok as I understand it those are the code names for the releases. To install a gui is easily done form the command line as this link refers too.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
For that matter you can install the regular desk top version and add the sever apps to it. All though I have see recommendations to use a light desktop as XFCE or fluxbox. But for the GUI for firewall that would be Firestarter. For more on security you can use these links
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
And for Samba maybe this link will help
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by simonduz on 2007-09-13
More excellent links.  Thank you very much.

Question:  What I am starting to understand, in the Linux world there are desktop environments (several to choose from) and then there are separate application with their own GUI's which may or may not be compatible with the desktop environment I choose.   So if I choose KDE as my desktop I would then have to choose applications that will run within KDE?  Placing links in the correct menus, launching within the desktop environment.  Is this correct?

---

### Post by rsambuca on 2007-09-13
Most applications will run equally fine on both KDE and Gnome.  They might not visually match your themes from you current desktop environment.  Most people nowadays run a mixmash of KDE/QT and Gnome/GTK programs.  

The only time you may want to be careful is if you have low systems resources like RAM.  If you have both types of programs running at once,  then both QT and GTK libraries will have to be loaded into ram.

---

### Post by overdrank on 2007-09-13
> **simonduz said:**
> More excellent links.  Thank you very much.

Question:  What I am starting to understand, in the Linux world there are desktop environments (several to choose from) and then there are separate application with their own GUI's which may or may not be compatible with the desktop environment I choose.   So if I choose KDE as my desktop I would then have to choose applications that will run within KDE?  Placing links in the correct menus, launching within the desktop environment.  Is this correct?

From my experience and from this forum is that you can use KDE apps in Gome and vice versa. You can even have XFCE, KDE, and Gnome install all at the same time and choose which environment you want to use at the login screen.

---

### Post by LowSky on 2007-09-13
> **simonduz said:**
> More excellent links.  Thank you very much.

Question:  What I am starting to understand, in the Linux world there are desktop environments (several to choose from) and then there are separate application with their own GUI's which may or may not be compatible with the desktop environment I choose.   So if I choose KDE as my desktop I would then have to choose applications that will run within KDE?  Placing links in the correct menus, launching within the desktop environment.  Is this correct?

Many application develope for other GUI should work in most other GUI based on the fact they are all based on linux. Little issue might appear like the placement of menus or how it runs in the background, but mostly all programs will work

---

### Post by Steveway on 2007-09-13
Not quite right.
You can use all apps in all enviroments.
The problem is only that for example a Gnome-app has some Gnome-dependecies, wich are getting installed, too.
But you normally don't want the additional dependencies because it fills your space up and up.
So you better stick to KDE and QT apps on a KDE System and vice versa.
Also GTK and QT apps look visually different, it just doesn't look to good if you use some of these and some of those.
If you have the space and don't mind for the little visual differencies then just go ahead and install what you want.
If you want to know more, wikipedia has very good articles just read.
Welcome, it will be difficult but you'll enjoy the result if you keep trying.

EDIT: lol, same thoughts but I was really slow.

---

### Post by dhughes on 2007-09-13
> **simonduz said:**
>  ...  I am on a mission to build a media server/file server/firewall server, and by Christmas I need 3 desktop computers (1 for each of my children).  I desperately want to use Linux for all.  But I have some requirements.

[*]I need the server to perform media streaming, file server functions with security, print server, firewall for my children's browsing, remote access for my home network, and it needs to play well with my Windows machines for work.

[*]The workstations may be a bit trickier.  I would like use a pre-built image for each child's computer so that they can boot using the network, use the image on the file server, and use only what I provide but they would able create and save files, and internet favorites.

So I ask, am I in over my head?  Keep in mind that I have never used Linux and I am trying to choose the best distro for the ease of building this infrastructure and it's administration.
Thanks in advance.

 The first one is easy try FreeNAS it's a Netowrk Attached Storage which I guess is really a souped-up fileserver. I use it to store data, stream movies and music, RSYNC to perform automated backups. I'm not the best at setting stuff up in fact it took me quite a while but it is quite easy, considering your experience with servers you should find it a breeze.

 It's Free BSD based but it's close to Linux's terminology e.g. the primary hard drive on controller 0 is hda in Linux asd0 in BSD, the first partitions are hda1 and asd0s1. It's still a bit buggy though. [http://www.freenas.org/](http://www.freenas.org/)

 You could also try Openfiler, it's similar and bigger (FreeNAS 32MB versus Openfiler 320MB) people seem to like it but I could never get it to boot on my hardware. My hardware is pretty old though it's over five years old.  [http://www.openfiler.com/](http://www.openfiler.com/)  In fact Openfiler may be more suited to your needs.

 As for the second one I don't know it's a bit (way way!) beyond my abilities, but it appears to be a thin client set-up you want. There must be some thin client guides using Linux and a fileserver/NAS.

---

### Post by simonduz on 2007-09-14
Thanks to everyone so far.  This is a very helpful discussion.

After a few more hours of reading I think I have my solution.  Ubuntu / Edubuntu Server with LTSP, and Samba, and 3 thin clients.   So I wanted to know if there are any differences between Ubuntu server with LTSP and Edubuntu with LTSP.  All the documentation seems to point to the Edubuntu installations??  :confused:

I love the idea of NAS but wouldn't it restrict the use of the server to just NAS?   If this all works well then I may just have to toss out my MCE PC and go with Myth also.  LOL

I just purchased a new Buffalo router to flash with DD-WRT so no more firewall issues.

Comments, suggestions?

---

### Post by dhughes on 2007-09-16
> **simonduz said:**
> ... love the idea of NAS but wouldn't it restrict the use of the server to just NAS?   If this all works well then I may just have to toss out my MCE PC and go with Myth also.  ...

 OK I see what you're doing, yeah I guess the NAS is just for storage.

 I've never used a thin client before, I've heard of them of course but never used on, it sounds interesting. It must require a pretty good network setup, Gigabit ethernet and a really good Gigabit switch?

---

