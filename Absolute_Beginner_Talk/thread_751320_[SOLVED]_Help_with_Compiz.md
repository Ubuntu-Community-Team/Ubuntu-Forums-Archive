---
title: "[SOLVED] Help with Compiz"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by laprettygurl on 2008-04-10
I'll admit that I have no clue what i'm doing at the moment. I installed gutsy on a whim last night on a desktop i just threw together the other day.

As I understand it Compiz is already installed with Gutsy, right? I have no advanced desktop setting button. 

So I tried this link:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

but it says it cannot find compizconfig-settings-manager. I checked and it looks like all the compiz packages are installed.

help? lol

thanks!

---

### Post by GoCool on 2008-04-10
Use synaptic to check that you have compiz-settings-manager installed.

Go to synaptic via:
Systems->Administration->Synaptic Package Manager  (I am not before my ubuntu, so there might be some variation)

Click on search

type compiz and press enter

Now scroll and check if you find compiz and whether you find a mark against it.

---

### Post by spiderbatdad on 2008-04-10
If you enter into a terminal ```
sudo apt-get install compizconfig-settings-manager
```
and you get the message you copied into your post, then either there is a typo in the command or
you need to enable the universe and multiverse repositories....You will need a working internet connection.
To enable repos...System>>Administration>>Software Sources>> check the boxes for universe and multiverse.

---

### Post by laprettygurl on 2008-04-10
Everything *looks* ok but i'm not sure what it's supposed to look like if it's not.

screenshot for you! [http://img225.imageshack.us/img225/2094/screenshotsk9.png](http://img225.imageshack.us/img225/2094/screenshotsk9.png)

> **GoCool said:**
> Use synaptic to check that you have compiz-settings-manager installed.

Go to synaptic via:
Systems->Administration->Synaptic Package Manager  (I am not before my ubuntu, so there might be some variation)

Click on search

type compiz and press enter

Now scroll and check if you find compiz and whether you find a mark against it.

---

### Post by laprettygurl on 2008-04-10
I have the internet working :)

hmm, did the first thing and then the second and this is all the text that was in the terminal

pauline@pauline-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for pauline:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
pauline@pauline-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
pauline@pauline-desktop:~$ 


hmm, i'm gonna mess around for a bit with this. thank you 
> **spiderbatdad said:**
> If you enter into a terminal ```
sudo apt-get install compizconfig-settings-manager
```
and you get the message you copied into your post, then either there is a typo in the command or
you need to enable the universe and multiverse repositories....You will need a working internet connection.
To enable repos...System>>Administration>>Software Sources>> check the boxes for universe and multiverse.

---

### Post by GoCool on 2008-04-10
You have the Synaptic Packet manager open thats why the error in your terminal.

Close the synaptic and try it again in your command prompt, it should work. Else let me know.

---

### Post by laprettygurl on 2008-04-10
k, closed everything but firefox...still not working 

pauline@pauline-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for pauline:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
pauline@pauline-desktop:~$ 

it's slightly maddening to me that i cannot do this myself :/ oh well, lol. 

> **GoCool said:**
> You have the Synaptic Packet manager open thats why the error in your terminal.

Close the synaptic and try it again in your command prompt, it should work. Else let me know.

---

### Post by booticon on 2008-04-10
I installed 7.10 last night, and IIRC, the name of the package I installed was gnome-compiz-manager, and I don't remember having to enable any non-default repository. After it's installed you should be able to manage the settings through System>Preferences.

Again, I may be wrong as this is just from memory, but it's just another idea.

---

### Post by Fate Reconciled on 2008-04-10
Umm.. Type compiz in the terminal and post output. Clean install doesn't include Xgl, I don't think. So 'sudo apt-get install xserver-xgl'. Then enable custom visual effects: System -> Preferences -> Appearance -> Visual Effects and select Custom.

---

### Post by laprettygurl on 2008-04-10
pauline@pauline-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

then you wanted me to do this, right? oh god i hope so, lol

pauline@pauline-desktop:~$ sudo apt-get install xserver-xgl
[sudo] password for pauline:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl
pauline@pauline-desktop:~$ 

what is window decorator?



> **Fate Reconciled said:**
> Umm.. Type compiz in the terminal and post output. Clean install doesn't include Xgl, I don't think. So 'sudo apt-get install xserver-xgl'. Then enable custom visual effects: System -> Preferences -> Appearance -> Visual Effects and select Custom.

---

### Post by Fate Reconciled on 2008-04-10
Yes, you did need Xgl. Open Synaptic -> Settings -> Repositories and make sure they're all enabled then Reload them. Search 'Xgl' in synaptic and it xserver-xgl should be on the bottom. By the looks of it, it's not detecting your graphics card either. What is your graphics card anyway?

Your window decorator is Gtk 2.x

---

### Post by laprettygurl on 2008-04-10
ohhh, it works! thankyou!

well atm it's onboard. :/ until i can get to my brother's house and see what i can find. i'm sure he has something decent i can use. (he's hardcore gamer, always upgrading)

> **Fate Reconciled said:**
> Yes, you did need Xgl. Open Synaptic -> Settings -> Repositories and make sure they're all enabled then Reload them. Search 'Xgl' in synaptic and it xserver-xgl should be on the bottom. By the looks of it, it's not detecting your graphics card either. What is your graphics card anyway?

Your window decorator is Gtk 2.x

---

### Post by Fate Reconciled on 2008-04-10
Ahh good. So give a thank and mark the thread as solved ;)

---

### Post by laprettygurl on 2008-04-10
i advance edited it into the title but it's not showing up on the main screen. hmm...

> **Fate Reconciled said:**
> Ahh good. So give a thank and mark the thread as solved ;)

---

### Post by Fate Reconciled on 2008-04-10
[http://ubuntuforums.org/showthread.php?t=568681&page=2](http://ubuntuforums.org/showthread.php?t=568681&page=2)

---

### Post by joshrobinson on 2008-04-10
towards the top rightish of the page, below where it says the page numbers, it says thread tools
click that, and go to mark thread as solved, you dont have to edit it into the title

---

