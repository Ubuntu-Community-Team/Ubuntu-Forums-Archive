---
title: "cant install.."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by nyp4life on 2008-02-05
hey everybody, im trying to install certain things using apt-get and adept but i keep getting error messages.. when i try with apt-get i get the following:

nyp4life@nyp4life:~$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  azureus: Depends: icedtea-java7-jre but it is not going to be installed or
                    sun-java6-jre but it is not going to be installed or
                    sun-java5-jre but it is not going to be installed
           Depends: libcommons-cli-java but it is not going to be installed
           Depends: liblog4j1.2-java but it is not going to be installed
           Depends: libseda-java but it is not going to be installed
           Depends: libswt3.2-gtk-java but it is not going to be installed
  sun-java6-bin: Depends: sun-java6-jre (= 6-03-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and when i try through adept i get another error message:

'There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.'

this happened when trying to install azureus, konversation, java, and kde4.. any ideas? do i have to install something i haven't?? thanks in advance..

---

### Post by Linux_Man on 2008-02-05
Hmm... Do you have all the repositories enabled? (Universe, Multiverse, ETC.) If so then I don't know what the problem is. Try an apt-get update and see if that fixes it.

---

### Post by emarkd on 2008-02-05
Maybe you don't have the universe and multiverse repositories enabled.  I'm not familiar with Adept, but in Synaptic there's an option under Settings > Repositories to enable these other locations.  See if you can find something like that.  After you get them enabled, remember to do a Reload or update before you try your install again.

---

### Post by nyp4life on 2008-02-05
ahh ok i tried apt-get upgrade and it said i had to run "apt-get -f install" because of a previous crash. thanks for the quick replies!

---

### Post by Linux_Man on 2008-02-05
Ok, did you enable multiverse/universe repositories? Type in sudo synaptic in the terminal then go to Settings--->Repositories and make sure all the boxes are checked. Then run apt-get -f install and then try to install normally.

---

### Post by nyp4life on 2008-02-05
yea after i ran apt-get -f install everything was normal.. i can once again download packages :D

---

