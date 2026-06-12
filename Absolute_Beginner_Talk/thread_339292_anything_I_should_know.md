---
title: "anything I should know"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by james.a.t.g on 2007-01-15
aliright so i just installed unbuntu is there anythink i shud know. dont wana be messin up my computer and stuff.

---

### Post by TehMark on 2007-01-15
Make sure you have a different account for root.  get a new source.list file

---

### Post by jd65pl on 2007-01-15
You might want to know some simple linux commands

[http://jamie.dumbill.googlepages.com/ubuntucommands2](http://jamie.dumbill.googlepages.com/ubuntucommands2)

Also if you want to install software for a specific task

[http://jamie.dumbill.googlepages.com/ubuntusoftwaresuggestions](http://jamie.dumbill.googlepages.com/ubuntusoftwaresuggestions)

Here are a few how tos....

[http://jamie.dumbill.googlepages.com/ubuntuhowto](http://jamie.dumbill.googlepages.com/ubuntuhowto)

---

### Post by teaker1s on 2007-01-15
welcome to the forums-firstly don't be afraid to ask:mrgreen: 

secondly terminal
[COLOR="Red"]sudo[/COLOR] is for gaining root privilege on command line, secondly [COLOR="Red"]gksudo[/COLOR] is for root privilege of graphical apps.

also you may want to edit your sources list to uncomment some of the repositories and use 
sudo gedit /etc/apt/sources.list[COLOR="Red"][/COLOR]

remove the [COLOR="Red"]#[/COLOR]
[COLOR="Red"]gksudo nautilus[/COLOR] to add and remove programs.

synaptic preferences general and tick recommended files as dependencies-stops dependency issues-be careful if you remove programs to see that something you need isn't accidently removed:mrgreen:

---

### Post by Jaydos on 2007-01-15
Do anything and everything you can. Trust me, you'll be addicted to tinkering with things in no time. Not much that can go wrong if you read the guides/posts by all the helpful people.
Something I reccomend you learn off by heart;
sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.backup (This command backs up your xorg.conf)
sudo cp /etc/x11/xorg.conf.backup  /etc/x11/xorg.conf (This restores the saved xorg.conf file.

---

### Post by meng on 2007-01-15
> **TehMark said:**
> Make sure you have a different account for root.  get a new source.list file
You don't need to have a separate admin account, as anything that requires superuser privileges will need to be authorized with your password. Search the wiki for "RootSudo". As for your sources.list file (the list of software repositories your system will use), whether or not you will need to expand it will depend on what you want to use your system for (what extra applications you would like to install). I guess most users would want to universe and perhaps multiverse repositories enabled.

---

