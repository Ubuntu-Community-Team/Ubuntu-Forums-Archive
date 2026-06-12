---
title: "The &quot;xorg.conf&quot; Well of Despair"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by sbergman27 on 2006-10-01
I couldn't help but notice a few threads which have been active over the last 5 hours:

"Resolution Trauma"
"More resolution woes"
"HELP - Screen resolution"
"Walk me through a screen resolution change"
"KDE. resolution, startup apps"
"resolution problems"
"How do I change my resolution"
"screen resolution problem"

Does this mean something?  RedHat Enterprise Linux, that distro that no desktop user pays attention to because RedHat is "only focused on servers" has "system-config-display", which edits xorg.conf in a user friendly way.  (It's in "Administration". There is another utility in "Preferences" that changes the resolution through XRANDR like Ubuntu's does.)

Yet Ubuntu, the "Linux for Human Beings" has but ongoing desperate threads on the message board.

What's up with that?

---

### Post by Mr Frosti on 2006-10-01
I will have to agree with you here. I have seen several tools, but most are just simple parsing scripts and have wildly unpredictable results. One of the best tools that I have seen is SuSE's SaX2 utility, which lets you configure (and test before saving) every part of the "xorg.conf" file. This is something sorely lacking from Ubuntu as many people end up modifiying the file at some point in time.

---

### Post by TheMono on 2006-10-01
Yes, we know. Mea Culpa, so to speak.

There is certainly work going on, but nothing definite yet.

I still favour the camp that wants to port Sax2 to a GTK+ GUI.

---

### Post by Mr Frosti on 2006-10-01
SaX2, as well as the rest of YaST2 is scheduled to be ported to GTK+ bindings for the release of OpenSuSE 10.2 in December 2006. This would be an excellent opportunity to repackage the SaX2 utility into .deb format for Ubuntu's purposes.

More information can be found here:

[http://en.opensuse.org/YaST2-GTK]("http://en.opensuse.org/YaST2-GTK")

---

### Post by sbergman27 on 2006-10-01
> **TheMono said:**
> Yes, we know. Mea Culpa, so to speak.

An xorg.conf config utility is simply a convenience to me.  I likely wouldn't even use it, myself.  But I look at these desperate pleas for help... and then I look at the public announcements about... Upstart... and I wonder if the "Ubuntu" (caring for fellow man) is being spent in the right place.

Don't misunderstand me, please.  I'm much more excited about Upstart than I am about a boring xorg.conf config facility.

But it is unreasonable to expect new users to just edit their xorg.conf.

---

### Post by skymt on 2006-10-01
One question: Many of these threads are started because people can't start X. What good would a graphical setup utility do them?

---

### Post by sbergman27 on 2006-10-01
> **skymt said:**
> One question: Many of these threads are started because people can't start X. What good would a graphical setup utility do them?

These threads are about changing the *resolution*.  Not about "I just installed Ubuntu and get a black screen".

Fault tolerance when X completely fails is a different topic.  Hopefully the update snafu from a few weeks ago will yield a resolution to the X fault tolerance issue.

---

### Post by UnknownVariable on 2006-10-01
I'm the creator of the "more resolution woes" topic. I did a bit more research on my problem and it seems that I'm editing everything correctly (as far as I know) it's just that my video card is either only partially supported, or I need to edit a bunch of other files, or something. Just a tad confusing :P

---

