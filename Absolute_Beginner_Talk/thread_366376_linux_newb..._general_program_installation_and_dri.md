---
title: "linux newb... general program installation and drivers"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by cregan89 on 2007-02-20
Ihave been using windows my whole life (only 16) and I actually work part time at bestbuy in the computer tech department so if people are wondering why linux is not succesful, it's because people with A+ certification and years of technical experience can't figure out how to install their graphics card drivers. Can somebody please tell me why you have to use the terminal to do EVERYTHING in linux? What is the point of having a GUI if you use the terminal for everything anyway? The average consumer will NEVER move to an operating system in which you have to use a console and remember commands and learn syntax for everyday computer usage so if the programmers that design linux ever want linux to be on more than a small percentage of people's computers, the terminal will have to be removed, not actually removed but obsolete. I know I sound negative but I'm in a bad mood because I can't find an operating system that isn't a piece of crap, vista is a joke so I decided to switch to linux but you litterally need a linux veteran sitting right beside you or you have to have a degree in computer engineering to use it. Anyway, I'm not going back to vista so I might as well learn how to use ubuntu. I have an ATI X800 graphics card, what driver should I use, where should I get it, and most importantly how do I install it? I think I installed the driver from ati.com but I don't know how to configure anything and my monitor is still stuck on 1024x768 even though it can do up to 1600x1200. I also want to install beryl. I should point out that I'm using ubuntu 6.06 because 6.10 won't boot up on my computer. I know there is lots of information in various forums but it never works the way it should work. Another thing I want to do, but I'll wait till I have my driver's and beryl properly installed, is install a virtual computer program with windows so I can play my games and use photoshop and stuff. Thanks in advance and sorry for sounding negative but I'm just really annoyed, hopefully somebody will be able to change my mind about linux!:)

---

### Post by Bachstelze on 2007-02-20
Before we go further, let me ask you a question : do you really want help or did you just come here to complain ? If you really do, please ask your question clearly without all the ranting.

---

### Post by halitech on 2007-02-20
I'm not sure why you think you need to do everythign in the console cause I seldom open the CLI anymore. I will for some things but most of the work I do with GUI apps. 

Personally I've been using Linux (Ubuntu mostly) for a year now and other then the "experts" on this site, I've done everything by myself. I agree, vista is a joke and kudos on wanting to learn more about linux and not wanting to go back to windows.

As far as your video card, I'm not sure. I have an older Raden 7200 that doesn't work with the newer drivers but from what I can find by doing a search (google and the search bar here are your best friends) this link should help.

[http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800]("http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800")

---

### Post by Maestro23 on 2007-02-20
Step away from the keyboard and take a few breaths.  In linux, you must walk before you can run. :)  Below is a few links for you to read/bookmark:

Commands and File Structure:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

How to Install in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Restricted Formats(mp3 and DVD): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

*For you ATI card you have some options:

1. Use the following HOW-TO: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
                                            [http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800](http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800)

2. Use the Envy script that will do everything for you: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

If you really want help, this is one of the best linux communities I have come across.  Post your questions or search for answers on your own.  Something you don't understand, ask.

Good luck.

---

### Post by sloggerkhan on 2007-02-20
You didn't really display any useful information.

You may be able to run 6.10 with different boot parameter on the CD, or you could install from the alt CD.

But if you want to use 6.06, try automatix. It has a GUI. Since you don't want to learn about the command line because you think you shouldn't have to, it's probably better for you.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by cregan89 on 2007-02-20
Firstly I do want to learn linux, I've had enough of windows and linux is extremely customizable so I am hoping that I can make the operating system work the way I want it to. Halitech, I would love to learn how to do most things through the GUI, I didn't think it was possible, are you saying that any program can be installed by using the mouse instead of typing a bunch of stuff I have no idea what it means? I just don't understand why they would make it so complicated, wouldn't it be easier to just double click your download and have an installer pop up like in windows? Maestro, if I have to read hours worth of information to use the operating system then I hardly think it's a reasonable alternative to windows. I NEVER use mac's but when I get in front of one I can still install drivers and programs without googling a single thing on the internet. If you really do need to read and study linux for hours then maybe it's not what I was looking for. And should I try and figure out how to boot 6.10 or am I fine just staying with 6.06? I'm done complaining now, lol I just want to know how to get ubuntu running properly on my computer.

---

### Post by halitech on 2007-02-20
I don't remember the exact number of programs available through Synaptic but it's over 20,000. To install one of them, you simply go to System - Administration - Synaptic Package Manager. From there, you can look through the entire list or you can searc by category or by name.

The only real reason you would need to do an install through the CLI (or terminal) would be if Synaptic doesn't have it or you want an updated version. Even then, there are .deb files you can download to install ( [http://www.getdeb.net/](http://www.getdeb.net/)) which allow you to doubleclick and have it open in gdebi installer and as long as you can provide the sudo password (your main login password) you can install.

Depending on  your hardware, you can probably update to 6.10 although I prefer 6.06 myself.

---

### Post by Repent on 2007-02-20
Here try this " [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) " to install your drivers it works unlike some of the other ways, it's fast and vary easy. You have my word on it.

Repent.

---

### Post by greyash99 on 2007-02-20
EDIT:beaten to it

---

### Post by dpar on 2007-02-20
For someone who seems to want everything to work perfectly 'out of the box', and doesn't want to take the time to read instructions, I really don't think you should be thinking about Beta software such as Beryl right now.

---

### Post by cregan89 on 2007-02-20
ok thank you maestro, I went through synaptic and updated the fglrx drivers and then edited the xorg.conf file to use the new driver and my windows are all moving smoothly and it has added a couple new resolutions, still nothing above 1024x768 though. I tried editing a couple things in the xorg.conf file that seemed related to resolution but that didn't do anything. Do you have any other ideas how I can fix my resolution? I wasn't expecting everything to work out of the box, I was actually impressed how compatible it was with all my hardware actually, windows has problems with my audio card and my network card but ubuntu worked with it right out of the box. I just didn't think it was going to be that difficult to install drivers and programs (I've never had to edit config files in windows to get a driver to work). So does anybody know how to fix my resolution problem?

---

### Post by Repent on 2007-02-20
Did you see my post, try it what do you have to lose? 

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by dpar on 2007-02-20
Try this site for info on video card drivers.........[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

tseliot is pretty good with video drivers.:smile:

---

### Post by cregan89 on 2007-02-20
Ya I saw it after I installed the other drivers but now I already have graphics card drivers installed. Do you think that the graphics cards drivers are the reason I don't have all the resolutions?

---

### Post by dpar on 2007-02-20
Sorry, I'm not really too good at drivers, but the Envy script certainly made my driver installation painless. I also use an Nvidia card, so I don't know anything about ATI setup.

---

### Post by Repent on 2007-02-20
It's what I used when all the others ways failed I have 29 resolution settings I can use. Lol... but I can't hold the alt & print scrn and hold the dropbox at the same time, so no pic of the settings. Oh just so you know this uses Envy to set up the drivers it just does it a little differently it installs Ati drivers as well as Nvidia.

[IMG]http://i15.tinypic.com/43h9de8.png[/IMG]

---

### Post by cregan89 on 2007-02-20
Ok i used envy but i still have the same resolutions...

---

### Post by Repent on 2007-02-20
If you used my way look in your Applications, System tools for you driver settings.

---

### Post by cregan89 on 2007-02-20
ok i edited the xorg.conf file again and put in 1280x1024 and it worked but I can only get it at 47Hz interlaced. Does anybody know how to include refresh rates into the xorg.conf file or a way to force the monitor into specific resolutions? I had similar problems in windows getting 1600x1200, never 1280x1024 though, and I had to tell the ati control center to overide the driver settings or I had to edit some driver or config files manually. Does anybody know where the monitor driver would be or how I could install a different driver? There is an ati control center like thing in my menu but it has almost no functionality. It just let's me change colour settings.

---

### Post by cregan89 on 2007-02-20
well I fixed it... I don't know how lol but I fixed it. I have all the resolutions and refresh rates. ok so Where do I start with beryl? Is beryl a program or is it a complete gui like gnome or kde?

---

### Post by Maestro23 on 2007-02-20
> **cregan89 said:**
> well I fixed it... I don't know how lol but I fixed it. I have all the resolutions and refresh rates. ok so Where do I start with beryl? Is beryl a program or is it a complete gui like gnome or kde?

[http://www.ubuntuforums.org/showthread.php?t=349732](http://www.ubuntuforums.org/showthread.php?t=349732)

---

