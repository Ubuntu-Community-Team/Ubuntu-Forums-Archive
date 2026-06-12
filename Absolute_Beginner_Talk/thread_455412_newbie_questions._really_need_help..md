---
title: "newbie questions. really need help."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by gugutz on 2007-05-26
i was a windows user, then i decided to try linux, so i installed ubuntu about 1 week ago.

but as a windows user several years, i´m really lost using linux now. so i´ve come to ask the community a few questions that would really, really help me:

1 - I use a 3dfx Voodoo 4 card. The maximum resolution that i´m getting is 800x600, and in the video settings there not even the option to change to 1024x768 or above. I´m thinking that maybe i have to configure my video card. In windows, all you have to do is install the drivers, but in linux i don´t know even where to start. Is there drivers for linux, or do i have to type some command lines, download a package, orsomething else?

2 - Software installation. I understand that in linux, each time you want to install a software, you have to compile it. Is this real? I don´t know how to compile the source of an application. Without the .deb packages, Is it the only way?

3 - A friend told me that by downloading .deb packages, all i had to do is use dpkg -i [name of the package] to install the software package on my Ubuntu, since it uses the Debian core. 
So i downloaded XMMS, because Ubuntu only comes with no support to run mp3 files. I downloaded the XMMS .deb package, and i read on it´s site other stuff that XMMS was dependant. I didn´t give attention and downloaded only the main .deb file, and tried to install it, dpkg said that i couldn´t be installed because it missed some dependencies. 
So i went to download the other stuff, but one thing depends on another, and that another dependes on another one.. The same thing for the Glide and Mesa3d packages that i downloaded trying to get my video card working. In the end, i kind of had to download more than 6 files and gave up.
So i think my question really is: Isn´t there like sort of a "Ultimate Package", or "All-In-One Package", some kind of file that would have all it takes to install an app?

4 - Is there how to use apt-get from the Ubuntu DVD? I heard that it has most of the applications that Synaptic have. I´m interested in trying Berryl and VLC.

I think that´s it, for now.
Thanks to all.
gugutz.

---

### Post by deadgobby on 2007-05-26
Lets install Automatix and get some Invida drivers going, all the restricted codecs as in Mp3 and DVD.  No you do not to install from source. You can edit your Repositories and add the extra tibs bits. Then when you open up your Synaptic Package Mang. You'll see a wealth of programs you can install. Just be clicking on the box and hit install. With Deb packages all you need to say to open with default installer. 

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
[http://ubuntuclips.org/](http://ubuntuclips.org/)
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

GObby

---

### Post by starcraft.man on 2007-05-26
Gobby... if your going to recommend automatix2 so quickly, you should make a clear disclaimer about it. It's _NOT_ in any way an official installer of Ubuntu, and it has caused numerous problems for people (from some reports of destabilizing whole systems after installing it to incredible troubles caused by it at upgrades). I just don't think it should be the first recommendation, certainly not without warning.

Anyway, as to installing software, most of the time its from the repos with apt. Read these two guides [here]("http://www.psychocats.net/ubuntu/installingsoftware#packagemanager") and [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") for more info.

As for the debian, assuming you have a desktop and are not running server, just double click it on desktop and it will install. :)

I don't know how well supported the voodoo cards are, those are old. If nvidia still has drivers, they would be installed via [Envy.]("http://www.albertomilone.com/nvidia_scripts1.html") Its a small script and it works (almost all the time) and doesn't have any ill effects to my knowledge >.>. Use the stable version, and read the small tut at the top, you install it like a deb and then run it from the System Tools menu in Applications, thats it.

---

### Post by gugutz on 2007-05-26
deadgobby, for what i understood, this "Automatrix" is a collection of softwares and drivers?

I saw the page saying what in the Automatrix, but in the Drivers sections, i didn´t see anything about 3dfx.
It will at least make my Ubuntu able to open DVDs and MP3 and movies formats?

And what about my Voodo 4500? Untill i install it properly, i will only get 800x600 resolution and no beryl. :(



starcraft.man, thanks for  the advices about the automatrix and the script for my video card. I don´t have an internet connection, so i´m gonna download it and try it when i get home.


One last question: since i don´t have an internet connectnio and can´t use apt, how do i install beryl? I downloaded all the packages and their dependancias, but it didn´t seem to work. Perhaps is because my video card isn´t set up correctly yet. Anyways, gonna try script and later i´ll post the results. Thanks, you guys.

---

### Post by paparucino on 2007-05-26
> **gugutz said:**
> 
One last question: since i don´t have an internet connectnio and can´t use apt, how do i install beryl? I downloaded all the packages and their dependancias, but it didn´t seem to work. Perhaps is because my video card isn´t set up correctly yet. Anyways, gonna try script and later i´ll post the results. Thanks, you guys.
First time you have an internet connection, go here 
```

http://doc.gwos.org/index.php/EyeCandyFeisty

```
There are two HowTo which will help you.

---

### Post by starcraft.man on 2007-05-26
> **gugutz said:**
> deadgobby, for what i understood, this "Automatrix" is a collection of softwares and drivers?

I saw the page saying what in the Automatrix, but in the Drivers sections, i didn´t see anything about 3dfx.
It will at least make my Ubuntu able to open DVDs and MP3 and movies formats?

And what about my Voodo 4500? Untill i install it properly, i will only get 800x600 resolution and no beryl. :(



starcraft.man, thanks for  the advices about the automatrix and the script for my video card. I don´t have an internet connection, so i´m gonna download it and try it when i get home.


One last question: since i don´t have an internet connectnio and can´t use apt, how do i install beryl? I downloaded all the packages and their dependancias, but it didn´t seem to work. Perhaps is because my video card isn´t set up correctly yet. Anyways, gonna try script and later i´ll post the results. Thanks, you guys.

The Envy script requires an internet connection, you still have to download the driver. Why don't you have a connection? Ubuntu requires an internet connection for daily use, its really difficult to run Ubuntu without it (the apt system is entirely internet based).

So what is the problem with internet, we will fix it if you tell us the problem, then you can use envy to install.

---

### Post by gugutz on 2007-05-26
hey guys, i brought my pc to my mother's house, so i could install some things. but now i can't install the device3dfx-source trhough apt, neither beryl.

envy needs a lot of other dependancies files, so i could now install it either.

Right now, i would give up everything else just to be able to change my video resolution.

Anyone have a 3dfx card that could teach me how to get it working.

---

### Post by deadgobby on 2007-05-27
here is link to help you get beryl installed. 
[http://ubuntuforums.org/showthread.php?t=263851&highlight=beril](http://ubuntuforums.org/showthread.php?t=263851&highlight=beril)

---

### Post by MrChips on 2007-05-27
Hey I have a 3dfx voodoo 3000, 
I had the same problem with 64studio (another distro) and I was stuck in 640x480 :P .  But both Ubuntu and 64studio are Debian so what worked for me in 64, it may work here too.  

If you just want to get out of 800x600 res bring up the terminal and type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

While in gnome (I assume) this will bring up a GUI, select the resolutions you want in the screen that follows and restart X or reboot.  You may have to reboot and then select your resolution once X starts again.

---

