---
title: "Ubuntu+Sony VAIO VGN FS315M Problemssss"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by hbayar_morph on 2007-02-19
I was a Windows freak, until Vista came out. And then... it disappointed me. :) I think you guys know why.

Ok, After this i looking for something new, interesting, blah blah... And i found Ubuntu (i saw some video on youtube, metcafe) I'm completely new to Ubuntu, even Linux. I installed Ubuntu 6.10 on my Vaio, but it doesn't recognize the drivers, like Video, Audio, Wlan, Memory stick. 

I hope you guys will help me.:) :)

---

### Post by aberry5555 on 2007-02-19
Could you be a little more specific with your answers, did you get any error messages or are you just experiencing slow graphics and no sound? Installing drivers in Ubuntu is, unfortunately, not as simple as in windows yet and so any extra information about your problems will be helpful.

Also, after you've posted you might consider seperating these out in to different posts, ie the video problems on one, the sound on another etc. as people tend to be more helpful if the thread follows one line of thought rather than several. 

Please post back any error messages you recieve or, alternatively, how it is behaving as opposed to how it should behave.

---

### Post by hbayar_morph on 2007-02-19
Tn, Ok, I will

I don't know how to install audio driver (Realtek ALC260)
I downloaded some drivers from [realtek](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC). And unziped, I found readme, but couldn't understand what it saying. :( Reame contains :
[I][I]...
  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code and install the driver
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Install ALSA Lib
        a. tar jxvpf alsa-lib-1.0.xx.tar.bz2
        b. cd alsa-lib-1.0.xx
        c. ./configure 
        d. make
        e. make install

Step 5. Install ALSA Utility
        a. tar jxvpf alsa-utils-1.0.xx.tar.bz2
        b. cd alsa-utils-1.0.xx
        c. ./configure
        d. make
        e. make install

Step 6. Run ALSA auto configuration
        ./alsaconf

Step 7. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already installed)
        excute alsamixer...
[/I][/I]
I could do only "unzip" :P What is next? How to do it? What is these are?

---

### Post by n8bounds on 2007-02-19
make and make install are commands given to you by the package build-essential, just 
```
 sudo apt-get install build-essential 
```
and then you will have them...did you search these forums for people with similar hardware as you?  certainly you are not the first ubunter to have a VAIO.....

---

### Post by rggavubt on 2007-02-20
You might want to start here first :

[http://monkeyblog.org/ubuntu/installing/#package_manager](http://monkeyblog.org/ubuntu/installing/#package_manager)

These commands are entered by going to Applications, Accessories, Terminal.  Here is a list of Linux commands :

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Hope this helps and good luck.  When entering commands I usually open the terminal and copy and paste commands from the instruction which is also open, so there are no typos.  Some installs require that you install dependency packages via System, Administration, Synaptic.  The above URL talks about Synaptic.

---

### Post by hbayar_morph on 2007-02-20
Thanx to all

> **n8bounds said:**
> ```
 sudo apt-get install build-essential 
```
and then you will have them..

I used Terminal, is it right. And then something like this:

```
hoodoo@hoodoo-laptop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2573kB/7934kB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com edgy/main g++-4.1 4.1.1-13ubuntu5 [2573kB]
Fetched 224kB in 15s (14.2kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 107162 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.17.1-50.50_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.4-1ubuntu12.3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.1-6ubuntu3_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.17.1-50.50) ...
Setting up libc6-dev (2.4-1ubuntu12.3) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up libstdc++6-4.1-dev (4.1.1-13ubuntu5) ...
Setting up g++-4.1 (4.1.1-13ubuntu5) ...
Setting up g++ (4.1.1-6ubuntu3) ...

Setting up build-essential (11.3) ...
hoodoo@hoodoo-laptop:~$ 

```

Is it finished yet? still no sound...

---

### Post by hbayar_morph on 2007-02-20
I wasn't sure and i did it again. It shows something like:

```
hoodoo@hoodoo-laptop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hoodoo@hoodoo-laptop:~$ 

```

It seems like done everything. But still no sound, How to enable sound? What is next? :)

---

### Post by getaceres on 2007-02-20
I don't know about sound but for the wireless, look at the network configuration utility (with the wireless switch turned on, of course). If it shows a wireless lan adapter, then your wireless it's working but it's not configured.
For the graphic card install the latest nvidia drivers installing this package:

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb)

then enter in a terminal with ctrl+alt+f1, login and run

sudo envy

just follow the instructions in the script.

---

### Post by Xanadu on 2007-02-20
I use a Vaio and didn't have to install any drivers - everything worked out the box.

For sound try the following:
1. Right-click on your speaker icon at the top right-hand corner;
2. Open Volume Control
3. Edit->Preferences
4. Check "External Amplifier" (should be near the bottom of the list)
5. Click the "Switches" tab
6. Uncheck "External Amplifier" if it's checked

If it was checked, that was probably your problem. Sound should play now unless you broke it with your alsa stuff.

Remember that Linux isn't like Windows - you don't usually have to install millions of drivers and reboot twenty times to get everything working. Most modern hardware will work straight from install. If it's not working, it's more likely a simple problem rather than a complex one.

---

### Post by hbayar_morph on 2007-02-21
@Xanadu;2186299

Tnx, it works now.:guitar:

---

