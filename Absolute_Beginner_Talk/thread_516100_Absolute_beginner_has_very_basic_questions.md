---
title: "Absolute beginner has very basic questions"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by JEfromCanada on 2007-08-02
I've had an Ubuntu CD sitting on my desk for a long time.  About an hour ago, I decided to install it on a PC that I was going to junk.

It's Ubuntu 6.06 LTS and it's freshly installed - absolutely out of the box, except for the 251 updates that asked to be installed immediately afterward.  And after an hour, I already have two puzzlers.

First, I use a KVM switch to cut down on the amount of hardware around my desk.  If I start out on my Ubuntu machine and don't switch to anything else, everything works fine.  But, if I switch to any of the other computers, the mouse goes completely berserk when I return to the Ubuntu box.

I use a Microsoft Optical Trackball mouse.  Upon returning to Ubuntu, any movement of the mouse makes the cursor go to random places on the screen (the direction of movement bears no relation to my movement of the thumbwheel).  Also, as the mouse moves, it appears to be activating both left and right button actions (either bringing up context menus, or activating processes) even though I am not touching any buttons.

My only recourse is to reboot when this happens.

Second problem.  I went to mozilla.org to download the latest Firefox (the 1.5 version came preinstalled with Ubuntu).  I downloaded the Linux variant, and it downloaded a "tar" file (I've never seen a tar file until now).  The file downloaded properly, and when I clicked on the "Open" selection in the download window -- which is how I would install programs on Windows -- the tar file opened and I was offered the ability to extract the contents, but I have no idea how to actually install the program.

If someone can help me with these very basic things, I might be able to learn a bit on my own afterward.

Thanks very much.

---

### Post by jgrabham on 2007-08-02
> **JEfromCanada said:**
> I've had an Ubuntu CD sitting on my desk for a long time.  About an hour ago, I decided to install it on a PC that I was going to junk.

It's Ubuntu 6.06 LTS and it's freshly installed - absolutely out of the box, except for the 251 updates that asked to be installed immediately afterward.  And after an hour, I already have two puzzlers.

First, I use a KVM switch to cut down on the amount of hardware around my desk.  If I start out on my Ubuntu machine and don't switch to anything else, everything works fine.  But, if I switch to any of the other computers, the mouse goes completely berserk when I return to the Ubuntu box.

I use a Microsoft Optical Trackball mouse.  Upon returning to Ubuntu, any movement of the mouse makes the cursor go to random places on the screen (the direction of movement bears no relation to my movement of the thumbwheel).  Also, as the mouse moves, it appears to be activating both left and right button actions (either bringing up context menus, or activating processes) even though I am not touching any buttons.

My only recourse is to reboot when this happens.

Second problem.  I went to mozilla.org to download the latest Firefox (the 1.5 version came preinstalled with Ubuntu).  I downloaded the Linux variant, and it downloaded a "tar" file (I've never seen a tar file until now).  The file downloaded properly, and when I clicked on the "Open" selection in the download window -- which is how I would install programs on Windows -- the tar file opened and I was offered the ability to extract the contents, but I have no idea how to actually install the program.

If someone can help me with these very basic things, I might be able to learn a bit on my own afterward.

Thanks very much.

OK, first I would recommend you update, and download 7.04.

But anyway

If you want to look for .deb files when installing software.

For firefox, open a terminal (Applications>Accessories>Terminal) and type


sudo apt-get install firefox


It will then say password
Type you password, it doesnt matter that nothing happens when you type, and press enter

Hope this helps

---

### Post by skwishybug on 2007-08-02
> **JEfromCanada said:**
> 
My only recourse is to reboot when this happens.
 
Second problem. I went to mozilla.org to download the latest Firefox (the 1.5 version came preinstalled with Ubuntu). I downloaded the Linux variant, and it downloaded a "tar" file (I've never seen a tar file until now). The file downloaded properly, and when I clicked on the "Open" selection in the download window -- which is how I would install programs on Windows -- the tar file opened and I was offered the ability to extract the contents, but I have no idea how to actually install the program.
 
This took me a a bit to figure out too. Extract it to your desktop (or location of choice) and it will create a firefox folder. Open a terminal window and type:
```
 sudo mv firefox /opt/firefox 
```
 
Firefox from the website come pre-compiled and ready to use. To access the file, you would either need to create a link to the file from the menu/desktop or use the terminal and launch /opt/firefox/firefox to use it.
 
Someone smarter than I can also tell you how to create a link to the file so that the command would simply be firefox

---

### Post by Paul133 on 2007-08-02
Why did you install Dapper (6.06) and not Feisty (7.04)? Feisty would probably be better for you. As far as the mouse, I can't help you there. 

Regarding the tar file, there is a way to unzip the tar ( "tar.gz" is a zipped file) and then install the program from source and I can give you a series of comands to run in your terminal to do it. 

However, Firefox is in the repositories, so you can easily install it. Just go to System > Administration > Synaptic Package Manager and search for firefox. Then you'll find the latest firefox and mark it for installation. 

Most software in Ubuntu is installed this way, not by downloading programs from the web, like in Windows. It takes a little getting used to, but it's pretty easy. Good luck!

---

### Post by spur on 2007-08-02
Sounds like your mouse is not detected properly and you may need to change the configuration. (I'm not sure how to do that as I have never had the need.)
The KVM switch would be reacting to it being effectively unpluged while you use the other machine. I set up a KVM that was purely mechanical using a switch box and had this problem. A kvm with built in software might be a better choice as it maintains the connection with both boxes even though you can only use one at a time.
I would update Firefox from the repositories only. Go to System ->Administration->Synaptic and choose the Firefox you want.
To ensure you will get it make sure you have the repositories enabled go to System-> Administration->software sources and tick the boxes on the first page.
To do it manually extract the contents of your tar file to anywhere than open the 'read me' file it should tell you how to install. The directions will be Linux generic so you will have to add 'sudo' to the begining of any command mentioned, then enter your password.
I hope this gives you a start on working things out. It gets easier as you go. Remember that Linux is not windows so don't expect windows commands to work as they don't and shouldn't. You have a new os to learn and while some things are similar and may seem the same they really aren't.

---

### Post by jgrabham on 2007-08-02
> **Paul133 said:**
> 
However, Firefox is in the repositories, so you can easily install it. Just go to System > Administration > Synaptic Package Manager and search for firefox. Then you'll find the latest firefox and mark it for installation. 


We seem to have said  several ways to install firefox, but the way paul133 says is the best way

---

### Post by JEfromCanada on 2007-08-02
Thanks for the initial responses.

jgrabham:

When I did what you suggested, I was told firefox is already up to date, yet the "Help->About" on Firefox still says 1.5.0.12.

If I can assume that means I have 2.0.0.6 installed "somewhere", how do I go about locating where it is.


skwishybug:

When I did what you suggested, I received an error message:
mv: cannot stat `firefox': No such file or directory

I extracted the tar.gz file to the desktop as suggested (there's a firefox folder there).


Where do I go to get information about the linux terminal commands?

I've seen "mv" before (about 20 years ago or more with QNX), but I don't know what sudo is!

---

### Post by Paul133 on 2007-08-02
Sudo allows you to temporarily (15 minutes, I believe) become root. This way, you can do things you can't normally (install prgrams, uninstall programs, create directories, etc.) without giving you permanenet root access so you can make a mistake. 

As jp said, there are many ways to install programs. Don't use the tar method unless you absolutely have to. If you'r comfortable with the terminal ```
sudo aptitude update && sudo aptitude install firefox
``` or ```
sudo apt-get install firefox
``` If you want to use the GUI, you can just go to System -> Administration -> Synaptic Package Manager.

---

### Post by JEfromCanada on 2007-08-02
My goodness!

In the time it took me to read and reply to the original two messages, I've been inundated with help!  Thank you all so much!

I used the System->Admin... method suggested by several of you, and that showed me that, for the distribution I installed, 1.5 is indeed the most current firefox available.

So now, since I have no investment in customization, it seems reasonable to update to 7.04.

My question... is there some way I can initiate that update from what I have now, or do I have to find a new distribution and install that?

---

### Post by Paul133 on 2007-08-02
While it's possible to upgrade, it's probably better just to do a fresh install of Feisty. First, download feisty from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Then burn to an ISO to a blank CD following these instructions: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 

After you've burned the disk,  insert the CD and restart your computer, installing FIesty the same way you did Dapper. During the installation, you should be able to format the partition Dapper is on and install Feisty over it.

---

### Post by JEfromCanada on 2007-08-02
Thanks Paul133.  I've now created a 7.04 bootable disk, and will see how things go.

Hope to see you all soon!

---

### Post by caro on 2007-08-02
> **JEfromCanada said:**
> Where do I go to get information about the linux terminal commands?

When I begun with ubuntu a few months ago, someone directed me here:
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

I found it go give pretty thorough and understandable command line instructions.  Good luck.

---

### Post by JEfromCanada on 2007-08-02
Thank you caro for that link.

I've just returned online after installing 7.04 distribution.  Except for firefox, which I can see is now up to date, I haven't explored the differences between the older and newer distribution.  I'm going to do that right now.

---

### Post by Paul133 on 2007-08-02
Great. Good luck with Ubuntu!

---

