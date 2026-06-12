---
title: "Synaptic Package Manager"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Ulysses on 2006-02-12
Okay.
Tried my level best to make it work and nothing wants to agree with me and it makes me feel kind of stoopid because the directions seem so damned straightforward
system/administration/synaptic package manager
Now, the wiki tells me that I am supposed to go into
settings/repositories
And then from that menu I'm supposed to click for the packages I want
And if I want the 'universide' option to click the package, then click 'edit' then type in 'universe' in the sections dialog box
Pretty simple, right?
It's picture 002 that I've attached here (though my confidence is low ; I'm not so sure I can pull that off anymore...)
[ATTACH]6087[/ATTACH]
I thought maybe the path was wrong BUT I DID NOT CHANGE IT. I left it alone. All I did was delete what was in the sections dialogue box and type in universe
Now, I clicked and chose everything but the CD option (the stated path was the CD driver and I've already installed that so I thought it redundant and unclicked it)
Bear in mind, I am more new than new with this so be patient with me please and type slowly when explaining things to me. Seriously.
So, when I've clicked and I chose to update everything the system rushes through then stalls like this.... (picture 004)
[ATTACH]6088[/ATTACH]
It will stall like this for fifteen minutes or more before telling me that it cannot update.
When it does resume, I get two pages of error messages:
Pictures 005 & 006
[ATTACH]6089[/ATTACH]

[ATTACH]6090[/ATTACH]

Please someone tell me what the heck it is I'm doing wrong
And, while we're playing the lets-help-the-newbie game, can someone point me in the right direction to aid me in my learnin skills?

---

### Post by orlox on 2006-02-12
why dont you just remove the repositories that don't work, and add them with the "add" option in settings->repositories. There you can choose three repositories and check inmediately for the universe and the multiverse options...I did it this way and it works perfectly....

---

### Post by Perfect Storm on 2006-02-12
Better to do it via command line in my opinion:

close synaptic open the terminal

```
 sudo gedit /etc/apt/sources.list
```

Now remove the **#** from the lines except where there's two of them (##).

also add

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

optional:

[b]## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
[/b]


```

sudo apt-get update
```

Now open synaptic or use apt-get in the terminal.

---

### Post by Ulysses on 2006-02-12
Hello

Woo-hoo...Looks like it works. I would have replied and got to you sooner but I had to step out for a little bit.
I followed the terminal directions and it seems to be okay. It's still going through the updates as we speak. I executed the update using the sudo commands, too.

This is what I am currently seeing in the terminal window. Hasn't changed for 4 minutes or so.
99% [Connecting to ca.archive.ubuntu.com (206.75.218.52)]deb [http://people.ubunt](http://people.ubunt) 99% [Waiting for headers]

I'm confident and feeling better...

Do I have to post again for you to direct me towards some tools I can use to learn myself some things about ubuntu? Because I need to be cured of my 'darn it, I'm pointing and clicking, why's it not working' disease.

Thank you, thank you, thank you again....

RAR

---

### Post by Perfect Storm on 2006-02-12
To learn more about apt-get:

```
apt-get --help
```
and
```
man apt-get
```

Use 'man' is a very good way to get information of an application.

eg.
```
man epiphany-browser
```

---

### Post by Ulysses on 2006-02-12
Morning

Thanks for the tip
Though the terminal is still locked at...

99% [Connecting to ca.archive.ubuntu.com (206.75.218.52)]
99% [Waiting for headers]

...at this very minute

And, it also failed at...

Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg
  Connection failed [IP: 206.75.218.53 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg
  Connection failed [IP: 206.75.218.53 80]

But my internet connection was up and running. The IP just not available, I guess?

Thanks...Again....

RAR

---

### Post by Perfect Storm on 2006-02-12
The server is properly down or very busy. Try change 'ca' with another country code.

---

### Post by Ulysses on 2006-02-12
Hello

OK, so long as you are here and offerring excellent online support, I'll make use of it and wait for you to tell me to go and fly a kite....

How do I stop it? It keeps on going back to try and re-connect. How do I interrupt it?

And, if you tell me to fly a kite, you'll have to direct me to a site - I've never flown a kite before

RAR

---

### Post by Perfect Storm on 2006-02-12
usually I just close the terminal.

---

