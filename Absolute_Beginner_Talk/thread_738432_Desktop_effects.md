---
title: "Desktop effects"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Roadrunner32000 on 2008-03-28
I've been playing around with Ubuntu for a couple of weeks and come across a problem that I can't find the answer to . I don't have a graphics card , just built in intel graphics chip . I don't appear to be able to enable desktop effects . Do I need to download any extra drivers ? I really don't know what to do as all my 'limited' experience is with windows .

Please help a clueless wonder :)

Many thanks

---

### Post by jan quark on 2008-03-28
when you go to
system > preferences > appearance > visual effects > normal or extra

are you getting an error message?

---

### Post by TeoBigusGeekus on 2008-03-28
Have you enabled the restricted drivers?
Go to System->Administration->Restricted Drivers Manager
and enable the restricted driver.

---

### Post by Roadrunner32000 on 2008-03-28
> **jan quark said:**
> when you go to
system > preferences > appearance > visual effects > normal or extra

are you getting an error message?

Wow! that was quick . Tried normal , says desktop effects could not be enabled :confused:

Teobigusgeekus , system says my hardware does not require any restricted drivers . mmm.

---

### Post by icechen1 on 2008-03-28
What Intel graphic card do you have?
You can do lspci | grep VGA in a terminal to know it,
Post also the output of glxinfo in a terminal.

---

### Post by Roadrunner32000 on 2008-03-28
> **icechen1 said:**
> What Intel graphic card do you have?
You can do lspci | grep VGA in a terminal to know it,
Post also the output of glxinfo in a terminal.

Ooh , and what's that in english . In windoze I'd look in device manager - I haven't a clue what this means

Sorry!  :(

got this in terminal :

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by icechen1 on 2008-03-28
> **Roadrunner32000 said:**
> Ooh , and what's that in english . In windoze I'd look in device manager - I haven't a clue what this means

Sorry!  :(

Open Applications > Terminal
Inside the window enter > glxinfo | grep "direct rendering"
then copy and paste the output here.
Then in the terminal enter > lspci | grep VGA
and paste the output here.The first comand says if you got 3D rendering enabled or not.The second command get your video card infomation.

---

### Post by lswest on 2008-03-28
it means open a terminal from applications-->accessories-->terminal

and type in ```
lspci|grep VGA
``` (remember, linux is case-sensitive) and hit enter, then copy and paste the output into a post.

---

### Post by Roadrunner32000 on 2008-03-28
> **icechen1 said:**
> Open Applications > Terminal
Inside the window enter 
then copy and paste the output here.
Then in the terminal enter 
and paste the output here.The first comand says if you got 3D rendering enabled or not.The second command get your video card infomation.

 glxinfo | grep "direct rendering" 
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter


Thanks for your patience !!

---

### Post by icechen1 on 2008-03-28
According to [http://www.linuxquestions.org/questions/ubuntu-63/xglcompiz-for-non-nvidia-ati-cards-475919/](http://www.linuxquestions.org/questions/ubuntu-63/xglcompiz-for-non-nvidia-ati-cards-475919/) ,you need Xgl to use desktop effect with that card.I am not sure how to set up Xgl with this card but [This]("http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl") might help.

---

### Post by Roadrunner32000 on 2008-03-28
> **icechen1 said:**
> According to [http://www.linuxquestions.org/questions/ubuntu-63/xglcompiz-for-non-nvidia-ati-cards-475919/](http://www.linuxquestions.org/questions/ubuntu-63/xglcompiz-for-non-nvidia-ati-cards-475919/) ,you need Xgl to use desktop effect with that card.I am not sure how to set up Xgl with this card but [This]("http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl") might help.

problem solved ! thanks all for your help . Proved my thought that a graphics card is needed though . The motherboard has an AGP slot so I'll either have to get some more RAM or find a reasonably priced graphics card

Thanks once again     :)

---

