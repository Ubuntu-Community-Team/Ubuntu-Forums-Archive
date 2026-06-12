---
title: "stardict"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by eneth80 on 2007-11-22
Dear people, 
I have stardict 2.4.8 installed but i'd like to install the newest version. I downloaded stardict_3.0.1-1_i386.deb from the site, and as i double click on it i get : Error: wrong architecture 'i386' . i ve tried 
sudo dpkg -i --force-architecture stardict_3.0.1-1_i386.deb but it does not work. 
Is there any solution for this?
ale

---

### Post by Partyboi2 on 2007-11-22
Couldn't you install it by:
```
sudo apt-get stardict
```?

---

### Post by eneth80 on 2007-11-22
aless@aless-office:~$ sudo apt-get stardict
E: Invalid operation stardict

??

---

### Post by Partyboi2 on 2007-11-22
opps,
I did a typo:
try:
```
sudo apt-get install stardict
```

---

### Post by eneth80 on 2007-11-22
oh yes sure, stupid me.. but it does not work anyway

sudo apt-get install stardict
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
stardict is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-date-time1.33.1 libgtkglext1 libboost-thread1.33.1 lesstif2
  libgnash0 gnash
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by nick_h on 2007-11-22
I think I replied to another thread on this subject.

You seem to be running Feisty.  The default version of stardict for Feisty is 2.4.8 and for Gutsy is 3.0.0

I have tried installing the deb you dowloaded in Feisty and I get 12 packages that need upgrading.

---

### Post by eneth80 on 2007-11-22
and do you the link to your old thread?

---

### Post by Bruce M. on 2007-11-22
> **nick_h said:**
> I think I replied to another thread on this subject.

You seem to be running Feisty.  The default version of stardict for Feisty is 2.4.8 and for Gutsy is 3.0.0

I have tried installing the deb you dowloaded in Feisty and I get 12 packages that need upgrading.

Does this mean the Feisty is incapable of running upgraded software?

ie:  StarDict, Firefox, Thunderbird to start with are in Ubunto repos, but what about downloading upgraded versions from their respective sites?

---

### Post by nick_h on 2007-11-22
> **eneth80 said:**
> and do you the link to your old thread?
[Link](http://ubuntuforums.org/showthread.php?t=613876) - I remember now, it was your thread.

Now I have tried installing it myself I can see the problems.  I don't recommend installing it without getting some further advice from an expert, but you have two options.   You could either force the installation by ignoring the dependency versions, or you could update the dependent packages.  However, if you upgrade the packages you don't know what you might break on the system.

You can still use multiple dictionaries on the Feisty version just not the dictionary groups.

---

### Post by nick_h on 2007-11-22
I have just looked on the stardict forums and there is an interesting post [here](http://www.stardict.org/forum/viewtopic.php?f=5&t=144).

---

### Post by nick_h on 2007-11-22
> **Bruce M. said:**
> Does this mean the Feisty is incapable of running upgraded software?

ie:  StarDict, Firefox, Thunderbird to start with are in Ubunto repos, but what about downloading upgraded versions from their respective sites?

You can quite often install software downloaded from product sites.  In this case though the software required updating some system libraries.  This could possibly cause unexpected problems.

There are some howto guides for upgrading Firefox and other packages.

---

### Post by Bruce M. on 2007-11-23
> **nick_h said:**
> You can quite often install software downloaded from product sites.  In this case though the software required updating some system libraries.  This could possibly cause unexpected problems.

There are some howto guides for upgrading Firefox and other packages.

Thanks for your reply.  Sorry for being late responding.
This seems restrictive in one way, but possibly more secure in another.
I remember trying to get a new FireFox for 6.04, it just didn't work.  :(
But I'd like to try the new StarDict.  I use it quite often.

---

