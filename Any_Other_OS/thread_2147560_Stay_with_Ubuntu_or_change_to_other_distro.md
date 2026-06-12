---
title: "Stay with Ubuntu or change to other distro?"
date: 2013-05-22
forum: Any Other OS
---

### Post by NapkinMan on 2013-05-22
Hello! 
A month ago I finally decided to install Ubuntu on my personal and only laptop. I didn't want to make a radical change to Linux yet as I used Windows all my life so I dual botted Ubuntu 13.04 (12.10 did not detect my wireless card) with Windows 7. I really enjoyed and am currently enjoying the experience of Linux but as I kept on trying differente distros on my virtual machine I started noticing the several diferences in them. I've tried (apart from Ubuntu) Mint 14, OpenSuse 12.3, Fedora 18 and Backtrack 5r3. After that, and please forgive me if i'm wrong, Unity just seemed very "juvenile" when compared to the other ones i tried. I use my laptop mainly for rather casual online gaming, programming as i've started learning some languages, some school work, multimedia (music making, photo editing, movies,music) and was also planning to set a server at my parents' home when I go there in vacation. Also i considered the change because I don't like the tabled feeling unity has and, don't ask me why, I don't feel confortable changing the "retail" GUI. With the new intel 965 graphic drivers I also got to run many games on Ubuntu like Urban Terror and even World of Warcraft through Wine and I'm feeling more and more distant from Windows as time goes by. My main question is: Taking all the activities I enjoy most in consideration, should I keep Ubuntu or change to Fedora/OpenSuse? Also, please forgive me if I posted in the wrong forum section. It is my first thread.

---

### Post by ibjsb4 on 2013-05-22
Welcome to the forums NapkinMan :)

Don't like Unity, just add a different desktop to it.  I like the Classic desktop, but there are several others to choose from.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install gnome-session-fallback
```

And choose your desktop at boot (login) by clicking on the login icon.

---

### Post by NapkinMan on 2013-05-22
Thanks a lot for the quick reply. I already sucessfuly installed cinnamon although the one i liked the most was the KDE of Opensuse 12.3. Regarding my other question, do you think Ubuntu is right for the things I do on my laptop or do you think there's a more appropriate distro?

---

### Post by ibjsb4 on 2013-05-22
What you want to do is pretty much standard on all distros.  Nothing wrong with KDE, but i think Ubuntu (that includes kde) offers the greatest amount of software.

---

### Post by NapkinMan on 2013-05-22
Thanks again. I'm already looking foward to keeping Ubuntu. Don't fix what's not broken right?. I'll just wait for a few more opinions :)

---

### Post by zombifier25 on 2013-05-22
I would say that unless you have very specific needs, Ubuntu is the best distro for doing... everyday stuffs. It has tons of softwares (including some like Steam for gaming), well supported by the community (most of the Linux guides you find on the Internet will be mainly for Ubuntu). Don't like Unity? There are other DEs you can try, like KDE.

---

### Post by NapkinMan on 2013-05-22
Thank you for the reply. The friend who convinced me to try Linux, although not explaining me why, said it was best to keep the GUI that came with my instalation. Although Ubuntu seems to be a little more slow than the other 3 I tried via Virtual machine and LiveUsb, everything seems to be working perfectly and I'm afraid of messing that up since everyone I know has run into some serious problems when installing linux for the 1st time.

---

### Post by addegsson on 2013-05-22
Try Kubuntu, it's a good alternative if you like Kde more than Unity.

---

### Post by NapkinMan on 2013-05-22
Thanks I'll download it and try it in my virtual machine :)

---

### Post by mips on 2013-05-22
Well there's also Kubuntu, Xubuntu and Ubuntu Gnome (does it have a name yet?).

---

### Post by NapkinMan on 2013-05-22
I've been playing with the Compiz configurations and with some forum searching narrowed the [COLOR=#333333]sluggishness problem to the cinnamon menu only. The menu, when clicked takes 2-3 seconds which does not seem normal, i also feel come lag when scrolling through the menu items.[/COLOR]

---

### Post by lykwydchykyn on 2013-05-22
What are the specs on your laptop?

---

### Post by NapkinMan on 2013-05-22
It's a HP G7000 Notebook
Intel Core2Duo 1.83 GHz
3GB RAM
Intel GM965 (x3100)

---

### Post by Elfy on 2013-05-22
> **mips said:**
> Well there's also Kubuntu, Xubuntu and Ubuntu Gnome (does it have a name yet?).
Ubuntu GNOME is the name as far as I can see

> Why aren’t you named Gubuntu?

    Gubuntu would sound too much like Goobuntu, Google’s internal distribution of Ubuntu. The GNOME Foundation Board did not want us to use a derivative of GNOME like GNOMEbuntu as our name. Anyway, we think the name Ubuntu GNOME is a good example of the simple usability we offer.


[http://ubuntugnome.org/faq/](http://ubuntugnome.org/faq/)

---

### Post by monkeybrain2012 on 2013-05-22
Ubuntu can do everything you need. There is a misconception that Ubuntu  is only for beginers, the "only" part is wrong. It is easy and polished enough for  beginers but you can also do all the advanced stuffs if you desire, as  it is Debian underneath. I haven't done backtrack and OpenSuse, but I am  triple booting with Fedora and Debian. I find that often some libraries  may be missing in Fedora and if you need to compile from source but you  can always find them in Ubuntu/Debian. Also some third party software  is built only for Ubuntu (hence works in Debian) but not Fedora/redhat,  to get them to work you need to compile them but as I said, sometimes  you may be missing some dependencies and have to hunt them down. So  overall there is no big difference, but I would give Ubuntu the edge.

(There are more hardcore distros like gentoo and slackware where you can only do things the hard way, but I have never used them. :))

---

### Post by NapkinMan on 2013-05-22
Thanks a lot monkeybrain. I was aware of Ubuntu not being only for begginers. I was needing help towards the features of each one. Ubuntu real seems to have everything. Had I partitioned well my hard drive I could triple bot with Opensuse (which is the one i was leaning towards to). Guess I just got demotivated due to the slowness my Ubuntu has been suffering from. I used Opensuse through LiveUsb and I could really tell the difference in the smoothness. YaST was also a pretty cool tool.

---

### Post by binaryhermit on 2013-05-22
> **NapkinMan said:**
> although the one i liked the most was the KDE of Opensuse 12.3. 
If you want KDE, you can just open a terminal and run ```
sudo apt-get install kubuntu-desktop
```

---

### Post by Buntu Bunny on 2013-05-22
> **NapkinMan said:**
> ... please forgive me if i'm wrong, Ubuntu just seemed very "juvenile" when compared to the other ones i tried...

I'd be curious as to what you mean by juvenile. I take you're referring to Unity(?). If you like Gnome classic, try Xubuntu.

---

### Post by Lemuriano on 2013-05-22
Beside a particular desktop environment like Kde, Xfce, gnome ect. I suggest you try distros with different package managers. In my case after testing apt-get and pacman I came across entropy/equo in Sabayon and realize that it was the one for me. I believed that in order to get the most out of your system, any gnu/linux user should familiarize with the package manager that your distribution use.    

Regards

---

### Post by NapkinMan on 2013-05-23
> **Buntu Bunny said:**
> I'd be curious as to what you mean by juvenile. I take you're referring to Unity(?). If you like Gnome classic, try Xubuntu.
Yup, thanks for pointing that out. I'll correct it right away.

---

### Post by NapkinMan on 2013-05-23
> **Lemuriano said:**
> Beside a particular desktop environment like Kde, Xfce, gnome ect. I suggest you try distros with different package managers. In my case after testing apt-get and pacman I came across entropy/equo in Sabayon and realize that it was the one for me. I believed that in order to get the most out of your system, any gnu/linux user should familiarize with the package manager that your distribution use.    

Regards

Correct me if I'm wrong but Fedora and OpenSuse both have different package managers, yum and zypper. Plus, I really liked YaST in Osuse.

---

### Post by Lemuriano on 2013-05-23
> **NapkinMan said:**
> Correct me if I'm wrong but Fedora and OpenSuse both have different package managers, yum and zypper. Plus, I really liked YaST in Osuse.
[URL="http://en.wikipedia.org/wiki/Comparison_of_Linux_Live_CDs#Package_management_and_installation"]
http://en.wikipedia.org/wiki/Comparison_of_Linux_Live_CDs#Package_management_and_installation[/URL] Indeed, here you would find different distros and the package managers they use. 

Since Sabayon allow me to use two package managers entropy and portage, my next project will be to learn the portage dance. :)

---

### Post by NapkinMan on 2013-05-24
To update you guys with my current situation. I've divided my ubuntu  partition in two, ending up with 80gb of Windows7, 35gb for Ubuntu and  another 35 for another OS to test. I've installed opensuse 12.3 on the  empty partition and am currently testing it. Everything seems to be  working fine after the updates. I also tried Fedora 18 KDE and it makes  all the difference. I'll keep testing it on vmware and if I eventually  get bored with osuse ill go with fedora for my third partition. I've  decided to: keep Windows7 until i am 100% confortable with linux, keep  ubuntu to have a stable and "main" linux distro. Thank you for all the  support.

---

