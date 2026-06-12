---
title: "Easiest way to install GTK2.0-Dev?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by bsf on 2007-09-25
Hello everyone i have a quick/easy question. What is the easiest way to install GTK2.0-Dev? I have downloaded literally 40 different packages from one computer and copied them to my ubuntu box, I don't have the internet yet on the other computer as I need GTK2.0-Dev to get it to work.
thanks for your help:)

---

### Post by bobplano on 2007-09-25
do you mean libgtk2.0-dev? that's the only one in the repos that i found. go onto that other computer with internet access and go to packages.ubuntu.com then look for the package (which is [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=GTK2.0-Dev&searchon=names&subword=1&version=all&release=all")

---

### Post by bsf on 2007-09-25
hi, yeah it was libgtk2.0-dev sorry about that! I done that and then it said to install this you need another package and so on... it went for literally 2 hours until i could just install libgtk2.0-dev

---

### Post by bobplano on 2007-09-25
ouch, dependency hell:(. the only alternative is to get an ethernet cable and plug in somewhere. it might be worth it, if for some reason ubuntu's wireless support doesn't get any better, or you're trying out other distros. that really sucks, but i never got it as bad as that

---

### Post by bsf on 2007-09-25
yeah it did suck! I am not attempting to get the rt73 driver to work.. man i suck at this :-(!

---

### Post by RomeReactor on 2007-09-25
Just as a comment on dependency hell: Synaptic comes with a great feature that creates a script on a machine without internet to download packages **and** their dependencies on another (provided they both run Linux). Just:

* Open Synaptic on the machine without internet;
* Search for whatever package you want to install, mark it for installation;
* Still in Synaptic, go to "File->Generate package download script";
* Copy that script to a machine with internet access, run the script;
* Copy the downloaded packages to the first machine, open Synaptic and go to "File->Add downloaded packages".

---

### Post by bsf on 2007-09-25
oh ok:) Shame this PC is Windows! Anyway i fixed it along with my wireless!
thanks everyone

---

