---
title: "Unsure how to install either Amarok or Compiz?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2007-11-02
Hi,

I am a little confused on how to use Synaptic & installing applications.  I want to try both Amarok as well as play with Compiz.  

I am assuming if i try & dont like it, i can uninstall the same way with no ill effects?  

I was looking through the catalog & searched for Compiz.  It came up with 27 different packages.  Do I install all of them?  

Amarok has 15 packages listed, again, do I grab them all? 

Help a newb!  

Thanks,
Rich

---

### Post by por100pre1 on 2007-11-02
If using **Gutsy** copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo aptitude install amarok compizconfig-settings-manager
```

This will install all packages needed, they could be many depending of your Ubuntu installation.

**Are you using Feisty or previous release?**

---

### Post by LinuxD on 2007-11-02
Yeah! a chance for me to help out a fellow new guy :)

Unlike the Add/remove program, synaptics seem to list all individual components whether or not they are programs themselves(at least from what I understand). When you try to install amarok and it shows you a bunch of other packages, these are other components which will be needed to run it, so they should be installed as well. 
If you decide that you don't end up liking it, just mark Amarok for _complete_ removal in synaptics and it should get rid of the dependant packages that came with it.

hope this helps!

---

### Post by RichTJ99 on 2007-11-02
Sorry for the confusion.  I am using Gutsy (7.10).  

As far as the code:

sudo aptitude install amarok compizconfig-settings-manager

Does this install Amarok in a stand alone format & also installs Compiz in a stand along format, or are these two now dependant on each other?  

If I had a third program (say Thunderbird as an example only), could I just add the code:

sudo aptitude install amarok thunderbird compizconfig-settings-manager  ?  

I know you can use Compiz & Amarok together but I thought they were also stand alone.

Thanks,
RIch

---

### Post by por100pre1 on 2007-11-02
> **RichTJ99 said:**
> Sorry for the confusion.  I am using Gutsy (7.10).  

As far as the code:

sudo aptitude install amarok compizconfig-settings-manager

Does this install Amarok in a stand alone format & also installs Compiz in a stand along format, or are these two now dependant on each other?  

If I had a third program (say Thunderbird as an example only), could I just add the code:

sudo aptitude install amarok thunderbird compizconfig-settings-manager  ?  

I know you can use Compiz & Amarok together but I thought they were also stand alone.

Thanks,
RIch

That command will install both programs but they won't depend on each other. You'll find compiz in **Appereance** and in **Advanced Desktop Effects Settings** under **System> Preferences**.

> **LinuxD said:**
> Yeah! a chance for me to help out a fellow new guy :)

Unlike the Add/remove program, synaptics seem to list all individual components whether or not they are programs themselves(at least from what I understand). When you try to install amarok and it shows you a bunch of other packages, these are other components which will be needed to run it, so they should be installed as well. 
If you decide that you don't end up liking it, just mark Amarok for _complete_ removal in synaptics and it should get rid of the dependant packages that came with it.

hope this helps!

**[COLOR="RoyalBlue"]Very well, LinuxD! Welcome to the forums![/COLOR]** :)

---

### Post by RichTJ99 on 2007-11-02
Hi,

Thanks, I was able to install both.  I cant figure how to make that desktop cube show up (the option is checked within the advanced section).  

Thanks,
Rich

---

### Post by jpietari on 2007-11-02
1. Enable Desktop Cube in Advanced Settings for CompizConfig
2. Shortcut --> ctrl + alt + [arrow]

The shortcut can also be changed

---

### Post by defrex on 2007-11-02
Compiz is installed by default in Gutsy (what you installed was the settings manager). Also, if you want to remove amarok later, you can use the command *sudo apt-get remove amarok*.

---

### Post by alwiap on 2007-11-02
the following link:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

will show you how to set up all the bells and whistles of compiz, enjoy

---

### Post by RichTJ99 on 2007-11-02
Im not sure why its not displaying a cube (the cube is enabled).

On a side note, how do you know how to install things using the command line? 

I saw a game called Tremulous, do I just use:

> sudo aptitude install tremulous 

---

### Post by Maestro23 on 2007-11-02
> **RichTJ99 said:**
> Im not sure why its not displaying a cube (the cube is enabled).

On a side note, how do you know how to install things using the command line? 

I saw a game called Tremulous, do I just use:

Programs for outside sources can come in many ways.  You have a .tgz, .deb., .bin, .rpm, etc...
apt-get and aptitude install programs from the Ubuntu Repositories.

The following 2 links discuss installing software in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (Other good info)

---

