---
title: "Absolute Beginner Indeed.."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by zombrax on 2007-06-19
Hey guys!

ok, i'm an absolute beginner to this. Installed the 7.04 server edn on my laptop and everything goes well. It reboots and asks me for login. I do remember the login username and password i created.

1) but how do i login as root? whats the password for this?

2) how do i start x-windows?

where can i find a manual or a good book that would take me through steps that i need to learn more about this o/s and things it can do?

thanks a lot fellas...

an absolute beginner whos in need of desperate help :)

---

### Post by FleetAdmiral74 on 2007-06-19
When booting up, choose the ubuntu recovery mode and it will put you in root automatically. Otherwise just use sudo or gksudo in front of your commands.

---

### Post by jdelphin on 2007-06-19
well usualy to start x you just put the command startx and voila but the ubuntu server i dont actually know if it has that .
for root do su and put your orignal passwd 
for a manual well for the server dont know if you find one tell me i would like to install it myself 

"note these indication work on the client and assumes the server shares some of the characteristic"
peace

---

### Post by Tomosaur on 2007-06-19
Root account is disabled in Ubuntu by default, but your own username has the ability to temporarily gain root priveleges (it is generally considered a bad idea to run as root for long periods of time, which is why it's disabled, among other reasons). You can manually re-enable root, but there's no real need to.

To perform a task with temporary root privileges, prefix your command with 'sudo'. For example:

```

sudo touch /etc/myfile.txt

```

This will create a file in the 'etc' directory called 'myfile.txt'. The 'etc' directory needs root privileges to be written to. Note that when you use 'sudo', you will be asked for your password. This is the same password you use to log in, and you will not see the password being typed, so be sure to spell it correctly.

Now, as for x-windows, you've installed the server edition, which doesn't come with a GUI (since servers are normally just set up once and then left to do their job, the GUI isn't really needed). If you don't actually intend to use the machine as a server, then just type the following command:

```

sudo aptitude install ubuntu-desktop

```

This will download and automaically install all the necessary stuff to get a GUI up and running. Once the installation is completed (and it may take a while, it downloads a lot of stuff), simply type 'sudo reboot' and your machine should restart. When it comes back, your GUI should be fully functioning :)

Welcome to the community!

---

### Post by aeiah on 2007-06-19
there isnt really a need to login as root. when you want to issue a command as root, you use the command 'sudo' before the command you want. the password is the same as your initial login password. sudo basically stands for 'super user do', and it grants you super user / root privilages for that command. so, if you wanted to make a folder named 'foo' to mount a partition on, you'd need root privilages, so you'd type:

```
sudo mkdir /media/foo
```

and if you wanted to install, say, fluxbox via the apt-get program you'd type

```
sudo apt-get intall xserver-xorg xfonts-base fluxbox xterm
```

or if you wanted the gnome environment you'd do

```
sudo apt-get install ubuntu-desktop
```

in ubuntu server, you dont get an x window environment by default, you need to install one separately. depending on the spec of your laptop and how often you'll be using the gui, you have a number of options to choose from. ive mentioned fluxbox and gnome. fluxbox is one of the lighter ones and provides a really quick gui on even rather old systems. gnome is the default ubuntu desktop environment. you've also got kde and xfce, amongst others. there are tutorials on this forum that can guide you through installing a desktop environment on top of the server edition. the server edition is basically the same as the ubuntu desktop version, except it doesnt have an x windows environment.

---

### Post by Jimmyfj on 2007-06-19
Having installed Ubuntu 7.04 server you have not yet installed the GUI - The install of the GUI you'll have to do from aptitude - Install xserver, gnome or kde from within aptitude too

---

### Post by drivel on 2007-06-19
> **zombrax said:**
> Hey guys!

ok, i'm an absolute beginner to this. Installed the 7.04 server edn on my laptop and everything goes well. It reboots and asks me for login. I do remember the login username and password i created.

1) but how do i login as root? whats the password for this?

2) how do i start x-windows?

where can i find a manual or a good book that would take me through steps that i need to learn more about this o/s and things it can do?

thanks a lot fellas...

an absolute beginner whos in need of desperate help :)

Oh,my friend~Ubuntu do not advise you login as root,you can use 'sudo' instead.
I think Ubuntu will run X automaticly and if you wanna run it can use command 'startx'
Have fun with Ubuntu!:popcorn:

---

### Post by drivel on 2007-06-19
> **Jimmyfj said:**
> Having installed Ubuntu 7.04 server you have not yet installed the GUI - The install of the GUI you'll have to do from aptitude - Install xserver, gnome or kde from within aptitude too

'sudo apt-get install ubuntu-desktop' is advised for him.

---

### Post by zombrax on 2007-06-19
err thanks so much for the fast feedback however, when i try to install the package, it tries and connect to the internet and shows me the url but it cannot connect.

i have both wireless and etthernet on my laptop and when it first asked to setup network, i did it through wireless but i dont think its set up properly. how can i manually configure the ethernet, give it an ip address etc?

pse help :) thanks once again.

---

### Post by zombrax on 2007-06-19
it says "could not resolve "security.ubuntu.com'" 

so i presume the dns is not setup properly etc?

---

### Post by andrewheiss on 2007-06-19
Newbie here!

I just installed Feisty Server to get a LAMP server set up and it went smoothly and quick and great. However, this is my first foray into Linux, so I wanted the GUI. I did the sudo apt-get install ubuntu-desktop and it worked just fine - no errors. 

However, after restarting the computer to boot into the desktop mode, I can't get anything to show on my monitor, like the video card never installed. The sound works--I even logged in blindly, but couldn't do anything.

I then used an old 6.06 CD to boot as a live CD to see if my video card is supported (it's integrated in an old Compaq smallform box), and it worked just fine.

How can I get the GUI desktop to work? How can I leave the blank screen GUI and get to the shell to fix it?

Thanks!

---

### Post by zombrax on 2007-06-19
oi!! stop hijacking my thread fool :)

---

### Post by andrewheiss on 2007-06-19
Oops... thought I was making a new topic after looking at your thread :o

---

### Post by Josey on 2007-06-19
> **zombrax said:**
> it says "could not resolve "security.ubuntu.com'" 

so i presume the dns is not setup properly etc?

If you get your ip automatically (dhcp not static) then internet should work when plugged in with ethernet cable.

Are you hooked to a router or modem or what?

---

### Post by zombrax on 2007-06-19
all good.. after a reboot, it seemed to find the router and its currently downloading happily all the updates and required files :)

---

### Post by zombrax on 2007-06-19
argh stuck again..

downloaded and installed all the packages.. started x and all i get is a black screen. help!! what do i do?? obviously its having issues with it.. what can i do to fix it? what commands do i need to use? what am i doing wrong?

can someone pse pse pse help me?

thanks!

---

### Post by zombrax on 2007-06-20
bump! sorry but i'm totally stuck..

when the laptop starts, i can see the ubuntu flash screen, its got the progress bar and it goes to the end and then i get a black screen...

please help.. thanks so much :)

---

### Post by bvanpelt on 2007-06-20
I too wanted X; I finally ended up just installing the desktop version. It comes with the X infrastructure in place, and made my life much easier than trying to figure out what packages were needed for X.

---

### Post by Chayak on 2007-06-20
Just out of curiosity... why did you install the server disk on a laptop?  There is no default GUI on that save the terminal.  You'd be better off installing the regular desktop version and then installing the server packages you need.  You don't really need the server kernel anyway as the only difference is in some timing and server hardware compatability that you'll never see the benifits of unless you're running a high load server anyway.

I've had issues in the past on trying to put ubuntu-desktop on a server install.  It's nothing that can't be fixed but I manage quite a few machines and don't have the time to waste on troubleshooting something that should have worked in the first place.  It saves time just to install the desktop version and then just add the server kernel and anything else you need

---

