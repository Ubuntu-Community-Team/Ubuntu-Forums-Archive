---
title: "Vmware"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by HybridTheory on 2007-02-27
Ok I need some help with Vmware-Workstation 5.5 I downloaded it as a Tar.gz file i used alien to turn it into a .deb i installed it and now I can't find it any where on ubuntu any clue what i can do or what is happing? :confused: 

thnx

---

### Post by Quillz on 2007-02-27
I just checked Synaptic, and VMWare Player is available. Do you need the workstation? If all you want to do is run a virtual machine, Player will suffice.

---

### Post by HybridTheory on 2007-02-27
> **Quillz said:**
> I just checked Synaptic, and VMWare Player is available. Do you need the workstation? If all you want to do is run a virtual machine, Player will suffice.

I already have the player but i also have the workstation i just cant find it after i installed it to run it

---

### Post by Quillz on 2007-02-27
Hmm... Try searching for it. Also, if it's like any other application, it should have a hidden directory in your home folder. It may have installed an executable there.

---

### Post by HybridTheory on 2007-02-27
> **Quillz said:**
> Hmm... Try searching for it. Also, if it's like any other application, it should have a hidden directory in your home folder. It may have installed an executable there.

I've found all kinds of workstation stuff here and there just nothing to run it

---

### Post by Onurzaim on 2007-02-27
As I know .rpm files can be turned to .deb files with alien.

If you have tar ball or vmware extract it and run >sudo ./vmware-install.pl and follow directions in terminal carefully.

---

### Post by HybridTheory on 2007-02-27
> **Onurzaim said:**
> As I know .rpm files can be turned to .deb files with alien.

If you have tar ball or vmware extract it and run >sudo ./vmware-install.pl and follow directions in terminal carefully.

travis@travis-desktop:~$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found

I think im doing something wrong 

Package: Vmware-workstation-5.5.3
Status: Same version is already installed

Converted Slackware tgz package
(Converted from a tgz package by alien version 8.50.) 

Thats what my installer stays so i know its installed or i hope...lol

Oh here i found that file this is what it said

travis@travis-desktop:~$ sudo /home/travis/work2-1/vmware-distrib/vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

---

### Post by petersjm on 2007-02-27
Open terminal and tryp "vmware" (without the quotes) and then hit the tab key, it'll beep, then hit it again. It should come up with a list of all commands beginning with vmware. See if "workstation" is there. If it is, type it exactly as it appears and workstation should load. After that, you can simply create your own application launcher with that command.

---

### Post by Onurzaim on 2007-02-27
Try searching vmware in synaptic package manager and remove it. Maybe it will help you to set your new version up.

---

### Post by HybridTheory on 2007-02-27
> **petersjm said:**
> Open terminal and tryp "vmware" (without the quotes) and then hit the tab key, it'll beep, then hit it again. It should come up with a list of all commands beginning with vmware. See if "workstation" is there. If it is, type it exactly as it appears and workstation should load. After that, you can simply create your own application launcher with that command.

travis@travis-desktop:~$ vmware-
vmware-config-network.pl  vmware-ping        

Thats what popped up

---

### Post by petersjm on 2007-02-27
> **HybridTheory said:**
> travis@travis-desktop:~$ vmware-
vmware-config-network.pl  vmware-ping        

Thats what popped up

Can you try it without the dash? Just "vmware" then tab, tab... Anything else pop up?

---

### Post by HybridTheory on 2007-02-27
Y'all do know im trying to install a tar.gz right? i turned it into a deb with alien without knowing really how i did it i was fooling around..so i may not even made the .deb right or something..

---

### Post by HybridTheory on 2007-02-27
> **petersjm said:**
> Can you try it without the dash? Just "vmware" then tab, tab... Anything else pop up?

That - thing pops up when i hit tab lol hmm i think its loading my vmplayer and not the workstation when i do the tab thing

---

### Post by bikeboy on 2007-02-27
I definitely don't think alien converts from tar.gz, only from rpm.

To extract the the tar.gz (which is a zipped tar file) try the following:
```
tar -xzvf nameoffileyoudownloaded.tar.gz
```

Then check the directory you extracted to for a folder called vmware-workstation or something like that. Go into there and take a look at the readme, it should tell you what command to run in order to install vmware-workstation. Hopefully that all works quite simply, if not some other person might be able to help with that part, as I've never tried it.

---

### Post by HybridTheory on 2007-02-27
> **bikeboy said:**
> I definitely don't think alien converts from tar.gz, only from rpm.

To extract the the tar.gz (which is a zipped tar file) try the following:
```
tar -xzvf nameoffileyoudownloaded.tar.gz
```

Then check the directory you extracted to for a folder called vmware-workstation or something like that. Go into there and take a look at the readme, it should tell you what command to run in order to install vmware-workstation. Hopefully that all works quite simply, if not some other person might be able to help with that part, as I've never tried it.

Then thats whats wrong lmao i turned a tar.gz into a .deb that didnt work right

---

### Post by HybridTheory on 2007-02-27
Ok so i unzipped it and this is what files i got 
Bin, Doc, Etc, Intaller, Iib, Man, FILES and vmware-install.pl and i dont have a clue on how to install it from here

---

### Post by jonathan.lees on 2007-02-27
You could follow the howtoforge guide here:

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

### Post by HybridTheory on 2007-02-27
> **jonathan.lees said:**
> You could follow the howtoforge guide here:

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Thats for Server...Im dealing with Workstation lol

---

### Post by petersjm on 2007-02-27
Okay, now we're getting somewhere. Right, CD to the directory you unzipped to. If it's on your desktop, the easiest way is to type "CD" in a terminal, followed by a space, then drag the folder into the terminal. It will fill it in for you. Hit enter. Now type the following:

```
sudo ./vmware-install.pl
```

and follow whatever instructions it gives you. When it's done, it should be installed and ready to go...

---

### Post by HybridTheory on 2007-02-27
> **petersjm said:**
> Okay, now we're getting somewhere. Right, CD to the directory you unzipped to. If it's on your desktop, the easiest way is to type "CD" in a terminal, followed by a space, then drag the folder into the terminal. It will fill it in for you. Hit enter. Now type the following:

```
sudo ./vmware-install.pl
```

and follow whatever instructions it gives you. When it's done, it should be installed and ready to go...

lol i already  beat you to that and yes i worked i hit enter like 500 times it got done no clue what i did workstation is there wont run lol so i gusess ill read over it this time

---

### Post by Maestro23 on 2007-02-27
VMware How-To: [https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

How to install in Ubuntu (Some links you might want to bookmark):
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Good luck.

---

