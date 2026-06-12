---
title: "OK Got her up and running--- BUT"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2005-10-27
Hi guys,

I got it up and running and want to try installing some new stuff but I have a few questions:

1). were do you get applications from?
2). what is "synaptic" and were do you get that from? (I read you need that)
3). How do I get my Linux on the internet? I am on XP for that until I get it up and running on the web.

Thanks everyone, you have all been a big help!!!!!

Bill

---

### Post by zugvogel on 2005-10-27
Hi Bill,

Applications are found under Applications > System Tools > Add/Remove Programs. That'll give you a basic list, then for a comprehensive list you can click on "Advanced" (that will take you to this "synaptic" thing).

If you connect to the internet by a cable (ie, not a modem) it should pick the internet up automatically (especially if you're connected to the internet while the computer starts ubuntu).

I'm not sure about the latest version of ubuntu, but on my version (the slightly out of date 5.04 version) you can add additional repositories which will let you download the extra capabilities that let your computer work as it should (eg, dvd / mp3 playing, and other useful bits). Maybe someone else can help you about that. I heard somewhere that these repositories were even automatically included in the latest version of ubuntu so maybe you don't have to do anything beyond clicking somewhere to enable them.

---

### Post by davmac on 2005-10-27
1) Basically you download and install them using synaptic or apt-get - See #2. There are many other ways but this is the most simple. Have a read of [http://ubuntuguide.org/#add-onapplications](http://ubuntuguide.org/#add-onapplications) for details of how to install some of the more common add on apps. The whole guide is worth a scan through - just to make sure you're familiar with what is covered. I've been using Ubuntu over a year now and I still find myself going back to it again and again.

2) Synaptic is a front-end for apt-get the tool for downloading and installing applications. You should already have this installed, System -> Administration -> Synaptic Package Manager. It'll list all of the applications you have installed and all of those that are available that you don't have.

3) Depends on how you connect to the internet; dial up, DSL Modem, Ethernet, etc.  Let us know and I'm sure we'll all do our best to get you connected....

HTH,

Dave Mac

---

### Post by darkmatter on 2005-10-27
[QUOTE=Micro Rotors]Hi guys,

I got it up and running and want to try installing some new stuff but I have a few questions:

1). were do you get applications from?
2). what is "synaptic" and were do you get that from? (I read you need that)
3). How do I get my Linux on the internet? I am on XP for that until I get it up and running on the web.

Thanks everyone, you have all been a big help!!!!!

Bill[/QUOTE]

To answer your first guestion, applications for Ubuntu ar available through Synaptic...the package manager of most Debian based OS's...it lists the programs available in the online repositories...just select the application(s) you want to install and hit apply. You can also install through the command line using the command
```
sudo apt-get install <packagename>
```
and simply replace <packgename> with...uhhh...the package name :)

Question two - Synaptic...You can get it from System -> Administration -> Synaptic Package Manager ;)

And for the third question, what type of internet connection do you use? 
What do you use for a modem? Network card?

---

### Post by jasay on 2005-10-27
[QUOTE=davmac]1) There are many other ways but this is the most simple. Have a read of [http://ubuntuguide.org/#add-onapplications](http://ubuntuguide.org/#add-onapplications) for details of how to install some of the more common add on apps. [/QUOTE]

If you're not online, you can get most of the same info by going to System>Help>Ubuntu 5.10 Starter Guide.  Also be aware that some info on  [www.ubuntuguide.org](www.ubuntuguide.org) has changed (e.g. w32codecs and libdvd are no longer available in the standard repos.)

---

### Post by HJThis on 2005-10-27
Hello,To all

@Micro Rotors

Well being a newbie myself at this one thing i would like to add
if i may is have a good look at this link posted by one of the Pros
here.

[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

i hope i'm right the guy who posted this info is called **Kyral**

it's a great way of doing things.

Best of luck

---

