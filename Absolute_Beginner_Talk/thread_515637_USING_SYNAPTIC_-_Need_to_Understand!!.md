---
title: "USING SYNAPTIC - Need to Understand!!"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Panganat on 2007-08-02
i can use Synaptic to install packages that is part of system. I see threads where it is being stated to download a package and use synaptic to install it.  How is this done? Do i have to save the package in a particular place for synaptic to see it.  The references made in the threads seems to leave out the basics (To me anyway as i am a Newb).  I am trying to install kismet and i am following the instructions but "cant find kismet":confused:

---

### Post by ushills on 2007-08-02
you can go to synaptic manager and search for kismet.

If kismet is found put a tick in the box next to the program name and press apply, this will install the application you don't need to download anything yourself.

The program will then appear in your menu's

Alternative go to Applications > Accessories > Terminal, and enter

```
sudo apt-get install kismet
``` if you know the programme name or 

```
sudo apt-cache search kismet
```, if you don't know the exact name.

Two ways of doing the same thing.

---

### Post by overdrank on 2007-08-02
> **Panganat said:**
> i can use Synaptic to install packages that is part of system. I see threads where it is being stated to download a package and use synaptic to install it.  How is this done? Do i have to save the package in a particular place for synaptic to see it.  The references made in the threads seems to leave out the basics (To me anyway as i am a Newb).  I am trying to install kismet and i am following the instructions but "cant find kismet":confused:

HI I don't understand what you mean for synaptic to see it. If you  have feisty it is in the repos so all you have to do is open synaptic and search for kismet. Then click on it to install and then apply. Hope that helps good luck!:KS

Edit: and maybe this link will help
[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

---

### Post by univremonster on 2007-08-02
Is this an issue of not knowing where Synaptec is located in order to run it?  If so it's under System -> Administration -> Synaptec Package Manager and then, like the previous posts say, just search for Kismet.  I tried it out and it is in the basic repositories, so just click and apply!  Hope that helps

---

### Post by steve.horsley on 2007-08-02
Kismet is in the Universe repository. You must enable that repository before a synaptic search will find it. 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

### Post by hyper_ch on 2007-08-02
You may want to read on this page the basic infos on how to use Ubuntu:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Panganat on 2007-08-02
thanks all i had to "activate" repositories and did not need a supository:)

---

