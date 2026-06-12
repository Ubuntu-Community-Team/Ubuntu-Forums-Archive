---
title: "How to install firefox onto KUBUNTU?"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by ronlondre on 2005-09-04
How do you install firefox onto KUBUNTU?  I've downloaded the linux verson and untared it. Followed the directions from firefox's web site, no luck. Can someone please give me the codes for installing it?

---

### Post by byen on 2005-09-04
[QUOTE=ronlondre]How do you install firefox onto KUBUNTU?  I've downloaded the linux verson and untared it. Followed the directions from firefox's web site, no luck. Can someone please give me the codes for installing it?[/QUOTE]
 ok..now you are trying really hard....its simple: 
first do this [click here](http://www.ubuntuguide.org/#extrarepositories)
Next open the  terminal(konsole in Kubuntu) and type:
sudo apt-get install mozilla-firefox

thats it...you are good to go! hope it helps.goodluck.

---

### Post by poofyhairguy on 2005-09-04
Do what above said. To make it not look like crap, run this program in the terminal:

> gnome-settings-daemon

---

### Post by sidhusummer on 2005-09-04
I am having trouble installing firefox as well. On running this command: apt-get install mozilla-firefox , I get the following:

"Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate
"

---

### Post by byen on 2005-09-05
have you updated the sources list as mentioned in the first step that i have stated earlier? please do this and try it out again .
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

let us know if you are having futher trouble. goodluck.

PS- i see (in your other post)that you have tried downloading the file and manually installing it. relax. dont try that hard... the whole idea behind synaptic apt-get is to get programs easily. By the way. Welcome to Ubuntu.

---

### Post by aysiu on 2005-09-05
Of course, apt-get is the easiest way to install Firefox:

[i]sudo apt-get update
sudo apt-get install mozilla-firefox[/i]

You can also use Synaptic, which is simply the graphical version of apt-get. I have a screenshot-laden tutorial [here](http://www.psychocats.net/essays/winuxinstall.php).

But if you absolutely insist on installing the one downloaded from Mozilla's website, the installation isn't that much more difficult, either. Just follow these steps (the links are to screenshots):

1. [Double-click on the .tar.gz](http://i22.photobucket.com/albums/b337/psychocats/7d9a1b93.png)
2. [Extract the contents](http://i22.photobucket.com/albums/b337/psychocats/5ecb8626.png)
3. [Double-click on firefox-installer](http://i22.photobucket.com/albums/b337/psychocats/993d7d90.png) and [run it](http://i22.photobucket.com/albums/b337/psychocats/cf84ab22.png)
5. [Follow the "wizard."](http://i22.photobucket.com/albums/b337/psychocats/2cffab86.png)
6. [To launch Firefox, double-click on firefox](http://photobucket.com/albums/b337/psychocats/?action=view&current=9d212f88.png)

---

### Post by Oliver Closov on 2008-04-09
> **sidhusummer said:**
> I am having trouble installing firefox as well. On running this command: apt-get install mozilla-firefox , I get the following:

"Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate
"


I am having this exact same problem, however updating has not helped so far.  Exact same problem when I tried to install Thunderbird. I have tried typing both sudo apt-get install mozilla-firefox AND sudo apt-get install firefox, just in case different distros have different protocols (which I imagine they do).
I am using Kubuntu 7.
I am a complete beginner who has previously relied on the "convenience" of the MS GUI world.
I went to the Mozilla webpage and found the Ubuntu install instructions which say to click on applications->add/remove programs->type in firefox->then click box, but it doesn't want to let me click in the box.

UPDATE:
Based on something I found on the suggested link, I tried adding repositories to the source list - Of the very few choices (and not even really understanding what the purpose was) I chose [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (which seemed harmless enough) and now it won't even let me open the add/remove apps gui (saying "The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. try running apt-setup (which when i tried said "command not found") and apt-set update (which said "E: Type 'http://archive.canonical.com/ubuntu' is not known on line 78 in source list /etc/apt/sources.list") to see if it helps resolve the problem (which it clearly did not)). PLUS when I tried to sudo apt-get install firefox the message i was getting changed to...
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the admistration directory (/var/lib/dpkg/), is another process using it?
I closed the add/remove gui i had open and tried sudo apt-get install firefox again and the message changed to ...
E: Type 'http://archive.canonical.com/ubuntu' is not known on line 78 in source list /etc/apt/sources.list
E: The list of sources could not be read.
I tried to open the file listed and delete the line, but it did not give me permission.

Will somebody please hold my hand?

Thanks,

Oliver

---

