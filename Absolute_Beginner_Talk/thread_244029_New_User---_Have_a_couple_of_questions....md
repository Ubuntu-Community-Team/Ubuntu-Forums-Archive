---
title: "New User--- Have a couple of questions..."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by starke1120 on 2006-08-25
I am new to linux and Ubuntu all together, so I hope some one can help me out.  I recently installed Ubuntu Server at work to host Knowledge tree.  I ran "sudo apt-get install ubuntu-destkop" to get a GUI interface since Im a newbie and dont know much about linux.. so here are my questions...

should I use 64 bit server on my HP DX5150, or just stick with 64 bit Desktop - is desktop version not as stable and fast for sharing files and sites, does it support more hardware then server?.  THe primary use is to run a LAMP to support Knowledge Tree DMS.

What is Breezy and Dapper???  See told you I was new!

Does Xserver take up a lot of resources?  Can I kill it and free up the resources once Im done, or it it best to just not install a GUI interface?

I think that is all...  Thanks in advance!

Dave

---

### Post by nalmeth on 2006-08-25
> **starke1120 said:**
> I am new to linux and Ubuntu all together, so I hope some one can help me out.  I recently installed Ubuntu Server at work to host Knowledge tree.  I ran "sudo apt-get install ubuntu-destkop" to get a GUI interface since Im a newbie and dont know much about linux.. so here are my questions...

should I use 64 bit server on my HP DX5150, or just stick with 64 bit Desktop - is desktop version not as stable and fast for sharing files and sites, does it support more hardware then server?.  THe primary use is to run a LAMP to support Knowledge Tree DMS.

What is Breezy and Dapper???  See told you I was new!

Does Xserver take up a lot of resources?  Can I kill it and free up the resources once Im done, or it it best to just not install a GUI interface?

I think that is all...  Thanks in advance!

Dave
It's a matter of preference I suppose. I haven't found the 64-bit xserver "unstable" really, but for purely desktop use, 32-bit makes things easier. Since this is not the case for you, I would try 64-bit server install, and use the command:
sudo aptitude update
sudo aptitude install ubuntu-desktop

aptitude makes removing a meta-package and it's dependencies a world easier. This way you can decide for yourself, and remove it easily if you don't want it with:
sudo aptitude remove ubuntu-desktop

Breezy is version 5.10
Dapper is version 6.06

---

### Post by Bachstelze on 2006-08-25
Hi and welcome to Ubuntu :)

Desktop and Server versions differ only by the packages installed by default. Desktop comes with a full environment with a GUI and lots of software while Server comes only with the necessary packages to boot the system and get a command line, then you can install whatever packages you want.

"Breezy Badger" and "Dapper Drake" are codenames for Ubunntu releases. Brezzy  is Ubuntu 5.10 (released October 2005) and Dapper is Ubuntu 6.06 (released June 2006).

About the X server, I don't know if it's possible to kill it properly, better not install it at all if you run a erver I guess, command line is not _that_ hard.

---

### Post by starke1120 on 2006-08-25
Guys, thanks for the welcome and thanks for the prompt replies.  I appreciate the help!  I think Im going to love ubuntu once I learn the command line a bit more...

one more question though, I did the "apt-get install ubuntu-desktop and it installed Xfce Desktop and not Gnome, is this normal?  I thought Gnome was the default desktop?

Thanks again!

Dave

---

### Post by Bachstelze on 2006-08-25
Are you _sure_ you installed ubuntu-desktop and not **x**ubuntu-desktop ? ubuntu-desktop definitely should install GNOME.

But anyway, if you want to install a server edition and then manually install ubuntu-desktop, you'd better do a full install from a desktop or alternate CD since that's precisely what it does.

---

### Post by starke1120 on 2006-08-25
Im pretty sure I typed ubuntu as I didnt know xubuntu was till I googled for Xfce Desktop...  But I could have miss typed it by accident...

I will do a fresh install of Ubuntu desktop version.. I was thinking I was getting some special version of Ubuntu by getting the Server edition, but as pointed out here, its the "essentials" without the GUI.

BTW, Im very impressed with this forum, fast replies... pretty soon Ill be able to upgrade out of the "newbie" category..:-D 

Thanks again

Dave

---

