---
title: "How to install a Driver"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-04-18
Here is my question, how do I install a driver or application in the command prompt.  Here is an example,  I tried the following to install a driver for my wireless NIC Card:  # sudo apt-get install BCMWL5.inf but it said it couldn't find the package?  Am I typing this wrong?:(

---

### Post by Sandlst on 2006-04-18
wireless drivers should be installed via ndiswrapper: do this ```
sudo apt-get install ndisgtk
```, then go to (System/Administration/Windows Wireless Drivers) browse to your .inf file, and it should get it working. apt-get install looks for software on the repositories on the internet, and wont look for local stuff.  Post back if you have any problems!

---

### Post by croak77 on 2006-04-18
[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

---

### Post by NeoGreen on 2006-04-18
Sorry, that command give me an error message stating that E: Couldn't find package ndisgtk****](*,)   Have I done something wrong?

---

### Post by qamelian on 2006-04-18
Open a terminal window and type the following:

```
sudo apt-get install ndisgtk
``` and press enter. Accept any dependancies apt wants to install.

When the install is finished, there will be a new entry under System > Administration called Windows Wireless Drivers. Launch this item for a graphical interface that will assist you to install your wireless drivers.

---

### Post by Sandlst on 2006-04-18
Have you enabled extra repositories?  If not, go [here.]("http://www.ubuntuforums.org/showthread.php?t=92672")

---

### Post by NeoGreen on 2006-04-18
I typed the command sudo apt-get install ndisgtk and I get a message that tell me that the package couldn't be found.](*,)

---

### Post by mrchrisblau on 2006-04-18
as stated above you, go here to enable more repos: [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by NeoGreen on 2006-04-18
Okay, this may sound like a dumb question but am I supposed to copy and paste the source list from the link onto my source list?  Another question, what is a source list and why do I need a repository.:(  Sorry, I am trying really hard to learn this stuff.

---

### Post by Sandlst on 2006-04-18
Yes-when you open your sources.list file, it should look similar to the recommended one, just delete everything in the file and paste over with the recommended one.  You don't *need* to use the repos, they just make life a lot easier for you :).  They contain software that has been tested to ensure it works very well on ubuntu, and also contains all the dependencies you need to install in order for the software to work.

---

### Post by NeoGreen on 2006-04-18
Not to get off the subject, what is the sources list?  Once I copied and pasted all the info onto my source list and ran updates and upgrades, it started installing all kinds of stuff.  Is this normal?

---

### Post by Sandlst on 2006-04-18
The 'upgrades' part probably did find some programs that had updates released in some of the other repositories-each line in sources.list starting with 'deb' is a link to a large set of software-different software is put onto different links based on what it is, if you want to see what kinds of sofware is on there, you can look in the commented section of the file (lines beginning with ##).  Basically it tells your computer where to look for software (and software upgrades) on the internet.

---

### Post by NeoGreen on 2006-04-18
Oh, okay, so it is normal.  Do you have to do this everytime you install a Ubuntu on a desktop or laptop?  I mean as far as copying and pasting the source list and then running the updates.:)

---

### Post by Sandlst on 2006-04-18
Afraid so....if there is a way around it, I haven't found it yet :P.  I think it enables only the basics by default to increase security/stability.

---

### Post by NeoGreen on 2006-04-18
Thanks for the info, :)

---

### Post by NeoGreen on 2006-04-18
Okay I have it, I went to systems, admin, then I saw the new window for wireless drivers. I went on to try to install the bcmwl5.inf file and I got a message that told me that it was already installed? Oh another thing, it says on one of the windows, the one that shows the driver that the Hardware Present:  No

---

### Post by Sandlst on 2006-04-18
In the window before, do you see an entry for it?  I've attached a screenshot so you know for sure where to look.
*EDIT* nevermind, I cant read tonight.:rolleyes: is the wlan a pcmcia cardbus card?

---

### Post by NeoGreen on 2006-04-18
It's actually built into the laptop, its a Broadcom. :(  I did get the driver to install though, it was driver bmcwl5a but once I configured it and activated it, but when I go to see it on my desktop, (you know those two little computer icons that show you if your are connected or not) I don't see the option for my wireless card just etho and lo.

---

### Post by Sandlst on 2006-04-19
Have you looked in (System/Administration/Networking)?  My wireless buscard works with those drivers, but since yours is on-board you might want to try and take a look at what croak77 suggested in the third post on this thread.

---

### Post by NeoGreen on 2006-04-19
Okay I'll check it out thanks:)

---

