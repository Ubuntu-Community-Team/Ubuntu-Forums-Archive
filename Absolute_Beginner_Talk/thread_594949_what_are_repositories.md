---
title: "what are repositories"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-28
What are repositories? And how can we get to the repositories, in other words where are they?

Thnx

---

### Post by llamakc on 2007-10-28
> **limac said:**
> What are repositories? And how can we get to the repositories, in other words where are they?

Thnx

They are either on a CD or on the Internet. When you use Synaptic to install software, it is the place that Synaptic goes and fetches the debs from.

---

### Post by Celegorm on 2007-10-28
Repositories are a central location from which you can download and install software that has been packaged especially for use with your operating system. Using repositories is the normal way of installing new software in linux. In ubuntu, they are accessed through add/remove and synaptic, or, for those that like the command line, apt-get or aptitude. The cd can also be used as a repository, as llamakc mentioned, and I'm pretty sure you can download packages on one computer, put them on a cd, and then use that cd like a repository on another computer.

---

### Post by gobuntu on 2007-10-28
Repositories are SOFTWARE SOURCES, meaning 'places' where available for you to install or download software from, or upgrade it,  typically free of charge. Places, of course can be CD's, DVD's, or websites.

Your Ubuntu installation must know which are those places, and that you establish via the Taskbar: System/Administration/Software Sources.

There, the repositories are grouped into tags: Ubuntu Software, Third Party Software, Updates, Authentication, and Statistics.

Click on those tabs to [X] the ones you wish to establish as your software-sources.

What that does is alter a configuration text file in your system, called "sources.list", located at /etc/apt directory.

With Gutsy, clicking via System is plenty to get you a good system, with no much need to immediately alter that list by hand.

Repositories HAVE TO BE proper for your Ubuntu version, and System does that for you very well, whereas by hand, they might not be proper.

Softwares are in "packages" and there are several formats. Ubuntu uses "deb" packages, meaning Debian-format.

---

### Post by limac on 2007-10-28
ok so what do people mean when they talk about 3rd party repos and where are the 3rd party repos located? And more importantly what are they.

---

### Post by limac on 2007-10-28
> **gobuntu said:**
> Repositories are SOFTWARE SOURCES, meaning 'places' where available for you to install or download software from, or upgrade it,  typically free of charge. Places, of course can be CD's, DVD's, or websites.

Your Ubuntu installation must know which are those places, and that you establish via the Taskbar: System/Administration/Software Sources.

There, the repositories are grouped into tags: Ubuntu Software, Third Party Software, Updates, Authentication, and Statistics.

Click on those tabs to [X] the ones you wish to establish as your software-sources.

What that does is alter a configuration text file in your system, called "sources.list", located at /etc/apt directory.

With Gutsy, clicking via System is plenty to get you a good system, with no much need to immediately alter that list by hand.

Repositories HAVE TO BE proper for your Ubuntu version, and System does that for you very well, whereas by hand, they might not be proper.

Softwares are in "packages" and there are several formats. Ubuntu uses "deb" packages, meaning Debian-format.

What are the differences between ubuntu software and third party software?

Thnx so far

---

### Post by FuturePilot on 2007-10-28
Third party repos usually contain either software that is not in the Ubuntu repositories, or a newer version of a particular program than what is in the Ubuntu repos.
For example, Exaile (a media player) is in the Ubuntu repos. But you can add a third party repo that will keep you up to date with the latest version.

Another example. The Opera web browser is not in the Ubuntu repos. But you can add the Canonical third party repo that will allow you to install Opera.

---

### Post by limac on 2007-10-28
ok so where is the third party repos usually located??

Thnx a lot so far

---

### Post by FuturePilot on 2007-10-28
They are all over the place. Usually you can find one (depending on what program you are looking for) by searching Google. Is there a particular program you are looking for?

---

### Post by limac on 2007-10-28
no I'm just wondering.

And I know this is off-topic but do you know what to do when it's said to:

Then download sourcecode:

cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock

And where exactly do we download this. In the terminal? or where?

Thnx so much

---

### Post by limac on 2007-10-28
the simey face is replacing  ": p"(no space between : and p) and then server is shown.

I don't know why the smiley face is shown.

---

