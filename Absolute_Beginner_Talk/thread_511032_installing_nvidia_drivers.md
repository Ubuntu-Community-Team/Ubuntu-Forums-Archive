---
title: "installing nvidia drivers"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Agent_34 on 2007-07-27
hey guys i just installed ubuntu for the first time and i downloaded nvidia drivers (nvidia-linux-x86_64-100.14.11-pkg2.run) and when i duble click on it well it just wants to open up in a text doc and im really new to ubuntu and well linux so i dont know what else to do with it 

HELP

---

### Post by Waappu on 2007-07-27
Hi

Download Envy. Isntall it and use it to install nVidia driver
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Darkriser on 2007-07-27
I followed [this thread]("http://ubuntuforums.org/showthread.php?t=263851") (STEP 2 -> Option 2) and everything went absolutely smooth.

Regards,
Marcel

---

### Post by kodoku on 2007-07-27
Hello,

You don't have to use Envy, just do 

> sudo apt-get install nvidia-glx

And then reboot, and then run Menu -> Preferences -> Desktop Effects, and then make sure the restricted driver is running.

---

### Post by maduranga on 2007-07-27
System>Administration>Restricted Drivers Manager

from theres you will be able to install the driver

---

### Post by Mornedhel on 2007-07-27
Agent_34, have you searched the rest of the forum to find an answer first ? I'm assuming not, since this is an *extremely* common question.

And, please read some of the stickies, they contain interesting information such as how to actually install software for Ubuntu. You have no idea how often newcomers ask "I don't know how to install this, it says compile" or "how do I install something.bin" ? only to have the helpers answer "just install it from the goddamn repositories".

Excuse the kinda violent tone, but this is getting tiring.

Edited some rambling out.
Second edit : Ah fsck, my 200th post is a rant. Apologies.

---

### Post by cwm33 on 2007-07-27
> **Mornedhel said:**
> Agent_34, have you searched the rest of the forum to find an answer first ? I'm assuming not, since this is an *extremely* common question.

And, please read some of the stickies, they contain interesting information such as how to actually install software for Ubuntu. You have no idea how often newcomers ask "I don't know how to install this, it says compile" or "how do I install something.bin" ? only to have the helpers answer "just install it from the goddamn repositories".

Excuse the kinda violent tone, but this is getting tiring.

Edited some rambling out.
Second edit : Ah fsck, my 200th post is a rant. Apologies.
As more and more new users take up Ubuntu, these already answered questions will continue to be asked.  I don't know why, but it's just an unwritten forum rule for new users to ask the same questions again and again.  I've been on more or less every different type of forum, and seen it happen.  If it doesn't happen here, I'll be INSANELY surprized, and a duck might literally fly out my posterior.

---

### Post by AlexenderReez on 2007-07-27
> **kodoku said:**
> Hello,

You don't have to use Envy, just do 



And then reboot, and then run Menu -> Preferences -> Desktop Effects, and then make sure the restricted driver is running.


for feisty and next version please use nvidia-xgl-new instead of nvidia-xgl for new kind of nvidia chipset (for new nvidia graphic card)


:)

---

### Post by C.S.Cameron on 2007-07-27
> **maduranga said:**
> System>Administration>Restricted Drivers Manager

from theres you will be able to install the driver

Hello Maduranga, fancy finding you here, small world.
Cork

---

### Post by BudaTx on 2007-07-27
I've installed PCLinux, DSL, RH etc. and now Ubuntu.  And after first reading the 7+ guides about *easy* ways to install Nvidia drivers on Feisty (and even asking in my own thread) I still haven't been completely successful with configuring my Riva TNTM64 and have to add that it would be nice to have a guide that will walk a new user through installing the legacy cards.  Yes, I have used Envy, dpkg -reconfigured to death (and I never knew Linux commands by rote until now), apt-get[ted] until I had so many Nvidia packages that I am now typing this reply from my liveCD before an impending re-install.  Hopefully I will get my Nvidia and SBLive completely working this time.  There are many *how-to install the easy way* posts from seasoned vets who have had success with certain models of cards, but as a general post/sticky it would be good to see a guide for legacy and late model Nvidia.  That's a lot to ask from volunteers and I've put many free hours in with Windows at friends homes & by phone so I understand the motive behind making someone successful and happy, but please have patience, We're trying to make it work and want to be successful too.   Thanks
Ubuntu Newbies with Nvidia

---

### Post by cwm33 on 2007-07-27
> **AlexenderReez said:**
> for feisty and next version please use nvidia-xgl-new instead of nvidia-xgl for new kind of nvidia chipset (for new nvidia graphic card)


:)
What exactly marks a chipset as "new"?  Where's the cutoff point? 4 series? 5 series? 6 series?  When I tried using the nvidia-xgl-new drivers on my system (Nvidia 6800GT), they completely cratered the system and I was unable to load any form of graphical interface.

---

### Post by AlexenderReez on 2007-07-27
> **cwm33 said:**
> What exactly marks a chipset as "new"?  Where's the cutoff point? 4 series? 5 series? 6 series?  When I tried using the nvidia-xgl-new drivers on my system (Nvidia 6800GT), they completely cratered the system and I was unable to load any form of graphical interface.

hm...i think your card has new kind of chipset:)...the only reason is you didn't install restricted - modules for your kernel:) ...search nvidia in synaptic....see the restricted modules for your kernel..figure it out....then install,reboot:) ...

---

