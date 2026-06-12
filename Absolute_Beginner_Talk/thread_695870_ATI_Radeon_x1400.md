---
title: "ATI Radeon x1400"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by garrettstarnes on 2008-02-13
I have a Dell inspiron E1505 with Ubuntu 7.10.  I have an ATI Radeon 
x1400 Graphics card that is not working.  I am new to ubuntu and linux, so I have no experience with the terminal.  I don't have an internet connection on that computer, however I do on my computer at work.  Could someone direct me, perhaps, to drivers if needed and how to correctly install them?  I would greatly appreciate it.  Thanks!!

---

### Post by marpstar on 2008-02-13
What exactly isn't working?  Are you not getting an display at all or is your 3D acceleration not working?  Give us a specific definition of "not working" and we can help...

-Cody

---

### Post by Paul S on 2008-02-13
> **garrettstarnes said:**
> I have a Dell inspiron E1505 with Ubuntu 7.10.  I have an ATI Radeon 
x1400 Graphics card that is not working.  Could someone direct me, perhaps, to drivers if needed and how to correctly install them?

You should be able to enable the ATI "fglrx" driver using the "restricted manager" in your menus.  I'm a KDE user, so can't give you the exact menu names in gnome.

The software should already be installed or be available on your installation CD.

HTH

---

### Post by garrettstarnes on 2008-02-13
Doesn't work means the special effects aren't working.  It is a restricted driver if I am not mistaken.  I can't even use the 'normal effects'.  I have to click on 'no effects'.  I was under the impression that the x1400 was a good card and that it should be able to handle the good effects.  But to answer your question, Yes the computer and the monitor does work.  But no, the effects don't work at all.  I would like to see the effects that linux has to offer.  Perhaps the 3-D desktop, if that is in the scope of things.  Thanks!!

---

### Post by spiderbatdad on 2008-02-13
you really need a working internet connection to make this happen.  Your can try to enable the drivers from synaptic if they are available on the live cd. make sure your cd is selected as a source under Administration>>Software Sources. Then browse synaptic. There is a driver xserver-radeon-c I think, there is also the linux-restricted-modules. That is probably what you need to have the restricted drivers manager activate for your card. IDK if it is on the live cd, but you could try

---

### Post by thisismalhotra on 2008-02-13
You can also install ENVY, it's a deb so you can click on the package and it installs. It should automatically install drivers for your card anf will configure them too, what I am not sure of is will you need internet or not ...

Website: -

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

One more things, you can download all repos on a cd and burn them at work, and use that as your source in synaptic....
This will help in that: -

[http://ubuntuforums.org/showthread.php?t=184112](http://ubuntuforums.org/showthread.php?t=184112)

---

### Post by garrettstarnes on 2008-02-14
What is a repo, and how will it help me?

---

### Post by kesman on 2008-02-14
Get yourself an internet connection in that computer so you can install the normal updates that also update compiz and your drivers. If it's not working after that, come back here.

---

### Post by garrettstarnes on 2008-02-14
I don't have an internet connection, and right now I am not able to get the connection.  That is why I asked for help.  If I had a working internet connection then I would try it.  Can I download anything to my flash drive and transfer it to my computer?

---

### Post by thisismalhotra on 2008-02-14
> **garrettstarnes said:**
> What is a repo, and how will it help me?

Repo is a short for repository which is a base of update and new softwares for your ubuntu installation. Most likely your special effects are not working for one of these two reasons a) drivers are bnot configured b)compiz the manager which handles extra effects is not updated.

If you are connected to internet your computer goes to the repository and check for updates and then will inform you to install them, since you do not have an internet connection I proposed to burn the whole repo on a DVD and tell your computer to do updates from it.

Hope that makes sense :KS

---

### Post by garrettstarnes on 2008-02-14
Thanks, that does make sense.  I will try to do that.  I do have a wireless card in the computer, but it is also missing the drivers.  I guess that is a problem for another post.  Thanks!!

---

### Post by garrettstarnes on 2008-02-14
Thanks, that does make sense.  I will follow the links to get the repos, and will try it that way.  Thanks so much!!

---

### Post by vinutux on 2008-02-14
install official "cytalyst driver 8.01" (or newer) from AMD/ATI download page for linux

it is a .run installer .download it --> right click and active execute under permission tab

make sur u rinstall "xserver-xgl" if u not install it with synaptic (system->administration->synaptic)

doble click and install it --> restart or relogin

now applay effect or whatever u want

.............................

:guitar:

---

### Post by thisismalhotra on 2008-02-14
> **garrettstarnes said:**
> Thanks, that does make sense.  I will follow the links to get the repos, and will try it that way.  Thanks so much!!

Dont know if it will work but try downloading it onto a flash disk too.. I have my doubts for it so if I were you I will do both DVD and flash drive.

---

### Post by garrettstarnes on 2008-02-14
This link,
[http://ubuntuforums.org/showthread.php?t=184112](http://ubuntuforums.org/showthread.php?t=184112)
does not work.  I would like to try to burn the repos to a cd.  Do you know where else I can find them?

---

### Post by raydeen on 2008-02-14
I have the same make and model of laptop and up until 7.10 was released I didn't have much luck either. Visit [http://www.mylittleubuntuguide.com/](http://www.mylittleubuntuguide.com/). The guy who runs that site has custom .ISO's for our particular machine. It looks like he's had some trouble with his images of late but he has scripts that you can download and run to fix whatever the problems are. His default ISO from about half a year ago had working graphics and wireless drivers. Try hitting the link below and see if that image works for you:


[http://www.mylittleubuntuguide.com/2007/10/21/beta-release-of-custom-gutsy-cd-for-dell-inspiron-6400/](http://www.mylittleubuntuguide.com/2007/10/21/beta-release-of-custom-gutsy-cd-for-dell-inspiron-6400/)

To be honest I'm surprised the official release isn't working for you. I don't recall having any trouble with mine. You might want to run a disc check on it to make sure it doesn't have any defects.

---

### Post by thisismalhotra on 2008-02-14
> **garrettstarnes said:**
> This link,
[http://ubuntuforums.org/showthread.php?t=184112](http://ubuntuforums.org/showthread.php?t=184112)
does not work.  I would like to try to burn the repos to a cd.  Do you know where else I can find them?

Try this...

[http://ubuntuforums.org/archive/index.php/t-205569.html](http://ubuntuforums.org/archive/index.php/t-205569.html)

---

### Post by garrettstarnes on 2008-02-22
I've tried all of these suggestions, but it seems as though I have to have an internet connection to get this to work.  I don't have an internet connection though on my computer;  I need the drivers for my wireless dell 1390 card to connect.  I really need to have the drivers on a cd so I can put it on manually.  How can I get the drivers without an internet connection?

---

### Post by garrettstarnes on 2008-02-27
Hi guys,

I didn't hear back from anyone.  Every tip that I've recieved says that I can't get the drivers unless I'm connected to the internet.  There is a problem.  My wireless card doesn't work yet either.  I don't have any other way to get online with that computer.  I can get online with another though.  I need to know where I can download the specific driver I need so that I can put it on a CD and install it from there.  Any suggestions?  Thanx.

---

### Post by thisismalhotra on 2008-02-27
why can;t you download driver from website and put them ona flash drive and use them at home..

---

### Post by garrettstarnes on 2008-02-27
I can do that too, I just need the specific drivers.  Most of the things I've been told to download are not the drivers, but are programs designed to go out on the web and get the drivers.  I do have one driver that I have not got to check yet.  I don't know how to navigate the terminal.  For instance, when I try to run the driver, I get an error message that I need to run the driver as a super user.  I don't know how to run from the command line.  I just double click it.  But if I double click it, it won't run as a super user.   Also, I have another file to try, but it says I have to navigate to the home folder.  I don't know how to change directories.  But honestly, I would try anything if I knew how to do it.  If you could tell me how to do any of this, I would GREATLY appreciate it.  Thanx!!

---

### Post by thisismalhotra on 2008-02-28
well if you are not comfortable with command line, you can do this,

instead of logging in as your login, type username as 'root' and then type password you use in synaptic. This will log you in as a root user/;super user.

Thanks you can pretty much do anything you want. One more thing you can not install driver or almost anything without being a superuser.

Be careful as you if you do something wrong it might screw something up. Also you icons etc etc may look different.

Let me know if that works for you...

---

