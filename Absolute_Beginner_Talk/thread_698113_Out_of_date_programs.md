---
title: "Out of date programs"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Poga on 2008-02-15
I'm new to Linux and Ubuntu.

     I'm currently using 7.10.  I've run the update manager, and have installed every listed update... yet I've noticed that some of my programs are still out of date.  For example, Pidgin is at 2.2.1 (which was released nearly a month before Gutsy was).  Also, I've installed some programs via Add/Remove that didn't come with Gutsy by default.  These include Ardour and Audacious---both of which are similarly out of date, even though I just installed them recently.  On the other hand, Firefox was automatically updated to 2.0.0.12 (which was released just a few days ago).

     I'm a bit confused.  Am I doing something wrong?  How often does Ubuntu update the repositories?  Also, is there any way for me to update the programs via Add/Remove or Synaptic even if the repositories aren't up to date?

---

### Post by sloggerkhan on 2008-02-15
Most programs won't update to newer versions than the ones at package freeze, particularly if you don't enable backports.

Many applications offer custom repos which get updated much more frequently. (Such as the ones at winehq.org). Look for those if you need the latest version.

---

### Post by jordanmthomas on 2008-02-15
There's distros out there that ARE rolling release, meaning they're always up to date.  This is actually one of the main reasons I left Ubuntu a year ago.

I like to live dangerously.  :)

---

### Post by Poga on 2008-02-15
What do you mean by "package freeze"?

     Also, what are custom repositories, and do they integrate into the system the same way as something would via Add/Remove or Synaptic?

---

### Post by Linux_Man on 2008-02-15
The package freeze is a point in development where no new packages are added, later though patches to fix various flaws are released via updates. As for the repositories, I don't know about add/remove but you would install them via apt-get or synaptic the same way as other software.

---

### Post by sloggerkhan on 2008-02-15
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
may help.

---

### Post by jordanmthomas on 2008-02-15
> **Poga said:**
> What do you mean by "package freeze"?

     Also, what are custom repositories, and do they integrate into the system the same way as something would via Add/Remove or Synaptic?

Package freeze means that at a certain date, the versions of programs that will be in a certain release of Ubuntu are set.  Programs will get security updates (like firefox, but it updates itself I think) but most programs will stay at that same version until the next version of Ubuntu.

Custom repositories integrate into Synaptic and once you have them set up (as simple as adding a line to /etc/apt/sources.list and perhaps importing a gpg key) you'll not even notice they're there.  Wherever you're getting your custom repo from will typically tell you how to add it in.

I haven't personally used it (and thus cannot recommend it), but many people really rave about
[http://www.getdeb.net](http://www.getdeb.net) ,
where you can get up-to-date programs

---

### Post by Poga on 2008-02-15
> The package freeze is a point in development where no new packages are added, later though patches to fix various flaws are released via updates. As for the repositories, I don't know about add/remove but you would install them via apt-get or synaptic the same way as other software.

     Unless I'm mistaken, I think I have a pretty good grasp on installing/uninstalling with Add/Remove and Synaptic.  (I have a general idea of this regarding the terminal, but haven't installed anything using this method so far.)  I tried installing programs via Synaptic, and also using it to simply upgrade ones that were already installed---but they still seemed just as out of date.

     I'm not quite sure I understand the different between Firefox being updated because of patches, whereas a program like Pidgin has not been.  To my knowledge, many of the updates to Pidgin since 2.2.1 have involved security issues as well.

     Also---and I hope this isn't too off-topic---is there a reason why Ubuntu would adopt a package freeze method, rather than supplying up-to-date software?  Even 'stable' out of date software would seem to do more harm than good.

---

### Post by Poga on 2008-02-15
I think part of my question has been answered here:
[http://www.getdeb.net/about.php](http://www.getdeb.net/about.php)

If others don't want to spend time answering my question for fear of redundancy, I understand.  Though I'd be interested to read any additional thoughts or explanations as well.  Either way, thanks.

---

### Post by jordanmthomas on 2008-02-15
> **Poga said:**
> Also---and I hope this isn't too off-topic---is there a reason why Ubuntu would adopt a package freeze method, rather than supplying up-to-date software?  Even 'stable' out of date software would seem to do more harm than good.
It's one of those preference types of deals.  The problem with updating packages as they come out is that a release of a program may have lots of problems that don't make themselves evident until lots of people have used the program.  I don't know if you were around when Ubuntu released a broken xserver package, but it was madness on the forums.  

That said, Arch releases programs as soon as possible into their testing repos and I've actually had very few problems and my system is ALWAYS the latest version.

---

### Post by Poga on 2008-02-15
Thanks for the quick responses.  They did a good job of answering my questions.

     I guess my preference would rely with more up-to-date software, but I can understand some of the arguments that could be made for stability (especially in cases of core programs).

---

