---
title: "how to install new software"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by vladaemyr on 2008-03-29
I am trying to install new software. but being a novice, I don't have a clue where to start. can someone please help me. whoever answers please be detailed on what I have to do remember I am a novice to this. thank you to all of you that answer.

---

### Post by T2manner on 2008-03-29
an easy way is to go to the add/remove apps.
in the main menu.

or if u know what app. it is
you could do
> sudo apt-get install [name of app. here] 
in terminal

---

### Post by drs305 on 2008-03-29
In its easiest form, if you know the name of the program, you can go to the terminal and type:
```
sudo aptitude install program-name
```

---

### Post by Inxsible on 2008-03-29
and finally you could install from the Synaptic Package Manager too. System>>Administration>>Synaptic Package Manager. Search for the software and right click and select 'Mark for Installation'

---

### Post by Victormd on 2008-03-29
As a novice, either go to Applications> Add/Remove and simply mark the program you want to install and click apply.  Another graphical way is to go to System>Administration>Synaptic Package Manager and either search the name of the application you want to install to see if it exists in the repositories (a network database with secure applications), then simpli mark it for installation.

---

### Post by lswest on 2008-03-29
since you're new to it, i assume you'll want a GUI (graphical user interface) and you have 2 to choose from.  One (basic one) is under Applications--> add/remove applications, and the more advanced one is under system-->administration-->synaptic package manager.  Both of them give you a search option, and you search for something, e.g. music player, and choose which one (judging by the description) suits your needs, and right-click and choose "install".  They're pretty straight-forward.

---

### Post by mdsmedia on 2008-03-29
If you don't know the name of the application, try Synaptic Package Manager under the SYSTEM menu. System -> Administration -> Synaptic Package Manager.

In there you can search for packages to suit your needs or just the particular package you need.

apt-get is wonderful if you know exactly what you want.

Beaten to the punch with a better explanation by lswest....and others :)

---

### Post by bwhite82 on 2008-03-29
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by drs305 on 2008-03-29
Since you say you are new and that means you will probably be adding quite a few apps, perhaps the easiest thing for you to do is put a shortuct to Synaptic on your panel. 
To do this, right click an empty space on the panel (the top, bottom, or side pane which has a few shortcuts already on it), and select  "Add to Panel". The click on Application Launcher. Click on the triangle to the left of System Tools to display the options, hightlight Syanaptic Package Mangaer, and click Add. Now you can open Synaptic by clicking on the panel shortcut you just created.

---

### Post by pbpersson on 2008-03-29
Assuming that you are coming from the Windows world, don't know what any of the packages are called, and are not too crazy about using the command line (console or terminal as it is also called):

Click on what in Windows would be the start menu

Go to Add/Remove programs

It will ask you to type your admin password

A window will appear showing you different categories such as development, games, graphics, internet, multimedia, office, etc

In that window you can mark which packages you want to install

When you click on "apply changes" it will install all the packages for you and configure everything - if there are quite a few it can take some time.

In certain circumstances it is helpful to set the window so you can see the details while the packages are installing - if the installation seems to hang it might be asking you to agree to a license for some software

---

### Post by pbpersson on 2008-03-29
Note -

Five different people just told you five different ways to install new software

We are all correct

In Ubuntu there are several ways to do everything AND several applications that accomplish the same task

This might be a little overwhelming, but it is the Linux way :)

---

### Post by T2manner on 2008-03-29
well
5 people said the same thing 5 different ways...

---

### Post by lswest on 2008-03-29
lol, yeah, my thoughts exactly T2Manner.  But yes, there are many ways to go about doing things in linux.  Perhaps the OP could mark this thread as solved so that we don't get a 6th explanation of the same thing? :lolflag:

---

