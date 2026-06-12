---
title: "Amarok Newbie Question"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by agregal on 2006-03-30
I'm so new to this whole Ubuntu/Linux area that I really don't have any knowledge at all.  I wanted to know how do I go about installing Amarok?  It's not on my system by default (I don't even know if it should be).

I keep reading about these 'respositories' what are they and how do they work?

I'm using a Dell laptop with dual booting to windows xp and ubuntu and my laptop DOESN'T have an internet connection.  Is that something that is pretty much required?  I use my Mac mini for web surfing, email, etc with a dsl connection.:confused:

---

### Post by localzuk on 2006-03-30
Take a look at [https://wiki.ubuntu.com/SoftwareManagement](https://wiki.ubuntu.com/SoftwareManagement) - it contains all you should need to know about installing software. As you want to use amarok, it is likely that you want to play MP3's also - so take a look at: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for information about this.

---

### Post by mishranurag on 2006-03-30
As far as I know, UBUNTU is heavily internet dependant, and you need to have an internet connection for seamless installation of any program not provided by default. The best you can do is visit [http://amarok.kde.org/](http://amarok.kde.org/) and download the files to install amarok and then transfer the files to your laptop and install it according to instructions provided on this website.

If you can get internet connection, you just type in the terminal 
sudo apt-get install amarok
and it will be done.

Best
Anurag

---

### Post by localzuk on 2006-03-30
Further to this, you can visit [http://packages.ubuntu.com](http://packages.ubuntu.com) and download the files required for amarok there and install them by typing
```
sudo dpkg -i files.deb to.deb install.deb
```

In either situation, you will probably require many different files as dependencies. The easiest thing to do, IMO would be to set up a home LAN and internet enable your laptop - this would be much less time consuming anyway :)

---

### Post by nalmeth on 2006-03-30
I think people are making this sound more complicated than it is.
Are you using KDE or GNOME for desktop?
GNOME has toolbar on top and on bottom, KDE has toolbar on bottom.
Odds are if you just installed Ubuntu 5.10 you have gnome.
Amarok will work in gnome, but it might be better to install a native music player. And yes you will need to install the non-free codecs for your non-free formats.
Automatix is the best way to do this:
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

Listen is my favorite music player for gnome, though I think Amarok is still better. Just a little fat, and lyrics don't work as well as in listen.
[http://listengnome.free.fr/](http://listengnome.free.fr/)

to install amarok from the command line, just type:
sudo apt-get install amarok

I've made this much less complicated haven't I?

---

### Post by pbaehr on 2006-03-30
> I've made this much less complicated haven't I?

Except that they don't have an internet connection on their Ubuntu box.

They'll need to install from a CD.

---

### Post by agregal on 2006-03-30
What is the best way to go about sharing my dsl internet connection on my mac mini with my dell laptop?  I have never set up a network before, what are the basic steps involved?  How much would it cost to do?

---

### Post by nalmeth on 2006-03-30
I was being sarcastic..
I didn't know there was no net either.. Oops

---

### Post by halitech on 2006-03-30
[QUOTE=agregal]What is the best way to go about sharing my dsl internet connection on my mac mini with my dell laptop?  I have never set up a network before, what are the basic steps involved?  How much would it cost to do?[/QUOTE]


with not knowing where you are it makes it hard to say a price but if you are in North America, you should be able to pick up a router for 25-50. just install it between the computers and the dsl modem. Now depending on if you use PPPoE to connect, you may need to configure the router to do that for you.

---

