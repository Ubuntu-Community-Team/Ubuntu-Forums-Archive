---
title: "How do I install New Software?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by TopFan on 2008-03-07
I want to install Google Earth on my Ubuntu 7.10 Dell Inspirion, but can't work out how to.

If I go to GE's home page, I can download the GoogleEarthLinux.bin file to my desktop, but what do I do with this file to get GE working?

I'm used to the Mac way of doing things where the application icon is just dragged and dropped into the Applications folder. Seems like the ideal and simplist way of installing software. What is the equivilent method on Ubuntu?

---

### Post by Fixman on 2008-03-07
right click->properties->permissions->allow executing this file as a program

---

### Post by SOULRiDER on 2008-03-07
> **Fixman said:**
> right click->properties->permissions->allow executing this file as a program

Dont do that, theres a better way. Theres repos with GE that you can install easily from. Allow me a couple of minutes to post how.

---

### Post by steveneddy on 2008-03-07
Google Earth is in the repos.

Go to

System --> Administration --> Synaptic Package Manager

Look for googleearth

install googleearth and googleearth-data

It will install it for you automatically.

Enjoy.

---

### Post by steveneddy on 2008-03-07
> **Fixman said:**
> right click->properties->permissions->allow executing this file as a program

This is totally incorrect.

---

### Post by SOULRiDER on 2008-03-07
Basically it goes like this. Open a terminal and do:

```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -

```

Then press alt +f2 and type
```
gksu gedit /etc/apt/sources.list
```
and add
```
deb http://dl.google.com/linux/deb/ stable non-free 
```
at the end.

Finally, run
```
sudo aptitude update
```
Now youre ready to install Google Earth.

You can also follow these steps with pictures at: [http://www.google.com/linuxrepositories/ubuntu704.html](http://www.google.com/linuxrepositories/ubuntu704.html)

From [http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

---

### Post by SOULRiDER on 2008-03-07
> **steveneddy said:**
> Google Earth is in the repos.

Go to

System --> Administration --> Synaptic Package Manager

Look for googleearth

install googleearth and googleearth-data

It will install it for you automatically.

Enjoy.

I had no idea it was there, i thought the google repos had to be added :)

---

### Post by steveneddy on 2008-03-07
You can do it both ways.

Getting it from the repos is easy and it will update when it is time to update.

The version from the repos is stable on Ubuntu systems.

I use the repo's version & it works great.

EDIT:

In my personal experience, my system is more stable and reliable if I choose to run most of my software
from the repositories sources.

I need daily dependability and reliability on my laptop and choose not to install
software that is outside of the repos unless it is totally necessary.

I have the want, but not the need for the latest and greatest available.

I also run the Nvidia graphics drivers from the repos.

This just keeps my system stable and working. I can't afford a crash at a critical moment.

---

### Post by Duck2006 on 2008-03-07
> **steveneddy said:**
> Google Earth is in the repos.

Go to

System --> Administration --> Synaptic Package Manager

Look for googleearth

install googleearth and googleearth-data

It will install it for you automatically.

Enjoy.

This is the best way to install, but if you want to install the *.bin file, from the terminal.
Open the terminal, and cd to the place where you have the file and type,

sh GoogleEarthLinux.bin

and it should install for you.

---

### Post by vishzilla on 2008-03-07
Medibuntu has Google Earth in it's repo. Check [here]("https://help.ubuntu.com/community/Medibuntu")

> Add the repo
Update/Reload
sudo apt-get install googleearth

---

### Post by TopFan on 2008-03-07
Thanks for your contributions everyone. FixMan's method worked first time.

I tried looking for GE via the Synaptic Packet Manager thingy, but couldn't find it. Probably me being a muppet.

I'm afraid the Terminal is out of bounds for me - no desire to do anything more complex than drag'n'drop etc.

---

### Post by oldos2er on 2008-03-07
> **TopFan said:**
> Thanks for your contributions everyone. FixMan's method worked first time.

I tried looking for GE via the Synaptic Packet Manager thingy, but couldn't find it. Probably me being a muppet.

I'm afraid the Terminal is out of bounds for me - no desire to do anything more complex than drag'n'drop etc.

 Like vishzilla said, you need to add the Medibuntu repository to your software sources.

 By not learning or using the terminal, you're denying yourself a straightforward, powerful way to have ultimate control over your system. I find the terminal to be less complex than a lot of graphic interfaces. Just my opinion.

---

### Post by TopFan on 2008-03-08
Hi Ann,

I appreciate that I'm not getting the most out of Ubuntu by not using the terminal, but I've used Mac for 20 years, had great fun and done everything I needed to do without using the terminal.

I'm not a techy - I need a simple, reliable and GUI OS with no exceptions. I don't need total control of my system - just enough to do what I want to do without needing any code etc.

I'm rapidly warming to Ubuntu. For folks like me it's definitely a work in progress, but fun to be a part of.

Enjoy the Terminal!

All the best,

TopFan

---

### Post by luvit on 2008-03-15
> **TopFan said:**
> I want to install Google Earth on my Ubuntu 7.10 Dell Inspirion, but can't work out how to.

If I go to GE's home page, I can download the GoogleEarthLinux.bin file to my desktop, but what do I do with this file to get GE working?

I'm used to the Mac way of doing things where the application icon is just dragged and dropped into the Applications folder. Seems like the ideal and simplist way of installing software. What is the equivilent method on Ubuntu?
I just installed Google Earth with ease in just a few steps.
Please [see my blog ]("http://www.yay4u.com/2008/03/install-google-earth.html")for simple intructions that worked for me.
I also have so very many more easy application install instructions in the blog ;)

---

