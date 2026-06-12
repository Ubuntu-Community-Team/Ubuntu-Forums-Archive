---
title: "Installing/compiling a program from its source"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by viviena on 2006-02-21
**EDITED** title to better reflect [my new problem]("http://ubuntuforums.org/showthread.php?p=768285#post768285") in post #8.

Hello all,

I'm a Linux newbie (though I'm adept in dealing with Windows' inanities ;)), and I'd like to use Ubuntu as my main OS, but the installation of a certain obscure yet important program (for me) is currently driving me nuts. If I'm desperate, I might even try to run it through a Windows emulator.

It's a program which needs to be compiled from source, and it's not available in Synaptic. I've tried both the general instructions as can be found in the forums and on Aysiu's guide, 'Installing Software in Ubuntu', and the instructions in its README file, but no matter what I try, I haven't been able to install it successfully. I've already installed build-essential, and it may be presumptuous, but I've also installed libqt3-headers, libqt3-mb, libqt4-qt3support, and qt3-dev-tools, as its README stated 'to compile it, you will need Qt3 development files'.

I tried first to follow the README's installation instructions:

> 1 - To extract the files :
tar -xvjf dragonflame_2-0_gnulinux.tar.bz2
cd dragonflame_2-0_gnulinux/

2 - To compile and install :

- an easy way to proceed
./install.sh

- another way
qmake dragonflame.pro
make

3 - To execute :
<dragon flame install path>/bin/dragonflame

I have no problems with extracting, but 'sudo ./install.sh' ('Install in ... ?' doesn't seem to work otherwise with simply ./install.sh) has never installed completely. The first question asks you to read the licence; fine. The second, 'do you agree with it?', no problems. However, answering 'Compile?' with 'y(Yes) - Default' outputs a long list of errors, ending with the error 'make: Target `first' not remade because of errors'. Then it asks 'Clean?', which seems okay (I chose 'y'), then 'Install in ... ?' with /usr/local in parentheses. I duly type /usr/local in, and it seems to do its job. Then I try to execute, and nothing. I navigate in Nautilus to /usr/local/dragonflame/bin, and there's nothing in there!

I've also tried the qmake method, but that also outputs a list of errors. The more general method as outlined in the guide fails for me, simply because there seems to be no ./configure. The actual .tar.bz2 file seems to have some other relevant files (including an actual Makefile in its main directory), but I'm not sure what to think of all this.

If anybody can help me, please do. :( I've had some success customising Ubuntu via the terminal with guides, but this just stumps me. I think I also had this problem when I tried to install it on Fedora a year or so ago, and I didn't know much more than I do now.

---

### Post by cwaldbieser on 2006-02-21
[QUOTE=viviena]Hello all,

I'm a Linux newbie (though I'm adept in dealing with Windows' inanities ;)), and I'd like to use Ubuntu as my main OS, but the installation of a certain obscure yet important program (for me) is currently driving me nuts. If I'm desperate, I might even try to run it through a Windows emulator.

It's a program which needs to be compiled from source, and it's not available in Synaptic. I've tried both the general instructions as can be found in the forums and on Aysiu's guide, 'Installing Software in Ubuntu', and the instructions in its README file, but no matter what I try, I haven't been able to install it successfully. I've already installed build-essential, and it may be presumptuous, but I've also installed libqt3-headers, libqt3-mb, libqt4-qt3support, and qt3-dev-tools, as its README stated 'to compile it, you will need Qt3 development files'.

I tried first to follow the README's installation instructions:



I have no problems with extracting, but 'sudo ./install.sh' ('Install in ... ?' doesn't seem to work otherwise with simply ./install.sh) has never installed completely. The first question asks you to read the licence; fine. The second, 'do you agree with it?', no problems. However, answering 'Compile?' with 'y(Yes) - Default' outputs a long list of errors, ending with the error 'make: Target `first' not remade because of errors'. Then it asks 'Clean?', which seems okay (I chose 'y'), then 'Install in ... ?' with /usr/local in parentheses. I duly type /usr/local in, and it seems to do its job. Then I try to execute, and nothing. I navigate in Nautilus to /usr/local/dragonflame/bin, and there's nothing in there!

I've also tried the qmake method, but that also outputs a list of errors. The more general method as outlined in the guide fails for me, simply because there seems to be no ./configure. The actual .tar.bz2 file seems to have some other relevant files (including an actual Makefile in its main directory), but I'm not sure what to think of all this.

If anybody can help me, please do. :( I've had some success customising Ubuntu via the terminal with guides, but this just stumps me. I think I also had this problem when I tried to install it on Fedora a year or so ago, and I didn't know much more than I do now.[/QUOTE]

Do you have a link to where you got the tarball from?  If you can explain what the program is supposed to do, I could try to make a .deb out of it for you with checkinstall.

---

### Post by viviena on 2006-02-21
This is the download link: [http://www.jrrvf.com/hisweloke/sindar/bin/dragonflame_2-0_gnulinux.tar.bz2](http://www.jrrvf.com/hisweloke/sindar/bin/dragonflame_2-0_gnulinux.tar.bz2)

I also came across some notes for this download which I hadn't noticed before. I don't know if it'll help in solving my problem:
[http://www.jrrvf.com/hisweloke/sindar/df20linux.html](http://www.jrrvf.com/hisweloke/sindar/df20linux.html)

As for the program, when installed, it's a comprehensive, cross-referenced dictionary for the Sindarin language, well-suited for a language geek. It has entries where one can look up a word's meaning as well as additional etymological notes. The main page for this program is: [http://www.jrrvf.com/hisweloke/sindar/df20.html](http://www.jrrvf.com/hisweloke/sindar/df20.html) .

TIA,
viviena :)

---

### Post by cwaldbieser on 2006-02-21
[QUOTE=viviena]This is the download link: [http://www.jrrvf.com/hisweloke/sindar/bin/dragonflame_2-0_gnulinux.tar.bz2](http://www.jrrvf.com/hisweloke/sindar/bin/dragonflame_2-0_gnulinux.tar.bz2)

I also came across some notes for this download which I hadn't noticed before. I don't know if it'll help in solving my problem:
[http://www.jrrvf.com/hisweloke/sindar/df20linux.html](http://www.jrrvf.com/hisweloke/sindar/df20linux.html)

As for the program, when installed, it's a comprehensive, cross-referenced dictionary for the Sindarin language, well-suited for a language geek. It has entries where one can look up a word's meaning as well as additional etymological notes. The main page for this program is: [http://www.jrrvf.com/hisweloke/sindar/df20.html](http://www.jrrvf.com/hisweloke/sindar/df20.html) .

TIA,
viviena :)[/QUOTE]
Well, I managed to compile it.  I am not sure where you want to install it, so I didn't try to make a .deb, after all.  You basically just copy the whole directory to where you want to install it.  The file you want to run (assuming you name the project directory is /df) is /df/bin/dflinux.  Just sym-link that in /usr/local/bin or add the directory to your command path.

The archive is a little big for me to post here.  If you PM me with some place I can send it (it is 1.2 MB tarred and gzipped), I can email, ftp it to a site, etc.

---

### Post by gord on 2006-02-21
it sounds like you need to 
```

sudo apt-get install build-essential

```

---

### Post by mdsmedia on 2006-02-21
[QUOTE=viviena]I've already installed build-essential[/QUOTE]

He's already installed it, as he said.

---

### Post by viviena on 2006-02-24
So, I got a binary thanks to Cwaldbieser's generosity, but unfortunately I'm still running into errors -- a 'libqt-mt.so.3 missing' error, even though it's already installed!... Well anyway, I might just try WINE instead, but thanks to all who posted. :)

---

### Post by viviena on 2006-02-24
I'm sorry to spam my own thread, but I actually seem to have moved past the missing libqt-mt.so.3 stage... Even though I'm running 64bit Breezy (and thus have the appropriate packages installed via Synaptic), I downloaded the libqt-mt.so.3 .deb package for 32bit, extracted the relevant libraries, and dumped them in /usr/lib32 (probably should've created a symlink though) -- my inspiration for this, strangely enough, was on reading a thread detailing the difficulties of installing a 64bit WINE. :) I don't know if it actually worked, but that message isn't showing up now... instead I'm getting:

```
Qt: Locales not supported on X server
No Plastik style available!
Aborted
```

... This is progress, at least. :twisted: I've searched the forums, but haven't found any conclusive solution, so if anybody has any suggestions, it would be much appreciated. :)

---

### Post by viviena on 2006-06-21
Close to half a year has gone by, and finally I've had some success... After fiddling about with it on 64-bit Breezy, I finally have the compiled binary working on 32-bit Dapper (I think using 64-bit prolonged my problem). Unfortunately there are still some encoding/display errors with entries (circumflexes and accents don't appear properly), but at least I can run it!... I'd like to thank everybody who helped, especially cwaldbieser. :D

---

