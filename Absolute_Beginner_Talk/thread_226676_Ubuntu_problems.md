---
title: "Ubuntu problems"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Gerriec on 2006-07-31
I am a raw beginner to Ubuntu Linux, got it off a Linux Format Special, complete with a "manual", but it is not of much help in my case. I could have downloaded the distro free of charge, and this forum is of far more use than the "manual". 

When I attempt to instal a program off a disc (one of three, that came with the distro) it informs me that "The Same Version is available in a Software Channel" and "Recommends me to install from the Channel instead".  Now what channel does this refer to and where is it ??  Why put it on the disc to start with.

Item two --- When I use a screensaver, after the screensaver runs for a few minutes the computer freezes, and I have to press the reset button and reboot.  Any known reason for this ??  Meanwhile the screensaver is disabled.

Item three --- As I am the sole user of this machine is it possible to do away with having to log on at boot up.??

I like Ubuntu and looking forward to lotsa pleasure.

Gerrie C.

---

### Post by Paerez on 2006-07-31
> When I attempt to instal a program off a disc (one of three, that came with the distro) it informs me that "The Same Version is available in a Software Channel" and "Recommends me to install from the Channel instead".  Now what channel does this refer to and where is it ??  Why put it on the disc to start with.
The original packages are on the ubuntu install disc so that you can install ubuntu without internet access. Then, when you add a program later, you can install them off the CD if you want, or just download them off the internet. Open up the Synaptic Package Manager from System->Administration, then open the repositories option (its in one of the menus, I forget which). Then remove the cdrom repository. Now you will get all your packages from the internet.
> Item two --- When I use a screensaver, after the screensaver runs for a few minutes the computer freezes, and I have to press the reset button and reboot.  Any known reason for this ??  Meanwhile the screensaver is disabled.
My guess is that it is a 3d program, and the default screensaver is "random" which sometimes runs a 3d screen saver. Just set it to "Blank Screen" and you should be fine.

> Item three --- As I am the sole user of this machine is it possible to do away with having to log on at boot up.??
I think this option is in System->Administration->Login.

> I like Ubuntu and looking forward to lotsa pleasure.
ubuntu love you long time

---

### Post by Gerriec on 2006-07-31
Many thanks for your reply.

> The original packages are on the ubuntu install disc so that you can install ubuntu without internet access. Then, when you add a program later, you can install them off the CD if you want, or just download them off the internet. Open up the Synaptic Package Manager from System->Administration, then open the repositories option (its in one of the menus, I forget which). Then remove the cdrom repository. Now you will get all your packages from the internet.

Yes, that I understand, but when I attempt to instal the program off the provided discs, I get the dialog box informing me about installing them off the "Software Channels". 

I had no problems installing the Ubuntu installation, the whole thing just fell into place perfectly, but the addon programs in the other two discs render the Software Channel messages. Why, and which channels are they referring to ??

Regards

Gerrie C.

---

### Post by Paerez on 2006-07-31
I think they mean to use "Programs->Add/Remove Programs". And by "Software Channel" they mean Ubuntu's Repositories.

I wouldn't use those packages anyways, since they may be out of date.

---

### Post by Metacarpal on 2006-07-31
The Ubuntu install CD is only one disc, so it sounds like the 3-CD version you have is an OEM build (ie, not directly from Ubuntu).  Your best bet would probably be to download and burn the install CD yourself.

[Here's where to find the .iso file for download]("http://www.ubuntu.com/download")

If you have over 256MB of RAM, use the "Desktop" CD.  If you have 256MB or less, use the "Alternate" CD.

After downloading, remember to make sure your CD burner is buring the iso as a "CD Image", not just burning the file itself onto the CD.  If you need help, just search the forums.  There are plenty of threads to help you with this.

---

### Post by Gerriec on 2006-07-31
**Paerez** --- Many thanks for your help. I guess that you may be correct, will follow your advice. Much obliged


**Metacarpal** --- Yes the Ubuntu install is only one disc, and it installed perfectly. I am not sure whether it is an OEM version but Linux Format issue it as a Ubuntu 6.06 LTS version, so I presume that it is authentic, if not they could be liable. My concern is not with the distro but with the other two CDs, and that seems to be resolved. Thanks for your response

Regards

Gerrie C.

---

### Post by Metacarpal on 2006-07-31
> **Gerriec said:**
> **Paerez** --- Many thanks for your help. I guess that you may be correct, will follow your advice. Much obliged


**Metacarpal** --- Yes the Ubuntu install is only one disc, and it installed perfectly. I am not sure whether it is an OEM version but Linux Format issue it as a Ubuntu 6.06 LTS version, so I presume that it is authentic, if not they could be liable. My concern is not with the distro but with the other two CDs, and that seems to be resolved. Thanks for your response

Regards

Gerrie C.

Oops - sorry, got confused!

---

### Post by Paerez on 2006-07-31
remember, if it's free, don't pay for it.

---

### Post by catlett on 2006-07-31
Ubuntu uses the APT package management system. There are a few different ways to interact with apt but they all go to the same place, online repositories.
These are servers that hold ubuntu "packages" for download.
The Ubuntu install cd is kept to 1 cd for simplicity. After the install users can customise and modifyt their systems through the online repositories. This has been a real issue for people with no internet connection or a very slow connection.
Linux Format (doing what they do best) must have downloaded and burned some of the repositories to cd and included them with the install cd. I real good idea actually.
If you have an internet connection then apt is activated. The update manager is monitoring packages and so on. When you went to install from the cd you got the "install from other software channels". This is the system saying to install through one of the apt front-ends. I believe you can go ahead and install anyway, ?Can you?
Now that you have an internet connection, you should get your packages through the gui front-end of apt, Synaptic.
Synaptic package manager is located in the top panel menu under System<Administration<Synaptic package manager. There is a search function where you can put an applications name in and it will search for it or you can browse through the entire list.
When you highlight an entry a brief synopsis of the application will come inti view so you can get an idea of whast the package does.
If you want to be a little more hands on, you can follow the Dapper Guide and get instructions on how to install programs [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
Or if you want the opposite, this is a script that installs just about everything you need painlesly [http://ubuntuforums.org/showthread.php?t=223087](http://ubuntuforums.org/showthread.php?t=223087)
And of course people in the forum are always eager to help someone configure their system. All you have to do is ask.

---

### Post by Gerriec on 2006-08-03
**catlett ---- ** many thanks for yor reply, sorry I have taken a while to acknowledge it but it got so far back.

Yes I did manage to instal the file, in spite of the error notice.

At the present moment I do not have an internet connexion thru Ubuntu, I am using Windows, waiting for an ethernet card to arrive.

Will follow up your url pointers. Always willing to learn.

Regards

Gerrie C.

---

