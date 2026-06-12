---
title: "extracting file"
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by thepcdoctor on 2005-09-01
I've downloaded a large game file with a linux.run extension but have no idea what I do next. I'm guessing it's a self extracting archive but when I click on it I don't know what to open it with. Can someone walk me through this maze??

---

### Post by thepcdoctor on 2005-09-01
I should add that file is executable text file but when I 'run terminal', or 'run' it checks file integrity and then window closes and that's the end of it. Right clicking- properties and 'open with' gives me option of text editor or word?  Should there be something else here? What's going on??  Very confused...! Is the file corrupt or  am I doing something wrong?

---

### Post by sapo on 2005-09-01
just type it in a terminal:

```
sh file.run
```

change the file.run for your filename.. btw  i wonder what is that thing that you are trying to install :p

---

### Post by thepcdoctor on 2005-09-02
It's americas army. I'll give your suggestion a try. What's the 'sh' command?

---

### Post by TristanMike on 2005-09-02
America's Army eh? Awesome game, I just discovered it myself. Just follow these instructions, worked for me. [https://wiki.ubuntu.com/AmericasArmy](https://wiki.ubuntu.com/AmericasArmy)

---

### Post by thepcdoctor on 2005-09-02
Did that but no luck. Americas army file is on my desktop. What am I doing wrong? Do I need to navigate to the path?? If so how do I do that? Sorry if this is a stupid question. I am a complete linux novice.

theboss@ubuntu:~$ sudo sh ./armyops230-linux.run
sh: ./armyops230-linux.run: No such file or directory

---

### Post by Qrk on 2005-09-02
Did you cd into the correct directory? It also helps if you take the icon from your desktop and drag it into the terminal, because then it will remember where it is from.

---

### Post by TristanMike on 2005-09-02
[QUOTE=thepcdoctor]Did that but no luck. Americas army file is on my desktop. What am I doing wrong? Do I need to navigate to the path?? If so how do I do that? Sorry if this is a stupid question. I am a complete linux novice.

theboss@ubuntu:~$ sudo sh ./armyops230-linux.run
sh: ./armyops230-linux.run: No such file or directory[/QUOTE]There are no stupid questions. Every question is just a step in learning. Yes, you would want to change to the directory where the file is located. In this case it would be:```
cd ./Desktop
```then it should go something like this```
sudo sh ./armyops230-linux.run
```of course, this is from the terminal. Should install for you. Let us know if there are any problems.

I have found this site [http://www.tuxfiles.org/](http://www.tuxfiles.org/) to give a basic but useful explanation of navagating the terminal.

---

### Post by thepcdoctor on 2005-09-02
ok...did that and got this message. Does this mean file is corrupt?  

Verifying archive integrity...Error in MD5 checksums: 594bca58c509052ce6719fb19e583d44 is different from bcae59c8dcd4a48d11e6d06bfa070a09
theboss@ubuntu:~/Desktop$

---

### Post by Qrk on 2005-09-02
Yes. It means you didn't get the whole file when you downloaded it. You can just delete that one and download the file again. Sometime larger files are really hard to download without any problems, especially if you have a slower connection.

---

### Post by thepcdoctor on 2005-09-03
Well I downloaded game again, it started to install to a point and then I got a message "no write permission to /usr/local/games" and installation aborted. What do I need to do now? Talk about dramas just to install a game!

---

### Post by thepcdoctor on 2005-09-03
Answered my own questions guys...an hours research but now know that you have to login as root user to install. Can this be set as default or is it not advisable?

---

### Post by Wolki on 2005-09-03
[QUOTE=thepcdoctor]Answered my own questions guys...an hours research but now know that you have to login as root user to install. Can this be set as default or is it not advisable?[/QUOTE]

This is not advisable. To temporarily gain root powers, start your command with "sudo "

Always running as root is a severe security problem.

---

### Post by thepcdoctor on 2005-09-03
ok...this is getting ridiculous. HOW DIFFICULT CAN IT BE TO INSTALL  A PROGRAM??
I've entered this in terminal:

theboss@ubuntu:~$ sudo -s -H
root@ubuntu:/home/theboss # sudo /home/theboss/Desktop/armyops230-linux.run

File integrity check is good
File uncompresses, asks me where I want to put it etc...installs and then....READ FAILURE ON FILE.TAR.BZ2

The setup program seems to have failed on x86/glibc-2.1                &#9474;
        &#9474;                                                              &#9474;
Fatal error, no tech support email configured in this setup            &#9474;
root@ubuntu:/home/theboss #  


Can anyone please explain what is going on here? Linux is sending me crazy!

---

### Post by TristanMike on 2005-09-03
[QUOTE=thepcdoctor]ok...this is getting ridiculous. HOW DIFFICULT CAN IT BE TO INSTALL  A PROGRAM??
I've entered this in terminal:

theboss@ubuntu:~$ sudo -s -H
root@ubuntu:/home/theboss # sudo /home/theboss/Desktop/armyops230-linux.run

File integrity check is good
File uncompresses, asks me where I want to put it etc...installs and then....READ FAILURE ON FILE.TAR.BZ2

The setup program seems to have failed on x86/glibc-2.1                &#9474;
        &#9474;                                                              &#9474;
Fatal error, no tech support email configured in this setup            &#9474;
root@ubuntu:/home/theboss #  


Can anyone please explain what is going on here? Linux is sending me crazy![/QUOTE]At the risk of sounding rude, you didn't do anything that we have advised you. First off, no one gave you the "sudo -s -H" command to run, so why did you run it? RUNNING AS ROOT IS NOT ADVISABLE, YOU ARE IN HARMS WAY! "sudo" means "I am root for this command and this command only" more or less. So try and start again, please don't get frustrated, it can be very frustrating but patience is a virtue. Try all of this from the beginning step by step.

First make sure the file is on your desktop. If it is, proceed to step 2, if not, move the file there.

Second: Open the terminal and from the "theboss@ubuntu:~$" line, type this exactly ```
cd ./Desktop
```Third: Your terminal should look like this ```
theboss@ubuntu:~/Desktop$
``` at this point type this ```
sudo sh ./armyops230-linux.run
```This should do it, just sit back and let it install. You should find "armyops" under Applications->Other->armyops. If you have any questions or problems with this, just let us know :)

As a side note to copy/paste in the terminal it is "shift+Ctrl+c" and "shift+Ctrl+v" respectively.

---

### Post by thepcdoctor on 2005-09-04
Thanks for helping me with this. I agree I have found this process very frustrating, but I like what I have seen of linux so far (except for its complexity that is...but I suppose it's like learning a new language...you have to put in the effort to become fluent).  
I used the sudo s h command because reading various posts led me to believe that the only way to install was to have root access as admin. This command was taken from the ubuntu unofficial guide. I confess I have no idea what I am doing. Why is this command not a good thing to execute? 

I followed your instructions and as last time installation commenced and then after some time 'read failure on armyops230.tar.bz2'

The setup program seems to have failed on x86/glibc-2.1                                                                             
Fatal error, no tech support email configured in this setup            
theboss@ubuntu:~/Desktop$ 

What does this mean?

---

### Post by TristanMike on 2005-09-04
It's no problem at all. Those are some good analogies. There could have been a reason those posts we suggesting to do this, however, "sudo" should be all you need in Ubuntu, just throw that on the beginning of whatever command you wish, and it will be run as "root" 

Hmm, where did you get the file? What is the file name *exactly*? I had no problems with the file I downloaded. Perhaps you could give a little more of the errors in the terminal, how far does it go? Does it start doing anything at all? I suppose most importantly, what are you system specs? Video Card? I'm kinda getting stumped but lets get just a little more info first.

EDIT: Anybody else with any ideas, feel free to jump in at any time :)

---

### Post by thepcdoctor on 2005-09-04
The file is 'armyops230-linux.run'. I've downloaded it 3 times from different sources, the install starts and then after some time the error message comes up and that's the end of it. 'read failure on armyops230.tar.bz2'  

Hitting enter brings up: The setup program seems to have failed on x86/glibc-2.1 Fatal error, no tech support email configured in this setup 
theboss@ubuntu:~/Desktop$. This is the only message I get.  Should I be looking somewhere else to?
It seems to spit the dummy at different stages, sometimes after a minute or 2, sometimes after much longer.

System specs:

AMD Athlon 2200
ASUS A7V8X MoBo
ATi 9800 128 video
768 RAM
40gig HDD
Ubuntu is only software

---

### Post by TristanMike on 2005-09-05
Ahh, now I'm thinking that your video card drivers need to be updated. Have you done so since installing? This may be your problem so here might be some reading for you...[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557) and here [http://www.ubuntuforums.org/showthread.php?t=22496](http://www.ubuntuforums.org/showthread.php?t=22496)

I'm kinda grasping at straws here, anyone else please?

---

### Post by thepcdoctor on 2005-09-06
I followed the advice here about updating video drivers: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
I'm not that it was successful though. I would have thought that the driver would not have been an issue until the game was launched??
Nonetheless I'll study those links you gave me.

---

### Post by thepcdoctor on 2005-09-06
I thought I had installed drivers but checking it would seem not:
theboss@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I'll try again. What's my kernal version and how to I find it? As in $ sudo apt-get install linux-restricted-modules-<your-kernel-version> xorg-driver-fglrx? 

Is this command the same as sudo apt-get install xorg-driver-fglrx?

Another question- I've swtiched on repositories. When upgrading how do I know what I should be uprading and what I don't need/should not. Do I switch off other repositories before uprading. If so, how do I do this?

---

### Post by TristanMike on 2005-09-06
[QUOTE=thepcdoctor]I followed the advice here about updating video drivers: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
I'm not that it was successful though. I would have thought that the driver would not have been an issue until the game was launched??
Nonetheless I'll study those links you gave me.[/QUOTE]Perhaps, you may be right, however it may dependent on a newer package that you get with the update. Like I said, grasping at straws. I'm suprised no one else has jumped in yet.

---

### Post by thepcdoctor on 2005-09-07
Can someone help me with the above queries?

---

### Post by matthateswindows on 2005-09-07
[QUOTE=TristanMike]There are no stupid questions. Every question is just a step in learning. Yes, you would want to change to the directory where the file is located. In this case it would be:```
cd ./Desktop
```then it should go something like this```
sudo sh ./armyops230-linux.run
```of course, this is from the terminal. Should install for you. Let us know if there are any problems.

I have found this site [http://www.tuxfiles.org/](http://www.tuxfiles.org/) to give a basic but useful explanation of navagating the terminal.[/QUOTE]
 I recently gave up on windows 2000 and installed the latest Kubuntu, but I don't really understand the software installation process. Can I use this same method to install file.tar.gz from my USB key? Do I extract the file to my desktop first? I'm trying to install GIMP and a couple of games.

---

