---
title: "What JAVA package/s should I install and how?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-29
I know these things change with time (different versions etc etc)

So, forgive me for asking a question that's been asked in the past.

Running ubuntu 7.1 Gutsy.

What's the best (compatible / stable) JAVA package / packages I should install on my system so that web base java AND desktop java programs run at their best.

There seem to be a few options, and don't want to make the mistake of installing a version that's not the best.

Thanks in advance.

:)

---

### Post by Teber on 2008-02-29
i installed java webstart 6. seems to be working ok

---

### Post by .nedberg on 2008-02-29
If you install "ubuntu-restricted-extras" you will be good! It provides the latest Java from Sun in addition to some other things (flash among others)

---

### Post by lswest on 2008-02-29
generally the sun-java6 packages are good (it's what i use with eclipse (we need it for CS:P usually i code my stuff in like text editor)) and for web-based apps and everything i use that stuff.  No problems with it so far.

---

### Post by PiggiePaul on 2008-02-29
Many thanks for the 3 different answers so far :D

:lolflag:


My main reasons are I went to a web site (actually Log Me In) and when I tried to connect to a remote PC, Firefox popped up saying I was missing some Java plugins and gave some options.

Also, I'd like to try that LimeWire clone (can't remember it's name) But I understand you need to make sure Java is 100% else you end up with a blank screen in these java based apps.

Hence my question.

Also, do I get the items you mention from the normal Synaptic installer area?

Thanks.

---

### Post by SOULRiDER on 2008-02-29
If youre just going to run stuff you can do
```
sudo aptitude install sun-java6-jre
```
If youre going to be developing
```
sudo aptitude install sun-java6-jdk
```
Easy as pie :)

---

### Post by SOULRiDER on 2008-02-29
> **PiggiePaul said:**
> 
Also, I'd like to try that LimeWire clone (can't remember it's name) o I get the items you mention from the normal Synaptic installer area?


You mean Frostwire?

---

### Post by jan quark on 2008-02-29
I always install this packages
```

sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by PiggiePaul on 2008-02-29
> **SOULRiDER said:**
> If youre just going to run stuff you can do
```
sudo aptitude install sun-java6-jre
```
If youre going to be developing
```
sudo aptitude install sun-java6-jdk
```
Easy as pie :)

Thanks, doing that now.

[COLOR="Blue"]The following packages are unused and will be REMOVED:
  liblzo1 python-qt3 python-sip4 
The following NEW packages will be automatically installed:
  gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin unixodbc 
The following NEW packages will be installed:
  gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-jre 
  unixodbc 
0 packages upgraded, 6 newly installed, 3 to remove and 0 not upgraded.
Need to get 33.0MB/33.2MB of archives. After unpacking 72.8MB will be used.
Do you want to continue? [Y/n/?] y[/COLOR]


72.8MB  WOW !!!!!!

Yes, Frostwire, that was it. Thought I'd give it a try and seen it mentioned a couple of times. (Only heard about it for the 1st time about 30 mins ago!)

---

### Post by SOULRiDER on 2008-02-29
Yeah, its not the smallest download but i think its even more for windoze users.

---

### Post by Teber on 2008-02-29
frostwire is more or less the equivalent of limewire pro, the version you should pay for. you'll probably like it :)

---

### Post by PiggiePaul on 2008-02-29
Thanks again to you all.

Just a little update:

I first used the command:

[COLOR="Blue"]sudo aptitude install sun-java6-jre[/COLOR]

which installed a LOT of data, but unfortunatly going to a JAVA page, it still did not work and firefox still offered me a choice of plugins I needed :(

I then tried this command:

[COLOR="Blue"]sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin[/COLOR]

Went back to the page, and IT'S WORKING :D

Am I right in assuming, the 1st part of that 2nd command above, does exactly the same as the command above it?

Just that it has the extra bit on the end that does something else?

---

### Post by SOULRiDER on 2008-02-29
What you needed to install to make FF work was the plugin package, so basically #2 is the same as doing
```
sudo aptitude install sun-java6-jre sun-java6-plugin
```

**Also, ALWAYS remember to use aptitude and NOT apt-get**, it handles dependencies better!

---

### Post by deadmnky on 2008-02-29
if your trying to use frost wire i personally have issues with it and have read a few post where others had as well. seems to work just fine in windows though. i use the fee version of lime wire since it has no issues to start up.

---

### Post by PiggiePaul on 2008-02-29
I went to the FrostWire site, and the 1st thing that struck me was..........................

Now THIS is how all application web sites should look (esp for the windows crowd)

Nice looking, a up to date, easy download link right there, absolute heaven :D
Nothing could have been easier and more user friendly.

Anyway, Frostwire installed and working fine.
Occasionally have a tiny hiccup where it does not seem to recognize anything I type (as if my keyboard is not working) but a restart fixes it, and then it's ok.

No big deal at all.

Only thing was, it did not seem to have a nice Icon with it, so I made one from their web site graphic.

Here:

[IMG]http://i26.photobucket.com/albums/c145/Paul-rs/FrostWire.png[/IMG]

Just copy this into your usr/share/pixmaps folder.

Looks nice on the AWN icon bar :)

---

### Post by PiggiePaul on 2008-02-29
> **SOULRiDER said:**
> What you needed to install to make FF work was the plugin package, so basically #2 is the same as doing
```
sudo aptitude install sun-java6-jre sun-java6-plugin
```

**Also, ALWAYS remember to use aptitude and NOT apt-get**, it handles dependencies better!

So your line above is (does) exactly the same as:

[COLOR="Blue"]sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin[/COLOR]

I must admit, without futher explanation (the problem when you don't have anyone in the flesh sitting next to you) this is a bit beyond me at the moment.

So, some VERY basic questions:

What does [COLOR="Blue"]apt-get[/COLOR] and [COLOR="Blue"]aptitude[/COLOR] stand for?
And what do you mean by [COLOR="Blue"]handles dependencies better[/COLOR] (what are dependencies?)

---

### Post by lswest on 2008-03-01
I can try to explain^^ Dependencies are files that are required by the package you're installing, without which it would not run.  (for example, say you're downloading an audio converter, but it doesn't have the actual converting programs, so then it downloads those too by specifying them as a "dependency")  

As to the difference between aptitude and apt-get, they're both programs to download and install .deb files from repositories (servers/hosts for the software you want/need) and both use the same sources.list (a file listing all the different URLs for the repositories) and the only difference i've noticed is that aptitude shows you the status of packages (installed, pending, etc.) whereas apt-get only can show you (through apt-cache search [search criteria]) what packages are available.  Two other programs that do pretty much the same are synaptic package manager and add/remove programs, however these both have GUIs, so they may be more becoming for you.  If anyone has anything else to add, feel free^^

---

