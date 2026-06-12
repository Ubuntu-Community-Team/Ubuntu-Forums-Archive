---
title: "Help - Trouble with Appz"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by Tomosaur on 2006-08-01
Are you talking about games that came preinstalled with Kubuntu, or games you have installed yourself?

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by ewl1217 on 2006-08-01
Did you download these games and install them from the repositories (with Adept, apt-get, or aptitude) or do so manually?

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by Tomosaur on 2006-08-01
Agh, lol you need to install the game. It depends on the type of archive you downloaded. Are they .deb or .tar (or indeed .tar.gz or .tar.bz2)?

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by ewl1217 on 2006-08-01
I suggest that you stick to installing programs with Adept (or any other frontend to apt). Apt is Kubuntu's package management system, which allows you to easily install a lot of software, mostly from online repositories. I don't know about the other games (I'll cheack soon.), but SuperTux is available this way. You may need to enable the universe (commnuity-supported) repositories for this. I'll be able to help a little more after I finish this upgrade I'm doing.

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by ewl1217 on 2006-08-01
No, apt (and therefore Adept) uses .deb files, not .package files. If any of the programs have a .deb package avaliable, that would be the easiest to use.

Could you post the contents of the file "/etc/apt/sources.list" (without the quotes) here? That's basically a listing of the repositories  apt is set to use. If I have that, I can help you to enable the repositories you need to install SuperTux.

**EDIT:** I think I know what the problem is with it not running. You need to make the file executable. You should be able to right-click on it and change the properties. Also, omit the "bash" command. As for installing the programs manually, check if there is any installer or directions provided with the download. I still reccomend apt when you can use it though. I know nothing about autopackage files though; I've always just stuck to apt.

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by Tomosaur on 2006-08-01
Since you have the 5 CD setup, you'll probably have the repositories already on there. I'm not sure how it works when you have the repositories on CD, but you can download .deb packages on windows then transfer them to linux using a USB stick or something. Be careful with writing to different filesystems though, it can occasionally corrupt the file you're trying to write. Your best bet would be to just figure out how to get synaptic to recognise the repositories on your CD. I think you can just add the CDs to your list from within Synaptic. Click Applications > Add/Remove, then check the menus for a way to add repositories.

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by Tomosaur on 2006-08-01
You're having dependency problems. Don't install from the web, just use the CD repositories until you're a bit more linux savvy.

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by ewl1217 on 2006-08-01
Is there any way you can get Internet access on your Kubuntu computer? You can download the files manually, but that's a hassle, considering you'll have to get all the other required packages (the dependencies) manually. I understand if you can't get it online, but it would be the easiest way to do things.

---

### Post by Tomosaur on 2006-08-01
Ah I see now. If there's no way at all that you can get your Kubuntu machine online (which would be by far the easiest way to sort things out), you will be able to use this file to get at least some of the stuff you want. Download the file in windows and burn it as an image to CDs / DVDs, then add your new CD to Kubuntu's repositories.

But still, getting the machine connected to the net is by far the easiest way to do this.

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by Tomosaur on 2006-08-01
Plug the cable into your computer. Hey presto, internets!

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by DavidSkelton on 2006-08-01
?

---

### Post by Tomosaur on 2006-08-01
The short answer is, you need the internet. 

To use install .deb packages, type this:

```

sudo dpkg -i blah.deb

```

To install rpm packages, you'll need to convert them to .deb packages using a program called 'alien', which, you guessed it, you need to download and install.

---

### Post by DavidSkelton on 2006-08-02
?

---

### Post by DavidSkelton on 2006-08-02
?

---

