---
title: "Absolute Beginner Talks"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Spacehopperjoe on 2007-03-29
So yeah, Just installed ubuntu ultimate on my computer and its looking nice. The only problem is I cant get it to work with my gfx card. Now I have an oldschool ATI Radeon 9800 and aparently ATI and linux arent good friends. Great, so I downloaded the Linux drivers and when I run it I get this error

"Could not open the file /home/spacehopperjoe/Des…ler-8.35.5-x86.x86_64.run."

I have no idea what is up with this, I knew Ubuntu would be more fun but I dont even know where to turn to try and get around this, I dont even know how to install things. Im used to exe files doing it themselfs!!!!

Help

---

### Post by gh0st on 2007-03-29
Welcome to Ubuntu first of all :) 

I'm not an ATI user myself so not an expert on it but I think there are some pretty good ATI drivers out there now for Ubuntu. Software installation is a bit different than Windows, you can still go and download a file and install in the way you tried but the common practice is to use a package manager to get stuff from repositories.

Basically the repositories are a central place where software is kept and when you want to install something you search them, most stuff you could need is available in the main Ubuntu repositories. You have a list of repositories setup on your system which you can change to add 3rd party ones.

You will see the "Add/Remove" programs icon on your main menu, it's at the bottom. You can use that to find cool software and install it with one click, I don't know if the drivers you need are in there though sorry. I think they might be. You can think of this as similar to the Add and Remove programs in Windows but the Add bit actually works, getting new stuff from the Internet for you.

Thats not the best explanation ever but hopefully it makes things a little clearer.

For your graphics driver there is a really cool little too called Envy, it will install the latest Nvidia or ATI driver for you, depending what you need.

Here is a link to the website - [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Don't worry about it saying Nvidia in the link, it does do ATI as well. There should be some instructions on the site to help you out with it. You need to download the .deb file and double click it to install the tool. Like you would and .exe in Windows.

If you need anything else or you get stuck let me know, good luck :)

EDIT: I should have mentioned before, the equivalent of a ".exe" installer for Ubuntu would be ".deb" file, so look out for those. Mostly you can use the package managers though. Happy hunting :-)

---

### Post by gh0st on 2007-03-29
Here is a link to the Envy installer file you need:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb)

Once you've installed it you should see an Envy shortcut in the System Tools menu. I'm assuming you are using Ubuntu Edgy here, might be different in other releases.

---

### Post by Spacehopperjoe on 2007-03-29
Here man thank you, I went for a smoke, came back and the answer was there! Envy is doing the trick and downloading the latest one for me, heres hoping it installs and I can get my dual moniters up and running :P

I was in the add/remove bit looking for help but I thought it wouldnt be much help, damn you windows!!! Im going to try it and look for wine.

---

### Post by joseywales on 2007-03-29
I too, being an absolute Linux beginner, am struggling to perform what used to be in Windoze a simple task - installing my video card (ATI Radeon 9800XT) driver.   I used the link above and ran Envy and everything appeared to be working flawlessly (not that I could tell one way or the other).  When asked to restart my computer I did so, but now when I try to enable Beryl it simply will not work.  It will not allow anything other than Metacity.  I've tried to change it numerous times but when doing so the screen will 'flicker' for a sec and revert back to the way it was before trying this.

Any ideas?  I'm dying to get into Linux, so any help is GREATLY appreciated.

Oh, and FWIW, I'm running Ubuntu Ultimate Gamers Edition.

TYIA.

Josey

---

### Post by joseywales on 2007-03-29
Also, to add to the issue noted in my post directly above, my previously 'Auto Hide' toolbars no longer reappear....completely gone when mousing over them.  All I can do now is Alt-Tab to change currently open applications.

So, add this to my list of questions that I'm searching for answers :) 

Josey

---

### Post by overdrank on 2007-03-29
> **joseywales said:**
> I too, being an absolute Linux beginner, am struggling to perform what used to be in Windoze a simple task - installing my video card (ATI Radeon 9800XT) driver.   I used the link above and ran Envy and everything appeared to be working flawlessly (not that I could tell one way or the other).  When asked to restart my computer I did so, but now when I try to enable Beryl it simply will not work.  It will not allow anything other than Metacity.  I've tried to change it numerous times but when doing so the screen will 'flicker' for a sec and revert back to the way it was before trying this.

Any ideas?  I'm dying to get into Linux, so any help is GREATLY appreciated.

Oh, and FWIW, I'm running Ubuntu Ultimate Gamers Edition.

TYIA.

Josey

Hi you may try this link and just add to your xorg
[http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html)
Hope this helps it work for me and Good luck!

---

### Post by gh0st on 2007-03-30
> **joseywales said:**
> Also, to add to the issue noted in my post directly above, my previously 'Auto Hide' toolbars no longer reappear....completely gone when mousing over them.  All I can do now is Alt-Tab to change currently open applications.

So, add this to my list of questions that I'm searching for answers :) 

Josey

Hi,

Beryl can be a bit tricky to get going sometimes, I used a guide off their site to set it all up but I use an Nvidia card and the guide was specifically directed at that. As for the disappearing toolbars that is a bit weird. Can you maybe move the mouse just off the bottom of the screen and right-click to get the context menu up? You can choose "properties" and switch autohide off. That should at least bring the toolbar back for you I think.

You should check out the official Beryl wiki to solve your Beryl problems: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

This link is for the Ubuntu section, there is an ATI guide on the menu that may be useful to you.

Moving from Windows to Linux is never easy but it is rewarding in the end. Ubuntu is one of the easier Linux distros to use I would say. Thing's aren't necessarily harder in Linux they're just different, you're conditioned to Windows that's all. I found when I first tried Linux it took a year or so to feel comfortable and confident with it (this was before Ubuntu existed by the way). I use it full time now but in the beginning I felt like everything was impossible. Stick at it and at some point you'll realize you are answering more questions than you are asking, then you know you're getting somewhere :) 

Here are a few good sites for the Ubuntu beginner to find their feet:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

[http://jamie.dumbill.googlepages.com/ubuntuhowto](http://jamie.dumbill.googlepages.com/ubuntuhowto)

[http://linuxappfinder.com/](http://linuxappfinder.com/)

Those are all good places to find out a bit more about Ubuntu, the first link particularly has great tutorials and guides for most things. Of course there also this wonderful forum as well to help you solve any Ubuntu issue. 

Hope that helps a bit, good luck in the brave new Linux world :)

---

### Post by Spacehopperjoe on 2007-03-30
Alright joseywales, me and you are in the same boat!!! I have been dying to get into linux for ages so i thought I should. The thing that worked for my 9800 pro was to downalod the binary drivers (i dont know what it was but it had binary in the name) from the handy start menu. You have to search for "Radeon" to find them, not ati.

Install them, or do whatever linux does, and then run envy and it will install the rest for you. It works out great but it wont support dual monitors!!!! It just has the same image cloned. 

So this leads me to my next question.......

Im reading this - [http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941) - right and the first thing it tells me is to: 

Let's get started!!!

1. Open up Xorg.conf using ONE of the following commands:
Gnome (Ubuntu):
Code:
gksudo gedit /etc/X11/xorg.conf

Where do I type that command in??? To get the rest going? I know I have Gnome (whatever that is) but i dont know how to use it. Just some noob questions.

---

### Post by Spacehopperjoe on 2007-03-30
So aye I found out where to type it in, (alt + F2) but alas it dosnt work. I still have two moniter displaying the same thing. Fun times.

---

### Post by gh0st on 2007-03-30
> **Spacehopperjoe said:**
> So aye I found out where to type it in, (alt + F2) but alas it dosnt work. I still have two moniter displaying the same thing. Fun times.

You need to use the terminal to type these commands into. It's like the equivilent of the command line prompt in Windows. It's basically what is underneath the visual GUI you are using. The window environment you are using is called Gnome, it's the whole graphical interface you see, the desktop, menu's windows and all that. They all from the Gnome interface.

To use the terminal look under "Accessories" on the menu. It's in there. It will just load a text prompt window. You can type your commands in there. You'll see a lot of people posting commands for the terminal in this forum. It's used a lot more in Linux than in Windows. It can seem really difficult at first but after a few goes with it you'll start to like the terminal, you can do anything on your system with practically one line of code. The trick is learning the commands and that can be the tough bit.

The basic structure of a Linux is system is layered like so:

1. The Linux Kernel - this is the core of the Linux system and does all the work really, interfacing with hardware, processing commands all that kind of stuff.

2. The X server is on top of the kernel, this is what handles your GUI display and links it to the Kernel, it has to be setup correctly with your video card to work. If it fails to load you just get booted to a command prompt. A bit like loading DOS on an old Windows machine. This is a direct interface to the system, it's loaded as a failsafe when the GUI fails. 

3. Your GUI environment or Window manager is on top of those,  in Ubuntu this Gnome. There are loads of different windows managers out there that can be used to interface with the Kernel. Gnome and KDE are the most popular, they each have their own specific look and feel. You can swap and change them as they just plug into the underlying system for want of a better term.

Thats not a brilliant explanation of the Linux structure but hopefully it helps you make some sense of it all. I'll see if I can find any decent links about it if you are interested?

EDIT: ALT+F2 is not the command you want. I should have said that before. CTRL+ALT+F2 command should kill the X server and take you into a purely text based environment. When you are in the text prompt CTRL+ALT+F7 will load the GUI again. It's called switching run modes. Because the Kernel (core system) and Xserver (GUI) are separate you can kill the xserver and the system is still running as it was before underneath, then reload the xserver and everything will be the same. You are always looking at the same system, it's just one way you are looking through a nice GUI the other way you see the raw system underneath. You can reboot the GUI without rebooting the main system, Windows can't do that and it's one of the reasons you rarely need to reboot a Linux system to install things.

**WARNING:** You should not need to switch run modes to enter terminal commands in most cases, just use the terminal link on the menu. You might need to do it for installing graphics drivers because the system cannot be updated while the current graphics driver is still in use. Even editing your xorg.conf you should be able to do in the terminal window, then reboot the xserver with CTRL+ALT+BACKSPACE and login again.

Hope that helps a bit :-)

---

### Post by Spacehopperjoe on 2007-03-30
Yeah Im understanding linux more and more. I used command prompt in windows but as you say its not half a beef so it will take some time. I looked about the web and found some vague info about the ALT+F2 and edited the right file easily. I had no idea what the CTRL+ALT+F7 would do and see when it restarted, I was looking at it but it never turned off I noticed. I thought it was broken. lol. 

My graphics are up and running, so now Im going to be a complete noob and want to see this beryl. I totaly want to see my desktop via cube vision, but I have no idea how to acctivate it.....I can get into the beryl manager and turned on the cube options but.....nothing. :( Am I missing something completly obvious again?

---

### Post by gh0st on 2007-03-30
:)  Haha yeah I did the same thing. I installed compiz ages ago and thought "nothings changed". You have to use certain commands to spin the cube and stuff.

If you have Beryl installed and it's turned on in the Beryl manager you just need to press CTRL+ALT with the direction keys to change workspaces and the cube should rotate, you can also hold down CTRL+ALT and use the mouse to drag the desktop and spin the cube.

I won't list all the commands here, have a look at this: [http://wiki.beryl-project.org/index.php?title=Tips/Default_Commands](http://wiki.beryl-project.org/index.php?title=Tips/Default_Commands)

This could have all the commands you need.

Have fun, don't get motion sickness :)

---

### Post by DivineOmega on 2007-03-30
Howdy, and welcome to the Ubuntu Community.

I've written a very easy to follow tutorial on my website on how to install ATI's official graphics drivers, as when I was installing them I could never find a simple to the point tutorial.

Link: [http://divineomega.co.uk/linux/how-to-install-ati-graphics-drivers-in-ubuntu/](http://divineomega.co.uk/linux/how-to-install-ati-graphics-drivers-in-ubuntu/)

---

### Post by joseywales on 2007-03-30
> **gh0st said:**
> As for the disappearing toolbars that is a bit weird. Can you maybe move the mouse just off the bottom of the screen and right-click to get the context menu up? You can choose "properties" and switch autohide off. That should at least bring the toolbar back for you I think.

I tried doing that but it didn't resolve the problem.  It was late so I didn't have an opportunity to keep troubleshooting these issues but I'm pretty sure that they'll still be waiting for me upon my next boot-up.

---

### Post by gh0st on 2007-03-30
> **joseywales said:**
> I tried doing that but it didn't resolve the problem.  It was late so I didn't have an opportunity to keep troubleshooting these issues but I'm pretty sure that they'll still be waiting for me upon my next boot-up.

Could you post a screen shot maybe so I can see what's going on? Dunno quite how you're gonna do that, normally you would just use the "Print Screen" button on your keyboard. Hopefully it will still work for you.

I've never heard of this problem before :-k 

I'll see if I can find some way of resetting the desktop to default layout, that might fix it I think. I'll have to get back to you.

---

### Post by gh0st on 2007-03-30
Found this thread about resetting Gnome. Have look at the 2nd post down it might be of some use.

[http://www.ubuntuforums.org/showthread.php?t=346496](http://www.ubuntuforums.org/showthread.php?t=346496)

Apparently if you just delete the gnome settings folder and log off then back on it recreates it with all the default settings.

You will need to use the "Show Hidden Items" option on the view menu in the file manager. You should find a file called .gnome in the home directory. I would read through this a bit before doing anything though.

I have never done this before myself so I can't vouch for the solution. You might wanna check out other possible solutions as well. I suppose it depends how brave you are :) 

Good luck :)

---

### Post by Spacehopperjoe on 2007-03-31
> **gh0st said:**
> :)  
If you have Beryl installed and it's turned on in the Beryl manager you just need to press CTRL+ALT with the direction keys to change workspaces and the cube should rotate, you can also hold down CTRL+ALT and use the mouse to drag the desktop and spin the cube.


When I hit CTRL+ALT I get the choice to change workspaces....It must not be turned on.

---

### Post by Spacehopperjoe on 2007-03-31
> **gh0st said:**
> :)  
If you have Beryl installed and it's turned on in the Beryl manager you just need to press CTRL+ALT with the direction keys to change workspaces and the cube should rotate, you can also hold down CTRL+ALT and use the mouse to drag the desktop and spin the cube.


When I hit CTRL+ALT I get the choice to change workspaces....It must not be turned on, but the beryl ruby is showing in the like, System tray thing.

---

### Post by gh0st on 2007-03-31
Well there's 2 possibilities here I'd say, either it's not installed properly or it's just not switched on.

Hopefully it's just not switched on. Have you right-clicked the Beryl icon in the "system tray" type area and tried the "select window manager" option, obviously it should be set to Beryl.

If it is already set to Beryl but there isn't any 3d stuff going on when you switch workspaces or whatever I can only assume it's not installed properly.

You'll have to go through this guide and check you did every step in it, maybe even uninstall Beryl and do it again using these guides.

Ubuntu Beryl guide - [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

Ubuntu Beryl with ATI guide - [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

I found when I installed Beryl the first time it didn't work and I had to follow the Beryl and Nvidia guide, then it worked.

I don't know what else to suggest sorry, hope the works for you.

---

### Post by Lucifiel on 2007-03-31
Edit: good luck on installing your ATI drivers and getting everything to work. :)

Now, I'm going to go slightly off-topic, here? 

*begin slight rant*

Being a real Ubuntu beginner, I'd like to say that this operating system looks and feels great. However, it really needs a lot more work if it's aiming to be really easy to use.

So far, I've had problems playing mp3s and even installing themes, both of which are really easy to perform under WinXP. Really, one shouldn't have to install any packages just to get something so simple to work. Even back in the days of Win 95 when Winamp was still around Version 1 to Version2, you didn't have to install any plugins just to play an mp3. (Or maybe it's 'cos I'm running Ubuntu v6.06 but I doubt so.) 

Then, there's the issue of trying to get Synaptic to update a package before you install it, so that you've the latest version instead of receiving any potential errors from installing an older version. 

And a whole lot of other issues. =/ I'd thought that Ubuntu would be really easy and free from frustrations but ... this is turning out to be a real hassle. After all, what kind of easy to use interface requires tons of commands via Terminal just to "make" and "install" a program? Sure, they're copy and paste but the commands vary from system to system, don't they? In the end, the "click to setup" system that Windows uses is far more newbie-friendly, though I admit it's more error-prone. 

Imho, Linux really needs a better system of installing a program, preferably one that automates the commands to perform the task and another interface that also allows advanced users to install manually.

*end slight rant*

---

### Post by Spacehopperjoe on 2007-03-31
> **gh0st said:**
> Well there's 2 possibilities here I'd say, either it's not installed properly or it's just not switched on.

Hopefully it's just not switched on. Have you right-clicked the Beryl icon in the "system tray" type area and tried the "select window manager" option, obviously it should be set to Beryl.

If it is already set to Beryl but there isn't any 3d stuff going on when you switch workspaces or whatever I can only assume it's not installed properly.

You'll have to go through this guide and check you did every step in it, maybe even uninstall Beryl and do it again using these guides.

Ubuntu Beryl guide - [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

Ubuntu Beryl with ATI guide - [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

I found when I installed Beryl the first time it didn't work and I had to follow the Beryl and Nvidia guide, then it worked.

I don't know what else to suggest sorry, hope the works for you.

Aye well you were right about it not being turned on lol. But when I do turn it on all my open windows flicker between each other and it goes back the gnome. I will try uninstalling it and following the guide you linked. Ta man, linux would have been unistalled long ago if it wasnt for the help im getting here.

---

### Post by Spacehopperjoe on 2007-03-31
> **Lucifiel said:**
> 
Being a real Ubuntu beginner, I'd like to say that this operating system looks and feels great. However, it really needs a lot more work if it's aiming to be really easy to use.

So far, I've had problems playing mp3s and even installing themes, both of which are really easy to perform under WinXP. Really, one shouldn't have to install any packages just to get something so simple to work. Even back in the days of Win 95 when Winamp was still around Version 1 to Version2, you didn't have to install any plugins just to play an mp3. (Or maybe it's 'cos I'm running Ubuntu v6.06 but I doubt so.) 

Then, there's the issue of trying to get Synaptic to update a package before you install it, so that you've the latest version instead of receiving any potential errors from installing an older version. 

And a whole lot of other issues. =/ I'd thought that Ubuntu would be really easy and free from frustrations but ... this is turning out to be a real hassle. After all, what kind of easy to use interface requires tons of commands via Terminal just to "make" and "install" a program? Sure, they're copy and paste but the commands vary from system to system, don't they? In the end, the "click to setup" system that Windows uses is far more newbie-friendly, though I admit it's more error-prone. 

Imho, Linux really needs a better system of installing a program, preferably one that automates the commands to perform the task and another interface that also allows advanced users to install manually.

*end slight rant*

From another ubuntu noob, I knew I was getting into command line stuff here tis what I was after. I didnt want a double click done method, after like a month my 120gb is always full of random **** I have downloaded but with linux, I actually know whats going in as I have put it there. I will get to know the operating system so much more installing stuff than just running the OS the way I would with XP. 

I think its like the diffrence between building your computer and having dell send you one, ya know?

---

### Post by gh0st on 2007-03-31
> **Lucifiel said:**
> Edit: good luck on installing your ATI drivers and getting everything to work. :)

Now, I'm going to go slightly off-topic, here? 

*begin slight rant*

Being a real Ubuntu beginner, I'd like to say that this operating system looks and feels great. However, it really needs a lot more work if it's aiming to be really easy to use.

So far, I've had problems playing mp3s and even installing themes, both of which are really easy to perform under WinXP. Really, one shouldn't have to install any packages just to get something so simple to work. Even back in the days of Win 95 when Winamp was still around Version 1 to Version2, you didn't have to install any plugins just to play an mp3. (Or maybe it's 'cos I'm running Ubuntu v6.06 but I doubt so.) 

Then, there's the issue of trying to get Synaptic to update a package before you install it, so that you've the latest version instead of receiving any potential errors from installing an older version. 

And a whole lot of other issues. =/ I'd thought that Ubuntu would be really easy and free from frustrations but ... this is turning out to be a real hassle. After all, what kind of easy to use interface requires tons of commands via Terminal just to "make" and "install" a program? Sure, they're copy and paste but the commands vary from system to system, don't they? In the end, the "click to setup" system that Windows uses is far more newbie-friendly, though I admit it's more error-prone. 

Imho, Linux really needs a better system of installing a program, preferably one that automates the commands to perform the task and another interface that also allows advanced users to install manually.

*end slight rant*

You make some fair points, I admit that Linux isn't always easy to use and can be confusing to new users at. However I would argue that if you are going into the terminal to install your software all the time then you're doing something wrong. The package managers in Ubuntu are great and almost anything you could ever need can be installed through Synaptic or Add/Remove. Which is just as easy as Windows if not more so IMHO. I use Ubuntu full time for all kinds of varied tasks, programming, graphics, office stuff, multimedia, general web stuff etc and since installing Edgy a few months ago I've never had to install anything with the terminal, honestly. I regularly install new software to mess around with and experiment but I do it all through Synaptic or Add/Remove in point and click fashion. Having ".deb" packages is just like having ".exe" installers on windows. I don't see the difference. They are both binary, one click installers.

You are right that having to install all your codecs and stuff is not great but I have used Windows since version 3.1 was out and I still have to install codecs all the time to setup a new machine. I have to use codec packs to handle Divx, Xvid, Ogg, Quicktime, Real Media etc on Windows XP so how is this different to installing the restricted codec pack for Totem in Ubuntu? Espcially if you use [Easy Ubuntu]("http://easyubuntu.freecontrib.org/") or [Automatix]("http://www.getautomatix.com/").

I am not trying to have a go at you in any way and like I say you make some really good points, so please don't take this the wrong way :) 

Ubuntu is far from perfect and I know that, it's not always easy for new users but imagine you'd never used a Windows PC in your life and you wanted to install one and set it up, I think you'd have just as much trouble. Thats just my opinion and I know I'm biased as a Linux enthusiast.

If you want an easy to use OS that has multimedia codecs and lots of other things out of the box (which neither Windows or Ubuntu do) you should check out Linux Mint, it's like Ubuntu with all of the setup done for you. I would really recommend it for novice users as an introduction to Linux.

[http://linuxmint.com/](http://linuxmint.com/)

I think a lot of the issues you raise will be resolved with the new release Fiesty Fawn, due in the next month I believe. Linux isn't for everybody thats true but great leaps have been made in the last 2 years, where will we be in another 2? Who knows. I'm sorry your Ubuntu experience hasn't been an altogether happy one. If there's anything I can do to help please let me know. Keep the faith :)  ...maybe try Linux Mint ;)

---

### Post by Lucifiel on 2007-03-31
> **gh0st said:**
> You make some fair points, I admit that Linux isn't always easy to use and can be confusing to new users at. However I would argue that if you are going into the terminal to install your software all the time then you're doing something wrong. The package managers in Ubuntu are great and almost anything you could ever need can be installed through Synaptic or Add/Remove. Which is just as easy as Windows if not more so IMHO. I use Ubuntu full time for all kinds of varied tasks, programming, graphics, office stuff, multimedia, general web stuff etc and since installing Edgy a few months ago I've never had to install anything with the terminal, honestly. I regularly install new software to mess around with and experiment but I do it all through Synaptic or Add/Remove in point and click fashion. Having ".deb" packages is just like having ".exe" installers on windows. I don't see the difference. They are both binary, one click installers.

You are right that having to install all your codecs and stuff is not great but I have used Windows since version 3.1 was out and I still have to install codecs all the time to setup a new machine. I have to use codec packs to handle Divx, Xvid, Ogg, Quicktime, Real Media etc on Windows XP so how is this different to installing the restricted codec pack for Totem in Ubuntu? Espcially if you use [Easy Ubuntu]("http://easyubuntu.freecontrib.org/") or [Automatix]("http://www.getautomatix.com/").

I am not trying to have a go at you in any way and like I say you make some really good points, so please don't take this the wrong way :) 

Ubuntu is far from perfect and I know that, it's not always easy for new users but imagine you'd never used a Windows PC in your life and you wanted to install one and set it up, I think you'd have just as much trouble. Thats just my opinion and I know I'm biased as a Linux enthusiast.

If you want an easy to use OS that has multimedia codecs and lots of other things out of the box (which neither Windows or Ubuntu do) you should check out Linux Mint, it's like Ubuntu with all of the setup done for you. I would really recommend it for novice users as an introduction to Linux.

[http://linuxmint.com/](http://linuxmint.com/)

I think a lot of the issues you raise will be resolved with the new release Fiesty Fawn, due in the next month I believe. Linux isn't for everybody thats true but great leaps have been made in the last 2 years, where will we be in another 2? Who knows. I'm sorry your Ubuntu experience hasn't been an altogether happy one. If there's anything I can do to help please let me know. Keep the faith :)  ...maybe try Linux Mint ;)

Oh, don't worry. I was just very frustated after learning that I can't really mount my NTFS volumes 'cos of some issue. That an issue with the installation of Flash would likely cause problems with ntfs-3g. And the alternative provided (ntfs-config) didn't seem to work, either.

For Codecs in Windows, I use the CCCP which takes care of almost everything for me(it plays everything from divx to ogm, etc., etc.) And my frustration actually isn't with installing packages but that often, you've to dig through tons of threads and pages to find out what you need to install. After which, you find out that the package available is of an earlier version and you can't figure out how to get Synaptics to recognise the latest version package. 

Ahhh... when I was talking about installing programs, I was thinking of something like ntfs-3g which requires FUSE. Before I reinstalled Ubuntu, I'd attempted to mount my drives. :/ However, the fuse package in Synaptics was slightly old: 2.4 as composed to the current version 2.6.0 And I couldn't really add in the package either so, I used Terminal. For most WinXP users, ntfs is a very important feature and from what I learnt in the feedback by one of the ntfs-3g mods, there's some bug that causes some inconveniences with ntfs-3g. 

Anyways, there were some other applications that couldn't be found via Synaptics. (Yes, I've enabled main, universal, etc., etc. settings under Repositaries) So, I'd to load them under Terminal. 

Also, I found this to be a really crippling feature: that unlike WinXP and most browsers, that Linux doesn't have a location bar. You can't even navigate to a directory by pasting a location. And another issue is that though your drives are added under Media(for many programs, that is), the directory listing is far too deep and difficult to navigate 'cos you can't paste a directory url at all. And there ought to be a walkthrough or guide for users, so they can learn about the changes made to the o/s or learn about Ubuntu and Linux, in general. 

If Linux intends to woo many more Windows fans, then it needs to update its' GUI experience. And also follow what Mozilla does: provide a readme file or integrate some explanations for the matching Windows functions in Linux during the installation process. And rename some of the functions too, so users can tell the function, just by glancing at some of the names. Plus, some of these functions ought to be merged/integrated or at the least, launched from a shared window like Keyboards and Keyboard shortcuts, etc. 

There're even more very basic functions which ought to be added as default(that is, no installing via packages) like Contrast, Graphics card panel, etc., etc.

Heh that's an interesting link. =) It looks decent but I've some faith in the Fawn version(hopefully, it'll be a lot better than Edgy). Though, I'm likely to boot into WinXP to watch my movies and play my games.

---

### Post by gh0st on 2007-03-31
Yeah I can't argue with you that there is a lot that need doing still to make Ubuntu better.

 As for the issues you raised in your reply:

I use NTFS-3G on my machine to access all kinds of NTFS drives and it works great, been using it for about 8 or 9 months, never had a single issue, touch wood :) I also have Flash 9 installed in Firefox and haven't seen any conflict between the 2 at all. Where did you read that?

You should check this thread out [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009) its written by an NTFS-3G developer and his guide is really good, I basically added his repositories to my sources list and did a quick upgrade with apt-get, it installed a new version of pmount and some fuse libraries. Now I can just plug in a USB ntfs drive and it pops up on the desktop. Worth a go if you have NTFS worries. There should be an option to install all this with the main system though you are dead right. I think a lot of it is to do with legal issues, Ubuntu don't wanna get sued for supplying copyrighted stuff by default. They should try and do a deal with the copyright holders though I think, definitely.

The location bar thing can be a pain but it's easy to turn on the address text box view if you want it. Just click the little button on the left hand side of the location toolbar, it's a little picture of a pad and pencil to toggle between modes. It should remember your settings when you open and close the file browser. It's not obvious enough that this function is present though and I think it could have been designed a little better from a usability standpoint.

I like your ideas about the new user guide feature like Mozilla. I think that would be useful and I have a feeling something very similar has been added to Fiesty but I can't swear to it. You seem to have a lot of good ideas for improving the Ubuntu experience, you should contact the Feisty Development team and put them forward. Thats the beauty of Linux you can make it what you want :) 

I would definitely check out Linux Mint if you want an easy to use distro for Windows users, it would have solved a lot of your issues right out of the box. NTFS read/write, Codecs, Plugins, Drivers etc. I know I keep going on about it so I'll stop now sorry. [Sabayon]("http://www.sabayonlinux.org/") and [Freespire]("http://www.freespire.org/") are also a great distros you might be interested in. They both concentrate on being ready to use straight out of the box. If Ubuntu isn't for you then maybe one of them would be a better fit ;)

Remember Ubuntu is only one type of Linux there are loads of other to explore. Good luck :)

---

### Post by Lucifiel on 2007-04-01
Oops... that should've been Fuse, not Flash. Oh my god lol... I completely confused the two names and oh, I would submit many suggestions but it's not too useful to search within the wiki as there're often many different terms used for the same phrase. Thus, I've a feeling that at least 50% of my suggestions are useless, already. Plus, so many of my suggestions are linked to one another and posting them one by one would only mess up the suggestions, and pasting them into huge separate chunks wouldn't work either.

Oh well, perhaps I won't submit them. *shrugs* It's true there're almost 30 suggestions on my list but... oh well, to add them to a wiki one by one is way too time-consuming for me. 

I've seen the ntfs-3g guide and even followed it. However, I'd some issues and need to fix that first. 

The location bar feature, huh? That must be in Edgy, then. I'm on Dapper, I think.

Well, I'd love to keep switching around but I think I'll just stick to Ubuntu.

---

### Post by jvc26 on 2007-04-01
I'd like to explain why things like ntfs and mp3 dont work out of the box with Ubuntu. The main reason is these are proprietary codecs - mp3 is a proprietary codec, ntfs is a proprietary, MS owned Filesystem.
> 
1/ Ubuntu's commitment to only include completely free software by default means that proprietary media formats are not configured 'out of the box'.

This was taken from [here]("https://help.ubuntu.com/community/RestrictedFormats") If you're interested I'd look at the [licensing agreement]("http://www.ubuntu.com/community/ubuntustory/licensing") basically, as ubuntu is  Free OS, and will stay that way, it means that you don't get proprietary stuff with their OS - its not hard to get them all sorted (ntfs-3g and mp3 and other codecs) but for the purposes of Ubuntu's licensing agreement thats how it is.
Il

---

### Post by gh0st on 2007-04-01
> **Lucifiel said:**
> 
The location bar feature, huh? That must be in Edgy, then. I'm on Dapper, I think.


I can't really say as I've never used Dapper, you might be right I dunno. Here's a quick screen shot of my file browser so you can compare. You might need to turn the location bar on in the "View" menu. 

I've highlighted the button I used to switch the location mode in crude red marker. I'm not much of an artist :) 

Hope that helps in some way but possibly not.

[ATTACH]28715[/ATTACH]

---

