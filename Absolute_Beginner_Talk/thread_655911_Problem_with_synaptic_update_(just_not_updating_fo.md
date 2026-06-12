---
title: "Problem with synaptic update (just not updating for me)"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by davidcanada2006 on 2008-01-01
hello to all,

i hate to say this, but since i'v been installing Ubuntu 7.10 on my old pc, it brings tones of troubles. but don't get me wrong, i find this strongly interesting to solve problems by tweaking a little bit of here and there. before i decided to joint the community of Ubuntu, all i heard was how easy it is to get it installed and blink! it will work right out of the box, but it actually isn't, to start off, i have to modify the config in the firefox for it can actaully display something. then i have this trouble that i have been working for weeks without even closely getting a clue of where goes wrong.

it's all about the synaptic update manager, when i first run it, it itself wants to load a repository index, and that is the start of the nightmare, i thought it would take a min to download, but i stopped at 7/14 files and never moved up. when i further bring down the lost pf details, it shows some of the files are simply failed to be downloaded, yet, no sign of retrying is displayed. then i try to config the **source** by using an integrated program which pings every server and choose one that is the fastest for me. and yet still, the index of repository stopped at some failed files.

then i try to read a little, and try to deselect everything (critical updates, 3rd party softwares....) but leave the **restricted driver** option up, since i have an TNT2 video card, i really want to get the 3D functionality working. and yet, it failed to download.

so, has anyone got an idea? 

thank you massively in advance

Dave

---

### Post by bump_ on 2008-01-01
First, just in case your sources got messed up, go to System -> Admin -> SOftware Sources.
Click the ones that end in "main", "universe", "restricted" and "multiverse". Then click on the "third part" tab on top

Here, if there is anything, activate it. For "updates" tab, get "gutsy-security" and "gutsy-updates".

Ok now see what happens when you type

```
sudo apt-get update

sudo apt-get upgrade
``` 
in the terminal

---

### Post by davidcanada2006 on 2008-01-02
it displays when i try get update :

0% [connecting to archive.canonical.com (1.0.0.0)] [Connecting to archive.ubuntu]

and freezes there.

then when i try the get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]

---

