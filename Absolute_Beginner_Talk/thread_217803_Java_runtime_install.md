---
title: "Java runtime install"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Cobra-34 on 2006-07-17
Hello i'm new to ubuntu and I need a step by step process for installing java on this OS.I've looked through the forums and either didn't look in the right place or something. Please help if you can.

---

### Post by OffHand on 2006-07-17
Install it with Synaptic. Search for jre. Install the Sun one.

---

### Post by madmetal on 2006-07-17
i am also new but a good start will be synaptic.
search in synaptic for java runtime its easy to install programs with synaptic.

---

### Post by OffHand on 2006-07-17
Editted my previous post. Search for jre and install sun's java.

---

### Post by Cobra-34 on 2006-07-17
I did a seach for jre-1_5_0_07-linux-i586.bin which is what I downloaded to my desktop. Then I did a seach in synaptic and it don't find it? I really didn't realize how different than this is from windows lol.

---

### Post by fatsheep on 2006-07-17
Go to System (top menu)>Administration>Software Properties.  You'll have to enter your password here.  After that then select "Ubuntu 6.06 LTS (source)" from the list (should be the first one), click "Add...", select "community maintained (universe)" and "non-free (multiverse)"  by clicking the check box.  Click add again.

Now go to Applications>Add/Remove and search for Java, you should be able to install from there.  

Hope this helps,

-sheep

---

### Post by madmetal on 2006-07-17
search in synaptic can find its packages so it wouldn't find the package you downloaded.
search in synaptic as subsonic_shadow suggested for jre- java runtime environment and check it for install.
its easier and better to install packages from synaptic.

---

### Post by Dinerty on 2006-07-17
Hey I found a great guide from these forums by a admin

**Written by **Artificial Intelligence****


If you want the latest version:
 
 Download Java Runtime Environment (JRE) 5.0 Update 7: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick Linux self-extracting file. Download it to your Desktop.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java
```

When asking for which version you want to choose pick;

```
3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing

```
java -version
```

Making a Launcher for Java Control Center;

```
sudo gedit /usr/share/applications/java.desktop
```

fill in;

[Desktop Entry]
 Name=Java Control Center
 Comment=Java Options & Configuration.
 Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
 Icon=
 Terminal=false
 Type=Application
 Categories=Application;System;



Save and exit.
 You can find it now under Applications tab ---> System Tools.

---

### Post by Cobra-34 on 2006-07-17
Ok Dinerty I did it exactly like it said. I went to a website for my kid to see if it works and when the page that used to tell him he needs runtime it now just disapears the whole page just disapears?

---

### Post by Cobra-34 on 2006-07-17
I get this error....user@edubuntu:~/Desktop$ sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
user@edubuntu:~/Desktop$

---

### Post by Skia_42 on 2006-07-17
> **Cobra-34 said:**
> Ok Dinerty I did it exactly like it said. I went to a website for my kid to see if it works and when the page that used to tell him he needs runtime it now just disapears the whole page just disapears?
Does your internet browser quit as well? If so I have the same problem, it occurs on all web browsers I have tried **except Opera.** Look up Opera in  synapic, install it, and try going to the same page.

---

### Post by Dinerty on 2006-07-17
> **Cobra-34 said:**
> Ok Dinerty I did it exactly like it said. I went to a website for my kid to see if it works and when the page that used to tell him he needs runtime it now just disapears the whole page just disapears?

Did you try it in Firefox mate?

> **Cobra-34 said:**
> I get this error....user@edubuntu:~/Desktop$ sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
user@edubuntu:~/Desktop$

Are you sure you definetly had the package on your desktop?



I'm by no means a expert mate, only been using linux about a week, so sorry if my answers dont help.

---

### Post by Cobra-34 on 2006-07-18
Yea it's on my desktop. I wanted to try this linux. I have found out that it is to complicated for me. I will stick with windows. Have fun with linux fellas.

---

### Post by T700 on 2006-07-18
Don't give up so easily!  Just go to the Automatix link in my sig and run it.  When it asks for a password, use the one you log in with.  It will install Java, along with lots of other things you will need to enjoy your Linux system.  It is fast, safe, and easy.

Paul

---

### Post by Cobra-34 on 2006-07-18
Thank you very much T700. That worked and I am very greatful. Thank you.

---

### Post by T700 on 2006-07-18
Glad to help.  In a previous version of Ubuntu, I too sweated and cursed and wrestled to install Java and various other things.  Then I found Automatix and life has been sweet since them.  Not only did it take care of all the codecs and programs I needed, I'm taller, thinner, and actually got a promotion at work.  [B]Thanks, Automatix!  ;-)

[/B]Paul

---

### Post by drosophyllum on 2006-07-18
This is one thing I hate about some beginners out there.
Im a beginner my self but Some other beginners just jump to windows the instant they see the over exagerated fata morgana learning curve! I have never had a problem that this wonderfull forum could not help me resolve. Thanks guys. Also the learning curve is not so big and hard to overcome just remember its a diffrent opperating system. I learned basic linux comands and my way through the system in a week. I found alternatives to my windows software instantly and I was amazed at how much more succure linux is. I customized it entirely!

(go to gnome art or gnome look, you will be amazed at the stuff you will find)

 Try to do that with windows. Cobra, give linux a chance and in two weeks you will hate windows and see exactly how unsuperior it truelly is.
btw automatix is really helpfull but if that doesn't work for others than try easyubuntu.

---

### Post by Cobra-34 on 2006-07-18
Yes well i'm not going to give up on it. I like it alot. I just got mad about feeling like I should know how to do this and couldn't figure it out. But like windows at first it took me some time to figure it out. I will give my best effort and things in this ubuntu will come with time. I want to thank all of you for your help.

---

### Post by Cobra-34 on 2006-07-18
Oh one thing. I tried to change the screen resolution. It's at 640x480. When I get it up it won't change. How can you change that?

---

### Post by drosophyllum on 2006-07-18
start it as a new thread.

---

