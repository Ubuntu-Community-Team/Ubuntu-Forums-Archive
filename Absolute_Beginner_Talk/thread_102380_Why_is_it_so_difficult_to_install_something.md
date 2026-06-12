---
title: "Why is it so difficult to install something ?"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by JnMrno on 2005-12-11
Can someone please tell me why does it have to be that difficult to install a program ?? cuz i'm new and i'm a bit dissapointed on linux because of that.

---

### Post by Todd_Z on 2005-12-11
Its soooooo easy!

System -> Administration -> Synaptic

Search for your program, and chances are, its there - it will auto. download all the libraries and junk that you need to run it - eez so nice!

---

### Post by Dogmeat on 2005-12-11
And now in breezy it's even easier! Just click Applications -> Add Applications (not sure if that's how it's named in English but it's the best translation I could make from my native language, it's the last item of the first menu.)

---

### Post by nihilism wow on 2005-12-11
[QUOTE=Dogmeat]And now in breezy it's even easier! Just click Applications -> Add Applications (not sure if that's how it's named in English but it's the best translation I could make from my native language, it's the last item of the first menu.)[/QUOTE]
Perfect translation. Also, apt-get is incredibly easy. I think it's easier than looking for a program online and then having to download it, then running an .exe and going through a wizard.

---

### Post by 23meg on 2005-12-11
Take a look at [this]("http://www.psychocats.net/linux/installingsoftware.php").

---

### Post by aysiu on 2005-12-11
[QUOTE=23meg]Take a look at [this]("http://www.psychocats.net/linux/installingsoftware.php").[/QUOTE] Or [this](http://www.psychocats.net/essays/winuxinstall.php) or [this](http://www.ubuntuforums.org/showthread.php?t=80295)

---

### Post by IYY on 2005-12-12
Difficult to install software? :???: 

I always found that in Ubuntu, installing software is easier and faster than in Windows. Just run Synaptic, search and install.

---

### Post by kingsidy on 2005-12-12
With Debian based distros it is easier I think. You have Synaptics, plus dpkg -i for package you download. It is easier to resolve dependancies. I used to use suse before Ubuntu and I think that Ubuntu has the better package management system compared to rpm based distros.

---

### Post by JnMrno on 2005-12-12
OK, thank you guys, that's what i needed:p 

The thing is I still don't know that much, but I'll keep trying, you guys were new once.

Thank again for encouraging me !!:p

---

### Post by Yafi on 2005-12-12
Hey, i'm also new to ubuntu and linux, and i would like to install the NVIDIA driver for my 6600GT, but when i type : sh NVIDIA-Linux-x86-1.0-8174-pkg1.run in konsole it says unknown file or map. Is there a kind soul in the room to help me ? :)

Tnx in advance dudes and dudettes :)

---

### Post by Unicast on 2005-12-12
This looks like a good place to start: [http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+installation](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+installation)

---

### Post by Turtle.net on 2005-12-12
In fact that's not difficult...that's different.
You have to choose a software in a library...so the difficult part is to find the software you want (since your Microsoft references will not work).
Have a look at [http://ubuntuforums.org/showthread.php?t=33183]("http://ubuntuforums.org/showthread.php?t=33183")

---

### Post by mistergq on 2005-12-12
I just tried the add applications, and man is that easy.  I am impressed.  :D

---

### Post by ncappel1 on 2005-12-13
Wow, thank you so much for this link! it has made my life a lot easier!

---

### Post by Paul28 on 2005-12-13
I just installed ubuntu two days ago, and I have NEVER used command line. So I don't think you can be more green than me.

That said, I have a question about how to UPDATE a program (namely, Firefox).
I would like to update to 1.5 but I don't know how. I downloaded it from the site but I can't figure out what to do next.

Can anyone help? 

Thanks

---

### Post by tronica on 2005-12-13
yeah its easy,

[http://ubuntuguide.org/#nvidia]("http://ubuntuguide.org/#nvidia")

---

### Post by MichaelM on 2005-12-13
[QUOTE=Paul28]I just installed ubuntu two days ago, and I have NEVER used command line. So I don't think you can be more green than me.

That said, I have a question about how to UPDATE a program (namely, Firefox).
I would like to update to 1.5 but I don't know how. I downloaded it from the site but I can't figure out what to do next.

Can anyone help? 

Thanks[/QUOTE]
If you don't mind starting to use the command line now... :)
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by Paul28 on 2005-12-14
Awesome, Thanks!!

Wow, I think I am going to really enjoy this new community. You guys are
great! I never expected an answer this fast:D

---

### Post by John0 on 2008-02-29
I have been using Ubuntu for a few years quite happily until recently, when I had a need for a program not found in the repositories.

I downloaded two likely programs for testing, but when it came to installing them my Ubuntu world fell down.

With one I was faced with a screen full of icons and folders and a program that was hidden somewhere, the other produced a message telling me I didn't have permission to proceed.

In the past, Linux has been mainly used by professionals and hobbyists, but now it is slowly coming into use by the general public and will need to have versions that do not need special knowledge in order to install them. Ultimately, this must inevitably mean the necessity for the production of an installation process which is possible with minimal user intervention (as in M$ .exe files). I am assuming that the philosophy of the Linux world is to make at least a viable alternative to Micro$oft and Apple?? Or am I wrong?

I for one do not want to learn last-century acronyms to perform a simple installation, and I know for a fact that the general public would be with me on this one. Non-linux-hobbyists often simply don't have the time to learn and research the daunting installation process necessary for non-repository items.

Thanks for reading

---

### Post by Iceni on 2008-02-29
Fortunately most developers provide .debs nowadays. You can run into the odd program you have to compile, but the main reason for this is usually either that it is not yet stable so repositories admins have chosen not to include it yet, and in this case it seems to me like a correct decition for the program developer to not make it easy to install the possibly harmfull software.

- or the program is developed specifically for red hat family, or it is simply not provided as .deb.

Btw, compiling is very very easy as long as you don't run into dependency hell.

Out of curiosity; what program were you looking for?

---

### Post by John0 on 2008-02-29
Perpustakaan Light- Muller and Stein Software
Readerware 
both small library catalog programs, Gnome's Alexandria doesn't have enough features, yet.

---

### Post by Iceni on 2008-03-01
I looked at readerware (non-gtk, ugh) and you don't have to compile it. Just unzip and run the executable.

---

### Post by Joseph5000 on 2008-03-01
I too find it hard it times, I went back to MS and now I am back with Ubuntu. It takes time, but you become more independent over time. I downloaded a few book torrents and there are torrents like: 	 	
VTC Ubuntu Linux || Video TutorialsDownload Torrent: VTC Ubuntu Linux Video Tutorials 
I just uploaded it through Btjunkie and it's a lot of material. You can also youtube and Google video stuff, There are a lot of tutorials. For non-geeks like you and me. Good luck

---

### Post by zvacet on 2008-03-01
[This](http://www.cutlersoftware.com/ubuntuinstall/) can be a start.

---

### Post by frankos44 on 2008-03-01
One of the most impressive thing about debian/ubuntu is it is easy to install applications unlike windows, where you:

. Go to a website
. Find the right package for your PC
. Download it
. Pay up else it runs out in 30 days
. A minimum of 20MB usual 50Mb or more for a small utility
. Enter a ridiculous long code on installation after you receive an email
. Register the program on the internet to activate it    
. Often stops something else from working because it over writes a shared file
. Stops working next time MS issues a service pack
. Download updated version to fix it... yet more cost

On Ubuntu linux:

sudo apt-get install package_name

Need I say more?!

---

