---
title: "java and firefox - HOW?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by alloftheabove on 2008-01-28
I'm getting really frustrated with trying to set up java so I can go play on Runescape on this computer.  I have ubuntu 7.10 installed.  Can someone work through getting the latest version of java setup with me?  I've tried manually installing it, which didn't work.  I got rid of the gcjwebplugin packages that were installed, but that didn't work.  I'm confused, and I need help.

EDIT:  Forgot to mention, when I setup the latest version of sun java manually, and looked at the link that was made from mozilla/plugins to the java plugin, it says it's broken.  When I setup the link, the command line told me that the file existed.

---

### Post by taurus on 2008-01-28
What happens when you run these commands from a termnal?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by alloftheabove on 2008-01-28
with sudo apt-get update:
```

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]  
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_CA
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_CA
Ign http://archive.ubuntu.com gutsy/universe Translation-en_CA
Ign http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Fetched 1B in 0s (1B/s)  
Reading package lists... Done

```

with sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And java -version:
```

java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea Client VM (build 1.7.0-b21, mixed mode, sharing)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Fetched 1B in 0s (1B/s)  
Reading package lists... Done

```
EDIT: when I go to runescape.com and get to the page where you play the game(it's made in java) it acts as though I don't have java installed

---

### Post by taurus on 2008-01-28
Does java plugin even show up on the list in firefox when you run this command from an address field of firefox?

```
about:plugins
```
I see that you are using IceTea java instead of Sun java.

---

### Post by alloftheabove on 2008-01-28
No, it doesnt.  Java definitely doesn't appear on ```
 about:plugins.
```
I'm just really confused right now.

---

### Post by taurus on 2008-01-28
Can you post the output of this command?

```
sudo update-alternatives --config java
```

---

### Post by alloftheabove on 2008-01-28
```

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
          3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/lib/jvm/java-6-sun/jre/bin/java
*+      5    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

---

### Post by taurus on 2008-01-28
What if you pick number 4 as your default java.  Then, restart firefox again.  Does firefox work with other sites that require java plugin?

---

### Post by alloftheabove on 2008-01-28
still acts as though I don't have java.  Same thing for sun java's verify page.  Don't know any other sites that use java, or I can't remember.

---

### Post by alloftheabove on 2008-01-28
BUMP

By the way, what's the easiest way to get a windows xp or vista simulator on ubuntu?

---

### Post by alloftheabove on 2008-01-28
bump

---

### Post by alloftheabove on 2008-01-28
Bump Again

---

### Post by billgoldberg on 2008-01-28
Ok, first remove java using synaptic. (completely remove it)

The way I installed java on this gutsy install is by using this program:

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

It should work if you use that program.

It should also work if you install sun java 6 using synaptic. (search for "sun" in synaptic).

About the xp simulation?

well wine and cedega run some windows apps.

I have xp running in virtualbox (in repositories), it was pretty easy to do.

---

### Post by alloftheabove on 2008-01-28
nope, I did what you said and java still doesn't work in my firefox browser.

EDIT:  Say, would I be able to run Microsoft Visual C++ 2008 express on virtualbox?

---

### Post by alloftheabove on 2008-01-28
bump

---

### Post by alloftheabove on 2008-01-28
bump again

---

### Post by alloftheabove on 2008-01-28
bump ala carte

---

### Post by alloftheabove on 2008-01-28
bump again!  Is there no one who can solve my problem?

---

### Post by alloftheabove on 2008-01-28
bump!

---

### Post by alloftheabove on 2008-01-28
bump!  Is anyone gonna finish helping me???

---

### Post by alloftheabove on 2008-01-28
I'm getting tired of bumping!

---

### Post by billgoldberg on 2008-01-28
mmm.

So the sun-java package didn't work nor did quickstart?

Strange.

Beats me.

Someone else will help, give them some time to reply.

---

### Post by YoG%*@ on 2008-01-28
hi,

can you check if you have the libjavaplugin.so in your firefox plugin directory  (usually something like /usr/lib/firefox/plugins) and where it points to (issue 'ls -l' in that directory?
does it point to your java6 runtime?

hth,
mux

EDIT:
oh, and bumping a thread every five minutes or so might be considered very impolite - as the poster before me said - give the people some time and i'm sure someone will be able to help you ;)

---

### Post by alloftheabove on 2008-01-28
Ok, I'll do some checking.

And thank you very much, I am semi new to forums in general, then again I've never actually bumped before.  I was just annoyed.

---

### Post by alloftheabove on 2008-01-28
Well, I looked, and there's one link to gcj (which I already uninstalled) and a link to sun java on my desktop.  I created this last link when I was trying to set it up the sun java way.  When I checked the plugins folder after installing sun java to my desktop, it said it was a broken link.  Both links were broken, and are broken.  I need to get rid of them.  The last time I tried doing the sun java way I created a folder called java (EDIT: into /usr/lib) and did the extracting of files there.  I also just found where I think quick start put the files it setup when I had it install java6.

---

### Post by YoG%*@ on 2008-01-28
> **alloftheabove said:**
> Well, I looked, and there's one link to gcj (which I already uninstalled) and a link to sun java on my desktop.  I created this last link when I was trying to set it up the sun java way.  When I checked the plugins folder after installing sun java to my desktop, it said it was a broken link.  Both links were broken, and are broken.  I need to get rid of them.  The last time I tried doing the sun java way I created a folder called java (EDIT: into /usr/lib) and did the extracting of files there.  I also just found where I think quick start put the files it setup when I had it install java6.


you can remove the links by unlinking them: 
```
unlink <linkname>
```

then try to uninstalling/reinstalling java6 (especially the sun-java6-plugin) as already suggested some posts above. restart firefox and see if it works. if it doesn't, you may have to create the symbolic link yourself.

---

### Post by alloftheabove on 2008-01-28
Exactly what do I link to?:confused:

---

### Post by YoG%*@ on 2008-01-28
> **alloftheabove said:**
> Exactly what do I link to?:confused:


mine links to

libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

which itself links to 

/etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so


does that help? you might try locating the 'libjavaplugin_oji.so' first and then create a symbolic link to that.

---

### Post by erfahren on 2008-01-28
see: [http://ubuntuforums.org/showthread.php?t=648117](http://ubuntuforums.org/showthread.php?t=648117) (particularly post #10)
also: [http://ubuntuforums.org/showthread.php?t=652574](http://ubuntuforums.org/showthread.php?t=652574)

(this thread went from one to three pages in the time it took me to find the links in my bookmarks!)

---

