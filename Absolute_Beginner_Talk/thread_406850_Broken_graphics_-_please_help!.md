---
title: "Broken graphics - please help!?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-04-11
Just as I thought I was getting the hang of Ubuntu...  :( 

Something seems to have gone badly wrong with the graphics on my machine.  I first noticed it this afternoon when I tried to run Blender, a graphics program.  It HAD been working fine, but now it just crashes the computer right back to the login screen.  

Then I noticed that as soon as my screensaver came on, exactly the same thing was happening - another crash back to the login screen.

EDIT:  After some looking around, I found I have something called NVIDIA X Server Settings.  When I start clicking my way through the info options on that program, I get the crash again when I come to one called 'OpenGL/GLX information'.  I've no idea what this means, but perhaps it will help someone to diagnose my problem - I'm desperate, and will post any other logs etc that you need (if you tell me where to find them!)

BTW, this is on a laptop, if that helps.

I tried to change the screensaver, but as soon as I click 'Screensaver' in the menu, boom - the same crash back to login.

I don't even know where to start looking for how to fix this, or if it's even fixable.  I'd be really grateful if anyone can suggest a solution.

Many thanks!

---

### Post by ayenack on 2007-04-11
Have you installed Specific Nvidia drivers from Nvidia home page or any other Repo's?

Also what Nvidia model of card have you got? Are the right drivers installed?

Best of luck. ayenack.

---

### Post by whitefort on 2007-04-11
Thanks for replying, ayenack.

I bought the laptop with Ubuntu (and Nvidia drivers etc) pre-installed, so I haven't done anything with drivers - and don't yet know how to!

Everything has been working fine, and in fact the laptop STILL works fine, except when I try to run Blender, a screensaver, or get info about the "OpenGL/GLX"

oh, after reading some posts, I also tried running something called GLGears (I think?), and that caused the crash too.

I'm wondering if this is that thing I've heard of where you have to reinstall the Nvidia stuff - I'm scared!  I really don't want to totally trash my laptop.  I'm also wondering if it's a different process installing the drivers on a widescreen laptop, than from a normal desktop.

The card is the Geforce Go 7300

---

### Post by ayenack on 2007-04-11
You may want to print this off it's quite long.

GLGears is just a screen saver which uses open GL as far as I know. There's a really easy way to install new drivers for your laptop graphic card it's called Automatix. It's a program that automates the download and install of different drivers, codecs etc.

There can be some serious problems with re-installing graphics drivers if it goes wrong you can end up with a machine that will only boot to the command line which sounds like it may be a problem for you.


So if you decide to do what I'm about to suggest please please download an iso image of ubuntu and burn it to a CD so you can install a fresh Ubuntu system if all else fails. Also burn any important files to a CD.

I'm not 100% sure this will solve your problem, what it will do is install new drivers for your Nvidia Graphics card so if the problem is with the drivers (which I'm guessing it is) this should solve it.

If you don't feel confident about this don't do it, it might not work and you might not even be able to get on-line to ask for help.

All these instructions were ripped from [http://www.ubuntuguide.org](http://www.ubuntuguide.org) it's a Wiki page you may wish to take a look at it.

Here's how to install Automatix.

 How to install Automatix2 on Ubuntu, Kubuntu, and Xubuntu

    * Read #General Notes
    * Automatix2 is Automatix written in python with a more user friendly interface and better overall design for automating the installation of the most commonly requested applications in Ubuntu/Kubuntu/Xubuntu linux.
    * Note: Before installing, please note that certain codecs it provides may be prohibited in certain countries. You are responsible for ensuring those laws are not broken.
    * Note: Please note that if you are using Xubuntu where it says "sudo gedit /etc/apt/sources.list" please replace with "gksudo mousepad /etc/apt/sources.list". 

type this into a terminal. 
sudo gedit /etc/apt/sources.list 

    * Add the following lines at the end of file 

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

    * NOTE: Kubuntu/Xubuntu users will need to uncomment (remove the # before the word "deb") all the additional sources as well as add the automatix repository.
    * Now save and close /etc/apt/sources.list and run the following commands from terminal (one by one, hitting enter after each step) 

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv CC919A31E23C5FC3
gpg --export --armor CC919A31E23C5FC3 | sudo apt-key add -

    * Update APT 

sudo aptitude update

    * Run the following commands to install Automatix2 

sudo aptitude install automatix2


    * Automatix2 can be started from the the Menu 

Menu -> System -> Automatix

    * Automatix2 can be run from terminal by typing the folowing 

automatix2

Once you've done this Applications>SystemTools>Automatix it will ask you for a password this should be the password you log on with. After that click on drivers and click on Nvidia. Any questions put a post up.

Best of luck. ayenack.

---

### Post by ayenack on 2007-04-11
Let me know how it goes.

Best of luck. ayenack.

---

### Post by compiledkernel on 2007-04-11
For future support of Automatix please refer here - [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

That be said, Refer to official documentation for nvidia related diagnosis. 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting)

---

### Post by ayenack on 2007-04-11
If you've got some I'll drink it. I've only had 18. :D

---

### Post by jem7v on 2007-04-11
Whenever there's a kernel or restricted modules update (such as was released today) you'll have to reinstall your NVidia drivers.  It's not as scary or complicated as it seems.

Here's the guide **I** would suggest using.  If you use Automatix to install your drivers you aren't really getting a feel for what's going on, because it's basically just a fancy Wizard for distancing yourself from the inner workings of your computer (and occasionally saving some time). For the learning experience, I'd definitely try doing it without Automatix first, and save Automatix for later once you know what's actually happening when the drivers are installed!
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

(I say occasionally saving time, because I know that it's actually quicker for me to reinstall my drivers from scratch using the official script from NVidia than it is for me to do it with Envy or Automatix or any of the other automated processes for doing it... I've found in the past that most of them try to give me the wrong version of the driver, and thus often cause more problems than they solved.  But Envy DOES have its uses! Envy is used in "method 4" on the page I linked to.)

---

### Post by whitefort on 2007-04-11
Thanks for the replies, everyone.

I'll definitely be keeping them for future reference, but for now, I've had to resort to drastic measures - my attempt at 'fixing' things made such a total mess of everything that I couldn't get Ubuntu to start at all.  I'm guessing that it's because I'm on a laptop that the normal instructions didn't work - the recent update installed on my desktop machine with no problems.

Now this is the bit where you all have to try not to laugh (or cry).  First thing in the morning I'm supposed to be using that laptop to give a demo of how amazingly cool Ubuntu is!!  It wasn't going to look too good if I went along and said, 'Yeah, it's really cool, but I can't show you, because the latest update broke my laptop, but no, it's really cool, HONEST!'

Anyway, since I know how good I am at breaking software, the first thing I did when I bought the laptop was to install a program called Mondo and do a full disaster recovery backup on to a bootable DVD.

So, I've just spent the last 30 minutes drinking coffee while the machine was restoring itself to 'just out of the shop' condition.  Every thing is perfect again, and all I have to do is set up my email stuff, my neat dynamic wallpaper, and a few other things.

It's telling me that I need to install 46 updates, but, er, I don't think I'll be doing updates on that machine any more.

Ubuntu IS cool, and I love it... but really, it's not nice when updates wreck your machine!

Sorry to ramble on for so long (if you're still reading) - and thanks for all the help. This forum is one of the BEST things about Ubuntu!

---

### Post by ayenack on 2007-04-11
Jem is correct. If you feel confident that this is the way to go it will bring you a far greater understanding of the command line and its uses which you really should learn if you want to get the best from any GNU Linux OS.

Do a bit of research, make sure you know where all your drivers are (use whereis at the command line) and you will be on the road to being a proficient Ubuntu user.

I have to say that I have never found Automatix to give me the wrong drivers. As far as I know the Nvidia drivers are unified.

Best of luck. ayenack.

I did not realise that Automatix was to be supported only on the official site. From now on I will direct people to the Automatix site.

Well it's 23:17 here so you got it done just in time mate you'll get a decent nights sleep.

---

### Post by jem7v on 2007-04-11
> **ayenack said:**
> I have to say that I have never found Automatix to give me the wrong drivers. As far as I know the Nvidia drivers are unified.

Sort of. There are two main branches of the driver: the current driver, and the legacy driver for older chipsets. Furthermore, there are different releases of each driver... i.e., some of the more recent ones seem to Maybe have moved some of the supported chipsets from the modern to the legacy driver, or something like that.  I'm running a slightly obscure chipset, so any driver wizard I've tried so far has given me the wrong one.

But if you're running a more common NVidia card, I imagine they'd work well.

---

### Post by adamz70 on 2007-04-13
Hey guys, I've encountered the same thing (as have others on the forum), including frequent and sudden X crashes upon loading screensavers, clicking 'OpenGL/GLX info' in the nVIDIA settings, etc. It also happens when I type "glxinfo | grep rendering" to detect 3d acceleration.

I thought it had something to do with my unsuccessful efforts to install Compiz (that resembled a blind man stuck in a revolving door), but you're suggesting it's the recent kernel/restricted modules update??

I will try to reinstall nVIDEO drivers as you suggested (manually - I had an enourmous disaster using Automatix/Envy), and in the meantime, here's another thread on the same issue:

[http://ubuntuforums.org/showthread.php?p=2424694]("http://ubuntuforums.org/showthread.php?p=2424694")

It links to this interesting, alternative solution:

[http://ubuntuforums.org/showpost.php?p=2413073&postcount=2]("http://ubuntuforums.org/showpost.php?p=2413073&postcount=2")

And I thought updates were supposed to be tested and intended to FIX your system!!  Grr.

---

