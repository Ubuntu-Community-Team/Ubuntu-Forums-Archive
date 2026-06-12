---
title: "Gusty run away process?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by natman on 2007-10-29
Hi, I am running gusty and sometime the system monitor shows near 100% usage of the processor, and top shows
scrollkeeperup as the thing using the most of the cpu, sometimes its gnash. Any help, i have killed both processes when this happens and it does not effect anything that i can see.

---

### Post by FuturePilot on 2007-10-29
That's interesting because scrollkeeper-up was hogging up my processor once for like 10 minutes. 100% CPU. Then it just went away. I have no clue what I did to make it stop. I don't think I did anything really, it just stopped. What is scrollkeeper-up anyways?

---

### Post by natman on 2007-10-29
Yeah, thats my question, what does scrollkeeper actually do?

---

### Post by mridkash on 2007-10-29
I remember when I installed ubuntu beta, it said "installing scrollkeeper" somewhere while installing and took almost 5 mins.

---

### Post by FuturePilot on 2007-10-29
Ah, here is what scrollkeeper is
> **DESCRIPTION**
       ScrollKeeper is a system for managing document metadata.   Its  primary
       function  is  to  act as a card catalog for documents, keeping track of
       what documents are available, where they  can  be  found,  and  various
       attributes  of  the  documents such as their language, format, subject,
       version, and position in a contents list.  It also manages other  meta&#8208;
       data such as document indices.

       ScrollKeeper  acts  as  a  middle  layer  between applications and help
       browsers.  When applications install documentation,  the  documentation
       is  registered  with ScrollKeeper.  Any ScrollKeeper-aware help browser
       on the system can then access this information.  In this  way,  Scroll&#8208;
       Keeper is a compatibility layer which allows any help browser to inter&#8208;
       face to all the documentation on a system, provided the  package  which
       ships  the  documentation  registers  it  with  ScrollKeeper.   It also
       removes much of the burden from application packagers and help  browser
       developers  by  providing  a standard set of tools and by doing much of
       the work inside of ScrollKeeper.

From the man page.

I'm not sure why it would run away like that though.

---

### Post by joao82 on 2008-04-11
This is the most idiotic program ever! When I search it on Google, all the results are from people complaining it hogs the system, all the way from 2005 to 2007! It's been 3 years and now it's hogging my system...
Here's what shows up when I try to remove this piece of junk:

joao@pc:~$ sudo apt-get remove scrollkeeper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  alacarte apturl bug-buddy capplets-data doc-base fast-user-switch-applet
  gedit gnome-app-install gnome-applets gnome-applets-data
  gnome-control-center gnome-panel gnome-panel-data gnome-session
  gnome-system-monitor gnome-terminal gnome-user-guide gnome-utils gthumb
  gucharmap language-selector nautilus nautilus-cd-burner nautilus-data
  restricted-manager scrollkeeper software-properties-gtk synaptic ubufox
  ubuntu-desktop ubuntu-docs update-manager update-notifier zenity
0 upgraded, 0 newly installed, 34 to remove and 8 not upgraded.
Need to get 0B of archives.
After unpacking 289MB disk space will be freed.
Do you want to continue [Y/n]?

bah...

---

### Post by Izkata on 2008-04-16
Well, here's a crude "fix":

> **thechanklybore said:**
> The only fix I can find is to literally make all of the scrollkeeper binaries non-executable.

sudo chmod -x /usr/bin/scrollkeeper*

It works for me.  No errors thrown during tonight's third attempt at an upgrade, when it went crazy again.

---

### Post by nogasbiker on 2008-07-21
Yep, it is happening on my machine too.  My immediate fix was to renice that thing to the basement to stay out of my way.  After getting tired of hearing my fans run on high, I finally killed the process.


Another clue to its dopeyness:  another process is eating cpu, similarly named:

  scrollkeeper-update -q -p /var/lib/scrollkeeper

Perhaps scrollkeeper doesn't run correctly when it is being updated?

---

