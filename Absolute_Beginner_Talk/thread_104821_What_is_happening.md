---
title: "What is happening ??"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by JnMrno on 2005-12-16
hi
Im running 5.04, and suddenly the device manager doesn't want to start up and other programs like bittorrent and banshee Music Player and in the synaptic when I click on the repositories option nothing happens,, 
WHAT is that ???
oh, and when I click on their icons they start loading but they just stop and don't open
what can I do ??

---

### Post by paulmilliken on 2005-12-16
[QUOTE=JnMrno]hi
Im running 5.04, and suddenly the device manager doesn't want to start up and other programs like bittorrent and banshee Music Player and in the synaptic when I click on the repositories option nothing happens,, 
WHAT is that ???
oh, and when I click on their icons they start loading but they just stop and don't open
what can I do ??[/QUOTE]

Hi JnMrno,

Do you still have this problem after rebooting the computer?  The reason that I ask is that, perhaps, one program is using a lot of the system's resources.

Paul

---

### Post by JnMrno on 2005-12-16
yes , it has been for days !
i just found another ===> the update icon that shows when updates available, i click on the show updates option, type password, but nothing happens !

---

### Post by kairu0 on 2005-12-16
Open up a terminal and try launching some of these programs by name.

Let's see if you can get an error message that way.

---

### Post by JnMrno on 2005-12-16
[QUOTE=kairu0]Open up a terminal and try launching some of these programs by name.

Let's see if you can get an error message that way.[/QUOTE]

I tryed to open the bittorrent :

** ERROR **: PyGTK (2, 6, 2) required, but (2, 6, 1) found.
aborting...
Aborted

---

### Post by bored2k on 2005-12-16
Did you happen to play with your UBuntu installation prior to these errors?

---

### Post by JnMrno on 2005-12-17
[QUOTE=bored2k]Did you happen to play with your UBuntu installation prior to these errors?[/QUOTE]
Are you asking if i've been installing stuff? if that, the answer is yes, i've been installing a lot since I started Ubuntu several days ago, codecs, java, several other programs:???:

---

### Post by bored2k on 2005-12-17
[QUOTE=JnMrno]Are you asking if i've been installing stuff? if that, the answer is yes, i've been installing a lot since I started Ubuntu several days ago, codecs, java, several other programs:???:[/QUOTE]
No no. Installing stuff doesn't break anything (for the most part). By playing I mean, well, **playing**, with *sudo* powers on.

---

### Post by paulmilliken on 2005-12-17
[QUOTE=JnMrno]I tryed to open the bittorrent :

** ERROR **: PyGTK (2, 6, 2) required, but (2, 6, 1) found.
aborting...
Aborted[/QUOTE]

Hi JnMrno,

This means that you need the stated version of PyGTK to run bittorrent.  PyGTK is a wrapper for the GTK+ library for use in Python (a popular scripting language).  The PyGTK website is [http://www.pygtk.org/](http://www.pygtk.org/).

1.  A couple of questions: did you install bittorrent from source with --nodeps or similar?
2.  If you installed using synaptic, are you using the correct repositories for your version of Ubuntu?

Paul

---

### Post by JnMrno on 2005-12-17
[QUOTE=bored2k] By playing I mean, well, **playing**, with *sudo* powers on.[/QUOTE]
Yes, i have

---

### Post by JnMrno on 2005-12-17
[QUOTE=paulmilliken]
1.  A couple of questions: did you install bittorrent from source with --nodeps or similar?
Paul[/QUOTE]
no, i'm using GnomeBittorrent, the one that comes with the UBUNTU
[QUOTE=paulmilliken]
2.  If you installed using synaptic, are you using the correct repositories for your version of Ubuntu?
Paul[/QUOTE]
that i don't know, I just read i needed to install more repositories, and when to do it via Synaptic, but the repositories "thing" doesnt want to open.

---

### Post by paulmilliken on 2005-12-17
> that i don't know, I just read i needed to install more repositories, and when to do it via Synaptic, but the repositories "thing" doesnt want to open.

You can check which repositories you are using by looking at the file /etc/apt/sources.list.  The new version of Ubuntu (5.10) is called Breezy and the repositories have "breezy" somewhere in the name.  From memory, 5.4 is called Warty.  Edit: Sorry, I checked, 5.4 is called Hoary.

Paul

---

### Post by JnMrno on 2005-12-17
ok, i'm trying to download de pygtk, i'll see if i can install it.
but, back in the repositories subject, what is the thing happening to my synaptic and the repositories thing I said early ?

---

### Post by paulmilliken on 2005-12-17
[QUOTE=JnMrno]ok, i'm trying to download de pygtk, i'll see if i can install it.
but, back in the repositories subject, why is it that i need them (I know that's basic but i'm a newbie)??, and what is the thing happening to my synaptic and the repositories thing I said early ?[/QUOTE]
The repositories are the locations where synaptic package manager and other package management tools will "look" for software packages that you can install or upgrade.  These repositories are designed to make it easy to install and upgrade software but providing a front-end to the apt-get tool.  One of the main advantages of these tools is that dependencies are automatically installed for you (unlike when you compile from source-code).

It sounds like your system has some problems due to some of the software that you installed.  If you have too much more difficulty with it you may want to consider backing up your /home/username directory and doing a fresh install?

Paul

---

### Post by JnMrno on 2005-12-17
i downloaded the pygtk-2.8.2.tar.gz, I did the "tar zxvf" command, then, the ./configure, but when I did the "make":
make: *** No targets specified and no makefile found.  Stop.

how can I install it then ???

---

### Post by paulmilliken on 2005-12-17
[QUOTE=JnMrno]i downloaded the pygtk-2.8.2.tar.gz, I did the "tar zxvf" command, then, the ./configure, but when I did the "make":
make: *** No targets specified and no makefile found.  Stop.

how can I install it then ???[/QUOTE]
What was the output of ./configure?

---

### Post by JnMrno on 2005-12-17
[QUOTE=paulmilliken]What was the output of ./configure?[/QUOTE]
This are the final lines:
  
  checking for headers required to compile python extensions... not found
  configure: error: could not find Python headers

or you want to see the entire content ??

---

### Post by paulmilliken on 2005-12-17
[QUOTE=JnMrno]This are the final lines:
  
  checking for headers required to compile python extensions... not found
  configure: error: could not find Python headers

or you want to see the entire content ??[/QUOTE]

No need for the entire content at this stage.

You have an unmet dependency.  This means you need to install the python headers before you can upgrade PyGTK.  This could get messy as there may be numerous dependencies that you will need to sort out.  At this stage, I recommend going to system>administration>synaptic package manager - then click on "search".  Type in pygtk and you'll get a list of packages.  The ones that are marked in green are already installed.  The synaptic package manager will install all the dependencies for you which will save you a lot of time.

Installing a large package from source can take a while to sort out dependencies so I recommend using a package manager where possible.

Paul

---

### Post by JnMrno on 2005-12-17
ok,
there is no one named pygtk in Synaptic, but there are some named like python-gtk-1.2, python-gtk-dev, among others, are they the same that pygtk???

---

### Post by paulmilliken on 2005-12-17
[QUOTE=JnMrno]ok,
there is no one named pygtk in Synaptic, but there are some named like python-gtk-1.2, python-gtk-dev, among others, are they the same that pygtk???[/QUOTE]
They are different packages but related.  If you click once on the name of the package, you will get a description.  Also, they probably depend on each other.  So, in Synaptic, if you insall one, some of the others may be installed anyway :)

I have to step out for a while now.  Hope that helped.

If you can't get the problems resolved then you should consider a fresh install.

Regards,

Paul

---

### Post by JnMrno on 2005-12-17
Hey, thank you very much man !!

---

