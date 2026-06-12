---
title: "Pleaseeeee help!!!!! Fiesty Fawn vs. nvdia drivers!!!!"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by dilipm on 2007-05-11
Hello everybody,
          I have almost tried everything, I mean everything in order to solve this problem. Well here is the way it goes::

Firstly, I am a bit new to linux..but am not that ignorant..a php java C++programmer myself I do have some inclination towards computers and OSs, anyway recently i wanted to know some shell programming with respect to my work so I thought why not install the current popular version of Linux, hence ubuntu. 
    Now, after I installed..the desktop looked quite neat and nice on my 1680x1050 res alienware laptop(btw my rig's specs are all at the bottom). Then a message popped up saying Restricrited drivers manager, so clicked an icon to open this window, it said that my nvidia drivers are currently not in use, do  i want to enable them? I said alright clicked the check box, it downloaded a couple of drivers from the internet then installed them finally prompted for a restart. so i did....here the problems started..after the restart what do I see!!!!? A patch of reddish purple colour on the left of screen, where as the right side is totally black and if u see carefully this black patch slowly , very slowly covers the entire screen. Its totally black after sometime. 

But the funny part is I could hear the startup ubuntu sound. I just typed my login into this black screen and the password to hear the login startup sounds. But I can do nothing, cannot see a thing, cannot type a thing. Anyway at this point I googled "black screen problem at startup after installing nvidia drivers on ubuntu feisty fawn". Well the fisrt link was some where here in this forum. They also did have black screen but were having different video cards...they were suggested some changes in the xorg.conf file which i also did but in vain.These other people with similar problem were atleast able to go to the console. ctl-atl-f1 thing, I even could not do that!!!!!! Anyway: 

Now here is the list of solutions I tried:

I.Put my Ubuntu CD in the drive and start the live version from the CD. Checked the internet for some solutions made a note of them. Restarted my compter, from the grub menu loaded in the recovery mode. at the console opened the xorg.conf. Now in some solutions I read there were problems where the xorg.conf was setup to a CRT screen, but not to a LCD or laptop screen. So what I tried was adding such kind of options to the to the xorg.conf
        At the    Section "Screen"      added the options
                     Option "UseDisplayDevice" "UFP-1"
                              or
                     Option "UseDisplayDevice" "DFP" (tried once each option after consequtive restarts)
Now what happened after restart, nothing...all I got was a blue screen saying Xserver cannot launch, please setup your xorg.conf file and then restart. And then all I got was a series of logs and errata regarding the error messages. This was my first try...

II. Now waht I thought was lemme clean install again, so I put in the Fiesty fawn 7.04 Cd again then reinstllaed the whole thing. Again after installing could see the desktop and everything, everthing is fine again saw restricted drivers manager window pop up. This time I did not install the drivers from there. Just ignored it. Opened the Desktop effects window to see what message I would get. Obviously as expected I was told to enable the 2D and 3D effects of my graphics card. But this time I went to the nvidia linux site
  
[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

which is the latest version for linux nvidia drivers and manually installed them. Now I went to the console mode manually installed theese drivers as follows:

    sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run (remember this installation is after Ubunutu's clean install)

 I was really expecting a proper desktop, but what happens, the same old bloody reddish-black screen!!!!!!!!

Now what I did was before I make any changes to the to xorg.conf I looked for the log file for xorg.conf to see what it actually says, I could not understand a word of it so I am pasting it here.

  [http://paste.ubuntu-nl.org/20114/](http://paste.ubuntu-nl.org/20114/)

I showed this log to a guy in in an IRC chat, who explained me to add the following to the xorg.conf, similarly at the  Select "screen" section. Btw I always edit the xorg.conf file in the console mode with the gdm stopped and using the "sudo nano /etc/X11/xorg.conf"  to edit the xorg.conf file

       Option "NoLogo" "True"
       Option "AddARGBGLXVisuals" "True"
       Option "AllowGLXWithComposite" "True"
       Option "RenderAccel" "True"

saved the xorg.conf file ....no use at all. cant see noting at startup.....

Again gone  into the console mode restore the xorg.conf file as follows 
                sudo dpkg-reconfigure -phigh xserver-xorg

rebooted..it started fine but the resoultion was different maybe because I selected vesa drivers, anyway that should not be problem I guess. Now opened the synaptic pacakge manager and uninstalled any nvidia glx drivers found.

Now what i did at the console was:

sudo apt-get install nvidia-glx-new

what this did was install the drivers again, well I guess!!? and then again restarted to see the damn black screen.

....that was my second type of instalation..

III. Well now I was really fed up,so what I did was go into the console again reconfigured the xorg.conf file, then at the desktop downloaded the automatix installer where I downloaded the nvidia drivers and installed them. After restart same old problem of black screen!!!
. Again at the console I did an automatix command

          automatix-nvidia-restore

which restored to previous xorg.conf file. I could restart again normally here. Later I opened automatix and uninstalled all the nvidia drivers with automatix.

Now I was really fed up, all the forums  either had recently posted this or did not have solution yet. I heard in some forum regarding Envy drivers. I downloaded this and installed them.. Still again the same old black scren turned up. I reconfigured the xorg.conf file again uninstalled Envy drivers also. 

Finally from all the forums and IRC chat all I could conclude was it has something to do with xorg.conf file options, no matter what driver I install there is no use. So what I finally started was to learn about the various display, screen and kinds of nvidia driver optins to edit in the xorg.conf file. I hope somebody can give me solution by then. I cannot sleep at nights until I solve this thing. I am right now not learing bash but learining how to configure xorg.conf file. Surprisingly there are not much proper documentations regarding specific options with respect to specific video cards to edit in the xorg.conf file. I hope there is any other kind of option which you help me, if i missed something. I had to write such a detailed message because I found many similar problems  in various forums, surprisingly some solutions above  I wrote above did work for some and did not for some. Its  still is not working for me :-(. Anyway I hope somebody can help.


NOTE: Please check the actual log I gave in the link above for any clues of  the black screen mystery????!!!!!!HELP

MY LAPTOP SPECS

Alienware laptop 3 years old 

Nvidia GeForce FX Go5700 128Mb Video Ram
1 Gig of RAM
Pentium 4 ,3.0 Ghz with HT
60gig hard drive.

---

### Post by mrmonday on 2007-05-11
Which version of the nvidia drivers are you trying to install? If you are trying to do the ones linked on the nvidia site, that would be why... Your card is not supported with them. Rather than messing around with old drivers, get [envy - http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html"). Follow the instructions on the site to install envy, then install your nvidia drivers using the tool. Allow envy to re-configure your xorg.conf automatically. If you get the same black screen again, try to get to a CLI (command line/ terminal/ konsole), you can do this by booting into recovery mode. In there do:

```
sudo envy -t
```

And uninstall your drivers.

Let me know how it goes.

---

### Post by dilipm on 2007-05-11
Hello Mr.Monday

Well I did install the envy drivers as I explained in my meggase ...but its the black screen again ..U suggested a command I guess thats for the uninstallation of envy drivers I guess....After that what?? Thanks

---

### Post by Rognalf on 2007-05-11
It's not for unstallation. Boot up i recovery mode. Log in and enter envy -t. This is for running envy in text mode.
I've used it both on edgy and feisty. This will install and setup the latest nvidia drivers for ubuntu. Remember to uninstall nvidia drivers through envy and uninstall envy prior to system upgrades (ie. form 6.10 to 7.04) though.

---

### Post by dilipm on 2007-05-11
alrite guys,,,,lemme tell u what the situation is.....As I tried every driver excpt Envy properly...I decided to clean install ubuntu again...So I formatted my hard drive..and installed ubuntu again...then installed envy ...then i went to the console and did 

 sudo envy -t

followed the instructions and installed it and then restarted the gdm...this time what I see is the blue screen I mean the console error message giving the xserver error...What I saw here surprisd me..I saw that the errror was the API conflict error,,which said the kernel was 9631 and the xmodule was 9755..it was mismatch error..So now I thought lemme complie the kernel to 9755 so it should work..so go to this nvidia site again and download the original 9755 linux drivers...

I checked if fx go5700 had any conflicts with these drivers but I found this site which said my video card is perfectly fine...U can check it out it u wanna

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

this has my video card listed here as a working one...

So now I download this driver and uninstalled the envy drivers as they did not work even after clean install of ubuntu...
Anyway i installed the new drivers with sudo sh it compiled the new kernel ...and I restarted to see the damn purplish black screen again...I am stuck guys....

All I am doing is overwriting the old xorg.conf file again to come back to the esktop..will I ever enable the 2d and 3d or not!!!!!!!!!!!!!!!????What am i doing wrong, I do not understand......
I again think it has to do something with the display screen and changing the options in the xorg.conf file???....i guess...:-(

---

### Post by Billy McCann on 2007-05-12
Oops.  nevermind.

---

### Post by dilipm on 2007-05-12
I donno if this would help just adding this

...lemme paste the 2 xorg.conf files....one which is working(I mean with no 2d 3d acclerarion) and the one which gets the purplsih black screen



The xorg.conf file which does not work, I mean the one with the black screen:

[http://paste.ubuntu-nl.org/20447/](http://paste.ubuntu-nl.org/20447/)



the file which is normal and works I mean the one with 2d and 3d disabled


[http://paste.ubuntu-nl.org/20446/](http://paste.ubuntu-nl.org/20446/)


I hope that helps
Cheers

---

### Post by Billy McCann on 2007-05-12
With the first one, the one that doesn't work, I must say that you're "Device" section looks rather anemic.  

Here's yours. 

```
Section "Device"
    Identifier     "nVidia Corporation NV36 [GeForce FX Go5700]"
    Driver         "nvidia"
EndSection
```

Here's mine.  
```

Section "Device"
        Identifier      "nVidia Corporation G70 [GeForce 7300 GT]"
        Driver          "nvidia"
        Busid           "PCI:4:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection
```

Your second one, the one that works, is just as scant, save the BusID, so maybe that has nothing to do with it.  You realize there's no BusID with your non-working xorg.conf, eh?  

It seems that you're more experienced at this than I am, but I thought I'd just throw this in to see if it helped.

Also, perhaps you should give xorg.conf a few more "modes" to play with, instead of ONLY ONE.

---

### Post by dilipm on 2007-05-12
no use ......I get the same black screen as soon i install...the latest drivers also....any more suggestions guys pleasee I even made the changes to the xorg.conf file...Again I changed back to the old xorg.conf file....
I

---

### Post by dilipm on 2007-05-25
Alrite guys....I am fed up with this, I think there is a bug with some nvidia cards...anyway I hope somebody gives me a solution or if it is a bug ubuntu has a new update. I will be trying this for another week then will be changing to another distro.

---

### Post by dilipm on 2007-06-06
Alrite brothers...these are thr most recent logs I am posting here after installing the nvidia drivers..I hope somebody can shed new light here

this is the nvidia installer log

[http://paste.ubuntu-nl.org/24516/](http://paste.ubuntu-nl.org/24516/)

this is the nvidia bug report log

[http://paste.ubuntu-nl.org/24517/](http://paste.ubuntu-nl.org/24517/)

and my current xorg.conf file

[http://paste.ubuntu-nl.org/24518/](http://paste.ubuntu-nl.org/24518/)

Finally my last 2 xorg.conf log files

this is the xorg.0.log

[http://paste.ubuntu-nl.org/24519/](http://paste.ubuntu-nl.org/24519/)


this is the Xorg.0.log.old

[http://paste.ubuntu-nl.org/24520/](http://paste.ubuntu-nl.org/24520/)

Plesae understand that in the xorg.conf file....u will see "nv" instead of "nvidia", I had to change it back to nv only to log on in ubuntu...But when its "nvidia" its black screen again...And the ohter change I made was added the line
Option "UseDisplayDevice" "DFP-0"
and changed the default depth to 24...thats it ...

WEll I hope this helps

---

### Post by dilipm on 2007-06-07
Alrite I made a mistake the nvidia bug report generated was after I changed back to open source drivers i.e after I changed nvidia to nv. So what I did was installed the nvidia drivers again and after the black screen I did the nvidia bug report....these are the actual new log links...I hope it helps

installer log file

[http://paste.ubuntu-nl.org/24530/](http://paste.ubuntu-nl.org/24530/)

bug report

[http://paste.ubuntu-nl.org/24531/](http://paste.ubuntu-nl.org/24531/)

and I think this is the xorg.conf file after the black screen

[http://paste.ubuntu-nl.org/24532/](http://paste.ubuntu-nl.org/24532/)


I hope this would help....thank you

---

### Post by dilipm on 2007-06-07
Anybody even checking this thread........hello moderator/s....I am the only one updating my own post.....anyway...please check it out nd help...

---

### Post by testube_babies on 2007-06-07
Hey there, I went through a similar (if not the same) problem with my Alienware laptop a while back, in which strange color blobs took over the screen whenever I enabled the nvidia driver.  Turns out, the 1680x1050 screens in these particular models don't always get detected correctly.   Here's how I got mine to work, and hopefully it will work with yours, too:

1)  In Section "Monitor" of xorg.conf, change the Horizsync and Vertrefresh numbers to a wide range, eg 20-100 for both.

2)  In Section "Device" insert Option "UseEDIDFreqs" "False" to override the faulty monitor detection.

3)  Enable the nvidia driver and cross your fingers.

If this doesn't work, I highly recommend posting your problem at the [nvnews forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"), where there are a number of experienced users (and at least one nVidia employee who works on the linux driver) who can help you.

---

### Post by dilipm on 2007-06-07
> **testube_babies said:**
> Hey there, I went through a similar (if not the same) problem with my Alienware laptop a while back, in which strange color blobs took over the screen whenever I enabled the nvidia driver.  Turns out, the 1680x1050 screen in these particular models don't always get detected correctly.   Here's how I got mine to work, and hopefully it will work with yours, too:

1)  In Section "Monitor" of xorg.conf, change the Horizsync and Vertrefresh numbers to a wide range, eg 20-100 for both.

2)  In Section "Device" insert Option "UseEDIDFreqs" "False" to override the faulty monitor detection.

3)  Enable the nvidia driver and cross your fingers.

If this doesn't work, I highly recommend posting your problem at the [nvnews forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"), where there are a number of experienced users (and at least one nVidia employee who works on the linux driver) who can help you.

I dont believe it.......u r a star....ur solution....has solved it....man man man .....where were u all these days   mate.....probably being created in a test tube....haha...well man u r the top man....U know what as a matter of fact i have been posting the same problem in nvnews.net....I dont want ot tell them the solution yet...lemme see what they come up with...unless they check here and post the answer...Anyway ..I posted this problem in many forums...I will redirect them here to give u all the credit...Thanks a lot ...I actually had a feeling it was some tweaking to do in the xorg.conf...file....Well thanx again....

---

### Post by testube_babies on 2007-06-07
Sorry I didn't see your thread earlier.  This problem plagued me for months.  Glad I could help.

...and I believe it was netllama at nvnews who solved the problem for me :D

---

### Post by NewspeakIsUngood on 2007-09-14
I had the same issue, after about 4 hours of banging my head against the wall this fixed it.

I need to apt-get you a beer some time, thanks.

---

