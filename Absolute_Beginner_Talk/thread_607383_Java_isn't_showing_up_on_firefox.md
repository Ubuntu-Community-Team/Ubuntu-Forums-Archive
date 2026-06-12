---
title: "Java isn't showing up on firefox"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by BakaGaske on 2007-11-08
Hey guys. Just recently installed Ubuntu a week ago. I've been trying to get this live stream of stocks to work, but when i load the page it says: 

"Java is not enabled or Java is not installed on your machine. Please, enable Java in your browser or install Java."

I have the 1.4 plugin for firefox 2.0. When I did a search for Sun Java on the Add/Remove, I don't really know which one to install.:confused:

Anyone got a suggestion in which version of sun java to get? :)

---

### Post by Dr Small on 2007-11-08
Remove whatever Java you installed from Add / Remove,
search for "Java" and install "Sun Java 5.0 Plugin" and "Sun Java 5.0 Runtime".

Try that and see if it helps or not.

Dr Small

---

### Post by BakaGaske on 2007-11-08
i just did what you told me, but it's not workin still. =\. umm, everything is enabled on firefox, could there be another reason? o_O.

Edit: I just remembered, after trying to run the live streaming again, firefox said i needed to install Java Icedtea 7 for it to work, and so I did...but to o anvil did it show up. Still got that msg.

---

### Post by Sef on 2007-11-08
To install Java via Add/Remove (under Applications.)

1) First, change the acceptance pollicy (upper right) to 'All Available Applications.'

2) Then in search, type this:  Sun Java 6

3) Chose the top option: Sun Java 6 web start

4) Click apply twice and java should be installed in Firefox and Ubuntu.

---

### Post by BakaGaske on 2007-11-08
Hmm it's wierd. I"m sure Java is installed. I uninstalled and reinstalled it via add/remove and yet it's still not working. I even tried it through the synaptic package manager and it's not working still. I find it very odd. =(.

---

### Post by mridkash on 2007-11-08
The best way to ensure java is to visit [http://java.com](http://java.com). Click the free download button and on the download page you'll see 'verify now' link. Click it and it'll tell you if java is installed or not.

I faced the same problem with net banking, later found out that the bank made its facility only for windows internet explorer.

Anyways, a better method to install java is to search for restricted extras in add remove. install ubuntu restricted extras and it'll install flash java etc automatically.

---

### Post by BakaGaske on 2007-11-08
yeah, i have the restricted extras as well. haha. oh man. this is horrible. lol. but yeah, i'm trying to access online investing and it's java it also says that it's compatible with firfox 2.0 as well. is there a way to use IE on ubuntu?

---

### Post by strabes on 2007-11-09
Easiest way:```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by rsambuca on 2007-11-09
I'll bet you are using the 64bit version of Ubuntu, right?  If so, there is no sun java plugin.  You either have to use Icedtea java, the old blackdown java, or install the 32bit browser.

---

### Post by BakaGaske on 2007-11-09
> **strabes said:**
> Easiest way:```
sudo aptitude install ubuntu-restricted-extras
```

as much as i would love to say it worked, it didn't :(

---

### Post by trevorsowers on 2007-11-09
this is the exact problem I have.  I have tried all the above as well and LOL still not working!!!

Sigh!

---

### Post by rsambuca on 2007-11-09
BakaGaske & trevorsowers

Open a terminal and enter ```
uname -m
```

Post your output here.

---

### Post by mridkash on 2007-11-09
What does the site java.com say?  [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

Have you tried to verify?

If it says, java is installed, then its ok otherwise firefox will prompt you to install it.

---

### Post by BakaGaske on 2007-11-09
> **rsambuca said:**
> BakaGaske & trevorsowers

Open a terminal and enter ```
uname -m
```

Post your output here.

yeah i am using the 64 bit. but why use 32? i have an amd turion 64. shouldn't i be using the 64bit version of ubuntu? haha. and i did install the icedtea java as well, and it still doesn't work. firfox did prompt me to install it and then restart firefox, but after i did, still didn't work. 

Sigh

---

### Post by trevorsowers on 2007-11-09
I tried the sun site and it says I have the wrong

---

### Post by rsambuca on 2007-11-09
> **BakaGaske said:**
> yeah i am using the 64 bit. but why use 32? i have an amd turion 64. shouldn't i be using the 64bit version of ubuntu? haha. and i did install the icedtea java as well, and it still doesn't work. firfox did prompt me to install it and then restart firefox, but after i did, still didn't work. 

Sigh

Just as I suspected.  If you really need the java webbrowser plugin, then you can keep the 64bit system, you just need to install a 32bit browser.  [Detailed instructions, including a script to do it all for you are here]("http://www.ubuntuforums.org/showthread.php?t=202537").

---

### Post by trevorsowers on 2007-11-09
Java works fine in Kazehakase browser but not firefox or opera!!!

---

### Post by moon2js on 2007-11-09
I'm not getting Java (missing plugin boxes on pages with embedded Java). Did the upgrade to Gutsy break something?

```
$ sudo apt-get -s install ubuntu-restricted-extras sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But I noticed that sun-java6-plugin is not installed. Isn't that what's needed for Java to work in Firefox?

When I go to install sun-java6-plugin, it wants to remove miro. I'd really rather keep miro AND have Java in Firefox.

---

