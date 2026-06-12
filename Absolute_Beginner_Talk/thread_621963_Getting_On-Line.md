---
title: "Getting On-Line"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by di22y on 2007-11-24
I am brand new to Ubuntu and I'm having trouble getting connected to the internet which is my main priority because at the moment I have to keep switching between Windows xp and Ubuntu(7.10) if I want to look up anything on the net which I need to do quite a lot because as I said I am new to Ubuntu. So I'm  looking for somebody to help me with this issue(Obviously).

Right then I have a BeWan PCI modem and I have entered my IP, DNS, user name, password etc. and I'm still unable to browse the net. Do I need to tell Ubuntu to conect before I open my browser if so How?(is my first question)

---

### Post by derby007 on 2007-11-24
I see help on another website at : [http://huw.org.uk/pages/misc/bewan-adsl-pcist.php]("http://huw.org.uk/pages/misc/bewan-adsl-pcist.php")
I hope its not too confusing...

---

### Post by buccaneere on 2007-11-24
> **di22y said:**
> I am brand new to Ubuntu and I'm having trouble getting connected to the internet which is my main priority because at the moment I have to keep switching between Windows xp and Ubuntu(7.10) if I want to look up anything on the net which I need to do quite a lot because as I said I am new to Ubuntu. So I'm  looking for somebody to help me with this issue(Obviously).

Right then I have a BeWan PCI modem and I have entered my IP, DNS, user name, password etc. and I'm still unable to browse the net. Do I need to tell Ubuntu to conect before I open my browser if so How?(is my first question)

I bet I'm newbie-er than you... BUT, this link got me online with Edgy:

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

---

### Post by di22y on 2007-11-24
> **derby007 said:**
> I see help on another website at : [http://huw.org.uk/pages/misc/bewan-adsl-pcist.php]("http://huw.org.uk/pages/misc/bewan-adsl-pcist.php")
I hope its not too confusing...

I am trying to follow the instructions above and I get upto this part of the Instructions

'Next you'll need to download some packages from the Debian repository. I'm unsure if all these are needed, I just used the list of dependencies from the broken debian packages. In a terminal run:

aptitude install libc6 libglib1.2 libgtk1.2 libx11-6 libxext6 libxi6 libc6-dev make gcc linux-source'

When I hit Enter I get

Reading package list... Done
Building dependancy tree
Reading state information... Done
Initializing package states... Done
Building tag databae... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory(/var/lib/dpkg/), are you root?

Does anybody have any idea what my next course of action should be?

---

### Post by buccaneere on 2007-11-24
> **di22y said:**
> I am trying to follow the instructions above and I get upto this part of the Instructions

'Next you'll need to download some packages from the Debian repository. I'm unsure if all these are needed, I just used the list of dependencies from the broken debian packages. In a terminal run:

aptitude install libc6 libglib1.2 libgtk1.2 libx11-6 libxext6 libxi6 libc6-dev make gcc linux-source'

When I hit Enter I get

Reading package list... Done
Building dependancy tree
Reading state information... Done
Initializing package states... Done
Building tag databae... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory(/var/lib/dpkg/), are you root?


Does anybody have any idea what my next course of action should be?

Try to execute the commands as root user:

exec sudo -s        'enter'

Then re-attempt the code

aptitude install libc6 libglib1.2 libgtk1.2 libx11-6 libxext6 libxi6 libc6-dev make gcc linux-source'

---

