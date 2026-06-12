---
title: "Ubuntu Studio?"
date: 2007-05-04
forum: Art &amp; Design
---

### Post by LostArt on 2007-05-04
What's up with the delay for Ubuntu studio on Feisty, Anyone know Anything??? I don't now much about programming but I'd love to help if possible.:) 

Can't wait for the release

---

### Post by Aphorism on 2007-05-04
Join #ubuntustudio on Freenode.net for more information and bleeding edge news.

There have been unforeseen delays.  The folks are working feverishly to get it out the door.

As you can expect, it is a massive undertaking to get it out the door, and it includes a lot of behind-the-scenes infrastructure that also needs to meet the level of quality that _MMA_ desires.


Hope this helps to clear things up.

Sincerely,
TJS

---

### Post by guitarmaniac on 2007-05-05
anyone know where I could get my hands on the ubuntustudio theme? there's a ubuntustudio meta package in the repositories but it doesn't seem to have any artwork in it.

---

### Post by LostArt on 2007-05-05
> **Aphorism said:**
> Join #ubuntustudio on Freenode.net for more information and bleeding edge news.

There have been unforeseen delays.  The folks are working feverishly to get it out the door.

As you can expect, it is a massive undertaking to get it out the door, and it includes a lot of behind-the-scenes infrastructure that also needs to meet the level of quality that _MMA_ desires.


Hope this helps to clear things up.

Sincerely,
TJS

thanks I'll sign up!:popcorn:

---

### Post by arbulus on 2007-05-15
> **guitarmaniac said:**
> anyone know where I could get my hands on the ubuntustudio theme? there's a ubuntustudio meta package in the repositories but it doesn't seem to have any artwork in it.

If you go to Ubuntu Studio's website, on the download page, there is a guide below the download mirror links showing how to add their repos and what commands to apt-get in order to get the themes and artwork.

Here's the link: [http://ubuntustudio.com/downloads](http://ubuntustudio.com/downloads)

The one to install is the ubuntustudio-artwork.  It's a meta-package that has all the artwork, icons, themes, etc.  Once you get the repo added just:

sudo apt-get install ubuntustudio-artwork 

Just a quick note, none of these things work on PowerPC Macs.  I have an iMac dual-booted with Ubuntu, and it wouldn't work.  But it worked just fine on my HP machine.

---

### Post by RubberBinder on 2007-05-15
sorry about the late reply.

I follow the instructions on the Ubuntu Studio website and after typing in the bash line, It says "permission denied" and I can't figure out why.

---

### Post by guitarmaniac on 2007-05-15
> **arbulus said:**
> If you go to Ubuntu Studio's website, on the download page, there is a guide below the download mirror links showing how to add their repos and what commands to apt-get in order to get the themes and artwork.

Here's the link: [http://ubuntustudio.com/downloads](http://ubuntustudio.com/downloads)

The one to install is the ubuntustudio-artwork.  It's a meta-package that has all the artwork, icons, themes, etc.  Once you get the repo added just:

sudo apt-get install ubuntustudio-artwork 

Just a quick note, none of these things work on PowerPC Macs.  I have an iMac dual-booted with Ubuntu, and it wouldn't work.  But it worked just fine on my HP machine.

thanks but I already figured it out :P should have posted back but was too lazy.

---

### Post by arbulus on 2007-05-16
> **RubberBinder said:**
> sorry about the late reply.

I follow the instructions on the Ubuntu Studio website and after typing in the bash line, It says "permission denied" and I can't figure out why.

I think I figured it out.

After you enter:
```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
```

and

```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

Then run

```
sudo apt-get update
```

Then you can apt-get the packages.

The apt-get update is what it leaves off.

---

### Post by RubberBinder on 2007-05-16
I don't think you understand, after entering

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

the terminal gives me a message saying "Permission Denied"

---

### Post by barmazal on 2007-05-16
why can't you type sudo gedit /etc/apt/sources.list and add the line manually if so?

---

### Post by RubberBinder on 2007-05-16
I'm going to make my own thread because I made one, but apparently the title was taken and I just posted here, oh well.

---

### Post by arbulus on 2007-05-17
Try this:

In the terminal:

```
sudo gedit /etc/apt/sources.list
```

and add this line to the end of that file

```
deb http://archive.ubuntustudio.org/ubuntustudio feisty main 
```

save and close then type

```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

