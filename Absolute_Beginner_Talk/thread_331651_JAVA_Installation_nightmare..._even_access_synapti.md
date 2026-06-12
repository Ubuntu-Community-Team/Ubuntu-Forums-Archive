---
title: "JAVA Installation nightmare... even access synaptic package manager"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by darweth on 2007-01-04
Hello... this is my first time usuing Ubuntu.  Just installed it tonight and am having a helluva time with JRE.  

Did a:  sudo apt-get install sun-java5-jre sun-java5-plugin

When I got to the blue licensing screen, it didn't seem like there was anything I could do.  Pressign enter did not work and the terminal was gone.  Just that licensing screen that I could scroll down but not advance or get rid of.  I closed the terminal.

I tried then installing Java via Add/Remove in Applications but it told me "E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct"

I went back to the terminal and did a sudo apt-get install sun-java5-jre sun-java5-plugin again and got the same message.  So I did sudo dpkg --configure -a and it seemed to set up or do something.  

So then I downloaded some .bin self-extracting file for the 10 update from their site and typed in sudo apt-get install java-package.  SOmething seemed to happen.  

Followed more directions and did a "fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin" which didn't work.  I don't remember the message, but I DID have the .bin file on the desktop.  

I then went back into add/remove and couldn't do much of anything.  Stupidly (probably) tried a sudo apt-get install sun-java5-jre sun-java5-plugin and got back to the licensing screen that doesn't want to respond.  I closed the terminal and now everything is bonkers.

NO Java and trying to access the synaptic manager in System now gives me a "E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem also!  Can't access the Synaptic manager.



Ahhh!  How can I resolve all of this? Opening a terminal and typing dpkg --configure -a with and without sudo did nothing.  How do I fix this AND how do I install JRE..??

---

### Post by darweth on 2007-01-04
Some updates... I was able to get into Synaptics again......

i sudo apt-get install sun-java5-jre sun-java5-plugin again... it mentions that i have 2 not fully installed JRE.       SO I did an apt-get remove and it said I should install properly before removing... ahhh.           It says it unpacks 85 mbs everytime or something... this is not on top of each other, right? 



anyway i get back to that blue licensing configuring .bin screen again with "OK" at the bottom and just totally get stuck.  ENTER/RETURN does not work.  How do I advance and complete the install?!?!?!?

---

### Post by taurus on 2007-01-04
See if you can scroll with the up/down arrow keys.  And use the Tab key to highlight Okay or Except in the license screen...

---

### Post by tzulberti on 2007-01-04
First, you could do:
sudo apt-get -f install
If it fails, you should remove java and reinstall it again... To remove it:
sudo apt-get remove sun-java5-jre sun-java5-plugin java

---

### Post by darweth on 2007-01-04
I am dumb.  I finally found out the arrow key is what takes me to OK.  Weird... uhhh, yeah.  Anyway.. it finished installing and now I have this

Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up html2text (1.3.2a-3) ...

Setting up debhelper (5.0.37.3ubuntu4) ...
Setting up fakeroot (1.5.9ubuntu1) ...

Setting up java-package (0.27) ...
bepogi@bepogi-desktop:~$ fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin
Error: The file "jre-1_5_0_10-linux-i586.bin" does not exist.
bepogi@bepogi-desktop:~$ sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb
dpkg: error processing sun-j2re1.5_1.5.0+update10_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update10_i386.deb
bepogi@bepogi-desktop:~$ 


that i586.bin I downloaded is on the desktop.  How do I successfuly make a fakeroot?

---

### Post by taurus on 2007-01-04
Maybe you have to change to ~/Desktop where you downloaded it first before you can run that command!!!

```
cd ~/Desktop
```

---

### Post by darweth on 2007-01-04
Ah thanks.  Sorry, I am a total newb. :)  I haven't used a command line before tonight in... well, a billion years.   I dragged the file to bepogi and it worked, but I will try to be smarter from now on!

---

### Post by taurus on 2007-01-04
If you're not sure about something, just ask, mate.  ;)

---

