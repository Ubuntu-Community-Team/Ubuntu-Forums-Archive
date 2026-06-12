---
title: "Help w/ Linux/Ubuntu"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by markgreene on 2005-08-06
Ok so I love how smooth linux runs on the machines I put it on, especially ubuntu b/c so far it has been the ONLY one to recognize ALL of my hardware without any problems including the centrino wireless on my dell laptop. 

I WANT to stay with linux but it is hard when I cant figure out how to install ANYTHING LOL. Example: I downloaded Skype in a .deb package. I google how to install the .deb package and a site told me to use the terminal (I used Root Terminal) to run dpkg -i PACKAGE_FILE_NAME. So I run it and it says something along the lines of "Configuring skype ...." and then puts me back at the bash prompt. The problem is now when I select Skype from the menu it dosn't run!

What is it I am doing wrong?

The other thing is what is my root password? How can I test to see if it is one of the ones I types in on setup?

Thanks in advance.

---

### Post by johannes on 2005-08-06
Here is a nice guide that might help get you started: [http://ubuntuguide.org/](http://ubuntuguide.org/) It includes installing Skype.

An easy way of intstalling nearly every program you want is to use the Synaptic application. Click the upper panel: System/Administration/Synaptic Pacage Manager.

Your root password is the one you entered during the installation of Ubuntu, the one you use to login.

---

### Post by poofyhairguy on 2005-08-06
How to install programs? The answer is synaptic:

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

---

### Post by markgreene on 2005-08-06
poofyhairguy - I have run that program out of administration menu but it didnt have skype or limewire listed in it. Someone in IRC  mention universal/multiversal - what is that?

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=markgreene]poofyhairguy - I have run that program out of administration menu but it didnt have skype or limewire listed in it. Someone in IRC  mention universal/multiversal - what is that?[/QUOTE]

Well....thanks for asking an easy question. Make my job easier.

Universe:

[https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29](https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29)

How to get it (follow these directions):

First do this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then this:

[http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache](http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache)

Way easier than it looks. Copy and paste.

Then install Java:

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

Then install Limewire:

[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

Then install Skype:

[http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)

Be sure to read the notes at the top of the guide! You don't have to know whats going on....just copy and paste and it will work.

Its a little pain in the ass.....but once you are set up, you are set up.

---

### Post by markgreene on 2005-08-06
Wow thanks a ton for all that man. I just got in from the movies w/ my g/f so I will look go through all the steps tmwo. 

Hey should it worry me that it says the universe packages are for advanced users only? Stuff like that has never intimidated me but w/linux I just wanted to make sure that it shouldnt.

Thanks again!

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=markgreene]
Hey should it worry me that it says the universe packages are for advanced users only? [/QUOTE]

Basically that means "If you cant figure out how to get into the universe, you shouldn't"

If you could follow the guide you are advanced enough (some people can't or won't).

---

### Post by markgreene on 2005-08-07
I have skype and limewire up and running. My mic on skype is VERY soft but I think I know how to fix that. I would like to know what all I was doing when I was copy and pasting though.

---

### Post by poofyhairguy on 2005-08-07
[QUOTE=markgreene]I would like to know what all I was doing when I was copy and pasting though.[/QUOTE]

Sure. You were:

1. Telling Ubuntu where to get its software from (more than the default).

(the copy and paste teh sources.list thing)

2. Telling Ubuntu that you told it where to get new software.

(sudo apt-get update)

3. Installing the software you need.

(sudo apt-get install software)

---

### Post by varunus on 2005-08-07
You can do everything that you just did from a console in Synaptic too; you can go to synaptic's repositories dialog to add new places to find software.  You can refresh your package lists (apt-get update) in Synaptic by clicking refresh.  You can also install software by clicking it and choosing "mark for install" and then clicking apply (apt-get install).

To change your mic volume, double click on the volume icon on your GNOME top panel.  It will bring up a volume control thing similar to what happens when you dbl-click windows' sound icon.

---

