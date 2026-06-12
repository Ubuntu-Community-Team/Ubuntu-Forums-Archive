---
title: "[SOLVED] installing java"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-07-17
i want to view a web page, but it says i need to install java. i followed the link and there are alot of java's there for linux. not wanting to upset the apple cart im posting here for help. i looked at the other post that relate to this and i see this should already have java on it. please keep in mind im new to linux and know nothing about it but am willing to learn

---

### Post by jvc26 on 2007-07-17
from terminal do:
```

sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin

```
Then restart firefox.
Il

---

### Post by rickycodie on 2007-07-17
go to getautomatix.com and install the package, then install java off of automatix. very easy.

---

### Post by jvc26 on 2007-07-17
If I was you, although a personal preference I'd avoid automatix if you can, it does make things simpler, but has caused problems for people in the past, isnt recommended by those who make Ubuntu, and also, if you do it yourself you get a picture of whats going on so you can repeat it yourself on later occasions.
Il

---

### Post by rjfioravanti on 2007-07-17
> **Illuvator said:**
> If I was you, although a personal preference I'd avoid automatix if you can, it does make things simpler, but has caused problems for people in the past, isnt recommended by those who make Ubuntu, and also, if you do it yourself you get a picture of whats going on so you can repeat it yourself on later occasions.
Il

second that... avoid automatix, installing it yourself is so easy anyways!

---

### Post by Bablefish on 2007-07-17
Just check Add Remove it's there

---

### Post by trucker33377 on 2007-07-17
sounds good ill install myself. did the sudo command . it show the accept lic. screen there is dark now i can still read it should i close it out and reopen firefox now

---

### Post by rjfioravanti on 2007-07-17
> **trucker33377 said:**
> sounds good ill install myself. did the sudo command . it show the accept lic. screen there is dark now i can still read it should i close it out and reopen firefox now

Did you agree to the license? You have to scroll to the bottom of the license and agree, then you should see it install itself, and return to command prompt... after that then you can restart firefox

---

### Post by trucker33377 on 2007-07-17
i still have term open it show the lic, and has ok  but i cant do anything in that screen. it unpack to that point then the term became shaded

---

### Post by ajgreeny on 2007-07-17
Scroll to the bottom of the accept license screen and then hit "Y" without the quotes, of course to accept, not OK.  All should then work alright and java be installed properly.
Or- I think you may just need to close the terminal and you may have already accepted.  Open FF again and see if the java plugin is there by typing about:plugins in the address bar.

---

### Post by trucker33377 on 2007-07-17
:( had i just waited 1 more sec:)

lonnie@lonnie-desktop:~$ sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
lonnie@lonnie-desktop:~$ 
ok now what please

---

### Post by rickycodie on 2007-07-17
copy the dpkg --config line into a new line and put sudo infront of it. then hit enter. try to install again.

---

### Post by rickycodie on 2007-07-17
i have automatix on 4 different boxes --no problems.

---

### Post by trucker33377 on 2007-07-17
humm I got it to reopen but i cant get past the lic agreement. i did hit the y key nothing happened there. im still not sure about the term becoming dark gray when it gets to this spot does that matter or are things as they should be?

---

### Post by Billsboy on 2007-07-17
You are not alone bud. I have the same issue.

---

### Post by testube_babies on 2007-07-17
Any reason why you want Java 5 instead of the newer Java 6?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)

...I think if you hit either the spacebar or left arrow at the license, the cursor will jump to the OK button and you can hit enter to accept.  But if it just freezes, I'm not sure how to solve the problem.

Also, regarding Automatix:
"Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu."

---

### Post by trucker33377 on 2007-07-17
well i am so new to linux, i want the latest java that works. this ver came up to install when i followed sudo command from earler reply. Im not even sure if my updates on ubuntu are installed i know i downloaded them, so I maybe ahead of myself. who knows. Im trying to do the mods for Linux Survival. lol got to start somewhere. when i installed this I lost windows so theres no turning back.

---

### Post by crimesaucer on 2007-07-17
> **testube_babies said:**
> Any reason why you want Java 5 instead of the newer Java 6?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)

...I think if you hit either the spacebar or left arrow at the license, the cursor will jump to the OK button and you can hit enter to accept.  But if it just freezes, I'm not sure how to solve the problem.

Also, regarding Automatix:
"Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu."


testube babies gave the correct info for Java 6....and yes, press "enter" on the ok button after scrolling down.


...afterwards, check to see you art using the new java 6 by writing in to Terminal this command:

```
sudo update-alternatives --config java
```


then follow the directions, it will look like this:

```

blah@blah-blah:~$ sudo update-alternatives --config java
Password:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.0
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/gij-wrapper-4.1
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
blah@blah-blah:~$

```


also, in Firefox, check your about plugins.

---

### Post by trucker33377 on 2007-07-17
i did a reboot when i got back on there were 2 updates for java 5. also i did what testube_babies said and saw during unpacking that files were missing from java 5. understand i was unpacking java6. do i need to remove java 5 if so how? thxs

---

### Post by crimesaucer on 2007-07-17
You don't need to remove it, all you have to do is:

```
sudo update-alternatives --config java
```

...and configure it to use your newest java6.


Then you can remove java5 in synaptic if you want to.

---

### Post by trucker33377 on 2007-07-17
hay ppl thanks got java 6 up and running. windows is slowly moving out of this computer LOL. close the book on this one

---

### Post by trucker33377 on 2007-07-20
heres the deal i put in a new HD and setup ubuntu 7.4. im trying to get java 6 to work on it. ive gone thru this posting everything looks good. but im not sure about plugins for firefox. when i try to use java it still is asking for a manual install

---

### Post by ajgreeny on 2007-07-21
Does firefox show the java plugin installed if you type about(colon)plugins in the address bar?  If so it is already installed.
PS Don't put the word colon in brackets as shown here, just type it normally, for some reason the colon and a p show up as a smiley in the forums.

---

### Post by ellgor on 2007-07-21
Hi. 
If, after installing whatever version of Java, and you still cannot access the web page,I found that the J2re1.4 is the one that makes things tick,
It is listed in the synaptic manager (all repositries enabled and updated) and a quick tip, if you click on the little box marked with a S above the list of packages and start typing J2re it will appear, to confirm, the Java package is labelled Blackdown edition and a Mozilla plugin right underneath, load both, they load auto  apart from a licence to agree to, hope this is of help.

Regards, Ellgor.

---

