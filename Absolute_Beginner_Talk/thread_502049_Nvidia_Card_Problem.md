---
title: "Nvidia Card Problem"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by gamingx2005 on 2007-07-16
Hello Guys,
           I am new here and I just finished installing Ubuntu Feisty Fawn 7.0.4. I am trying out Linux for the first time. After installing Ubuntu I tried to install the Nvidia Geforce FX 5200 AGP card that I have. I read the instructions for doing it from the book "Ubuntu Unleashed" by Keir Thomas published by Appress. According to him I downloaded the Nvidia GLX and from the terminal typed [COLOR="Red"]sudo nvidia-glx-config enable[/COLOR]. I rebooted the system and on rebooting Ubuntu GUI is not starting up and I am starting up in terminal mode. I get an error saying that the X server could not be started and some other things I couldnt understand. Can someone please help me with this?

---

### Post by techno-mole on 2007-07-16
the nvidia drivers are already included in ubuntu, at least drivers that will run nvidia cards, so im not sure why you had to install the graphics card, if you mean the latest drivers then you could have either installed envy, which pretty much downloads and installs the latest nvidia drivers then configures it for you.
or you could just open a terminal and type sudo aptitude install nvidia-glx-new.
but being as your starting up in terminal mode then you will probably need to re-configure your x server.
sudo dpkg-reconfigure -phigh xserver-xorg this should enable you to sort out your problem.
i would recommend using envy for nvidia drivers, i use it and ive had no problems with it.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) this is the home page for envy.
cheers

---

