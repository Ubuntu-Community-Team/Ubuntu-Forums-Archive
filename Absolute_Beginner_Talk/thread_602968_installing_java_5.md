---
title: "installing java 5"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by campbuds on 2007-11-04
I need to install java 5 so I can run logmein. But wen I use the add/remove program it says it is not available. how do i get this?

---

### Post by rudeboyskunk on 2007-11-04
Go to System>Administration>Synaptic, and do a search for java.  There should be java 5 and java 6, so just select java 5 and install that (make sure all of your repositories are enabled, by going to System>Administration>Software Sources first).

---

### Post by campbuds on 2007-11-06
I don't see the software sources list.

---

### Post by campbuds on 2007-11-06
I have downloaded the BIN file from Suns website, but how do I install it?

---

### Post by Dr Small on 2007-11-06
Give it executable permissions:
```
chmod +x filename.bin
```

Run it:
```
./filename.bin
```

---

### Post by campbuds on 2007-11-06
no such filename  when i copy and paste what you gave me

---

### Post by Dr Small on 2007-11-06
You must replace "filename" with your "filename" of the .bin file.

---

### Post by campbuds on 2007-11-06
I right clicked and went to properties and permissions and made it executable.

installed it and when i go into firefox it says i still need the java plugin

---

### Post by Dr Small on 2007-11-06
Applications > Add / Remove
Search for "java"
Install the "Sun Java 5.0 Plugin"

Dr Small

---

### Post by campbuds on 2007-11-06
comes up as not available

---

### Post by campbuds on 2007-11-06
I really would liek to get this to work. Apparently in researching on the forums you need Java 5 for logmein to work, java 6 kicks out an error (which I was getting) but I just can't seem to get Java 5 install. I use logmein for work and this is all I need to get working to abandon windows on my laptop.

---

### Post by Maestro23 on 2007-11-06
> **campbuds said:**
> comes up as not available

Enable your sources as posted earlier. Are you running Gnome?

System>>Admin>>Software Sources

Make sure Universe/Multiverse is enabled.

---

### Post by campbuds on 2007-11-06
whoops... didn't know I was on to page 2

---

### Post by Maestro23 on 2007-11-06
> **campbuds said:**
> anything else? I would really like to get logmein working and from what I have read this is all I need. For whatever reason it will not work with Java 6

Open Synatpic search for/install:

> sun-java5-bin

sun-java5-jre

sun-java5-plugin

Get those installed and you should be go to go.

---

### Post by campbuds on 2007-11-06
that's the thing. I don't have "software sources" on my administration menu.

so I would have tried the synaptic package manager but I cannot even get to "software sources" because it isn't on the menu. I tried the synaptic package manager and found just plaqin old java folder on the left but it says nothing about install when i right click and I have even found java 5 but still nothing on the right click about installing.

---

### Post by Maestro23 on 2007-11-06
> **campbuds said:**
> that's the thing. I don't have "software sources" on my administration menu.

so I would have tried the synaptic package manager but I cannot even get to "software sources" because it isn't on the menu. I tried the synaptic package manager and found just plaqin old java folder on the left but it says nothing about install when i right click and I have even found java 5 but still nothing on the right click about installing.

What are you running? Gnome? KDE?

So you have nothing like below (see screenshot).

---

### Post by campbuds on 2007-11-06
> **Maestro23 said:**
> Open Synatpic search for/install:



Get those installed and you should be go to go.

I searched for those things as you said. They came up on the left section with nothing in the right section. No option to install anything.

---

### Post by campbuds on 2007-11-06
I am using vs. 6.06 I think. I don't quite recall.

how would I know it if is gnome, or kde?

---

### Post by g2g591 on 2007-11-06
did you install Kubuntu or Ubuntu, because you're talking about synaptic package manager (which is on Gnome) and not Adept, I assume you're using Ubuntu, also another key way to tell is if you have a "start" (k) button.

---

### Post by campbuds on 2007-11-06
oh... I thought this forum was all ubuntu.

that is what I am using ubuntu

---

### Post by Maestro23 on 2007-11-06
> **campbuds said:**
> oh... I thought this forum was all ubuntu.

that is what I am using ubuntu

So take a look at the screenshot in my earlier post.  If you are using Ubuntu (Gnome) you should have a menu tree like in the screenshot.

---

### Post by philinux on 2007-11-06
I think you need to post exactly which operating system version you have installed and which desktop version your running.

---

### Post by campbuds on 2007-11-06
yes it looks like that (although not that pretty and done up)

It is called "Software Properties" on my menu and I didn't see anything on there about repositories

---

### Post by Maestro23 on 2007-11-06
> **campbuds said:**
> yes it looks like that (although not that pretty and done up)

It is called "Software Properties" on my menu and I didn't see anything on there about repositories

So exactly what version of Ubuntu are you running? (6.06-Dapper, 6.10-Edgy, 7.04-Feisty, 7.10-Gutsy)  Also when you click on "Software Properties" do you see a window like below:

---

### Post by campbuds on 2007-11-06
I am using 6.06 Dapper

---

### Post by Maestro23 on 2007-11-06
> **campbuds said:**
> I am using 6.06 Dapper

Read the following link.  Get your sources enabled and then try and install all the java5 packages I posted earlier.  Post back your results.

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by campbuds on 2007-11-06
It is working! Thanks guys!

---

### Post by Maestro23 on 2007-11-06
> **campbuds said:**
> It is working! Thanks guys!

Good deal.  Please mark this thread SOLVED using the Thread Tools.

Thanks.:)

*Future Reference: When asking for help, post what your system specs are and what Version of Ubuntu you are running in the the very 1st post. It willl help people to help you...

---

### Post by stchman on 2007-11-06
> **campbuds said:**
> I need to install java 5 so I can run logmein. But wen I use the add/remove program it says it is not available. how do i get this?

This will install also the web browser plugin and the SDK.

```
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin
```

---

