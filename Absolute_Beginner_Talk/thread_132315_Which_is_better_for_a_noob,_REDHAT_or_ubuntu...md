---
title: "Which is better for a noob, REDHAT or ubuntu.."
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-18
I don't know any of the console commands, but im willing to learn.. In general, which has more ways to do things through graphic windows.. REdhat or ubuntu.. AND: which has more options for configuring hardware graphically?

Aside from that, what does redhat have that ubuntu doesn't and vice versa?

---

### Post by tseliot on 2006-02-18
[QUOTE=systemintheglitch]I don't know any of the console commands, but im willing to learn.. In general, which has more ways to do things through graphic windows.. REdhat or ubuntu.. AND: which has more options for configuring hardware graphically?[/QUOTE]
Fedora is the free version of RedHat (actually they are different projects)

If you want those features you might want to use PCLinuxOS (which is Beautiful and terribly easy to install and to use) or OpenSUSE 10 (which I dislike for the package manager) or SimplyMepis.

I feel that neither Fedora nor Ubuntu suit your needs.

---

### Post by anirban.sam on 2006-02-18
go for ubuntu

---

### Post by systemintheglitch on 2006-02-18
But why? Can you give me some reasons? I would rather support a free software company.. But i do get redhat for free from my University. 

Tell me about the configuration.. I want something to ween me off of graphical editing.. I want to lean commands etc, but not right away.. slowly.:)

---

### Post by tseliot on 2006-02-18
[QUOTE=systemintheglitch]But why? Can you give me some reasons? I would rather support a free software company.. But i do get redhat for free from my University. 

Tell me about the configuration.. I want something to ween me off of graphical editing.. I want to lean commands etc, but not right away.. slowly.:)[/QUOTE]
PCLinux and OpenSuse are free and let you configure your hardware by means of a graphical interface. Of course you can use the command line as well.

In Ubuntu as in Fedora (never tried Red Hat myself) you might have to use the command line for several tasks. It's also true that if you read the guides available on the forums you can do what you need just by copying and pasting commands from those guides.

---

### Post by Jucato on 2006-02-18
If I'm not mistaken, Red Hat is the enterprise version (non-free) while Fedora Core is the free, community-driven version. Again, if I'm not mistaken, the difference between Red Hat and Fedora Core is the kind of support that you get (paid-for versus community-driven).

I've heard that PCLinuxOS and SimplyMEPIS are at the forefront of easy-to-use distros, especially for people coming from Windows, or those who would, for personal reasons, rather not work with CLI (comman line interface) most of the time.

Ubuntu is a happy mix between GUI and CLI. It gives you the power to choose between the two, and either can be equally as powerful. As for the advantages of a CLI? One word: POWER. Using the comman line gives you some options and/or time-saving features that the GUI doesn't have. For example, to install a number of packages, you can either choose packages one by one in the GUI, or copy-paste the commands into the command line. 

If you can't believe that the keyboard can at times give more power than the mouse, just consider this: Aside from a sort of touch-screen interface, most sci-fi films out there still have some type of keyboard. (of course, you can't do graphics with keyboards. :D )

---

### Post by codejunkie on 2006-02-18
[QUOTE=systemintheglitch]But why? Can you give me some reasons? I would rather support a free software company.. But i do get redhat for free from my University. 

Tell me about the configuration.. I want something to ween me off of graphical editing.. I want to lean commands etc, but not right away.. slowly.:)[/QUOTE]

red hats ok if it's free try it and grab a copy of ubuntu and suse you can install all of them on the same computer and try them out. as a personal opinion redhat seems a little bloated for me as does suse but they are both great distros. 
with ubuntu i think the forum and the people on it play a big role in making this distro what it is, if you have a problem all you have to do is search this forum if by chance you cant find the answer post a new thread you'll get an answer 90% of the time. with most of the other distros forums this isn't the case if you can't find it on google then good luck, that's the attitude you get on most of them.

as for your question about the configuration with ubuntu, pretty much anything you wan't to do in ubuntu can be done via gui some times things require entering or copying and pasting commands into a terminal. for instance to configure the xserver, you can enter or copy and paste this into a terminal
```
sudo gedit /etc/X11/xorg.conf
```this opens text file where you setup the options for your graphics card & monitor by hand, if you don't wan't to setup the xserver up by hand you can enter
```
sudo dpkg-reconfigure xserver-xorg
```
in a terminal this will open a gui where you choose you card and montior options basicly in ubuntu you can have things as easy or as hard as you wan't. if you prefer they easy way the most you'd ever have to do is copy a few lines of code into a terminal or a text file, if you want to do it the hard way you can find a way to do that to.

---

### Post by Ghetto_Smurf on 2006-02-18
fedora is good, but not a best choice for desktop computer. fedora is more like a user-friendly server linux. go for ubuntu if you want a complete desktop

---

### Post by taurus on 2006-02-18
It's real hard to say one distro is better than the others.  You just have to play around with each distro for a few days (or even a week) and judge that yourself...  Some people like Ubuntu while others stand behind Fedora Core, SUSE, etc.  So, if you have a fast internet connection which you should since you are to university, download them all and try one at a time.  It doesn't hurt.

---

### Post by nalmeth on 2006-02-18
You can use a user-interface for just about anything now in ubuntu thanks to scripts like automatix, although you will have to use a command line to install that :neutral: 

The thing about ubuntu is debians package management system, which I think is far superior to red hat's rpm system ](*,) And thanks to alien you can install rpm's aswell. All that you would be concerned about to begin with, is that ubuntu uses .deb packages, while fedora, suse, redhat, etc uses .rpm packages. 

The more you learn the command line, the more you will see how useful it is. ubuntuforums is chock full of howto's which make learning the command line very easy, because all you are doing is copy and pasting commands.

If you're using kde, try downloading yakuake. I got mixed results using it in gnome. Eterm is cool for its backgrounds.

to install these in a terminal go:

sudo apt-get install yakuake eterm

to remove packages, go:

sudo apt-get remove whatever

---

### Post by SMF on 2006-02-18
You sound like you know what you want but I can only suggest you take this test.

[http://www.zegeniestudios.net/ldc/index.php](http://www.zegeniestudios.net/ldc/index.php)

It helped me make up my mind or at least form an idea of what would be good for me. Although I have taken the test several times and both times it suggested SUSE and Mandriva as top choices for me, I went with Ubuntu which was also listed in the results of my test.

:)

---

### Post by theturner on 2006-02-18
Ubuntu releases are more up to date than Red Hat (not Fedora). Since development is always progressing, I'd recommend Ubuntu.

---

