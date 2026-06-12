---
title: "Flash Player unpacking and installing"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by esteban2x on 2006-04-15
I have the Flash player tar gz file. I'm new and mixed up as to what arguement I use after tar to unpack the program. Any hints?

---

### Post by aysiu on 2006-04-15
Do this.

Go to a terminal:
In Ubuntu: Applications > Accessories > Terminal
In Kubuntu: KMenu > System > Konsole

Type this:
```
cd ~/Desktop
rm install_flash*.tar.gz
```

Then, follow these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

And finally:
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

=================================

Translation:

Throw the .tar.gz in the trash. You don't need it.

Enable extra repositories, because you're going to need them to install a nonfree package (nonfree doesn't mean it costs money--it means it's proprietary).

Use apt-get to not only download but also install Flash.

For more info on apt-get, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by oscar on 2006-04-15
[edit] aysiu beat me [/edit]

---

### Post by mostwanted on 2006-04-15
Flash player can also be installed through Synaptic for easy removal later on. Enable the multiverse repository and install the flashplayer-nonfree package as well as the alsa-oss package (takes care of sounds problems with Flash).

---

### Post by aysiu on 2006-04-15
[QUOTE=mostwanted]Flash player can also be installed through Synaptic for easy removal later on. Enable the multiverse repository and install the flashplayer-nonfree package as well as the alsa-oss package (takes care of sounds problems with Flash).[/QUOTE] Yes. This is the graphical (point-and-click) version of what I just outlined above.

---

### Post by mostwanted on 2006-04-15
[QUOTE=aysiu]Yes. This is the graphical (point-and-click) version of what I just outlined above.[/QUOTE]

Woopz, didn't read your comment carefully enough. Thought you were outlining how to install source packages :)

Sorry.

---

### Post by AndrewCaul on 2006-04-15
[QUOTE=mostwanted]Woopz, didn't read your comment carefully enough. Thought you were outlining how to install source packages :)

Sorry.[/QUOTE]
Nope. aysiu was explaining how to delete it and install it using apt-get. I found it pretty funny. :)

---

