---
title: "Need help! :( another n00b"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Luj0 on 2007-02-21
Hy all.

Have a little bit of a problem.
New here, so if you can help me you are a genious :) 

In the synaptic package manager, all the files are installed, shoudnt i be able to install new appz with it? 

What program do i need to install applications? For example: i need an application to watch tv on my tv card.

What are repositories? can i update them maybe

Can I install Desktop effects, i'm sure you know what are these, so when i move around my workspaces they look like a cube, i saw that, look's nice. I have ATI, heard that ATI doesnt support that...

I'm sorry if i said something wrong, total n00b here, but willing to learn... Love linux :guitar: 

Tnx for help.

Luka

---

### Post by Maestro23 on 2007-02-21
> **Luj0 said:**
> Hy all.

Have a little bit of a problem.
New here, so if you can help me you are a genious :) 

In the synaptic package manager, all the files are installed, shoudnt i be able to install new appz with it? 

What program do i need to install applications? For example: i need an application to watch tv on my tv card.

What are repositories? can i update them maybe

Can I install Desktop effects, i'm sure you know what are these, so when i move around my workspaces they look like a cube, i saw that, look's nice. I have ATI, heard that ATI doesnt support that...

I'm sorry if i said something wrong, total n00b here, but willing to learn... Love linux :guitar: 

Tnx for help.

Luka

Installing in Ubuntu:
 [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Additional Themes:  [www.gnome-look.org](www.gnome-look.org)

Beryl(Cube and 3D EyeCandy): [http://www.ubuntuforums.org/showthread.php?t=349732](http://www.ubuntuforums.org/showthread.php?t=349732)

Good luck.

---

### Post by Tomosaur on 2007-02-21
Synaptic should work fine. Click System > Administration > Synaptic Package Manager

When it loads up, it'll scan your computer for which packages are already installed. You can then search for extra programs to install, or remove/reinstall ones you already have. Repositories are web addresses which contain packages. Synaptic uses them. To enable more (and thus be able to download more software), there is a menu item in Synaptic which allows you to enable / disable new repositories. I can't remember exactly which menu you click, but a simple investigation should bring up the repository configurator :)

The desktop effects you're talking about are provided by beryl. Beryl is available through synaptic. You may have problems with your ATI graphics card - but there are numerous howtos on this forum for any problems you may have.

Good luck :)

---

### Post by Luj0 on 2007-02-21
> **Maestro23 said:**
> Installing in Ubuntu:
 [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

Good luck.

I was on this page, when adding extra repositories i have to click on repositories, i click and nothing happens, it says that there shoud be a lt of application to download, but i cant find one that is avalible to download... there is only files aplications... that i can mark for removal? Doing something wrong or?

---

### Post by Carlos Santiago on 2007-02-21
Hi.

First of all, Synaptic shows the applications that you have installed. Thats why, all the applications that you see are installed! ;-)

On Synaptic you also have a search button to search web for more applications, then you will find lots of application that wont be installed by default. 

The repositories are the web sites of your trust where the applications reside. 
By default you have archive.ubuntu.com repository, but you can had more.

If you don't care if you use only GPL software or FREE but not GPL (has you probably don't), activate universe and multiverse on ubuntu repositories.
  
To do so, open repositories window, then select universe and multiverse, and close it. Then hit reload.

After that you will find even more software on your searches!!!

Concerning you TV card, i cannot help much, because I don't have a TV card.

Give a try to MythTV.  How?

Simple as this, hit the search button and type MythTV. Then select it for install. Finally click on apply!

Then you just have to run the application!

And the best of all is that you can install software with no problem, because it should not contain any malicious software. Remember, it cames from a repository of your trust.

---

### Post by Luj0 on 2007-02-21
> **Carlos Santiago said:**
> Hi.

1>>First of all, Synaptic shows the applications that you have installed. Thats why, all the applications that you see are installed! ;-)

Hehe not such a n00b :D

2>>On Synaptic you also have a search button to search web for more applications, then you will find lots of application that wont be installed by default. 
The repositories are the web sites of your trust where the applications reside. 
By default you have archive.ubuntu.com repository, but you can had more.

3>>To do so, open repositories window, then select universe and multiverse, and close it. Then hit reload.

.
1>>
Hehe not such a n00b :D
2>>
When i type anything into search, i gives me stuff, application that i allready have installed.  With search button i cant find new software That why i asked about repositories, because i think the problem is here ?
3>>
This is the problem, when i click on repositories, nothing open, i see window in a milisecond and it closes. So i cant open repositories...
Is this somekind of a Bug or something? :confused:

---

### Post by tgalati4 on 2007-02-21
Unless something is broken (it is possible), it takes time (several minutes perhaps) to update the application lists that the new repositories bring.  Be patient.  Run **top** in a terminal window to see if you have synaptic running.  It's possible that it is just taking time to load.  Also, don't close synaptic right away after adding a package.  It takes time to update the local package database.  Closing synaptic right after downloading will cause problems.  It's just one of those things that you get used to in Linux.

---

### Post by annda on 2007-02-21
if it's not working you will have to it manually:

in a text editor open the file  /etc/apt/sources.list with root rights, for example type this in the terminal:

```
gksudo gedit /etc/apt/sources.list
```

and uncomment the universe and multiverse repositiories (delete the # at the beginning of appropriate lines). save the file and open synaptic again. hit reload and you should be able to use the new repositories.

---

### Post by Luj0 on 2007-02-21
> **annda said:**
> if it's not working you will have to it manually:

in a text editor open the file  /etc/apt/sources.list with root rights, for example type this in the terminal:

```
gksudo gedit /etc/apt/sources.list
```

and uncomment the universe and multiverse repositiories (delete the # at the beginning of appropriate lines). save the file and open synaptic again. hit reload and you should be able to use the new repositories.

I dont know how long do i have to wait:)  but im sure that my sources.list are empty :confused:  so i gues there is the problem... How can i add ?
I didnt delete anything now :D there isn't anything to delete

---

### Post by macogw on 2007-02-21
Your sources.list is empty?  How'd THAT happen?  No wonder nothing's listed as installable.  Go to ubuntuguide.org and scroll to the "enable extra repositories" part and copy and paste that chunk into your sources.list.

---

### Post by Luj0 on 2007-02-21
> **macogw said:**
> Your sources.list is empty?  How'd THAT happen?  No wonder nothing's listed as installable.  Go to ubuntuguide.org and scroll to the "enable extra repositories" part and copy and paste that chunk into your sources.list.

This solved my problem. I'm sorry I coudnt explain my problem better, not as good in english, and in linux :D

Thank you everone very much.

luka

---

