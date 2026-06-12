---
title: "[SOLVED] Brand new iPod Classic won't work &amp;amp; I broke packages(?)"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Mega_Fauna on 2008-02-29
Hi,

I think I broke a few packages screwing around here.

I've spent the past four hours trying to get my brand new (this morning) 80gig iPod classic to work with Amarok or do anything other than mount, and I can't do it. Can someone help please.

Details:

1)     Have followed these instructions: [http://ubuntuforums.org/showthread.php?t=619615](http://ubuntuforums.org/showthread.php?t=619615)
        Problem: step 4 gives me this.

```
]user@user-desktop:~/Desktop/libgpod-0.6.0$ sudo apt-get install build-essential libglib2.0-dev libgtk2.0-dev libsgutils1-dev checkinstall
Reading package lists... Done
Building dependency tree      
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.14.1-1ubuntu1) but 2.15.6-0ubuntu2 is to be installed
E: Broken packages
```

Things go downhill from there, if someone can get me past this first step, then I'll try again. I had gone past this step earlier as this is a new error, previously make wouldn't run because apparently I was missing packages which are (I think) part of GTK+ and Gnome 2 but I can't figure out how to install them. 

I used a .deb to install libgpod-0.6.0 which may be part of the problem.

Thanks, at my wits end.

---

### Post by finer recliner on 2008-02-29
i just bought an 80 gig classic ipod (black) yesterday as well :)

i tried that tutorial, and after much frustration, i gave up to find another solution.

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

^this tutorial was much easier to follow, and worked for me.

remember to uninstall and reinstall amarok. possibly restart the computer before running the ipod-read-sysinfo-extended command.

enjoy

---

### Post by Mega_Fauna on 2008-02-29
Hi,

Thanks for the tutorial but I think I've screwed up my packages so I can't install anything yet. But when things are fixED, I'll try your tutorial over the previous one.


When I try to install libglib2.0-dev or releated packages I get the following error:

[INDENT][B]libglib2.0-dev:
  Depends: libglib2.0-0 (=2.14.1-1ubuntu1) but 2.15.6-0ubuntu2 is to be installed[/B][/INDENT]

Note: I've tried the fix packages thru synaptic, it hasn't worked yet.....

---

### Post by Mega_Fauna on 2008-03-02
[UNHAPPY AND UNWANTED SOLUTION]

Screwed up packages that can't be fixed by Synaptic apparently mean a reinstall of Gutsy. Wow. Can't believe that things are so easily and so utterly broken.

---

