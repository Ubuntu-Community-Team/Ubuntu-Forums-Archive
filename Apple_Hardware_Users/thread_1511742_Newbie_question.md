---
title: "Newbie question"
date: 2010-06-17
forum: Apple Hardware Users
---

### Post by EMTChristian on 2010-06-17
Hello my name is Christian and I am an extreme newbie.

Back story first

About 2 months ago I started having issues with snow leopard.  Basically my graphics were fine for 2 weeks when I installed, then my screens went black.  After a lot of talking with apple and trouble shooting I bought a new Ati Radeon HD 4870 with a Dvi port and a mini port for monitors.

Using the leopard boot disk (10.5.1) I was able to get one screen working but not the mini port. Every time I tried to update anything system software related my screen would go dark again and hibernate.  Basic frustration I am sure you can image.  A friend of mine suggested I try this operating system.

So I am, my old card was a Geforce 7300 GT I believe, after I installed this software, I tried putting that in for giggles and I got mirror desktops, I poked around a bit on the web and forums and updated from the synaptic updater in admin.  After I updated my screens went black again.  Fun.  I put the Ati Radeon back in and went back to my old configuration and currently using a single screen again.  I would really like to have both monitors back.  Of course I would like to be able to use programs like WOW and Second life as well.

So I guess the question is.  Is there a walk through available or can somebody hold my hand and help me get both monitors running as well as some other programs?

Oh I also got Wine in, but I'll be fried if I can get it to work yet.

Thanks for reading my book.

- Christian

---

### Post by linuxopjemac on 2010-06-17
It looks like the current nVidia driver you are using gives the dual head problem, just like in OSX? Is that the right conclusion ?

I know that for nVidia there is this command to configure:
```
nvidia-xconfig
```

for the ATI catalyst driver there is this equivalent (ATI catalyst control center):
```
sudo amdcccle
```

---

### Post by EMTChristian on 2010-06-17
I tried both the nvidia-config and got 
WARNING: Unable to locate/open X configuration file.


ERROR: Unable to write to directory '/etc/X11'.


The Sudo amdcccle got   Command not found.

- Christian

---

### Post by linuxopjemac on 2010-06-17
What kind of card are you using now?

The first is a problem of permissions I think, try:
sudo nvidia-xconfig

The second, you don't have the ATI catalyst driver installed.

---

### Post by EMTChristian on 2010-06-17
Right now I have the Pro Mac version ATI Radeon HD 4870

Now I've downloaded the ATI Catalyst Center file twice, but I can't seem to find the command to install it.  I will take a look for the ATI catalyst driver.  

- Christian

---

### Post by linuxopjemac on 2010-06-17
```
sudo apt-get fglrx-amdcccle
```

---

### Post by linuxopjemac on 2010-06-17
if you feel like doing it yourself:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by EMTChristian on 2010-06-17
> **linuxopjemac said:**
> ```
sudo apt-get fglrx-amdcccle
```

Invalid operation fglrx-amdcccle

Seems like I keep downloading the same driver file also

ati-driver-installer-10-6-x86.x86_64.run

-Christian.

---

### Post by linuxopjemac on 2010-06-17
sorry, my bad:

sudo apt-get install fglrx-amdcccle

---

### Post by linuxopjemac on 2010-06-17
with that file you downloaded I presume you have to do the following:

```
sudo sh ./ati-driver-installer-10-6-x86.x86_64.run --buildpkg Ubuntu/lucid
```

(this is for Lucid Lynx, check this)

---

### Post by EMTChristian on 2010-06-17
sudo apt-get install fglrx-amdcccle  This worked fine.  It installed.

The next line I copied and pasted to the terminal window  and the reply was that it couldn't open
./ati-driver-installer......run

By the way I appreciate you putting up with my barrage of questions.  I really am lost and trying to figure this out.  If you could point out good places online to read I would appreciate that as well.

Thank  you again

- Christian.

---

### Post by linuxopjemac on 2010-06-18
now you can use the control center:
```
sudo amdcccle
```

---

### Post by EMTChristian on 2010-06-18
Indeed I can.

Now to see if I can find a way to get the mini port on my ATI Radeon HD 4870 card to display.  There is a ton of stuff to absorb on this OS.

- Christian.

---

