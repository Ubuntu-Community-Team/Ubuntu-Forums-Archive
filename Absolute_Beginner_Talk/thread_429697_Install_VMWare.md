---
title: "Install VMWare"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-05-01
Can anyone tell me how to install VMWare on my computer. I have downloaded VMWare Server for Linux, it has the following filename: "VMware-server-1.0.3-44356.tar.gz". Any help would be appreciated.

---

### Post by Cypher on 2007-05-01
That would be a "tarball"..Execute
```

tar -xvzf VMware-server-1.0.3-44356.tar.gz

```
to extract the contents into the current directory. You will see a list of files go across as the extraction is happening. Once it's done, go into the newly created directory and find any README/INSTALL or other files which might have further instructions..

---

### Post by starcraft.man on 2007-05-01
Easy GUI way is to right click on file and select "extract here" :).

Knowing the terminal commands is always good though, never belittle the power of the CONSOLE! *dun dun DUNNNNN* :p

---

### Post by thecomputingexpert on 2007-05-01
There is a file called "vmware-install.pl", when i double click it it asks me whether I want to run it, display or run in terminal, when i click Run it gives me well... nothing, run in terminal does the same, and displaying it just opens it in a text file

---

### Post by oilchangeguy on 2007-05-01
go to [www.getautomatix.com](www.getautomatix.com) install automatix, from there you can easily install vmware player, and much more.

---

### Post by thecomputingexpert on 2007-05-01
VMWare player does not allow me to produce my own virtual machines which wont help, well that was the case last time I used it, I have downloaded VMWare Server so that I can install Windows XP on a virtual machine

---

### Post by zvacet on 2007-05-01
There are two wys to solve your problem.First,you can install vmware server from synaptic,but   that is not last version.Second look to this page
[http://www.debuntu.org/]("http://www.debuntu.org/")

---

### Post by Calash on 2007-05-01
Going from memory here, but I think you have to co to the console, browse to the directory with the vmware-install.pl file in it and run


$sudo ./vmware-install.pl


Make sure you have the licence code available (being able to copy and paste it makes life easier), it will ask you for it when it runs the config part.  For most of the questions I let it use it's default settings...did not have any issues.

---

### Post by Duck2006 on 2007-05-01
Try virtualbox then.
You can get it from automatix

---

### Post by ali4949 on 2007-05-01
Hold on buddy, before you give up on the vmware server install, I just got done with it and it was a breeze.
Use synaptic and select the server  packages, I dont think its that big of a difference in functionality. Make sure you select all the packages which have server in the name  and while you are doing this go to vmware site and register for the server, its free and get your license, save it in a text file, apply the changes in synaptic and enter the license when it prompts you. 
After that fire up the vmware server, its under applications - system tools- vmware server..... and start creating your virtual machines and all the OS es you would like.
I had tried the vmware player but no joy, and also had used the easyvmx site to create virtual machines to work with vmplayer, but for a noob like me it was too much to comprehend. 
I think for the first time use the easy way, and make things work and experience the software, and then move to terminal session. Just my opinion.
hope you get the server working . 
And on a side note the Automatix install of the vmware server didn' t go through all the way and I had to run dpkg --configure -a to complete the process, and that install gave me errors/ non working vm server so I ended up removing it and doing the install through synaptic.

---

### Post by scotttkd on 2007-05-01
there is also a tutorial on howtoforge.org that walks through the setup.  I believe it will work on feisty but it has been a while since I looked at it.  I am running virtualbox and tweaked it with this excellent link from bohdi - [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox) and things work very well.  only thing I am missing is cut and paste between guest and host.  that is supposed to be coming soon according to the virtualbox forum.

---

### Post by SteveHoffmanUK on 2007-05-02
Ali4949 wrote:

> Use synaptic and select the server packages, I dont think its that big of a difference in functionality. Make sure you select all the packages which have server in the name and while you are doing this go to vmware site and register for the server, its free and get your license, save it in a text file,

I did all that.

Then he wrote:
> apply the changes in synaptic and enter the license when it prompts you

What does that mean? Do you mean mark for installation? Well, I did all that (above) What do I have to do to make it prompt me for the license number? I go to Applications > System Tools > VMWare Server Console, click on it, the little wheel whizzes around for a bit, then stops, and no sign of VMWare.

In Synaptic I tried uninstalling everything with "VMWare" in it and then reinstalling it, but the same thing happens. When I uninstalled everything, I noticed that VMWare Server Console still showed under System Tools. What's going on?

Thanks for any help you can give.

ON EDIT: The link in Zvacet's message says, "Since Ubuntu 7.04, Feisty Fawn, Ubuntu is using a standard kernel 2.6.20. Because of a few changes in the API, VMware-server and VMware-workstation 5.5 fail to install under Ubuntu 7.04 Feisty Fawn." So another reason for me to revert to Edgy. Feisty is also "losing" my external hdd sometimes, in a rather random pattern. I am deeply unimpressed with Feisty.

---

### Post by Duck2006 on 2007-05-02
Give virtualbox a try  then. It loads a lot better than VMWare and no nubmers to input.
You can get it from automatix

---

### Post by zvacet on 2007-05-02
**programs>accessories>terminal**

```
vmware
```


If this make server to run then enter licence number.

---

### Post by SteveHoffmanUK on 2007-05-03
Duck2006 and Zvacet:

Thanks for your help. I am now reinstalling Edgy, so maybe a fresh install will sort things out. Here&#347; hoping....

---

### Post by veloce on 2007-05-03
Vmware server does work under feisty.  Quite well actually.

I installed it under Edgy and upgraded to Feisty.  Needed to download the patch:
vmware-any-any-update109.tar.gz from the vmware site.

However, at some stage you do need to provide it the license number.  I did that under Edgy.

---

### Post by FerGeCo on 2007-05-03
if you use feisty you can install vmware-server with the synaptic package manager .. just search for vmware-server and the package manager will enable the correct repo's

---

### Post by wormser on 2007-05-03
There are some issues when installing VMware Server in Feisty.  I found this post and it worked for me.

[http://ubuntuforums.org/showpost.php?p=2384779&postcount=52](http://ubuntuforums.org/showpost.php?p=2384779&postcount=52)

---

### Post by FerGeCo on 2007-05-03
> **wormser said:**
> There are some issues when installing VMware Server in Feisty.  I found this post and it worked for me.

[http://ubuntuforums.org/showpost.php?p=2384779&postcount=52](http://ubuntuforums.org/showpost.php?p=2384779&postcount=52)

I just installed it from the repo's (ok .. it's not the latest version) and that worked for me ..
Installed 2 vm's so far ..

---

### Post by wormser on 2007-05-03
> **FerGeCo said:**
> I just installed it from the repo's (ok .. it's not the latest version) and that worked for me ..
Installed 2 vm's so far ..

I forgot... that is for the latest version on VMware.

---

### Post by lancest on 2007-05-04
Virtual Box is running under Fiesty.
Nvidia Geforce 7400 (latest driver in Linux)
[FONT="Franklin Gothic Medium"]Windoze [/FONT]XP installed
Start VBox
 Choose fullscreen- not happening . [COLOR="Blue"]**How to get full screen (widescreen) to work?**[/COLOR]

---

