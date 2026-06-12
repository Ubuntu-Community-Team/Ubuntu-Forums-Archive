---
title: "Programmes opening then closing"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by davetatem on 2008-02-12
Sometimes when I try to open a new programme, most often Synaptic Package Manager or Add / Remove, the window starts to open and then closes again almost instantly.  It's happened with Firefox too but usually other programmes will open normally.  It's not a major hassle but it means I have do a complete restart.  I'm using Gutsy.  Anyone any ideas?

---

### Post by dca on 2008-02-12
For firefox you may be able to try this:
[http://ubuntuforums.org/showthread.php?t=256039](http://ubuntuforums.org/showthread.php?t=256039)
 
It's from an older vers but may be relevant.
 
For Synaptic:
[http://ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+segmentation+fault](http://ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+segmentation+fault)

---

### Post by BLTicklemonster on 2008-02-12
If you try to open these programs from the terminal, you will probably get some message that you can post here and see if someone can help you with it.

---

### Post by Nirevus on 2008-02-12
Not sure of your level of experience with Linux, so I thought I'd add that to open these programs from the terminal, you just need to load it up Applications > Accesories > Terminal and then type the name of the program. For example:

```
firefox
```

To open synaptic (and be able to make changes to the packages) you will need to type:

```
sudo synaptic
```

And then enter your password when prompted.

---

### Post by BLTicklemonster on 2008-02-12
Sorry, I should have been more specific.

Once you do that in the terminal, if the program won't open, then the terminal ought to have information in it that will be helpful in diagnosing the problem. Try copying and pasting the results here.

---

### Post by davetatem on 2008-02-13
Thanks for the advice, it's most helpful. 

I hadn't thought of using the terminal to start it (only three weeks into Linux!).  

The fault has just replicated and I get 'Segmentation fault (core dumped)' 
as the error message

---

### Post by rahul_bhise on 2008-02-13
i to have a same type of problem but with firestarter. when i start the firestarter it opens alright but after working for few minutes it automatically closes
```
brahul@uhome:~$ sudo firestarter
[sudo] password for brahul:
Firewall started
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7

Segmentation fault (core dumped)
```

---

### Post by Nirevus on 2008-02-14
DaveTatem, to fix your problem run the following commands in the terminal:

```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
sudo apt-get upgrade
```

This should fix the segmentation fault with Synaptic.

---

### Post by davetatem on 2008-02-14
Many thanks for the advice.  I've run the scripts and it's looking good!:)

---

### Post by Nirevus on 2008-02-15
Good to know, is Firefox still having issues? If so you could try Swiftweasel, it's what I use and I find it faster than Firefox anyway.

---

