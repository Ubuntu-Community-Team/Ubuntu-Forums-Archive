---
title: "Help Installing things on Ubuntu"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-05-27
I recently installed Ubuntu, and I was trying to install Java, but I'm running into a problem: When I type "chmod a+x jre-6ul-linux-i586.bin", in the terminal, it says "No such file or directory". I downloaded the file to /home/myname/Programs/Java, and I navigated to there so it says root@myname-desktop:/home/myname/Programs/Java# at the beginning of the line. What am I doing wrong?

Also, I'm also having problems with AIM. I downloaded the .tgz file, followed the instructions on the website for extracting it, and everything seemed to work fine. Then when I typed "usr/local/bin/aim" in the command line like it said, it said "No such file or directory". When I use the GUI and try to run the file called "aim" at that location, nothing happens. Again, what am I doing wrong?

Thanks!

---

### Post by steveneddy on 2007-05-27
> **Yes said:**
> 

Also, I'm also having problems with AIM. 

Why don't you just use GAIM?

---

### Post by ugm6hr on 2007-05-27
> **Yes said:**
> I recently installed Ubuntu, and I was trying to install Java, but I'm running into a problem: When I type "chmod a+x jre-6ul-linux-i586.bin", in the terminal, it says "No such file or directory". I downloaded the file to /home/myname/Programs/Java, and I navigated to there so it says root@myname-desktop:/home/myname/Programs/Java# at the beginning of the line. What am I doing wrong?


Try installing java from Synaptic Package Manager.  I'm sure it's there.

---

### Post by raja on 2007-05-27
Sun java is in the repositories. Just do ```
sudo aptitude install sun-java6-jre
``` or if you want the jdk ```
sudo aptitude install sun-java6-jdk
```

---

### Post by theredcross on 2007-05-27
also/ it should be noted there is no "usr" folder. there is a "/usr" folder, however; and the terminal gets very picky about these things. Use synaptic/adept for installing software whenever possible, its cleaner and more convenient.

---

### Post by Yes on 2007-05-27
What do I want to download for GAIM?  The two possiblities seem to be Fedora Core and CentOS/RHEL?

And I'll try that, ugm.

---

### Post by steveneddy on 2007-05-27
> **Yes said:**
> What do I want to download for GAIM?  The two possiblities seem to be Fedora Core and CentOS/RHEL?

And I'll try that, ugm.

Um - do you know where the Synaptic Package Manager is?

And on second thought, I think GAIM is already installed by default.

Applications --> Internet --> Gaim Internet Messenger

and the location of the Synaptic Package manager is:

System --> Administration --> Synaptic Package Manager

Most of everything you actually want to install in in synaptic, already packaged up and ready to go. just click and apply.

GAIM will let you log onto AOL Instant Messenger, Yahoo Messenger ICQ, Jabber...all of the popular messengers, all at one time, all in one window.

---

### Post by steveneddy on 2007-05-27
> **raja said:**
> Sun java is in the repositories. Just do ```
sudo aptitude install sun-java6-jre
``` [/CODE]

I couldn't find that, I had forgotten it started with sun-

---

### Post by Yes on 2007-05-27
Wait, no, I don't got it.  I got the GAIM, but when I can't figure out how to install Java through the Synaptic Package Manager.  Can anyone explain it to me?

---

### Post by Yes on 2007-05-27
Also, why does it say that I do not have permission to delete anything from the desktop?

---

### Post by nagius on 2007-05-27
Hi

Go to system - administration- synaptic package manager then click on the search type java and click on the java package on the right the click apply.

---

### Post by Yes on 2007-05-27
What java do I want?

---

### Post by Pizzarth on 2007-05-27
jre 5, the jdk if you're planning on programming, but my favorite ( eclipse) can use either. I don't think 6 is stable yet.

they should have the sun- tag in front of them

---

### Post by Yes on 2007-05-27
Ok, I've installed "sun-java6-jre" from the Synaptic Package Manager.  Now, when I go to System -> Preferences, there is a "Sun Java 6 Plugin Control Panel" and "Sun Java 6 Policy Tool".  However, when I try to play a game that needs the Java, it says that I don't have it.  Did I install the right thing?

---

### Post by Pizzarth on 2007-05-27
> jre 5, the jdk if you're planning on programming, but my favorite ( eclipse) can use either. I don't think 6 is stable yet.

they should have the sun- tag in front of them

I guess I was right about the new one not being stable eh

---

### Post by Yes on 2007-05-27
So will there be an option for Jre5?

---

### Post by Pizzarth on 2007-05-27
hm? just uninstall jre6, jre5 should still be in the repositories, install that next

---

### Post by 13thMonkey on 2007-05-27
It could be that your system isn't using the version of Java you've just installed.

Open up a terminal and enter 
```
sudo update-alternatives --config java
```
and enter the number next to the version you want (java-6-sun in this case).

---

### Post by Yes on 2007-05-27
Ok, I've done all that, but I still can't run Java applets.  Is there anything else I have to do?

Thanks!

---

### Post by Yes on 2007-05-27
Also, how do you delete folders/flies from the terminal?

---

### Post by teknosexual on 2007-05-28
> **Yes said:**
> Also, how do you delete folders/flies from the terminal?

Navigate to the folder your file to be deleted is located and type the command: **rm file-to-delete.extension**

Note: You will probably need to be root for many files, which is accomplished by typing: **sudo rm file-to-delete.extension**

You can also type the full folder path, so you don't have to navigate to the folder where your file is. For example, you might type: **rm /home/username/files/file-to-delete.extension**

---

