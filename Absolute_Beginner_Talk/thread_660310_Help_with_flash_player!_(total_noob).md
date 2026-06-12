---
title: "Help with flash player! (total noob)"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-01-06
Well, I feel like a complete jerk asking this question. If I had seen someone ask a question like this I'd tell them to look up a book on it and figure it out for themselves or something of the like, because it seems as though something that could be easily figure out like this. Well, I've been spending the last 3 days stubbornly trying to figure out how to install Macro Media Flash Player. I will do my best to try organizing my question with out leaving any holes  so it should be easy for someone who knows Ubuntu to answer, and so that there are not any misunderstandings.

Starting off with the page to download Macro Media Flash Player off of.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

First off, I don't know if I should download the ".tar.gz", the ".rpm", or the YUM. I went ahead and tried to download the first two and have been messing with them. I haven't touched the YUM. 

I have this book that i downloaded called, Wiley Ubuntu Linux Bible Jan 2007. but I'm starting to think it might be out dated as when I went to where it taught how to install the program it told me to access a program that doesn't even exist. The name of the program is...... okay well I've just spent the last half hour trying to find the name of the program that it told me to access to install programs. I suppose it is not important anyways, after realizing that I didn't have the program i googled around and saw people complaining about not having the program and found a link to download it, but how am I supposed to install it when I don't know how ;-). Anyways, I then scrolled down a little bit on the Adobe website and saw that they give instructions on how to install the files using the console. Welp, they didn't work either. 

Here are the instructions:

Installation instructions
.tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

.rpm installation

   1. Click the "Download .rpm" link. A dialog box will appear asking you where to save the file.
   2. Save the .rpm file to your desktop and wait for the file to download completely.
   3. In terminal, navigate to the desktop and type # rpm -Uvh <rpm_package_file>. Click Enter. (Note: This must be done as a root user). The installer will instruct you to shut down your browser(s).
   4. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

YUM repository installation

   1. Click the “Download .rpm” link. A dialog box will appear asking you where to save the file.
   2. Save the .rpm file to your desktop and wait for the file to download completely.
   3. In terminal, navigate to the desktop and type # rpm -Uvh <rpm_package_file>. Click Enter. (Note: This must be done as a root user).
   4. Once the installation is complete, in terminal, type # yum install flash-plugin. Click Enter. (Note: This must be done as a root user).
   5. To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.
   6. To get the most up-to-date Flash Player in the future, simply type # yum update flash-plugin in terminal. You will not need to repeat steps 1-4.

I always get some kind of error that involves the word bash? I tried using the help commands and some "sudo apt-get" thing I saw in the console. If someone could dumb things down for me immensilly and explain how to install this, I'm sure I could figure out how to install other programs. I still have a couple weeks before my Ubuntu Linux For Dummies comes in the mail. I looked all over for a pdf of it online, but couldn't find one. Also if anyone knows if the book is worth reading let me know. I'm assuming that, that Wiley Bible must not be a very good reference as I've been a computer tech for a while now and I MYSELF get headaches from it. I enjoy for Dummies books, They make me smile.:lolflag:

---

### Post by cadcrazy on 2008-01-06
Download tar.gz file. Right click on it and choose extract here. Now open that folder and double click on file flashplayer-installer and choose run in terminal option.Follow onscreen options and done

---

### Post by eapache on 2008-01-06
Ubuntu's package manager has it. Open Synaptic (System>Administration>Synaptic Package Manager) and use search to find and install 'flashplugin-nonfree'

The package manager is a front-end to a server database hosted by ubuntu. This db includes pretty much all the open-source and free/restricted software you'll ever need. The package manager allows you to install, remove, and update any software on your computer automatically.

---

### Post by cadcrazy on 2008-01-06
No its not a good idea to install flash player from ubuntu repo. Stay away from it , use the one from adobe website instead

---

### Post by eapache on 2008-01-06
cadcrazy: I've been using the one from the repos for quite a while and it hasn't given me any problems. Why do you recommend not using it?

---

### Post by whoscheesemine on 2008-01-07
cadcrazy : "Download tar.gz file. Right click on it and choose extract here. Now open that folder and double click on file flashplayer-installer and choose run in terminal option.Follow onscreen options and done"

I have already done that and all that happens is the terminal pops up real quick and goes away. Kind of like with XP, if you type certain commands into the RUN feature or open certain "DOS based" programs the command prompt will pop up real quick and then go away, unless you type in cmd in the RUN feature. Did I make some sort of mistake while installing my Ubuntu to cause it to run that way? If so does anyone mind telling me the commands to type in the terminal to install the program I am trying to install? This is because I am not oppose to learning the Linux console language.

**Just a thought, as I am trying to learn this myself. I figure that to install it all i have to do is type in ./flashplayer-installer once I am in the "Install_flash_player_9_Linux" directory. The only problem is that that directory is on my desktop, and I am not sure exactly what directory that is located in (that knowledge would be appreciated but isn't my point) I remember reading in my book that the /opt folder is where "optional" software is located or supposed to be located. Well in the terminal I typed "/" and hit enter to make sure I was in the root directory, from what I understand, and then i typed in "/opt" and hit enter which seemed to take me to the /opt directory. Afterwords I figured:  Hey! I'll just extract it there and run it in the terminal from there. Well, I tried and I got an error that said,

 [HTML]http://www.geocities.com/lookin4busstop/opt.jpg[/HTML]

So I figured that's okay. I'll just I'll just put it a level up from it, but it won't allow me to put a file in that folder either. So I'm trying to figure out how I'm supposed to do this, and I think to myself, "Well I guess I'll just follow the directions on the website and do it from the desktop." So I extract the files to the desktop. I go to the terminal, and well I'll just show you how that one went. It's the part I have highlighted black with white text.

[HTML]http://www.geocities.com/lookin4busstop/itsclearlythere.jpg[/HTML]

Okay, so I don't understand why I can't change the directory to a directory that's clearly there, but perhaps there is something I simply do not understand.

I thought hey maybe I could put it in my Windows partition. Access it from there.

[HTML]http://www.geocities.com/lookin4busstop/does_not_show_disk.jpg[/HTML]

Clearly that didn't work as well. 

=========================================================

Half way through typing this post, I got distracted by some personal matters and I had to finish typing it. So until I press the "post" button, the last post I have seen is eapache's that said: "cadcrazy: I've been using the one from the repos for quite a while and it hasn't given me any problems. Why do you recommend not using it?" I'm sure though after I press "post" someone will probably have already answered my questions.

---

### Post by whoscheesemine on 2008-01-07
> **eapache said:**
> Ubuntu's package manager has it. Open Synaptic (System>Administration>Synaptic Package Manager) and use search to find and install 'flashplugin-nonfree'

The package manager is a front-end to a server database hosted by ubuntu. This db includes pretty much all the open-source and free/restricted software you'll ever need. The package manager allows you to install, remove, and update any software on your computer automatically.

I did that and its not there.

I typed it in just like you did word for word and it finds nothing

---

### Post by wolfen69 on 2008-01-07
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by manmohanpv on 2008-01-07
eapache..ur suggestion works great fro firefox..

i installed flash plugin from adobe initially, but it was giving some problem while maximizing the youtube videos from firefox...

Now i tried it from synaptic..all looking fine in firfox...

but no idea..why it is not working if i try youtube from konqueror...it is asking me to download flash player..any suggestion?

-thanks
manmohan

---

### Post by wolfen69 on 2008-01-07
> **eapache said:**
> cadcrazy: I've been using the one from the repos for quite a while and it hasn't given me any problems. Why do you recommend not using it?

many people are/were having problems with flashplugin-nonfree from the repos. i tried to install it today on a fresh install, and did not work. the link(deb file) i provided above does work everytime.

---

### Post by whoscheesemine on 2008-01-07
> **wolfen69 said:**
> here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

Actually that didn't work for me either. Here's a screenshot.

[HTML]http://www.geocities.com/lookin4busstop/Screenshot.jpg[/HTML]

---

### Post by eapache on 2008-01-07
You're running 64-bit Ubuntu, so you want this one instead:

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb)

As for your file navigation woes, there are a few differences between Ubuntu and Windows. Because the root of the filesystem is / and not C: cd-ing to /disk is like cd-ing to C:\Disk Basically, putting a slash before a relative paths turns it into an absolute path.

Also, normal users don't have permission to write to the system. Individual users can only write inside of their directory (/home/username). The root user is the only user that can write anywhere. To run a command as root, prefix the command with sudo.

Example:```
cd /media
cd disk
sudo mkdir cheese
cd cheese
```

---

### Post by hyper_ch on 2008-01-07
> **eapache said:**
> cadcrazy: I've been using the one from the repos for quite a while and it hasn't given me any problems. Why do you recommend not using it?

Current version in the repos is broken. Hence a "manual" install is required.

---

### Post by mdpalow on 2008-01-07
Please see the link in my signature. Should be hassle free.

good luck...

---

### Post by whoscheesemine on 2008-01-07
> **eapache said:**
> You're running 64-bit Ubuntu, so you want this one instead:

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb)

As for your file navigation woes, there are a few differences between Ubuntu and Windows. Because the root of the filesystem is / and not C: cd-ing to /disk is like cd-ing to C:\Disk Basically, putting a slash before a relative paths turns it into an absolute path.

Also, normal users don't have permission to write to the system. Individual users can only write inside of their directory (/home/username). The root user is the only user that can write anywhere. To run a command as root, prefix the command with sudo.

Example:```
cd /media
cd disk
sudo mkdir cheese
cd cheese
```


how would I make it so that I am the root user?

---

### Post by eapache on 2008-01-08
One of the security features of Ubuntu is that nobody can log on as the root user (without some serious tweaking). However, users with administrative powers (set somwhere under System>Admin>Users and Groups) can run programs 'as root' by prefixing the terminal command with 'sudo'. Most things under System>Admin are launched the sudo prefix, which is why they prompt for your password before allowing you in.

---

