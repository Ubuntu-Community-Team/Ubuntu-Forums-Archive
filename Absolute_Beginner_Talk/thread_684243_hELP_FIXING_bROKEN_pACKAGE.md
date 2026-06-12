---
title: "hELP FIXING bROKEN pACKAGE"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by eul0gy on 2008-01-31
ok here's my problem.  when i open up my add/remove tab i get this:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

i tried both in the terminal and it hasn't fixed anything. 

NOW when I go to my package manager it get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

im starting to get aggravated with ubuntu. it's has never failed me until now and this is epic.  HELP!!!!

---

### Post by overdrank on 2008-01-31
> **eul0gy said:**
> ok here's my problem.  when i open up my add/remove tab i get this:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

i tried both in the terminal and it hasn't fixed anything. 

NOW when I go to my package manager it get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

im starting to get aggravated with ubuntu. it's has never failed me until now and this is epic.  HELP!!!!

Hi and you will need to run the command in the terminal ```
sudo dpkg --configure -a
```

---

### Post by eul0gy on 2008-01-31
THIS IS WHAT I GOT:

sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-11-1ubuntu2); however:
  Package sun-java5-bin is not installed.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-plugin

---

### Post by SunnyRabbiera on 2008-01-31
hmm, what package did you try to install?

---

### Post by eul0gy on 2008-01-31
maybe automatix??  to the jave runtime package??? i really don't know. i'd remove them but i can't open my add/remove programs.  arghhhhh!!!!

---

### Post by SunnyRabbiera on 2008-01-31
well the add/remove applet is a very basic way to download and install applications but to make sure nothing else is up I want you to go to system, then to administration, then to synaptic package manager.
open it up then type in your password and if you get any errors please tell me.

---

### Post by eul0gy on 2008-01-31
still cant open add/remove programs.  i had no problem opening up the package manager. but when i fix broken packages nothing happens. help??

---

### Post by SunnyRabbiera on 2008-01-31
well the best way for me to help you is to know what exactly did you install to cause this mess.
The first clue is automatix, you said you installed it right?
and you installed the java runtime as well right?
lets start with you telling me what you installed right before you got this issue.

---

### Post by eul0gy on 2008-01-31
haha i appreciate all this help man. if i recall the last thing I remember downloading is the java runtime envoirnment 5 i think from the add/remove list. automatix was right before and that download really didn't work.  i'm sure it was java.

---

### Post by eul0gy on 2008-01-31
i also just sent off for the 7.10 gutsy live disc. im running 7.04 feisty right now. hopefully we can fix this problem until the disc arrives

---

### Post by Zack McCool on 2008-01-31
Have you tried 
```

sudo apt-get remove sun-java5-plugin

```
To remove the broken package, then install the java runtime itself before installing the plugin?

---

### Post by SunnyRabbiera on 2008-01-31
Yes more then likely its probably java then if that is indeed the case.
alright if you can go back into synaptic and then search for the jre package and I will give you these instructions on how to uninstall it:
when you find it right or left click on the little box next to it and select "mark for complete removal"
now if it asks to mark additional packages, then do so and click the "ok" button.
after this go to the "apply" button and click on it
another window will pop up and click on apply once more...
this will uninstall java.
now dont worry I will help you get java back later on, in fact i will teach you how to get the official version from suns website installed so this might not occur again.

> **Zack McCool said:**
> Have you tried 
```

sudo apt-get remove sun-java5-plugin

```
To remove the broken package, then install the java runtime itself before installing the plugin?

this is another method to use if the above did not work

---

### Post by asmoore82 on 2008-01-31
[SIZE="4"][http://mjg59.livejournal.com/77440.html]("http://mjg59.livejournal.com/77440.html")[/SIZE]

As I understand it, the Automatix2 "developers" have been little help with these numerous problems.

---

### Post by SunnyRabbiera on 2008-01-31
> **asmoore82 said:**
> [SIZE="4"][http://mjg59.livejournal.com/77440.html]("http://mjg59.livejournal.com/77440.html")[/SIZE]

As I understand it, the Automatix2 "developers" have been little help with these numerous problems.

eh its a double edged sword, its good for beginners but horrid in the long run...

---

### Post by eul0gy on 2008-01-31
> **asmoore82 said:**
> [SIZE="4"][http://mjg59.livejournal.com/77440.html]("http://mjg59.livejournal.com/77440.html")[/SIZE]

As I understand it, the Automatix2 "developers" have been little help with these numerous problems.

doesn't suprise me. i've sat here and just read numerous bad comments on automatix. screwz it.

---

### Post by eul0gy on 2008-02-01
I FIXED THE PROBLEM!!! This is why I love ubuntu. thanks alot guys!!!

---

### Post by antisocialist on 2008-02-01
> **eul0gy said:**
> I FIXED THE PROBLEM!!! This is why I love ubuntu. thanks alot guys!!!

just a heads up for future problems, do EXACTLY what ubuntu tells you to, when it said to run dpkg --configure-a you didnt do it until someone told you, and you didnt open synaptics when it told you to.

in the future you may be able to solve your problems alone by following the steps that the ubuntu developers work so hard to put there for you

EDIT: also please mark this thread as solved by going to thread tools>mark this thread as solved as it will make it easier for people trying to help others because they will know you do not need help anymore

---

