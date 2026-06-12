---
title: "New to Ubuntu... with an x server problem"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by darien42 on 2007-10-12
Hey everyone,
I am compeltely new to linux (having finally had it with Windows) and when setting up my computer yesterday, I ran into a problem.

I tried to activate the cool desktop features for Ubuntu so that I can change the themes and what not and it said that I had to download an Nvidia Accelerated Graphics Package.... which I did. It installed properly but when I went to reboot, my computer would refuse to get past the flash screen. I thought maybe it was some sort of fluke accident so I did a re-install of Ubuntu, got all the updates and everything was working fine so I decided to the Nvidia patch again and behold, the same problem.

So here is what is going on. When I try to boot, I get to the splash screen and then it starts showing up as text and then I get a couple of nasty looking error messages that explain what the confliction is. It is saying that it failed to start the X server on the account that there is an API mismatch. The Nvidia Kernal is running 1.09755 while the X sever is running 1.0-9631 and that they have to be identical.

I have tried to run the X configure process but that doesnt work... 

Is there anything I can do to get my poor computer to run? I've heard about putting Ubuntu into "Graphics Safe Mode"... but I dont know how to do that.... (I told you I'm new lol!) :(

Help me Obi-Wan Kenobi... you're my only hope... (sorry, had to throw it in)

My system specs are as followed:
Core 2 Duo E6600 @ 2.7Ghz
2GB OCZ 4-4-4-12 @ 800Mhz
EVGA GeForce 8800 GTX
EVGA 680i SLI MOBO (version A1)

If there is any additional information you need, please let me know.
Thanks,

Darien42

---

### Post by trucker33377 on 2007-10-12
dont know if i can help but i had about the same thing happening to me i did away with fiesty and installed gutsy and i love it no problems so far but i mainly edit photos and print them. it did automatically  ask for my video driver and install went smooth.

---

### Post by Hospadar on 2007-10-12
Did you download the Nvidia drivers from the website?  If that's the case (or even if it's not maybe) you just have some configuration issues you need to sort out.  when you boot up, and get that blue error screen, hit Ctrl-Alt-F1, this will take you to a text terminal (ctrl-alt-F# let's you switch between different virtual sessions, the gui when it's running is on ctrl-alt-F7)

login to this text terminal with your usual username and password and use the command ```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb
``` to download the envy script, this is a program to set up graphics drivers.

now use ```
sudo dpkg -i envy_0.9.7-0ubuntu12_all.deb
``` to install the package.

next, let's run envy with ```
sudo envy -t
```

You'll want to first choose the "uninstall" and "clean" nvidia driver options.  then choose the "install nvidia driver" option.

Now if you arn't already there, you can use Ctrl-atl-F7 to get back to the gui, or just restart.

---

### Post by darien42 on 2007-10-12
I was able to get the download for Envy done but when I went to run the application, it came back saying that there are dependency problems and it couldnt install anything. 

The applications that are not installed are:
Build_Essential
XServer-Xorg-Dev
Module-Assistant
Fakeroot
dh-make
debhelper
dpkg-dev
dpatch

Are these programs I will have to obtain before I can install Envy?

If so, where can I get them?

Thanks for the help, 

Darien42

---

### Post by om1 on 2007-10-12
try this
```
sudo apt-get install XXX
```
where XXX is put the name of the package you need to install
example 
```
sudo apt-get install XServer-Xorg-Dev
```

---

### Post by darien42 on 2007-10-12
Got it! 

Thanks for everybodys help. It is greatly appreciated. 

Darien42

---

