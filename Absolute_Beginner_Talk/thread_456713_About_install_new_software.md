---
title: "About install new software"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by can.lu on 2007-05-28
So far, I haven't been able to install anything I wanted yet. Using Synaptic Package Manager is supposed to be simpler but the situation is always, I need to install A, but then A require, B, C,D,E,F and then B needs G,H,I......till I lost all the interests to keep digging.

Am I doing right? Or it is just like this "fun".

---

### Post by borris.morris on 2007-05-28
it should install all dependencies too. if all else fails you can use synaptic to find the package and then "sudo aptitude install package_name" and it should take care of it.

---

### Post by dhruva023 on 2007-05-28
can you please clearly write, what you really trying to install.

synaptic manager, does ask for the dependences, but u don't have to search for those, it will done automaticaly.

---

### Post by ramjet_1953 on 2007-05-28
Exactly how are you doing this?

Synaptic package manager is just that, a package manager and it automatically sorts out dependencies and installs them.

If I were you, to start out, use the [COLOR="Blue"]Applications>Add / Remove[/COLOR] menu, until you get your feet.

It is a simpler interface and has lots of software that can be downloaded with a couple of clicks of the mouse.

Regards,
Roger :cool:

---

### Post by can.lu on 2007-05-28
Simple as you guys said, I tried to install Amarok on Ubuntu with Synaptic Package Manager. Then it told me not all the depends can be installed. Following is the msg SPM gave me.

amarok:
 Depends: amarok-gstreamer but it is not going to be installed or
 	amarok-engines but it is not going to be installed or
	amarok-engine
 Depends: kdelibs4c2 but it is not going to be installed
 Depends: libtag1c2 but it is not going to be installed
 Depends: libtunepimp2c2 but it is not going to be installed

Is there anything wrong with my setup of repositories?

---

### Post by aysiu on 2007-05-28
> **can.lu said:**
> 
Is there anything wrong with my setup of repositories? Yes. Dependency errors stem from conflicting repositories in about 99% of cases. [Get a fresh set of repositories](http://www.psychocats.net/ubuntu/sources#mirror) and try again.

---

### Post by can.lu on 2007-05-28
Thank you for the answer. I've followed the link you gave me. It seems work (system told me there are some update I have to do so I haven't tried to install anything yet)

then my question comes: I just install the latest version of Ubuntu, why the system doesn't give me the latest repositories? how often should I check repositories? 

regards,

---

### Post by ryanVickers on 2007-05-28
> ...need to install A, but then A requires, B, C, D, E, F and then B needs G, H, I...

Yes, this is normal, but it should go out and find b, c, d, etc. automatically, so it's not a problem.  Try using the Add/Remove thing instead if it doesn't work.  Also, I've noticed a check box that sometimes appears, make sure it's on (the one to get dependencies).

---

### Post by aysiu on 2007-05-28
> **can.lu said:**
> 
then my question comes: I just install the latest version of Ubuntu, why the system doesn't give me the latest repositories? how often should I check repositories?  It's not a question of latest or earliest. It's a question of good v. bad. If you're experiencing dependency errors, you probably have a bad (i.e., conflicting) set of repositories.

The tutorial I gave you got rid of that bad set and replaced it with a good, working set.

Are you sure you didn't do anything to modify the original repositories list since the beginning of the installation? Did you, by chance, use some kind of script like Automatix?

---

### Post by can.lu on 2007-05-28
Thank you for the prompt replay.

This is my very first time install Linux and I did it two days ago. I didn't do any change yet coz I don't want to do stupid things before I understand it. It took me some guts to run the script in the link you gave me as I don't understand majority of it.

So it seems that I should keep my repositories up-to-date and I just realized that some websites (the 3rd parties) may be very slow.

---

