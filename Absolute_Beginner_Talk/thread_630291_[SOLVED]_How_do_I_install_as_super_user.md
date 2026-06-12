---
title: "[SOLVED] How do I install as super user"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by pajim17020 on 2007-12-03
Hi, I am trying to install ati video driver. When I run the install it is telling me that I have to run it as super user. What is that and how do I do it? Thanks

---

### Post by lamalex on 2007-12-03
You need to run the command with a ```
sudo
``` in front of it. What method are you using to install the driver? If you're using 7.04 or later, you can use the restricted drivers Manager from System > administration to install the ATI driver.

---

### Post by pajim17020 on 2007-12-03
I am running it by double clicking the icon then selecting "run in terminal" it does run but then it says I need to run as super user. So I opened a terminal and tried this.
jim@mycomputer:~$ sudo install ati-driver-installer-8.42.3-x86.x86_64.run
[sudo] password for jim:
install: missing destination file operand after `ati-driver-installer-8.42.3-x86.x86_64.run'
Try `install --help' for more information.
jim@mycomputer:~$ 
I did try using the restricted drivers manager. When I did the display went to an awful 16 bit vga. I couldn't get it to go back to 32 bit. So I downloaded this driver from ati but haven't been able to install it.

---

### Post by lamalex on 2007-12-03
You might want to try envy, it's worked well for me at installing the ATI drivers. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
but to answer your question, try preceding the install command with a ./
```
sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
```

---

### Post by tuwe on 2007-12-03
> **pajim17020 said:**
> I am running it by double clicking the icon then selecting "run in terminal" it does run but then it says I need to run as super user. So I opened a terminal and tried this.
jim@mycomputer:~$ sudo install ati-driver-installer-8.42.3-x86.x86_64.run
[sudo] password for jim:
install: missing destination file operand after `ati-driver-installer-8.42.3-x86.x86_64.run'
Try `install --help' for more information.
jim@mycomputer:~$ 
I did try using the restricted drivers manager. When I did the display went to an awful 16 bit vga. I couldn't get it to go back to 32 bit. So I downloaded this driver from ati but haven't been able to install it.

try ```
sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
```

you may need to change to the directory where that file is located first, and make it executable by ```
chmod +x ati-driver-installer-8.42.3-x86.x86_64.run
```

hope this helps

ps. did you edit your xorg.conf properly? you might want to check out my xorg.conf: [http://www.freizeitmoscher.de/?page_id=13](http://www.freizeitmoscher.de/?page_id=13)
the relevant stuff is in the "Device" section.

---

### Post by Sef on 2007-12-03
> I am running it by double clicking the icon then selecting "run in terminal" it does run but then it says I need to run as super user. So I opened a terminal and tried this.
jim@mycomputer:~$ sudo install ati-driver-installer-8.42.3-x86.x86_64.run
[sudo] password for jim:
install: missing destination file operand after `ati-driver-installer-8.42.3-x86.x86_64.run'
Try `install --help' for more information.
jim@mycomputer:~$ 

Where did you put the download file?  (To which directory did you download the ati drivers to?)

---

### Post by pajim17020 on 2007-12-03
Ok, this is what I tried.
jim@mycomputer:~$ sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
[sudo] password for jim:
sudo: ./ati-driver-installer-8.42.3-x86.x86_64.run: command not found
jim@mycomputer:~$ sudo ./install ati-driver-installer-8.42.3-x86.x86_64.run
sudo: ./install: command not found
jim@mycomputer:~$ chmod +x ati-driver-installer-8.42.3-x86-x86_64.run
chmod: cannot access `ati-driver-installer-8.42.3-x86-x86_64.run': No such file or directory
jim@mycomputer:~$ 

The file is on the desk top. Should it be elsewhere?

---

### Post by lamalex on 2007-12-03
you need to ```
cd Desktop/
```

---

### Post by tuwe on 2007-12-03
> **pajim17020 said:**
> Ok, this is what I tried.
jim@mycomputer:~$ sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
[sudo] password for jim:
sudo: ./ati-driver-installer-8.42.3-x86.x86_64.run: command not found
jim@mycomputer:~$ sudo ./install ati-driver-installer-8.42.3-x86.x86_64.run
sudo: ./install: command not found
jim@mycomputer:~$ chmod +x ati-driver-installer-8.42.3-x86-x86_64.run
chmod: cannot access `ati-driver-installer-8.42.3-x86-x86_64.run': No such file or directory
jim@mycomputer:~$ 

The file is on the desk top. Should it be elsewhere?

you did not change to the Desktop folder before issuing the commands.

try
```
cd Desktop
chmod +x ati-driver-installer-8.42.3-x86.x86_64.run
sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
```

did you read [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a) ?
The installation is explained in detail there.

---

### Post by pajim17020 on 2007-12-04
First I want to thank everyone for your help. I never would have figured this out with out it. I finally got the ATI driver working. These are the codes I ran to get it working.

  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
  sudo aticonfig --initial --input=/etc/X11/xorg.conf

 echo SKIP_CHECKS="yes" >> $HOME/.config/compiz/compiz-manager

# Driver whitelist
 WHITELIST="nvidia intel ati radeon i810 fglrx"
 

They came from here- [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Advanced_Desktop_Effects_.28Compiz_Fusion.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Advanced_Desktop_Effects_.28Compiz_Fusion.29) 
:guitar:

---

### Post by rash1205 on 2007-12-15
guyz i've got some problems wiht mine installing ati on ubuntu 6.06

i've written these on termilal

$ sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper



writing this code some package reading is started but it says " packege fakeroot "  not found
what should i do now
somebdy plz help me:confused:

---

### Post by rash1205 on 2007-12-15
ive problem with mine

i m trying to install ati driver and collected codes from ububtu sites but still some problems are found

i ve written this code in terminal
 
$ sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential developer


but it says package fakeroot not found
Can anyone give me some ideas????

---

### Post by rash1205 on 2007-12-15
guyz problem solved

HOOOOOOOOOOOOOOOOOOOOOOO
just type folloings if installer is on the desktop

sudo /home/user-name/Desktop/ati-driver-<version>-x86.x86_64.run

enjoy better refresh rate + higher   resolution

---

### Post by rash1205 on 2007-12-15
another problem

anyone can say how to access other drives of the computer
i cant accass other drives without the file system drive

---

### Post by flamelab on 2007-12-15
Oh god you are downloading the most problematic driver , with the lowest perfomance and beta AIGLX support !
Follow these instructions or run for days in order to fix Xorg -->[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

