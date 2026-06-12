---
title: "installing programs"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by much better on 2005-12-03
Hi everybody .
I don't have internet at my linux box so i am wondering how to install new programs and all the libraries the programs depends on ( anyway but apt-get )
Best regards

---

### Post by jorn on 2005-12-03
Hi!
There was a post regarding this issue som days ago but I can't find it. There is a website where you can download the apps and burn them to cd or dvd.
When I find it Iwill post.
Jorn

---

### Post by jorn on 2005-12-03
Hi!
Maybe this is something for you?
[http://www.ubuntuforums.org/showthread.php?t=61875&highlight=install+apps+internet](http://www.ubuntuforums.org/showthread.php?t=61875&highlight=install+apps+internet)
Jorn

---

### Post by much better on 2005-12-03
does the .deb files contain the librares the program depends on ?

---

### Post by Sanne on 2005-12-03
You could still use apt by creating your own local packages repository, either on your disk, or on a cd. You would have to download the packages and their dependencies on another computer with online access.

Please have a look at those wiki entries describing the procedures:

[Repository on hard disk]("https://wiki.ubuntu.com/PersonalRepositories")
[Repository on a CD]("https://wiki.ubuntu.com/AptMoveHowto")

---

### Post by much better on 2005-12-04
this is not helping 
Lets take this example : Kmail it exists in packages.debian.org at this url : [http://packages.debian.org/stable/mail/kmail](http://packages.debian.org/stable/mail/kmail)
so if you want to install it you have to download it with 20 depends ? and every one of those needs another depends and then you have an endless sequence !!!!
why it is not like windows just one file without complications ... Installing new software under linux is a nightmare .

---

### Post by d1337 on 2005-12-04
Sorry you feel that way, but I personally disagree.  Why isn't the machine on the internet?  That would be my first fix.  The install CD for Ubuntu, IMHO, has plenty of functionality just by what is included.  Don't take this the wrong way, but the etiquette involved in asking for help rarely involves > why it is not like windows
Windows often needs internet access itself for updates...albeit most security updates are more specific to online security.
Also, the example that you used is kmail.  What will kmail do for you on a machine that isn't on the net?

d1337

---

### Post by Kvark on 2005-12-04
It is open source so many different programs can use the same code. When they all depend on that shared code you only have to download, install, store on hard disk, load into ram memory and update that code once. If they would all ship with a separate copy of that shared code then you would have to download, store, etc, etc once for each program.

If your Ubuntu computer was connected to the internet when it would be a piece of cake to just type away with apt-get or click away in Synaptic Package Manger.

Maybe you could get DVDs with loads of packages on, add the DVDs as local repositories and install from them with Synaptic.

---

### Post by aysiu on 2005-12-04
[QUOTE=much better]
why it is not like windows just one file without complications ... Installing new software under linux is a nightmare .[/QUOTE] Really? See the second link in my sig. I would beg to differ.

---

### Post by kalos on 2005-12-04
[QUOTE=much better]Installing new software under linux is a nightmare.[/QUOTE]
I must admit I was of the same opinion when I was first introduced to Linux. But That is only because of the unfortunate position that you're in: No access to broadband. If there is anyway you could get your computer connected, you will find that Synaptic makes software installation a breeze (pun intended : ) Even with dial-up, I don't think it would be hard, just slow.

However, since for now you don't have this option (I assume), you will have to make a repo CD. Sanne referred to some instructions on how to use [AptMove]("https://wiki.ubuntu.com/AptMoveHowto"). Apt is the backend for synaptic and the howto has some cut and paste instructions. I believe you could even do this from a liveCD if you can't access an Ubuntu (or Debian-based) computer with internet access.

To simplify life in the future, you might want to get more than just Kmail. Are there any other programs that you might need? Even if you don't want to install now, you won't have to worry about making another AptMove disc.


To answer your deb question (to the best of my knowledge), the reason linux software has so many dependencies is efficiency. It saves space both on servers and on your linux computer.
[Some](http://www.psychocats.net/essays/winuxinstall.php) would argue that software installation is easier on Linux, regardless it is much more dependent on an Internet connection.
Windows programs have all of these dependencies as well, but they are almost always packaged with them. I imagine (but don't actually know) that if you purchase any Linux software, you won't have to worry about dependencies.

-kalos

---

### Post by much better on 2005-12-05
d1337 : 
I am sorry too but i used to have internet before but now i cant have internet for personal and i am sorry but i am tring install a program from more than a week with no succes 
and to be clear i am not defending about windows .. God knows how much i hate it and i will never use it again but i am not talking about security updates .. just the programs ..
and about kmail : it was just an example ;) 

Kvark :
yes it will be much easier if i have internet but i dont 

aysiu :
ok i will read what in it now

kalos :
Not everybody have internet .. in my case i had internet the last 4 years but now i dont and that will not be forever just month or tow

---

### Post by much better on 2005-12-05
Hi aysiu i read that and i agree with you but if you go to blender3d.org and downloaded the linux version of blender you will be able to use it just by pressing the program icon .. The same thing goes for wings3d you will download just one file to work with all linux distros and that is really cool and it will be coller if all linux programs works the same way .. if so then you can download your software from coffenet or get them from cd or any other way .
so i want to ask you why the other programs not like blender and wings ?

---

### Post by Sanne on 2005-12-05
much better, blender also depends on a lot of libraries, but it is much likely that every linux distribution comes with those by default.

You can see the libraries a binary executable depends on by doing:

ldd /path/to/the/program

I just did this with blender 2.40rc1 from blender.org which I'm testing currently, and got several lines of output.

In Linux there's much more variety in which libraries a program could use than in Windows, like for example the graphical toolkit that gets used, that draws buttons, menus and the visual surface of the program. In Gnome we have GTK, Kde programs use the QT/KDE libs, and others still use neither but toolkits like WxWidgets or the Fox toolkit. If every program brought it's own copy of those libraries, there would be far too much redundancy, and you'll get hard disk space problems pretty soon. ;)

This situation might not be ideal, but it's the price for the freedom of coice I think, in this case the freedom for the developers which toolkit to choose.

---

### Post by much better on 2005-12-06
untill i get my internet acsses back i want to try something .. I know a friend that use a debian based distro but not ubuntu i asked him yesterday how he install his programs and he answerd my he use apt-get
So my question : can i use the programs that ge downloaded on ubuntu and if so how to do that ?

---

### Post by aysiu on 2005-12-06
[QUOTE=much better]Hi aysiu i read that and i agree with you but if you go to blender3d.org and downloaded the linux version of blender you will be able to use it just by pressing the program icon .. The same thing goes for wings3d you will download just one file to work with all linux distros and that is really cool and it will be coller if all linux programs works the same way .. if so then you can download your software from coffenet or get them from cd or any other way .[/QUOTE] But why dig around on some website when you can get a plethora of software via Synaptic?

---

### Post by much better on 2005-12-08
i am still waiting the answer of my question ..

---

### Post by aysiu on 2005-12-08
[QUOTE=much better]untill i get my internet acsses back i want to try something .. I know a friend that use a debian based distro but not ubuntu i asked him yesterday how he install his programs and he answerd my he use apt-get
So my question : can i use the programs that ge downloaded on ubuntu and if so how to do that ?[/QUOTE] This may be your best shot, but it'd be better with Ubuntu packages than Debian ones...

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by bootlinux on 2005-12-08
If you wanted to install Debian's Sarge 3.1 rather then Ubuntu then you can purchase the 14CD set and use the CDs as your repository for Synaptic with no internet involved. You can Order these CDs over the intenet. Check out Distrowatch.com. 
Like a lot of other distrbutions Debian is where Ubuntu gets it's packages from anyway. There could be compatablity issues between Ubuntu and Debian repositories so I wouldn't advise using Sarge CDs on a Ubuntu install.
Just my 2cent worth.

---

