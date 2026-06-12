---
title: "trying to install X-Lite,for over 24 hrs!!"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by bigislandman on 2008-02-01
Hi 
I am almost at the point of no return, I installed 7.10 because I am sick of MS, i am one of 6 PC users in the house, the only one to go Linux. They think I am stupid doing this, I  am beginning to think they are right.
This is my second post, the first didn't get a response, but the forum has been helpful , but will not cure the problems. I have gone to Counterpath.com and downloaded the Linux version of X-Lite ( i dont want to use Ekiga, I have been using X-Lite for the past 4 years)
I have tried saving to disk and archive manager, it makes no difference in the long run , I then open it , I have double clicked on it , extracted xten-xlite I have gone into the terminal and tried many versions of get it to install inc sudo apt-get install xten-xlite then swaped that for extensoftphone as the tell you in the read me file , I have tried sudo make install etc, get nowhere, here are a couple of the many  trys over the past 24 hrs
hornysettler@hornysettler:~$ sudo make install extensoftphone
make: *** No rule to make target `install'.  Stop.
hornysettler@hornysettler:~$ sudo apt install xten-xlite
sudo: apt: command not found
hornysettler@hornysettler:~$ sudo make install xten-xlite
make: *** No rule to make target `install'.  Stop.
hornysettler@hornysettler:~$ sudo apt-get install xten-xlite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xten-xlite
hornysettler@hornysettler:~$ sudo apt-get install xtensoftphone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xtensoftphone
hornysettler@hornysettler:~$ sudo apt-get install ./xtensoftphone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package .
hornysettler@hornysettler:~$ 

I have tried this link..
[http://monkeyblog.org/ubuntu/installing/#installing_with_terminal](http://monkeyblog.org/ubuntu/installing/#installing_with_terminal)

I have tried this as well.
[https://help.ubuntu.com/7.10/add-applications/C/advanced.html](https://help.ubuntu.com/7.10/add-applications/C/advanced.html)

Last night I secretly reloaded the whole operating system and started clean. I guess I must stupid.
My brother-in-law is an ex techy with the BBC, he wishes me luck then shakes his head and says Linux has broken many of his friends in the past.
Can anyone help please?  i would go out and buy a book but its been snowing for the last 10hrs.

---

### Post by emarkd on 2008-02-01
Lets clear up a bit of confusion.  You can only use apt/aptitude/Synaptic to install .deb files.  If you downloaded a .deb file, just double-click it and it'll install.  If you downloaded a .tar that contains source code, you'll have to compile it.  Here's a good tutorial: [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

If you'll give us a bit more information about what you've downloaded, we'll try to help more.  Don't give up yet!

---

### Post by emarkd on 2008-02-01
You could've also downloaded a file that contains neither.  In that case, there will be some sort of install script or something and you'll have to read the readme to find out what to do with it.

---

### Post by emarkd on 2008-02-01
Um, maybe I'm missing something, but at [http://www.counterpath.com/x-lite.html](http://www.counterpath.com/x-lite.html) I only see Windows and Mac supported.  Am I missing something?

---

### Post by bigislandman on 2008-02-01
Thanks for the reply .
this is the screen with a linux version
[http://www.counterpath.com/x-lite-downloadsurvey.html](http://www.counterpath.com/x-lite-downloadsurvey.html)

you click on down load , put in a name/email then click continue and you then see 3 options 
MS
Mac
Linux

I dwnloaded the Linux version
This is the read me txt


[I][U]
* X-Lite 2.0 Linux Release Notes *
**********************************

INSTALLATION:

Untar the file:
> tar -zxvf X-Lite_Install.tar.gz

This should expand the files into xten-xlite directory.
> cd xten-xlite

The executable is xtensoftphone, it should already have +x permission. If it does not, change the permission:
> chmod +x xtensoftphone

To run the executable:
> ./xtensoftphone

Copy the executable to a defined $PATH if you so wish.


NOTE:
Executable is tested to work with:
OS: Fedora Core 3, Suse 9.2
Platform: i386, Athlon, i686
Sound Driver: snd_via82xx, snd_usb_audio, snd_intel8x0 (OSS emulation)


KNOWN ISSUES:
- Using GSM codec might crash on some platform combination.

Use at your own risk!! Please report any bug/problem to xlite linux forum. 
[/U][/I]Click on the '?' on the top left to open a link to the support forum.

---

### Post by emarkd on 2008-02-01
Ah, so according to that there's no real installation needed.  That's pretty common.  Did you try doing those steps?  If you don't understand them, just ask and we'll be happy to help.

---

### Post by bigislandman on 2008-02-01
Ok
Have dumped everything, and started again.
Downloaded the file and saved to disk , not archive manager, then clicked on open.

I am left with the file x-lit_Install.tar.gz. on the desktop

I click on that and get a file on the desktop xten-xlite

double click on that and a file browser window opens with the read me txt , xtensoftphone and xten-xlite.

open the read me and read

open terminal

type as instructed to un tar the file

this what you get..

hornysettler@hornysettler:~$ tar -zxvf X-Lite_Install.tar.gz
tar: X-Lite_Install.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 

tried the others as well

hornysettler@hornysettler:~$ tar -zxvf X-Lite_Install.tar.gz
tar: X-Lite_Install.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
hornysettler@hornysettler:~$ xtensoftphone
bash: xtensoftphone: command not found
hornysettler@hornysettler:~$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~$ chmod +x xtensoftphone
chmod: cannot access `xtensoftphone': No such file or directory
hornysettler@hornysettler:~$ 

double clicking on the xtensoftphone does nothing, right click on it and gointo permission and there is no way to enter , 

So do i have to write sudo apt_make instal xtenphone?

Ok, maybe I have lost the plot here , 

tar: Error exit delayed from previous errors
hornysettler@hornysettler:~$

---

### Post by emarkd on 2008-02-01
Ok, the confusion is that when you open the Terminal,you're at your home directory, not your Desktop, so to use those commands, you'll have to first cd Desktop.  But you can do all of that from the GUI.  If you right-click on the tarball and select, extract, it'll handle the first command.  Then double-click on the new folder it creates, find xtensoftphone and double-click it.  Let me know what happens.

---

### Post by bigislandman on 2008-02-01
I get down to xtensoftphone, double click on it and i get a new message, could not open archive type not supported, with a no entry sign

---

### Post by emarkd on 2008-02-01
Hmm... Ok, lets go back to the commandline.  You've already got it extracted, so you can skip the first part.  You'll change directory to the proper place by doing:

```
cd Desktop/X-Lite_Install
```

or whatever the extracted directory is called.  Then, do

```
./xtensoftphone
```

What does that give you?

---

### Post by emarkd on 2008-02-01
If that doesn't work, give us the exact error message.  I downloaded the package from your link and it works fine.  I extract and double-click and it starts right up.

---

### Post by bigislandman on 2008-02-01
This is what I get

hornysettler@hornysettler:~$ cddesktop
bash: cddesktop: command not found
hornysettler@hornysettler:~$ cd Desktop/X-Lite_Install
bash: cd: Desktop/X-Lite_Install: No such file or directory
hornysettler@hornysettler:~$ cd desktop/xten-xlite_install
bash: cd: desktop/xten-xlite_install: No such file or directory
hornysettler@hornysettler:~$ cd Desktop/xtensoftphone_install
bash: cd: Desktop/xtensoftphone_install: No such file or directory
hornysettler@hornysettler:~$ cd Desktop/X-lite_Install
bash: cd: Desktop/X-lite_Install: No such file or directory
hornysettler@hornysettler:~$ cd Desktop/xten-xlite.tar
bash: cd: Desktop/xten-xlite.tar: Not a directory
hornysettler@hornysettler:~$ cd Desktop/xten-xlite_install
bash: cd: Desktop/xten-xlite_install: No such file or directory
hornysettler@hornysettler:~$ 

I have tried a number of ways.. no luck so far

I will clear everything and download a new lot to and save to disk , then try and go from ther again, thanks for your patience, if you need any snow !!

---

### Post by emarkd on 2008-02-01
You don't have to do that.  You're just trying to change into the extracted directory on your desktop, so you'll have to find what it's named.  I was just giving an example using a guess.  When I extracted it here, it became xten-xlite.  If yours is the same, you'd do

```
cd Desktop/xten-xlite
```

and then run the other command.

---

### Post by bigislandman on 2008-02-01
still nothing but cant find file

hornysettler@hornysettler:~$ cd Desktop./xtensoftphone_install
bash: cd: Desktop./xtensoftphone_install: No such file or directory
hornysettler@hornysettler:~$ cd Desktop/xtensoftphone_install
bash: cd: Desktop/xtensoftphone_install: No such file or directory
hornysettler@hornysettler:~$ chmod +x xtensoftphone_install
chmod: cannot access `xtensoftphone_install': No such file or directory
hornysettler@hornysettler:~$ 


On my desk top I have 3 files
first is xten-xlite.tar  5.6 MB  tar file
The second file is
xten-xlite  11.3 MB 
third is
xtensoftphone    5.6MB

Clicking on the xtensoftphone file does nothing

---

### Post by emarkd on 2008-02-01
Did you try 

```
cd Desktop/xten-xlite
```

---

### Post by bigislandman on 2008-02-01
so this is something new

hornysettler@hornysettler:~$ cd Desktop/xten-xlite
hornysettler@hornysettler:~/Desktop/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/Desktop/xten-xlite$ chmod +x xtensoftphone
chmod: cannot access `xtensoftphone': No such file or directory
hornysettler@hornysettler:~/Desktop/xten-xlite$

---

### Post by emarkd on 2008-02-01
Did you do something after you extracted that file?  That should be there.  From that same location, what do you get if you do:

```
ls -l
```

---

### Post by bigislandman on 2008-02-01
I get this

hornysettler@hornysettler:~/Desktop/xten-xlite$ ls -l
total 8
-rw-r--r-- 1 hornysettler hornysettler  872 2005-05-12 17:45 README
drwxr-xr-x 3 hornysettler hornysettler 4096 2008-02-01 16:08 xten-xlite
hornysettler@hornysettler:~/Desktop/xten-xlite$

---

### Post by emarkd on 2008-02-01
ok, that last one is another directory.  See where its line starts with a 'd', so do

```
cd xten-xlite
```

and try to run ./xtensoftphone again.

---

### Post by bigislandman on 2008-02-01
-rw-r--r-- 1 hornysettler hornysettler  872 2005-05-12 17:45 README
drwxr-xr-x 3 hornysettler hornysettler 4096 2008-02-01 16:08 xten-xlite
hornysettler@hornysettler:~/Desktop/xten-xlite$ cd xten-xlite
hornysettler@hornysettler:~/Desktop/xten-xlite/xten-xlite$ 
hornysettler@hornysettler:~/Desktop/xten-xlite/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/Desktop/xten-xlite/xten-xlite$ /extensoftphone
bash: /extensoftphone: No such file or directory
hornysettler@hornysettler:~/Desktop/xten-xlite/xten-xlite$ 


Could it be that  this Ubuntu version  just cant run E-Lite?

---

### Post by emarkd on 2008-02-01
No, you're trying to access files that aren't there.  That's why it says No such file or directory.  You'll have to do 

```
ls -l
```

to see what's actually in the directory.

---

### Post by bigislandman on 2008-02-01
I started all over again and got much further , then ...

this is where I am

hornysettler@hornysettler:~/Desktop$ ls -l
total 2052
-rw-r--r-- 1 hornysettler hornysettler 2094582 2008-02-01 17:56 X-Lite_Install.tar.gz
hornysettler@hornysettler:~/Desktop$ tar -zxvf X-Lite_Install.tar.gz
xten-xlite/README
xten-xlite/xtensoftphone
hornysettler@hornysettler:~/Desktop$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/Desktop$ chmod :x xtensoftphone
chmod: invalid mode: `:x'
Try `chmod --help' for more information.
hornysettler@hornysettler:~/Desktop$

---

### Post by emarkd on 2008-02-01
Just do:

```
xten-xlite/xtensoftphone
```

That takes care of the directory and the executable at once.

---

### Post by cubeist on 2008-02-01
Big Island Man.  I appreciate the difficulty you are having, but at this point, before we can really do much more to help you I would strongly advise that you take 15 minutes and view some tutorials that explain the basics of navigating in the terminal.  Once you know how to get around and view files, opening the program will be very easy.

Here are a couple short tuts I found for you...

[http://www.genetics.wayne.edu/dwomble/unixintro.html](http://www.genetics.wayne.edu/dwomble/unixintro.html)

and a list of the commands

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by bigislandman on 2008-02-01
that did not work

this is where I am now

hornysettler@hornysettler:~/Desktop$ ls -l
total 2056
-rw-r--r-- 1 hornysettler hornysettler 2094582 2008-02-01 17:56 X-Lite_Install.tar.gz
drwxr-xr-x 2 hornysettler hornysettler    4096 2008-02-01 18:00 xten-xlite
hornysettler@hornysettler:~/Desktop$ 

should the next command be to install  xtensoftphone, eg a sudo apt install xtensoftphone?

---

### Post by emarkd on 2008-02-01
No, you're not going to install it.  It's a standalone binary.  Just do

```
xten-xlite/xtensoftphone
```

to execute it.

---

### Post by bigislandman on 2008-02-01
Hmmm   didnt like that

hornysettler@hornysettler:~/Desktop$ ls -l
total 2056
-rw-r--r-- 1 hornysettler hornysettler 2094582 2008-02-01 17:56 X-Lite_Install.tar.gz
drwxr-xr-x 2 hornysettler hornysettler    4096 2008-02-01 18:00 xten-xlite
hornysettler@hornysettler:~/Desktop$ xten-xlite/xtensoftphone
bash: xten-xlite/xtensoftphone: No such file or directory
hornysettler@hornysettler:~/Desktop$

---

### Post by emarkd on 2008-02-01
I'm trying here but I don't really know what else to say.  I downloaded the software myself to have a better idea what's going on here and it all works fine on my end...

you could try changing to that xten-xlite directory and running ls -l to see what's there...

---

### Post by emarkd on 2008-02-01
You can even get there fine from the GUI.  After you've extracted the file, double-click the xten-xlite folder to open it in your file browser.  You'll see xtensoftphone sitting right there.  Double-click it and it just runs.

Are you sure you downloaded the Linux version...

---

### Post by cubeist on 2008-02-01
Here is another technique.  On your desktop open the folder and navigate to where the actual program binary is (it has a different icon than folders or files).

Once you know where it is you can repeat the path in the terminal

just go slow and cd into a directory then use ls -l to see what is there and then cd into the next directory... once you see the program, then execute it with
./name_of_program

---

### Post by bigislandman on 2008-02-01
dont know why  either.

hornysettler@hornysettler:~/Desktop$ ls -l
total 2056
-rw-r--r-- 1 hornysettler hornysettler 2094582 2008-02-01 17:56 X-Lite_Install.tar.gz
drwxr-xr-x 2 hornysettler hornysettler    4096 2008-02-01 18:00 xten-xlite
hornysettler@hornysettler:~/Desktop$ xtensoftphone
bash: xtensoftphone: command not found
hornysettler@hornysettler:~/Desktop$ +x xtensoftphone
bash: +x: command not found
hornysettler@hornysettler:~/Desktop$ ls -l
total 2056
-rw-r--r-- 1 hornysettler hornysettler 2094582 2008-02-01 17:56 X-Lite_Install.tar.gz
drwxr-xr-x 2 hornysettler hornysettler    4096 2008-02-01 18:00 xten-xlite
hornysettler@hornysettler:~/Desktop$ 


Thank you for all your help, I no you put a lot into this , I has to weigh up .. should spend more time ( after a nights sleep, re load the whole Op Systma agin in case there is a bug , the disk and drive did check out OK, or just stick XP Media back on, and leave it for a year or two.
I need the phone for my work, .
I f anyone has any bright ideas, I am going to grab a pizza and then have one last look at it before bed

Thanks for you time
regards
bigislandman

---

### Post by nickpaton on 2008-02-01
OK came into this rather late.

I've also installed it to see what happened.

Here are the exact steps:

Download X-Lite_Install.tar.gz to Desktop

Double left click > Extract icon

Extract to Desktop.

Resultant folder on Desktop is

xten-xlite

First you need to move to the Desktop

Open Terminal and type:

```
cd Desktop
```

Now you need to move to xten-xlite folder:

```
cd xten-xlite
```

My Terminal now reads 

```
nick@nick-laptop:~/Desktop/xten-xlite$
```

In Terminal type 

```
ls -l
```

I now see:

```
total 5784
-rw-r--r-- 1 nick nick     872 2005-05-12 22:45 README
-rwxr-xr-x 1 nick nick 5903204 2005-05-12 19:51 xtensoftphone
```

With xtensoftphone in green

Once again in the Terminal type:

```
./xtensoftphone
```

This loaded xtensoftphone and the install wizard etc.

It's as easy as that!!

Good luck and give this another go.

Nick

---

### Post by nickpaton on 2008-02-01
Once you have the set up Wizard (let's hope now!!)  if you have an onboard mic, you may find it doesn't work in the Wizard mic setup section.

Try this:

in a terminal type:

```
alsamixer
```

This will open up a window similar to an audio equaliser and should include the mic.

You may need to turn up the mic volume.  Use left / right arrow keys to move to the mic section.

use the up / down arrows to increase or decrease the mic volume.

Once the level is set to around 2/3rds within alsamixer, press Esc key to exit and recheck the mic audio wizard.

HTH

Good luck

Nick

---

### Post by bigislandman on 2008-02-01
Thanks when I finish my pizza, I will give it a try

---

### Post by bigislandman on 2008-02-01
Thanks nick 

this is what I got , I did try a number of other things as you can see.

hornysettler@hornysettler:~/xten-xlite$ chmod +x xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ /xtensoftphone
bash: /xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ ls -l
total 5784
-rw-r--r-- 1 hornysettler hornysettler     872 2005-05-12 17:45 README
-rwxr-xr-x 1 hornysettler hornysettler 5903204 2005-05-12 14:51 xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ ls -l
total 5784
-rw-r--r-- 1 hornysettler hornysettler     872 2005-05-12 17:45 README
-rwxr-xr-x 1 hornysettler hornysettler 5903204 2005-05-12 14:51 xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ /xtensoftphone
bash: /xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ +x xtensoftphone
bash: +x: command not found
hornysettler@hornysettler:~/xten-xlite$ ,/xtensoftphone
bash: ,/xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ 
hornysettler@hornysettler:~$ cd xten-xlite
hornysettler@hornysettler:~/xten-xlite$ ls -l
total 5784
-rw-r--r-- 1 hornysettler hornysettler     872 2005-05-12 17:45 README
-rwxr-xr-x 1 hornysettler hornysettler 5903204 2005-05-12 14:51 xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ /xtensoftphone
bash: /xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ ls -l
total 5784
-rw-r--r-- 1 hornysettler hornysettler     872 2005-05-12 17:45 README
-rwxr-xr-x 1 hornysettler hornysettler 5903204 2005-05-12 14:51 xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ chmod +x xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ /xtensoftphone
bash: /xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ ls -l
total 5784
-rw-r--r-- 1 hornysettler hornysettler     872 2005-05-12 17:45 README
-rwxr-xr-x 1 hornysettler hornysettler 5903204 2005-05-12 14:51 xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ ls -l
total 5784
-rw-r--r-- 1 hornysettler hornysettler     872 2005-05-12 17:45 README
-rwxr-xr-x 1 hornysettler hornysettler 5903204 2005-05-12 14:51 xtensoftphone
hornysettler@hornysettler:~/xten-xlite$ /xtensoftphone
bash: /xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ +x xtensoftphone
bash: +x: command not found
hornysettler@hornysettler:~/xten-xlite$ ,/xtensoftphone
bash: ,/xtensoftphone: No such file or directory
hornysettler@hornysettler:~/xten-xlite$ 

It worked up to a point. then nothing when it should have loaded

---

### Post by bigislandman on 2008-02-02
I am toataly hacked off, its now 12.37 
This is what I have after reloading the whole system as well

Please can any body offer any explanation and or help

This is what I have , and it just will not find the file!!
hornysettler@hornysettler-laptop:~/Desktop$ cd xten-xlite
hornysettler@hornysettler-laptop:~/Desktop/xten-xlite$ ls -l
total 5788
-rw-r--r-- 1 hornysettler hornysettler     872 2005-05-12 17:45 README
-rwxr-xr-x 1 hornysettler hornysettler 5903204 2005-05-12 14:51 xtensoftphone
drwxr-xr-x 2 hornysettler hornysettler    4096 2008-02-02 00:30 xten-xlite
hornysettler@hornysettler-laptop:~/Desktop/xten-xlite$ ./xtensoftphone
bash: ./xtensoftphone: No such file or directory
hornysettler@hornysettler-laptop:~/Desktop/xten-xlite$ /xtensoftphone
bash: /xtensoftphone: No such file or directory
hornysettler@hornysettler-laptop:~/Desktop/xten-xlite$ +x xtensoftphone
bash: +x: command not found
hornysettler@hornysettler-laptop:~/Desktop/xten-xlite$ xtensoftphone
bash: xtensoftphone: command not found
hornysettler@hornysettler-laptop:~/Desktop/xten-xlite$ 


XP is looking mighty good at the moment, I dont want to go back , but if I cant  run this there is no advantage for me

Thanks to all those who have helped so far

---

### Post by nickpaton on 2008-02-02
I'm determined to get this working for you!

I had missed out changing to Desktop and then to xten-xlites folder, but I see you realised that.

I am doing a complete HOWTO with pictures, which I'll post a link to in a few hours.  This will also include setting up alsamixer and creating a Desktop launcher for Xlite.

It looks a neat program and at the moment I cannot see why it's not installing properly for you.

Get back to you in a few hours!

Nick

---

### Post by nickpaton on 2008-02-02
Here's a step by step Howto for installing X-Lite, setting it up, and creating a Desktop start up icon:

[http://nickpaton.fireflyinternet.co.uk/downloads/Installing Xlite.doc]("http://nickpaton.fireflyinternet.co.uk/downloads/Installing Xlite.doc")

You may well have a lot of further questions.  Please feel free to ask at any time.

Good Luck

Nick

---

### Post by cubeist on 2008-02-02
Excellent, excellent job Nick Paton.  You really went above and beyond.  I have been a unix and ubuntu linux user for a long time and I learned something new with your ALSA Mixer info.  I hope this works for him.

:guitar:  Rock On! \\:D/

---

### Post by nickpaton on 2008-02-02
Thanks and it's a pleasure Cubeist.  I think I used something similar when first learning about Alsa.

Nick

---

### Post by tigerhawk33 on 2008-04-07
I think the library file is missing, so try this in the terminal:

sudo apt-get install libstdc++5

This will get you the right lib file to run X-Lite.

Now go to the folder on your desktop screen, open it, double click on the xtensoftphone icon and it should start from there.

---

