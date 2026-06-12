---
title: "[SOLVED] OK, what do I need to do to be able to youtube?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-30
What does one need to do/install/change in order to be able to watch crap on youtube? I tried to go there a few minutes ago and I needed to install a multimedia codec. Normally I would have just hit yes but what came up was something called "gstreamer" and it only had one star next to it. Is there a better option? should I just hit "install" or what?

Thank you all in advance.

---

### Post by lespaul_rentals on 2007-11-30
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by samuel.rajesh on 2007-11-30
> **lespaul_rentals said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

Use the command line or use Synaptic manager and search for ubuntu-restricted-extras and install.

---

### Post by odinb on 2007-11-30
Hi!

This is what I install to get a good browsing experience::

Firefox (the browser itself)
w32codec (for windowesmedia)
libdvdcss (for DVD)
msttcorefonts (for ms fonts)
flashplugin-nonfree (for flash)
sun-java6-plugin (for Java)
mozilla-mplayer (right click, options, choose x11 for video and ALSA for sound!) (for experinece of in/browser functional player for Quicktime and Relaplayer media also.)

Make sure you uninstall all other mozilla players (like Totem-mozilla), or stuff like quicktime will not work.

---

### Post by boriquajake on 2007-11-30
> **odinb said:**
> Hi!

This is what I install to get a good browsing experience::

Firefox (the browser itself)
w32codec (for windowesmedia)
libdvdcss (for DVD)
msttcorefonts (for ms fonts)
flashplugin-nonfree (for flash)
sun-java6-plugin (for Java)
mozilla-mplayer (right click, options, choose x11 for video and ALSA for sound!) (for experinece of in/browser functional player for Quicktime and Relaplayer media also.)

Make sure you uninstall all other mozilla players (like Totem-mozilla), or stuff like quicktime will not work.


That looks like exactly what I need to do. How do I get all that stuff? Is there some basic CLI (note the lame attempt at the proper use of jargon) promt that I should use before each of those things. Something like "sudo apt get w32codec" for example? I have no idea what I am talking about.

After I installed the restriced extras I went back to youtube and clicked on the first random video from the home page. Anyway, firefox just sort of sat there while the window occasionally dimmed. It was an oddly Windows-like experience. No offense, I could not be happier since making the switch. It was just sort of jarring because I have gotten so used to everything just being easier. Heh heh.

To sum up I have two questions:

1. How do I get all those goodies odinib recommneded

2. Why does Firefox hang and die now when I try to go to youtube since I installed the restricted extras?

Thanks again

---

### Post by odinb on 2007-11-30
You need to have medibuntu installed: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After that you just start the packet manager (adept) and search for the items in my list one by one and request install.

Good luck!

---

### Post by boriquajake on 2007-11-30
> #

With your favourite web browser, go to [WWW] [http://packages.medibuntu.org/pool/](http://packages.medibuntu.org/pool/).
#

Choose the directory labelled as the distribution you are using.
#

Click either free or non-free depending on where the package you want to install is located.
#



If you click on the link specified, it doesn't take you to a place that lets you pick anything to do with your distro. Help me.

---

### Post by odinb on 2007-11-30
What part do you not understand?

Just follow the instruction:

Adding the Repositories

Below are the instructions to add the Medibuntu repository to your system's list of APT repositories.

Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution.

    *

      Ubuntu 6.06 "Dapper Drake":

      sudo wget [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/medibuntu.list

    *

      Ubuntu 6.10 "Edgy Eft":

      sudo wget [http://www.medibuntu.org/sources.list.d/edgy.list](http://www.medibuntu.org/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/medibuntu.list

    *

      Ubuntu 7.04 "Feisty Fawn":

      sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

    *

      Ubuntu 7.10 "Gutsy Gibbon":

      sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

    *

      Then, add the GPG Key:

      wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by SunnyRabbiera on 2007-11-30
its either that or use automatix
its not in the repositories but you can look it up on the net.

---

### Post by boriquajake on 2007-12-03
> What part do you not understand?

Just follow the instruction:




I am sorry for being so obtuse but when I click on the link found in the medibuntu stuff I get this: 

> Index of /pool/
Name	Last Modified	Size	Type
Parent Directory/	 	-  	Directory
free/	2007-Oct-17 20:04:14	-  	Directory
non-free/	2007-Sep-27 15:07:05	-  	Directory
lighttpd/1.4.13

I gather that from there I am supposed to click on the "non-free" option so that is what I do. From there I get to this:

> Index of /pool/non-free/
Name	Last Modified	Size	Type
Parent Directory/	 	-  	Directory
a/	2007-May-28 22:04:27	-  	Directory
g/	2007-May-28 18:55:37	-  	Directory
i/	2007-May-28 17:23:24	-  	Directory
n/	2007-Sep-27 15:07:05	-  	Directory
p/	2007-May-28 19:19:41	-  	Directory
s/	2007-Aug-05 22:35:12	-  	Directory
w/	2007-May-28 22:04:31	-  	Directory
lighttpd/1.4.13

My question is what the heck does this mean? Am I supposed to just know which of these I am supposed to click on? If you read the instructions I posted earlier you will see that they do not match what happens you try to follow them.

That is what I do not understand, smart-***. I don't know what is expected on the other forums but I purposely posted this on the "absolute beginners" forum in order to avoid dicks like you.

---

### Post by dadawan on 2007-12-03
boriquajake,

  Here is a detailed description of exactly what you need to do in order to be able to see video on YouTube and Google Video, and to be able to play DVD's:

[http://www.bornthree.com/HowTo/GutsyEmbelish1/EmbelishingUbuntuGGPart2.html]("http://www.bornthree.com/HowTo/GutsyEmbelish1/EmbelishingUbuntuGGPart2.html")

The tutorial  has screenshots of every step, along with some explanation.   Hopefully it will go smoothly for you.

-Kevin

---

### Post by ruibernardo on 2007-12-03
Just to say that since Gutsy Gibbon you don't need to install flash player or use automatix to install it. 

You just need open Synaptic, enable the universe or multiverse repository, update and install the packages gstreamer0.10-plugins-ugly-multiverse, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ffmpeg. 

Then restart Firefox. Gnash, the opensource flash player that is installed by default in Ubuntu 7.10 Gutsy will do the rest.

---

### Post by lespaul_rentals on 2007-12-05
<snip>

To boriquajake, try typing the following in Terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then, open Synaptic or Add/Remove Programs, and you should be able to access restricted applications.

Also, you mentioned that Firefox seems to be having some issues.  Firefox often crashes when I use it, you might want to try Opera.

---

### Post by boriquajake on 2007-12-10
> **lespaul_rentals said:**
> <snip>

To boriquajake, try typing the following in Terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then, open Synaptic or Add/Remove Programs, and you should be able to access restricted applications.

Also, you mentioned that Firefox seems to be having some issues.  Firefox often crashes when I use it, you might want to try Opera.


Dude, thank you very much. You solved my problem. How did you make it so easy when the "official" medibuntu instructions were so hard?

---

### Post by lespaul_rentals on 2007-12-11
> **boriquajake said:**
> Dude, thank you very much. You solved my problem. How did you make it so easy when the "official" medibuntu instructions were so hard?

Hey, no problem.  I just remember how frusterating it can be for a new user.  ;)

---

