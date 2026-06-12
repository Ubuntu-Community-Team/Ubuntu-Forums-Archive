---
title: "How the hell?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by blazer666 on 2006-06-19
I am really getting frustrated with Linux, how the hell do you install anything? I cant install dvix codecs, graphics card drivers, media plugins. 

How can i get things to work please? I download an archive and extract it to my desktop, I then cant see anything in the folder that has been extracted that will allow me to run it. 

EG:

I downloaded the NVIDIA drivers for my 7900GTX card it was a file called NVIDIA-Linux-x86_64-1.0-8762-pkg2.run 

If i click on this file i get the error window pop up saying Could not open the file /home/derek/Desktop/NVID…-x86_64-1.0-8762-pkg2.run.  ??? eh ](*,) 

Please can someone help me, Im used to double clicking on things and it works.

Thanks :lol:

---

### Post by rbalfour on 2006-06-19
1) Use the Package Manager to install apps.

2) /home/derek/Desktop/NVID&#8230;-x86_64-1.0-8762-pkg2.run
Right click and check excute permission to it and run it from a Terminal
$ ./NVID&#8230;-x86_64-1.0-8762-pkg2.run

3) READ the HOW-TO section -> [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

4) You can try using this. -> [http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)
it works well, getting the codecs to watch those downloaded movies.

---

### Post by raffytaffy on 2006-06-19
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by bohboh on 2006-06-19
Dont know about your nvidia drivers, but to install you can use the various installer systems:

Automatix
Synaptic
Add/Remove
Command line apt-get (Make sure you add repos to /etc/apt-get/sources.list)

When downloading directly from a site i look for the .tar files, untar and read any help files (README etc). They normally tell you what you need to do.

---

### Post by Gustav on 2006-06-19
Most programs are installible via the synaptic package manager (system->administration->synaptic package manager)

Here´s instructions on how to install the nvidia driver: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by someusernoob on 2006-06-19
System > Administration > Synaptic Package Manager.

There you'll find all the software you need. you might enable some repositories* for things like codecs, but that may be not legal in your country (thats why all those codecs arent shipped with the Ubuntu installer)

Use the nvidia drivers you find in there, they are automaticly updated when your kernel gets an update, saves you some uninstall/install troubles.

*Setting > Repositories > Add (and check universe and multiverse) Reload Synaptic after you did this.

Edit:lol everyone is so fast here.

---

### Post by u.b.u.n.t.u on 2006-06-19
Please check my wiki link in my signature. I add step by step instructions for Nvidia, to get 3D.

---

### Post by FredB on 2006-06-19
[QUOTE=u.b.u.n.t.u]Please check my wiki link in my signature. I add step by step instructions for Nvidia, to get 3D.[/QUOTE]

I installed my 3d enabled server for nvidia using the method described in your wiki... 3 weeks ago... And even with kernel update, I didn't have a single problem with my nvidia card ;)

---

