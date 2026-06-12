---
title: "New Release! New Questions:-)"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Scubastev013 on 2007-10-14
Hey everyone,

I have been using 7.04 basically as a hobby system to learn more about linux and open source computing.  I'm really by no means a proficient user, and admit that I'm really a n00b :-)  Anyways, with the upcoming release of 7.10 (and since its a LTS), I'd like to make Ubuntu more of a primary desktop.  I'm running a Dell E1505 Inspiron. 

Here are my questions:

1. I have a Intel(R) Wireless WiFi Link 4965AGN wireless card.  I'd like to make that work, all previous efforts with a bunch of sets of isntruction found on the internet didn't work for me.  What is the best way to approach this situation?

2.  I have a Logitech MX 3200 keyboard and a MX 600 Mouse which basically work fine for me.  My only gripe is not being able to use the back/forward buttons or the center wheel scroller in Firefox and other applications.  (I feel like my dad when he goes and hits the back button everytime isntead of using the mouse:-))

3. Where is a good site where I can learn to install other types of files?  The .deb files isntall themselves, but the other formats I can't seem to do.  I need a very beginner friendly tutorial that can help me out!

Thanks in advance for any help you guys give me.  I really appreciate it!

~Scuba

---

### Post by jimrz on 2007-10-14
> **Scubastev013 said:**
> Hey everyone,

I have been using 7.04 basically as a hobby system to learn more about linux and open source computing.  I'm really by no means a proficient user, and admit that I'm really a n00b :-)  Anyways, with the upcoming release of 7.10 (and since its a LTS), I'd like to make Ubuntu more of a primary desktop.  I'm running a Dell E1505 Inspiron. 

Here are my questions:

1. I have a Intel(R) Wireless WiFi Link 4965AGN wireless card.  I'd like to make that work, all previous efforts with a bunch of sets of isntruction found on the internet didn't work for me.  What is the best way to approach this situation?

2.  I have a Logitech MX 3200 keyboard and a MX 600 Mouse which basically work fine for me.  My only gripe is not being able to use the back/forward buttons or the center wheel scroller in Firefox and other applications.  (I feel like my dad when he goes and hits the back button everytime isntead of using the mouse:-))

3. Where is a good site where I can learn to install other types of files?  The .deb files isntall themselves, but the other formats I can't seem to do.  I need a very beginner friendly tutorial that can help me out!

Thanks in advance for any help you guys give me.  I really appreciate it!

~Scuba

1.  First thing = d/l the "live"cd for 7.10, pop it in and see how it reacts with your card.

2.  You wil need to edit xorg.conf to get your extra buttons working. I have a different mouse but same issue is easily fixed. Search these forums for "MX 600" and I'm sure you will find someone has posted the appropriate values.

3.  "Search" is your friend. There are numerous HowTo's here on the forums for installing about anything. Also, take a look [**[COLOR="Sienna"]here[/COLOR]**]("http://psychocats.net/ubuntu/index.php") for a site, run by one of the forum mods, that has lots of good ubuntu info.

---

### Post by ThrobbingBrain66 on 2007-10-14
> **Scubastev013 said:**
> Hey everyone,

I have been using 7.04 basically as a hobby system to learn more about linux and open source computing.  I'm really by no means a proficient user, and admit that I'm really a n00b :-)  Anyways, with the upcoming release of 7.10 (and since its a LTS), I'd like to make Ubuntu more of a primary desktop.  I'm running a Dell E1505 Inspiron.

7.10 is *not* an LTS, 8.04 will be.

---

### Post by jayaramk on 2007-10-14
installing files in ubuntu.....


it u downloaded the source code available in the .tar.gz or any such kind as zipped files u first need it extract it.... and then open the terminal......
1. firstly u need to configure the downloaded files.. so type
                        ./configure
2. if there are no errors and to find whether alll the dependencies are found then type
                          make
3.u now need to install by typing the command
                   make install
   and thats it ur downloaded source code is successfully installed....

 a little bit of house keeping... removing backup files type....... clean install in the terminal..... thats it and its done!!!!!!


the process is same for any type of linux

---

### Post by Frak on 2007-10-14
> **Scubastev013 said:**
> 

1. I have a Intel(R) Wireless WiFi Link 4965AGN wireless card.  I'd like to make that work, all previous efforts with a bunch of sets of isntruction found on the internet didn't work for me.  What is the best way to approach this situation?
Try the Live CD and see if it works.

> 2.  I have a Logitech MX 3200 keyboard and a MX 600 Mouse which basically work fine for me.  My only gripe is not being able to use the back/forward buttons or the center wheel scroller in Firefox and other applications.  (I feel like my dad when he goes and hits the back button everytime isntead of using the mouse:-))

Goto Firefox and type about:config in the URL bar then search for "middlemouse.scrollbarPosition" (without quotes) and make sure it is set to true.

> 3. Where is a good site where I can learn to install other types of files?  The .deb files isntall themselves, but the other formats I can't seem to do.  I need a very beginner friendly tutorial that can help me out!

Thanks in advance for any help you guys give me.  I really appreciate it!

~Scuba
[GetDeb.net]("http://getdeb.net") is a great place for .deb's, and I seriously suggest you stick with .deb's. RPM's are not reliable to install on Debian based systems, and .tar.gz/bz2 (source) is a pain-in-the-*** to install, remove, and maintain.

Hope that helps :guitar:

---

### Post by Palmyra on 2007-10-14
First, please separate all your issues into different threads with appropriate titles.

Second, we can only help you with your wireless card if you provide the name of the chipset.  The chipset is the manufacturer's name, not the name the wireless card is sold under.  Do a Google search to find your card's chipset.

Third,  I don't know enough about mice to help you.

Fourth,  see the following page on how to install anything in Ubuntu:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

