---
title: "guide to properly compiling source code"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Jakykong on 2005-12-16
Hi!
well i posted [URL="http://www.ubuntuforums.org/showthread.php?t=104647"this thread[/URL] about an hour and fifteen minutes ago, in the hopes of solving my problem.
since then, the thread has become burried on page 2 of the forum ... a sure sign that my question isn't going to be answered.
So instead of being rude, i figured, new thread, simpler question. 

I am trying to install programs. A lot of the programs i used to use on knoppix don't seem to come with kubuntu, and apt-get doesen't seem to have them available (i tried adding sources ... lots of sources).
Since some of the programs come only in RPM format uncompiled, i was wondering if anyone could show me a tutorial on compiling .tar.gz source files and how to install the compiled executables?
Thanks so much, again!

---

### Post by Evil Whisper on 2005-12-16
if you have the RPM's you could try alien to install them.
Alien converts rpm's to debs so you would use it like this.

```

sudo apt-get install alien

```

```

sudo alien the-name-of-your.rpm 

```

```

sudo dpkg -i the-name-of-your-rpm.deb

```

Edit:
I'm not the greatest at compiling things so I removed the bit of how
to compile because It kinda works for me but I think it would be best
for somone else to tell you how to do that.

---

### Post by Emerzen on 2005-12-16
I'm not sure if it's exactly the same in Kubuntu, but here's how in Ubuntu:

1st -> Install via Synaptic: 'build-essential' & 'checkinstall'

2nd -> download your tarball to the desktop

3rd -> right-click on it, and "extract all" here

4th -> open terminal and 'cd' into the folder

5th -> type -> "./configure" (without the quotes)

6th -> type -> "make"

7th -> type -> "sudo checkinstall"

If all goes well open Synaptic and you should be able to manipulate the program from there.  If errors pop up look for missing dependencies in the messages.  90% of the time this is the problem-> also, install the "dev" versions of any packages too if it complains about a package you already have.  Good luck.

---

### Post by Emerzen on 2005-12-16
Some other common problems:

It complains that their is no "configure" file -> skip the ./configure part and start w/ make.

During checkinstall it tells you that it couldn't install the package, try removing anything but alphanumeric characters from the description it asks for.

---

### Post by Jakykong on 2005-12-16
[QUOTE=Emerzen]I'm not sure if it's exactly the same in Kubuntu, but here's how in Ubuntu:

1st -> Install via Synaptic: 'build-essential' & 'checkinstall'

2nd -> download your tarball to the desktop

3rd -> right-click on it, and "extract all" here

4th -> open terminal and 'cd' into the folder

5th -> type -> "./configure" (without the quotes)

6th -> type -> "make"

7th -> type -> "sudo checkinstall"

If all goes well open Synaptic and you should be able to manipulate the program from there.  If errors pop up look for missing dependencies in the messages.  90% of the time this is the problem-> also, install the "dev" versions of any packages too if it complains about a package you already have.  Good luck.[/QUOTE]


uhhh ... problem with step 1: Adept is what comes with Kubuntu ... and it has build-essential, but no checkinstall ... ./configure works on the tarball ok, but make never seems to work ...  obviousely i can't do step number 7 due to the problem at step number one ... any ideas?

---

### Post by Jakykong on 2005-12-16
[QUOTE=Evil Whisper]if you have the RPM's you could try alien to install them.
Alien converts rpm's to debs so you would use it like this.

```

sudo apt-get install alien

```

```

sudo alien the-name-of-your.rpm 

```

```

sudo dpkg -i the-name-of-your-rpm.deb

```

Edit:
I'm not the greatest at compiling things so I removed the bit of how
to compile because It kinda works for me but I think it would be best
for somone else to tell you how to do that.[/QUOTE]

i tried alien :-( didn't work ... never suceeded at making my rpm into a .deb ... and gave me wayyy too many error messages that i could barely understand

---

### Post by Jakykong on 2005-12-16
is it possible some of these problems sprung up because i'm using an AMD64 chip ... seems to have its own section on the forum ... which tells me its a little bit "special" :-)  

Again, thanks so much for whatever help you can provide ... i'd be completely lost without you all!

---

### Post by Emerzen on 2005-12-19
Use Adept to install Synaptic, then try installing checkinstall.  It's very possible that AMD64 is the cause of your troubles, but I don't have work w/ 64bit yet so I couldn't tell you anything useful.

---

