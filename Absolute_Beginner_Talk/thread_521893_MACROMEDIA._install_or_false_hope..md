---
title: "MACROMEDIA. install? or false hope."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-09
ok, so i go and i get the files it says you need to get it to work, IE: the download. i get them, follow the instructions to the LETTER, AS IN A-Z and, the terminal has the respect to tell me im stupid and that ive typed in an address that doesnt exist..

---

### Post by tjsullivan1 on 2007-08-09
Did you download the files and then try to compile them? Or did you get an error message when you tried wget? Do you have an X server (e.g. Gnome, KDE, XFCE)?

---

### Post by jfinkels on 2007-08-09
To install the flash plugin, enable the 'multiverse' repository in "System > Administration > Software Sources" and then enter the following in the terminal:```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

---

### Post by the.phantom on 2007-08-09
well from the wiki here are 3 ways to do it at least !
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

note i installed fiesty last night and did it with #2 and one click and it was working !

---

### Post by jake16424 on 2007-08-09
> **the.phantom said:**
> well from thw eiki here are 3 ways to do it at least !

note i installed fiesty last night and did it with #2 and one click and it was working !

yeah i can have feisty in all of about 30 min, i have it on disk, but i decided to try to make this work instead,, if it doesnt work out in the next 2 or 3 days,, ima go over to feisty...

i still dont have sound because of my audio drivers they wont install either.

for the record, i downloaded the .yum file, didn't seem all that tasty to me.. then i extracted then it told me to input a thing into the terminal i did then it said,, after all that, that the file isnt there or the directory doesnt exist.

---

### Post by jake16424 on 2007-08-09
> **jfinkels said:**
> To install the flash plugin, enable the 'multiverse' repository in "System > Administration > Software Sources" and then enter the following in the terminal:```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

as far as i got E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by tjsullivan1 on 2007-08-09
What version of Ubuntu are you running? Yum is the Fedora (Red Hat) equivalent of apt-get.

---

### Post by jake16424 on 2007-08-09
> **tjsullivan1 said:**
> What version of Ubuntu are you running? Yum is the Fedora (Red Hat) equivalent of apt-get.

idk what apget is either,, no clue.. an dim using 6.06

---

### Post by tjsullivan1 on 2007-08-09
> **jake16424 said:**
> idk what apget is either

apt-get is the command line utility for installing things. You should be able to install flash as has been previously described: sudo aptitude update && sudo aptitude install flashplugin-nonfree.

I would run it as:
```
sudo apt-get update
``` and then ```
sudo apt-get install flashplugin-nonfree
``` from the command line. 

If you aren't sure how to get to the command line press alt+f2 (this will bring up a dialog box) and type "gnome-terminal" and hit enter. Then type the commands.

---

### Post by jake16424 on 2007-08-09
> **tjsullivan1 said:**
> apt-get is the command line utility for installing things. You should be able to install flash as has been previously described: sudo aptitude update && sudo aptitude install flashplugin-nonfree.

I would run it as:
```
sudo apt-get update
``` and then ```
sudo apt-get install flashplugin-nonfree
``` from the command line. 

If you aren't sure how to get to the command line press alt+f2 (this will bring up a dialog box) and type "gnome-terminal" and hit enter. Then type the commands.

ive run that damned line about 4 times, no kidding... :confused::(

---

### Post by jfinkels on 2007-08-09
Please read some of the links in my profile, especially the first one "Installing software" and some (or all) of psychocats tutorials! They will help you understand your new Linux system, I promise!

---

### Post by tjsullivan1 on 2007-08-09
It could be that the flash player isn't in your repositories. I would check for you but I am on my MacBook right now (my ubuntu box is at work). 

What happens if you go to [http://www.adobe.com/products/flashplayer/]("http://www.adobe.com/products/flashplayer/")? Does it allow you to download from there (it does on my Mac... but I'm not sure about ubuntu.)

---

### Post by jake16424 on 2007-08-09
ive been to that website,, i do what it says,, nothing happens except i extract the files, then it gives me a thing in terminol saying, 

directory doesnt exist, or, file is missing.

---

### Post by tjsullivan1 on 2007-08-09
What is the extension at the end of the file that you download? And how are you extracting the file?

---

### Post by jake16424 on 2007-08-09
> **tjsullivan1 said:**
> What is the extension at the end of the file that you download? And how are you extracting the file?

idk, its a .yum file, they say,,

and,, im using the archiver, whatever is default,, idk enough to mess with stuff yet, =\

its a Option 1: .tar.gz file,, haha,, ^_^ sorry guys,,

---

### Post by tjsullivan1 on 2007-08-09
Is it possible for you to go to that site and get a tar.gz or .deb file?

---

### Post by tjsullivan1 on 2007-08-09
It actually might be possible to use alien to convert it to a .deb. I'm not sure if it will work, but open a terminal and type ```
sudo apt-get install alien
``` If that works reply back.

---

### Post by jfinkels on 2007-08-09
You should not be downloading any software! It is totally unnecessary. Please click on the first link in my signature to learn about installing software. .yum packages are only useful in distributions that use the Yellowdog Update Manager; Ubuntu uses the APT package manager to install programs. To install a program, just type:```
sudo aptitude install *programname*
``` THERE IS NO NEED TO DOWNLOAD AND MANUALLY COMPILE AND INSTALL FROM SOURCE CODE.

---

### Post by jake16424 on 2007-08-09
it is a Option 1: .tar.gz, that is copy and pasted right from there site,,

---

### Post by tjsullivan1 on 2007-08-09
> **jfinkels said:**
> You should not be downloading any software! It is totally unnecessary. Please click on the first link in my signature to learn about installing software. .yum packages are only useful in distributions that use the Yellowdog Update Manager; Ubuntu uses the APT package manager to install programs. To install a program, just type:```
sudo aptitude install *programname*
``` THERE IS NO NEED TO DOWNLOAD AND MANUALLY COMPILE AND INSTALL FROM SOURCE CODE.

Clearly, he is having an issue downloading the software that way. Although, reading up on installing software can't hurt jake. 

For the time being, open a terminal window and navigate to the directory that your .deb package is in and type ```
dpkg -i *thenameofyourpackage.deb*
``` 

It has been a while since I have installed anything on Ubuntu using dpkg, but if I am remembering correctly that should work.

---

### Post by jfinkels on 2007-08-10
> **jake16424 said:**
> as far as i got E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

> **tjsullivan1 said:**
> Clearly, he is having an issue downloading the software that way. Although, reading up on installing software can't hurt jake. 


I apologize, I was not paying attention to what you wrote, jake!

jake, the message you keep getting, may mean that you have another program open that is using the apt package manager. If you have any other instances of Synaptic, for example, or aptitude running, make sure that they are closed! You can only have one instance of apt package manager running.

If you try the command again without Synaptic running, and are still getting an error, please post it back here.

---

### Post by jake16424 on 2007-08-10
> **tjsullivan1 said:**
> Clearly, he is having an issue downloading the software that way. Although, reading up on installing software can't hurt jake. 

For the time being, open a terminal window and navigate to the directory that your .deb package is in and type ```
dpkg -i *thenameofyourpackage.deb*
``` 

It has been a while since I have installed anything on Ubuntu using dpkg, but if I am remembering correctly that should work.

i can download just fine, you guys are 2 steps behind what i really need help with,, here ill upload pics,, 

i hope veryone here helping notices the drawing ^_^ hehe,, well.. yeah thas where i have my problem.

---

### Post by jake16424 on 2007-08-10
> **jfinkels said:**
> I apologize, I was not paying attention to what you wrote, jake!

jake, the message you keep getting, may mean that you have another program open that is using the apt package manager. If you have any other instances of Synaptic, for example, or aptitude running, make sure that they are closed! You can only have one instance of apt package manager running.

If you try the command again without Synaptic running, and are still getting an error, please post it back here.



whats this aptitude

---

### Post by tjsullivan1 on 2007-08-10
Well if Adobe has their instructions right it is because you typed "/flashplayer-installer" nor "./flashplayer-installer". That period is key. Try going back into your terminal and typing ```
./flashplayer-installer
```.

---

### Post by tjsullivan1 on 2007-08-10
Judging by the screenshots you still need to extract the folder from the tarball. To do that click extract. If it asks you where put it on your desktop (or somewhere you can get to it). 

Then, go to your terminal. Type: ```
cd /home/jacob/install_flash_player_9_linux
```
This will change your directory to the flash folder. Then type: ```
./flashplayer-install
```

---

### Post by tjsullivan1 on 2007-08-10
> **jake16424 said:**
> whats this aptitude

Aptitude is the command line version of Synaptic. You can also use apt-get (my personal choice). It is possible then that jfinkel was correct that you don't have to download anything. If you have already done what I suggested above, don't worry. If not, try ```
apt-get install *flashplayer*
```

I'm not really sure what the package is called, but it should be something similar to that.

---

### Post by jake16424 on 2007-08-10
BELLOWS A WAR CRY THAT MAKES YOU QUAKE.


i have extracted the file, idk how many times, deleted it, then reextracted it, and no i didnt forget the "." ... grrr...=(

---

### Post by tjsullivan1 on 2007-08-10
I didn't mean to make you angry, but the screenshot is missing the "." 
Are you certain that you extracted the folder? That is another thing that hadn't been done yet in the screenshots.
Try jfinkels way with aptitude or apt-get.

---

### Post by jake16424 on 2007-08-10
u didnt.,, haha,, it takes alot to get me angry,, and,, people who try to help isnt one of the reasons i get angry,,

i havnt a clue on what todo with either approach mentioned by you just now..

---

### Post by tjsullivan1 on 2007-08-10
Okay. So let's start fresh. You have recently downloaded the *install.tar.gz* file onto your Desktop. Now, open terminal. Navigate to your desktop: ```
cd /~/Desktop
```
Remember commands are case sensitive (so the D must be capitalized in Desktop). Then type: ```
tar -xvfz *install.tar.gz*
```
This will extract the gunzipped file (onto the Desktop). Next, change you directory to the new folder that was created from the extraction: ```
cd */~/Desktop/install*
``` 
Now it is time to finally run the ./ function: ```
*./flashplayer-install*
```
**Please note that anything in italics may not be the proper name, you may have to modify it for the specific file name.**

---

### Post by jake16424 on 2007-08-10
> **tjsullivan1 said:**
> Okay. So let's start fresh. You have recently downloaded the *install.tar.gz* file onto your Desktop. Now, open terminal. Navigate to your desktop: ```
cd /~/Desktop
```
Remember commands are case sensitive (so the D must be capitalized in Desktop). Then type: ```
tar -xvfz *install.tar.gz*
```
This will extract the gunzipped file (onto the Desktop). Next, change you directory to the new folder that was created from the extraction: ```
cd */~/Desktop/install*
``` 
Now it is time to finally run the ./ function: ```
*./flashplayer-install*
```
**Please note that anything in italics may not be the proper name, you may have to modify it for the specific file name.**

first code gets me this far [CENTER]jacob@jacob-desktop:~$ cd /~/Desktop
bash: cd: /~/Desktop: No such file or directory
jacob@jacob-desktop:~$





[/CENTER]

---

### Post by tjsullivan1 on 2007-08-10
type: ```
ls
```
and ```
pwd
```
What does it say?

---

### Post by jake16424 on 2007-08-10
Desktop   Firefox_wallpaper.png  install_flash_player_9_linux
Examples  Incomplete             install_flash_player_9_linux.tar.gz
jacob@jacob-desktop:~$


and


/home/jacob
jacob@jacob-desktop:~$

---

### Post by tjsullivan1 on 2007-08-10
Okay. Disregard my earlier message to navigate to the desktop. Instead, it looks like you have the install folder that needs to be opened. So, type: ```
cd install_flash_player_9_linux
``` and then type: ```
./flashplayer-install
```. That should do it. If not, I'll get back to you tomorrow.

---

### Post by jake16424 on 2007-08-10
> **tjsullivan1 said:**
> Okay. Disregard my earlier message to navigate to the desktop. Instead, it looks like you have the install folder that needs to be opened. So, type: ```
cd install_flash_player_9_linux
``` and then type: ```
./flashplayer-install
```. That should do it. If not, I'll get back to you tomorrow.



bash: ./flashplayer-install: No such file or directory
jacob@jacob-desktop:~/install_flash_player_9_linux$




im going to bed, catch you guys all later.. just so u know, im gonig back to windows, so i can continue to download via Utorrent,, just for tonight,, ill be back to ubuntu tomorrow after noon.. tlak to you all later. =)

---

### Post by tjsullivan1 on 2007-08-10
Okay. I installed flash this morning and this is the exact code. After you have downloaded the install_flash_player_9_linux.tar.gz file to your DESKTOP. ```
root@Iuppiter:~# cd /home/tjsullivan1
root@Iuppiter:/home/tjsullivan1# ls
Desktop  Examples  test
root@Iuppiter:/home/tjsullivan1# cd Desktop
root@Iuppiter:/home/tjsullivan1/Desktop# ls
gcc-3.3.3.tar.gz  install_flash_player_9_linux.tar.gz
root@Iuppiter:/home/tjsullivan1/Desktop# mv install_flash_player_9_linux.tar.gz /home/tjsullivan1
root@Iuppiter:/home/tjsullivan1/Desktop# ls
gcc-3.3.3.tar.gz
root@Iuppiter:/home/tjsullivan1/Desktop# cd ..
root@Iuppiter:/home/tjsullivan1# ls
Desktop  Examples  install_flash_player_9_linux.tar.gz  test
root@Iuppiter:/home/tjsullivan1# tar -xvzf install_flash_player_9_linux.tar.gz 
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
root@Iuppiter:/home/tjsullivan1# ls
Desktop   install_flash_player_9_linux         test
Examples  install_flash_player_9_linux.tar.gz
root@Iuppiter:/home/tjsullivan1# cd install_flash_player_9_linux
root@Iuppiter:/home/tjsullivan1/install_flash_player_9_linux# ls
flashplayer-installer  flashplayer.xpt  libflashplayer.so
root@Iuppiter:/home/tjsullivan1/install_flash_player_9_linux# ./flashplayer-installer 

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla-firefox
dir= /usr/lib/mozilla-firefox


----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Browser installation directory = /usr/lib/mozilla-firefox

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.

root@Iuppiter:/home/tjsullivan1/install_flash_player_9_linux# 

```

---

### Post by walkerk on 2007-08-10
> **jake16424 said:**
> as far as i got E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

you have to close synaptic before running apt in the terminal

---

### Post by jfinkels on 2007-08-10
> **jake16424 said:**
> u didnt.,, haha,, it takes alot to get me angry,, and,, people who try to help isnt one of the reasons i get angry,,

i havnt a clue on what todo with either approach mentioned by you just now..

I *highly, highly, highly* suggest that you install programs using either 'aptitude', 'apt-get', or 'Synaptic' and I recommend that you learn how to do that FIRST before struggling through installing software using the terminal. These programs are front-ends for the APT package management system, which is the system that Ubuntu uses to download, install, and manage packages (which contain programs, libraries, and other data files). This is your first stop for installing ANY software.

Since we're having some difficulties using the terminal, I will tell you how to install flashplugin-nonfree through a GUI application.

1. Enable the multiverse repository (a database of packages which are not necessarily completely free and open source software) by going to "System > Administration > Software Sources" and selecting the check box next to "Software restricted by copyright or legal issues (multiverse)".
2. Open Synaptic Package Manager, located at "System > Administration > Synaptic Package Manager".
3. Press the "Reload" button.
4. Press the "Search" button.
5. Type in "flashplugin" and press enter.
6. Right click on the package "flashplugin-nonfree" and select "Mark for Installation".
7. Click Apply and go through the installation dialog.
8. When you're done, restart firefox and Flash will be installed and working.

If you need Java for a webpage, follow the same procedure, but search for and install the package "sun-java6-jre" or "sun-java5-jre" depending on what version of Ubuntu you are running.

I understand that this is all new (we were all beginners once). I appreciate that you are sticking with this. Remember to copy any output from the commands you run in the terminal here into the forums and wrap them in [ CODE ] tags to give us a better idea of what's going on in your computer (if you are running terminal commands).

---

### Post by jfinkels on 2007-08-11
How did it go, jake?

---

### Post by jake16424 on 2007-08-11
> **jfinkels said:**
> How did it go, jake?

sorry, i logged off last night, i sent a post about it,, i was tired,, so i let everyone know i was going to bed,, i havent tried your way yet,, ima try the code first then ima try the gui...

---

