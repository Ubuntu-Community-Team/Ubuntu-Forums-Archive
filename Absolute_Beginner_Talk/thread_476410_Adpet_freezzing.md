---
title: "Adpet freezzing"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by natman on 2007-06-17
When i start up i see the little adept update manager telling me to get new updates, i click and fetch the list and apply.
Then the program just freezes when its about to apply updates, all i see is the status bar,preparing upgrade of sun-java5-bin 0%                show details

Can anyone tell me how to fix this?
Thanks

---

### Post by Damanther on 2007-06-17
You could try the synaptic package manager and see if it behaves differently.

Alternatively you could fetch the list of updates in adept, 'uncheck' the java update to see if it has something to do with that particular package.

---

### Post by meborc on 2007-06-17
try running the update from the terminal

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by natman on 2007-06-17
Hi medroc,
I ran those commands and it asked did i want to download 83Mb of new stuff i agreed and then it gave me trouble about sun java 5 bin, next thing the terminal pops into a liences agreement for sun java 5, i tried to press enter but nothing happened.

I also when to synaptic and tried to completly remove sun java 5, it gave an error saying 
Package is in a very bad inconsistent state - you should E: sun-java5-jre: Package is in a very bad inconsistent state - you should

Any ideas?

---

### Post by meborc on 2007-06-17
when the java licence comes up press TAB then enter... i think :)

---

### Post by natman on 2007-06-17
I have no idea whats going wrong, but when i try to upgrade all i get is this
[HTML]Hit http://archive.ubuntu.com feisty-backports/main Sources
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources
Hit http://archive.ubuntu.com feisty-backports/restricted Sources
Fetched 5B in 0s (7B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
natman@natman-laptop:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
natman@natman-laptop:~$ 
[/HTML]
I went to ksysguard and kill'd all other pacakge managers, I dont even want sun java , if i could just get rid of the dam thing

---

### Post by meborc on 2007-06-17
the error you are getting means another package manager is running... klose the synaptic package manager and resume from the terminal

update
upgrade
-f install

etc...

more info on how to get java working here - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

---

### Post by natman on 2007-06-17
Thanks for all the help, seems to be fine now.
Thanks

---

