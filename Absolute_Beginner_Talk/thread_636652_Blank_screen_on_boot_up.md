---
title: "Blank screen on boot up"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Fungal Fractoids on 2007-12-10
I tried installing 7.10 on my Asus F3JP laptop from the desktop cd. All my hardware seems to work fine from the cd bt when I try to boot from the installation I get past the GRUB menu options then the screen just stays blank. The laptop has an ATI 1700, I read on the 7.10 release notes that this is a known bug with some ATI hardware, but the solution wwas a bit too obscure for a noob like myself. Apparently I need to edit the xorg.conf, it says- Add 'Option "LVDSBiosNativeMode" "false" to the driver section of xorg.conf.

 I can get into safe mode from the GRUB menu so I assume I would need to do this with the root% command, no? If so, can anyone give me a step-by-step idiots-guide on how to do it?

Another forum I was reading on how to edit the xorg.conf said to use this command- sudo gedit /etc/X11/xorg.conf. But when I do it either says I am using gedit the wrong way or that the directory doesn't exist (that's when I remove the space between 'gedit' and '/etc'

Another potential solution I found was to get the 'fglrx drivers'- is this likely to solve my problem? If so what would be the correct app-get command to install them? (I can access the internet from safe mode).

ny help would be greatly, greatly appreciated

:guitar:

---

### Post by PmDematagoda on 2007-12-10
Try:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After that is done, do:-

```
sudo startx
```

That can bring you to the GUI from where you can start to configure Ubuntu to use your ATi card.

---

### Post by Fungal Fractoids on 2007-12-10
Wonderful! I'm off to give that a shot (running the net off the cd atm). If it works I will be back to give you  big  sloppy kiss :lolflag:

---

### Post by Fungal Fractoids on 2007-12-10
Hmmm... Well, that worked. Kinda. It loaded the GUI but I have no admin privileges, so can't even change the network settings. When I went to 'switch user' it said I couldn't do it because GNOME wasn't being used. When I changed the graphics driver like you suggested I first tried the ATI driver and got this message:L

Fatal Error: no screens found
XI0: fatal IO error 104 (connection reset by peer) on x-server ":0.0" after 0 requests

Then I tried the vesa(sp?) driver and that worked. But now I'm stuck with no admin access.

Is there something else I need to be doing?

---

### Post by Fungal Fractoids on 2007-12-10
Ok, so I've been reading something where someone used apt-get to get the fglrx driver. He had a F3JP with a radeon 1700 like me and said this worked to fix his resolution problems ([http://forum.notebookreview.com/showthread.php?t=107505](http://forum.notebookreview.com/showthread.php?t=107505)). Would it be likely to fix my problem? 

It seems I don't have internet access in safe mode (apt-get was looking in the E: drive, not the net), So if I download fglrx and put it on a disk, then use the 'driver disk' function from the original boot options on the desktop cd, is that likely to work.

Any replies would be very muchly appreciated, I'm tearing my hair out here :confused:

---

### Post by kpkeerthi on 2007-12-10
> 
Then I tried the vesa(sp?) driver and that worked. But now I'm stuck with no admin access.

Can you elaborate? What do you mean by not having admin access?

---

### Post by jaybombalous on 2007-12-10
> **Fungal Fractoids said:**
> Hmmm... Well, that worked. Kinda. It loaded the GUI but I have no admin privileges, so can't even change the network settings. When I went to 'switch user' it said I couldn't do it because GNOME wasn't being used. When I changed the graphics driver like you suggested I first tried the ATI driver and got this message:L

Fatal Error: no screens found
XI0: fatal IO error 104 (connection reset by peer) on x-server ":0.0" after 0 requests

Then I tried the vesa(sp?) driver and that worked. But now I'm stuck with no admin access.

Is there something else I need to be doing?

right now u wanna use vesa, that has nothing to do with why it told u gnome wasn't running.

if the video works, then stick with vesa till u work around the other problems, vesa is not causing u to have admin or gnome problems. They are two completely different things.

Stop thinking like a windows user.

edit: u issued the above command using sudo, correct? sudo is admin privileges, so u must have admin rights, just gnome isn't working?

---

### Post by Fungal Fractoids on 2007-12-10
Well, when the GUI first loads I get a message telling me that it might load up with privileged access and that it might not be a good idea for security reasons, the only options though are 'ok' or 'quit'. Quit goes back to the root, ok takes me to the GUI but, as I said, without admin access. So when In try to use system things like network or user accounts it gives me an access denied message. When I go to 'change user' I get a message telling me that GNOME isn't in use so that function isn't available. I'm totally flummoxed.

Is it worth trying a fresh install? I dunno whether it would make a difference but when it first loaded to a blank screen I mashed the keyboard a bit just trying to get it to react, Maybe I inadvertently set it to a non-admin user account or something?

---

### Post by Fungal Fractoids on 2007-12-10
> **jaybombalous said:**
> 

Stop thinking like a windows user.

Did I mention that I'm a total n00b? ;)

I really am just poking around in the dark, if you have any ideas on why I have no admin access, please, spell them out simply for me! I just thought the GNOME had something to do with it because thats why it said I couldn't use the change user option... But don't blame me, blame Bill gates and his secret brainwashing techniques! :p ;)

---

### Post by Fungal Fractoids on 2007-12-10
> **jaybombalous said:**
> 
edit: u issued the above command using sudo, correct? sudo is admin privileges, so u must have admin rights, just gnome isn't working?

Maybe. Sudo works in safe mode, but once the GUI loads I can't even use sudo in the terminal...

---

### Post by jaybombalous on 2007-12-10
I do have a thought on what is causing your problems, but like u I am new to this as well but I will try to help you. But, I believe your fix is easy.

First try this, change the driver to vesa, save xorg.conf and **reboot** back into ubuntu.

if that doesn't work, then we will need to figure out to disable the 'lock' that on the root account. This is locked by default, its not your fault. This keeps people from doing stupid ****.

---

### Post by kpkeerthi on 2007-12-10
I'm not sure what you are trying to say. But lets give it a shot one more time. 

1. Reboot and from GRUB, choose recovery mode. Let the system boot.
2. Login to command line and at the prompt, type
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
3. Select "vesa" for the driver and default the rest.
4. Reboot.
**5. From GRUB, boot "normally". DO NOT CHOOSE RECOVERY MODE this time**

Let me know if you can login graphically and get on to your desktop. We'll proceed from here.

---

### Post by Fungal Fractoids on 2007-12-10
Ay, people like me! ;)

I'm pretty sure I'm using vesa, I used the sudo dpkg-reconfigure command, chose the vesa driver and got into the GUI. So what is this disable lock that you speak of? I guess there's some command that I can use in safe mode?

---

### Post by Fungal Fractoids on 2007-12-10
> **kpkeerthi said:**
> I'm not sure what you are trying to say. But lets give it a shot one more time. 

1. Reboot and from GRUB, choose recovery mode. Let the system boot.
2. Login to command line and at the prompt, type
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
3. Select "vesa" for the driver and default the rest.
4. Reboot.
**5. From GRUB, boot "normally". DO NOT CHOOSE RECOVERY MODE this time**

Let me know if you can login graphically and get on to your desktop. We'll proceed from here.

Aye, aye cap'n!

GEt back to you in ten mins..

Oh, and thanks for this- I dunno what i'd do without you guys...

---

### Post by jaybombalous on 2007-12-10
the key, is after u change the driver u need reboot the computer, because u can't login to gnome as root user, that account is locked by default to avoid problems.

U can change this behavior, but for now u should leave it as is.

SO when u reboot, now u will be presented with a graphical login where u can login as a normal user and then use sudo to access admin privileges.

Do you get it now?

---

### Post by kpkeerthi on 2007-12-10
After you get X working with "vesa":

1. Open terminal and type
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

``` 


2. Follow [FGLRX installation in Gutsy]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") installation in gutsy.

3. Restart normally. If X doesn't work, you can revert back to vesa by booting in "recovery mode" and running

```

mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

Reboot again.

---

### Post by Fungal Fractoids on 2007-12-10
Ok, when I enter

```
sudo apt-get install xorg-driver-fglrx
```

into terminal I get this message

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages

```

The Gutsy guide says: If the system complains about dependencies, use your preferred package manager to download python2.4 and, if necessary, its dependencies.

What would be the best way of going about this?

---

### Post by kpkeerthi on 2007-12-10
Install the dependencies first..
```

sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

```

Then install the driver...
```

sudo apt-get install xorg-driver-fglrx

```

---

### Post by Fungal Fractoids on 2007-12-10
When I try to get the dependencies I get this message

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dh-make is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dh-make has no installation candidate

```

[edit]

Aha... Was playing around with Software Sources and changed the server from 'Australia' to 'main'- seems to be working now...

---

### Post by Fungal Fractoids on 2007-12-10
Ok! So it installed fine. I went into restricted drivers and selected the ATI driver, That's right is it? The problem is pretty much solved?

Awesome... Thanks so much for your patience and help!

---

### Post by kpkeerthi on 2007-12-11
> **Fungal Fractoids said:**
> Ok! So it installed fine. I went into restricted drivers and selected the ATI driver, That's right is it? The problem is pretty much solved?

Awesome... Thanks so much for your patience and help!

Thats it. Glad it worked for you.

---

### Post by silverguy on 2007-12-24
cool that you got it sorted. im having similar 104 fatal problems i was justa bout to reinstall ubuntu USB style whne i came across ur post.

iam gunna try the VESA driver solution its one i ahvent tried before. And dont knock windows users for thinking in windows.

its the staple diet of most of the population and to get people use linux i think we stillf further require linux simplification, cause iam baffled to the point of the good  ol days of reintsalling quake everytime i wished to run it in windows 3.11.... i just cant get x to work :( 

well keep up the good work well get there together.:lolflag:

---

### Post by silverguy on 2007-12-24
argh

i manually edited the xorg and now my monitor just goes to stand by everytime ubuntu tries to load. this really sucks.

:confused:

i think ill just have to what i always do and find out alone what to do and how to run ubtuntu off a USB key, and reinstalltion here we come.

---

### Post by silverguy on 2007-12-25
well i fixed my problems and i am back in ubuntu as we speak.

i say i fixed it but it really was trial an error approach ... which took hoursss....

basically 

1. sudo rm -r /etc/X11
2. sudo apt-get install --reinstall xserver-xorg

these commands will reinstall xorg (the graphical user interface for linux/ubuntu)

Then at the log in screen, on the left second down there is a log in option for gnome (maybe second from bottom?) i dunno literally the Linux font are sooo small at log in its barely legible... just hit and miss 

hope this helps the "FATAL SERVER XIO 104"  people in some way

---

