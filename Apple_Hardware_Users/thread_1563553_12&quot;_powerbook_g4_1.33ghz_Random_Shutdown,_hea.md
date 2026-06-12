---
title: "12&quot; powerbook g4 1.33ghz Random Shutdown, heat, keyboard issues,  new linux user"
date: 2010-08-29
forum: Apple Hardware Users
---

### Post by LinNub on 2010-08-29
Hello all, 

I'm running Ubuntu 10.04 on a 12" Powerbook G4 1.33ghz with 1.25 gb ram. 
I have the Go 5500 video card

Couple issues that I have questions about that I didn't find on my forum searches. I am very new to Linux, tried Ubuntu on a sony vaio in 07 with little success, so i'm trying it again on this machine. Please spell out any steps you might assume I already know--because I don't.


1. My laptop randomly shut down today-- is this because of poor cpu power management? The fan has been whirring out of control, and I've read that powerpc chips have heat issues with ubuntu--but haven't figured out how to fix it. 

2. Getting ghosting in the gui whenever i move a window--video settings? do i need to fix something here? Also at start up, I get lots of visual noise (streaks, and pixel junk) and the screen blanks before showing the login box. 

3. Keyboard, I followed keyboard instructions and changed the keyboard to a mac laptop keyboard, but nothing has changed--did i miss another step here?

4. I want to use this machine for media, netflix, anime, dvd's and social media-- Is there something I can do to enable netflix and flash?

5. what programs should i install/update that are needed for a smooth operating system? 

SHOULD I EVEN BE USING UBUNTU ON A POWERPC?

Please help!  

Thank you very much!

---

### Post by linuxopjemac on 2010-08-29
Your machine (PowerBook G4 12' 1.33 GHz) gets overheated. This can be dangerous. Use it at your own risk.

Install the nouveau driver:
```
sudo apt-get install xserver-xorg-video-nouveau
```

Then install the right xorg.conf file:
```
wget http://mac.linux.be/files/xorg/powerbook4.txt
sudo mv powerbook4.txt /etc/X11/xorg.conf

```

---

### Post by LinNub on 2010-08-29
So should I give up on linux with this machine?

I'd rather not go back to osx, but I don't want my laptop to die a slow death.

---

### Post by linuxopjemac on 2010-08-29
I said that you can use Ubuntu or whatever Linux on that machine, but that you have to be careful. Check the temperature of the machine
lm-sensors will be your friend.
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)
```
sudo apt-get install lm-sensors
```

---

### Post by dngfng on 2010-08-30
SwedishWings has programmed a nice little Fan Control Daemon - give that one a go and let him know how its working for you.

[http://ubuntuforums.org/member.php?u=690076](http://ubuntuforums.org/member.php?u=690076)

---

