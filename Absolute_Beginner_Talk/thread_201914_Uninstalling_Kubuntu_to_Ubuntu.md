---
title: "Uninstalling Kubuntu to Ubuntu"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by JanVH on 2006-06-22
I run Dapper. Just to check it out I installed the Kubuntu-desktop with

$sudo apt-get install kubuntu-desktop

Because I don't like KDE very much, I'd like to remove it, so I followed the orders at [here]("http://psychocats.net/ubuntu/puregnome.php")...

It's fine now, all the KDE-related stuff is almost gone. Only when I'm booting I get the Kubuntu-background instead of the Ubuntu-background. When the login-screen pops up it's the gnome-Ubuntu one...

Anyone has a clue how to solve this?

---

### Post by bruce89 on 2006-06-22
```
sudo update-alternatives --config usplash-artwork.so
```
Sorry, nicked from below.  I forgot what the command was.

---

### Post by uzi09 on 2006-06-22
this seems to be a problem with both apt-get and aptitude and with both KDE and XFCE desktops.

the only way i got mines to go away was after an update. unfortunately, i haven't come across a clear cut way of getting it back to normal.

i think the best way to see the different environments is to just use live cds. everytime i've tried downloading a desktop, it ruins my settings some how :S

---

### Post by user1397 on 2006-06-22
[quote=JanVH]I run Dapper. Just to check it out I installed the Kubuntu-desktop with

$sudo apt-get install kubuntu-desktop

Because I don't like KDE very much, I'd like to remove it, so I followed the orders at [here]("http://psychocats.net/ubuntu/puregnome.php")...

It's fine now, all the KDE-related stuff is almost gone. Only when I'm booting I get the Kubuntu-background instead of the Ubuntu-background. When the login-screen pops up it's the gnome-Ubuntu one...

Anyone has a clue how to solve this?[/quote]i had the **exact** same problem, and here's howto fix it: paste this in a terminal: ```
 sudo update-alternatives --configure usplash-artwork.so
```


Choose usplash-default.so for the brown Ubuntu splash.

Then, paste this in a terminal: ```
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by user1397 on 2006-06-22
[quote=uzi09]i think the best way to see the different environments is to just use live cds. everytime i've tried downloading a desktop, it ruins my settings some how :S[/quote]i couldn't agree with you more!

---

### Post by uzi09 on 2006-06-22
[QUOTE=erik1397]i had the **exact** same problem, and here's howto fix it: paste this in a terminal: ```
 sudo update-alternatives --configure usplash-artwork.so
```


Choose usplash-default.so for the brown Ubuntu splash.

Then, paste this in a terminal: ```
sudo dpkg-reconfigure linux-image-`uname -r`
```[/QUOTE]


hmm, guess there is a clear-cut answer :D

thanks!

---

### Post by bruce89 on 2006-06-22
[QUOTE=erik1397]```
 sudo update-alternatives --configure usplash-artwork.so
```[/QUOTE]
I tried that, and found it didn't work - this does though
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by JanVH on 2006-06-22
Thx for the quick help...

I got the following message when running update-alternatives...

```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.
```

---

### Post by user1397 on 2006-06-22
[quote=bruce89]I tried that, and found it didn't work - this does though
```
sudo update-alternatives --config usplash-artwork.so
```[/quote] yes, thats right, my bad.:-k
[quote=JanVH]Thx for the quick help...

I got the following message when running update-alternatives...

```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.
```[/quote]this means that there is no other usplash available, only the default ubuntu brown one.  just try the second part and then post back .

---

### Post by JanVH on 2006-06-22
Yes it works!

Thx alot, two thumbs up!

---

### Post by user1397 on 2006-06-22
[quote=JanVH]Yes it works!

Thx alot, two thumbs up![/quote]no prob!

---

