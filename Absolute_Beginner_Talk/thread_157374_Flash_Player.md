---
title: "Flash Player?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-09
Where can I get Macromedia Flash Player for Firefox on Linux Ubuntu Breezy?

---

### Post by aysiu on 2006-04-09
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree flashplayer-mozilla
``` The terminal to enter commands is Applications > Accessories > Terminal in Gnome and KMenu > System > Konsole in KDE.

For more info, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by dylonium on 2006-04-09
can you explain that in easier words? I am just styarting with Ubuntu so I'm really nooby.

---

### Post by aysiu on 2006-04-09
[QUOTE=dylonium]can you explain that in easier words? I am just styarting with Ubuntu so I'm really nooby.[/QUOTE] The easier words are here:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

That explains the different ways of installing software in Ubuntu and a bit about how the repositories system works.

While you can do this whole thing (enabling extra repositories, installing Flash) through point-and-click using Synaptic Package Manager (in System > Administration), it's easier for me to give you terminal commands because I can just type them out, and you can copy and paste them to the terminal.

apt-get is a way to install software
Synaptic Package Manager is a point-and-click version of apt-get
Adept is the Kubuntu version of Synaptic, but I highly recommend using Synaptic instead of Adept.

If you want to see Synaptic in action, go here:
[http://www.psychocats.net/essays/winuxinstall](http://www.psychocats.net/essays/winuxinstall)

The *apt-get* commands I gave you earlier are just the easiest way for me to do what's outlined in that Synaptic tutorial.

---

### Post by _simon_ on 2006-04-09
Just a note - remember there is currently no flash player 8 for linux. At some point Macromedia will be releasing Flash Player 8.5 for Linux but I don't know when.

You'll find a fair few sites now requiring version 8... unfortunately you won't be able to view the flash content on those. :(

---

### Post by Bloch on 2006-04-09
If you go to the macromedia site [www.macromedia.com](www.macromedia.com) it will detect you do not have flash installed and give you a download. You have to run the downloaded program (a shell script) from the command-line. Ubuntu is made to be easy, but you will still have to invest some effort in learning the basic commands of the commandline (also called the bash shell, or simply the terminal)

---

### Post by aysiu on 2006-04-09
[QUOTE=Bloch]If you go to the macromedia site [www.macromedia.com](www.macromedia.com) it will detect you do not have flash installed and give you a download. You have to run the downloaded program (a shell script) from the command-line.[/quote] I don't see why you would do that when you can install it through apt-get or Synaptic > Ubuntu is made to be easy, but you will still have to invest some effort in learning the basic commands of the commandline (also called the bash shell, or simply the terminal) While I agree that one should invest effort in learning the command-line, this particular task can be accomplished fully, using Synaptic Package Manager.

---

### Post by dylonium on 2006-04-09
Thanks, I'll try this out- but if it doesn't work Ill post back! Thanks again!

---

### Post by aysiu on 2006-04-09
[QUOTE=dylonium]Thanks, I'll try this out- but if it doesn't work Ill post back! Thanks again![/QUOTE] Don't hesitate to ask more questions. And if you have errors, copy and paste them here.

---

