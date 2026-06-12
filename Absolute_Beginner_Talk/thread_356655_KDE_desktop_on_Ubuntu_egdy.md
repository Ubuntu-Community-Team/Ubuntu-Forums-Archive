---
title: "KDE desktop on Ubuntu egdy"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by gizmoarena on 2007-02-08
if i do not have any internet conncetion, can I use install kubuntu-desktop thingy by apptitude or synaptic?

when i checked synaptic from live CD, there was the entry for kubuntu-desktop.
but when i installed ubuntu egdy, there is no option in synaptic for installing kubuntu-desktop.

i have kubuntu drapper cd, can i use that for installing kde?
i have ubuntu drapper dvd as well, it that any good for ubuntu edgy (for updating anything)

consider, i have no internet connection.

---

### Post by Maestro23 on 2007-02-08
You can use the Live CD as a source. Something like:

> 
#sudo apt-cdrom add
#sudo apt-get update
#sudo apt-get install <program>


---

### Post by gizmoarena on 2007-02-08
thanks for your quick reply :)

I still cannot install kubuntu-desktop. 
> E: Couldn't find package kubuntu-desktop

is it really possible to install kubuntu-desktop without having internet connection?

---

### Post by r4ik on 2007-02-08
-

---

### Post by %hMa@?b&lt;C on 2007-02-08
is kde-core on the livecd?

---

### Post by gizmoarena on 2007-02-08
nope. there is nothing related to KDE.

i have kubuntu CD, would that work?

---

### Post by %hMa@?b&lt;C on 2007-02-08
> **gizmoarena said:**
> nope. there is nothing related to KDE.

i have kubuntu CD, would that work?
yes, that would work, as it has all of the KDE packages.

---

### Post by gizmoarena on 2007-02-08
i can't do it. synaptic is not showing anything of the kubuntu cd even after i added it as a repo.

what is the easier way?


> gizmo@desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/main Translation-en_US
Ign cdrom://Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/restricted Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Reading package lists... Done


gizmo@desktop:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
**[COLOR="Red"]Couldn't find any package whose name or description matched "kubuntu-desktop"[/COLOR]**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by gizmoarena on 2007-02-08
i guess i am going back to mandriva2007 again :(

---

### Post by shareMenaPeace on 2007-02-08
See here how to install it

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

[http://ubuntuforums.org/showthread.php?t=351135&highlight=install+kde](http://ubuntuforums.org/showthread.php?t=351135&highlight=install+kde)
> 
sudo aptitude install kdebase

---

### Post by gizmoarena on 2007-02-08
thanks but it doesn't work, check out my quote on my previous post.

**NOTE: CONSIDER, I DONT HAVE INTERNET.**

---

### Post by gizmoarena on 2007-02-08
**[COLOR="Red"]gizmo@desktop:~$ sudo aptitude install kdebase[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
[COLOR="Red"][B]No candidate version found for kdebase
No packages will be installed, upgraded, or removed[/B][/COLOR].
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by %hMa@?b&lt;C on 2007-02-08
> **gizmoarena said:**
> i can't do it. synaptic is not showing anything of the kubuntu cd even after i added it as a repo.

what is the easier way?
can you browse the cd, and find packages on it?

---

### Post by gizmoarena on 2007-02-08
> **jeffc313 said:**
> can you browse the cd, and find packages on it?

I have tried that as well, there's nothing related to 'kde', I have searched both ubuntu and kubuntu CD's.

---

### Post by shareMenaPeace on 2007-02-08
The second link i posted above and the command are for install without internet.
[http://ubuntuforums.org/showthread.php?t=351135&highlight=install+kde](http://ubuntuforums.org/showthread.php?t=351135&highlight=install+kde)

But try aptitude if this not work apt-get

Ok and maybe you have the server version only? Meaning there is no Desktop on it - than you need the desktop iso version.

---

### Post by gizmoarena on 2007-02-08
> **shareMenaPeace said:**
> The second link i posted above and the command are for install without internet.
[http://ubuntuforums.org/showthread.php?t=351135&highlight=install+kde](http://ubuntuforums.org/showthread.php?t=351135&highlight=install+kde)

But try aptitude if this not work apt-get

Ok and maybe you have the server version only? Meaning ther eis no Desktop on it - than you need the desktop version.

i am confirm that i am using a desktop version. moreover, i have checked out the synaptic entries when i was using it as a live cd. there was "kubuntu-desktop" option and other kubuntu, kde packages.

but after installing it, those kubuntu things just vanished :|

---

### Post by gizmoarena on 2007-02-08
okay ... i found a solution ... I HAVE TO INSTALL KUBUNTU ... then get the other programming /developement packages from ubuntu DVD. i hope that might work.

thanks for your cooperation guyz. thanks a lot :D

---

### Post by shareMenaPeace on 2007-02-08
What you mean after you installed it?
Did you was able todo it? Maybe boot and choose from login session kde?

And in worst case you will be able to install kde somehow from the kubuntu cd.

---

### Post by gizmoarena on 2007-02-09
No I couldn't do it! What I did was installing my 4-cd Mandriva 2007 which has almost everything I want - works for me :D

thanks again dude (Y)

---

