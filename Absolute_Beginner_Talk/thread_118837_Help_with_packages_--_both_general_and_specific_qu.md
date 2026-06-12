---
title: "Help with packages -- both general and specific questions"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by valkyrie on 2006-01-17
I am very new to kubuntu. This is the first Linux distro I've tried and so I am stumbling around a bit. (I did manage to successfully configure my wireless PCMIA card, for which I am incredibly proud of myself :lol: ) 

The specific question: I wanted to install Gizmo Project on my laptop. So naturally step one was to look at the [Gizmo support faq](http://support.gizmoproject.com/index.php?_a=knowledgebase&_j=questiondetails&_i=135), which helpfully told me what to put onto my computer before installing Gizmo. Now, Google, [Apple](http://developer.apple.com/networking/bonjour/index.html), and ubuntuforums.org have made it pretty clear that Bonjour / mDNSresponder / zeroconf are all the same thing. In fact, according to [the most relevant thread](http://www.ubuntuforums.org/showthread.php?t=59542&highlight=mdnsresponder) I found on the subject, I should be able to just input ```
sudo apt-get install mdnsresponder
``` and bingo everything will be installed! However, I get this instead: ```
Reading package lists... Done Building dependency tree... Done E: Couldn't find package mdnsresponder
``` Synaptic and Adept were also unable to find mdnsresponder, bonjour, or zeroconf. 

I did download the source code from Apple, following a link I found from Google (see [http://wiki.kde.org/tiki-index.php?page=Zeroconf+in+KDE)](http://wiki.kde.org/tiki-index.php?page=Zeroconf+in+KDE)), but I'm even less sure about compiling code than I am about installing packages. Where should I go from here?



And, my general questions: Am I just (somehow) not configured to look in the correct place with Synaptic/Adept/apt-get? 

Personally I see a huge convenience factor in using packages for installation as opposed to compiling source code, but would I be better off getting over it and choosing to compile code instead? Thanks!

---

### Post by matthewv on 2006-01-17
Have you added the extra repositories from ubuntu??
Do this by going to synaptic --> settings --> repositories. Press add, select the ubuntu 5.10 and check all boxes, press ok, ok again, and then reload package lists when prompted... hope it works...

PS: Welcome to the forums... :)

EDIT: mDNSresponder is definitely in the universe repositories, so adding the extra repos should be all u need..

---

### Post by Sef on 2006-01-17
>  I'm even less sure about compiling code than I am about installing packages. Where should I go from here?

Check out this link to psychocats to find out more about how to compile from source:

[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

> Synaptic and Adept were also unable to find mdnsresponder, bonjour, or zeroconf.

Even though Synaptic/Adept have lots of packages, they do not have every one.  If you use search in Synaptic/Adept, and nothing is found then that package is not in the repository.

>  Am I just (somehow) not configured to look in the correct place with Synaptic/Adept/apt-get?

You may have not enabled the repositories, but we all have done that times. 

> Do this by going to synaptic --> settings --> repositories. Press add, select the ubuntu 5.10 and check all boxes, press ok, ok again, and then reload package lists when prompted... hope it works 

If you only have 5.10, Breezy, on your system, then you don't have to select Ubuntu 5.10.  Just check on the boxes.

---

### Post by valkyrie on 2006-01-17
Cool, now I know about repositories :mrgreen:

Unfortunately I tried checking them *all* and was still not able to find mDNSresponder in a repository search.  (On the plus side, I found some more interesting games.)  Can I search for, then manually enter the appropriate repository address?

(and thanks for the welcome! the forums are an excellent resource thus far.)

---

### Post by matthewv on 2006-01-17
sry.. i think it has been replaced with the package mdns-scan in breezy :)
mdnsresponder only exists for warty and hoary.. sry

---

### Post by valkyrie on 2006-01-17
Well I'll give the new version a shot and see if it works out -- the worst that can happen is it doesn't work!

Thanks again for the help.

---

### Post by jimrz on 2006-01-17
If that does not work, zeroconf is in the universe repo for breezy.

---

