---
title: "How do I install a Netgear FA511 on Ubuntu Server 6.10?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Mortuis on 2006-06-12
I installed Ubuntu Server 5.10 on a thinkpad 770 last year and recently upgraded it to 6.06.  When I installed it, it recognized my wireless PCMCIA card so I never head to deal with what's involved in linux hardware installation.

Today, however, my wireless router crapped out and I want to get the server up and running again until I can afford a new one.  So I pulled a non-wireless NIC out of my windows server (another thinkpad 770) and plugged it into the Ubuntu Server, only to realize I have no idea what to do from here.

I'm a linux newbie, I don't know what files to look at, what my hardware's particulars are, anything.  I've tried googling for about an hour but can't seem to find any information on NIC installation that doesn't involve using some GUI application.  Again, this is Ubuntu Server so I have no graphical environment.

Could anyone help me out here?  Where do I start looking? What should I be googling for?  I don't even know where to begin.

---

### Post by catlett on 2006-06-12
[http://www.ubuntuforums.org/showthread.php?t=125763](http://www.ubuntuforums.org/showthread.php?t=125763) Sorry I don't know anything but this thread may be a good place to start.

---

### Post by Mortuis on 2006-06-13
Didn't think to search hardware help, thanks. :-)

---

### Post by catlett on 2006-06-13
I hope you don't mind but I followed the link in your signature to your blog. While being nosy [-X   I noticed this
> I went ahead and did "apt-get remove" on all of them. I followed this up with an "apt-get install" and got a dependency error. Cute, so I went ahead and installed one at a time and found my problem was with libmysqlclient12-dev, he wanted libmysqlclient12 installed first. So I went to install libmysqlclient12 only to find he was already there. Wanting this problem to go away, I went ahead and removed libmysqlclient12, then installed libmysqlclient12-dev who installed libmysqlclient12 automatically this time. Nice, nice and stupid. But it was working so I wasn't complaining. Just a tip that you may already know, use aptitude instead of apt-get when installing and removing.
Aptitude will resolve dependency issues where apt-get will just say there is a problem. All you do is aptitude install instead of apt-get install.
Aptitude will remove an application, add an application or hold an application back from upgrade to resolve. Simply if you run aptitude instead of apt-get you won't have dependency issues pop up because aptitude will stay on top of it. Also if you end up with a problem, run "aptitude update" and then "aptitude upgrade" and aptitude will go through everything and resolve any issue. Ay least it always has with me.
Just to give you my issue. I use the Debian mutimedia repository. Every now and again an update will come through that will bring on errors from update manager. I run aptitude upgrade and it takes care of it. Usually by holding a package at it's current state. Instead of trying to upgrade it along with the new package which is usually looking to connect with other updated packages.(if that makes sense:eek: )
Sorry this got long. Enjoyed your blog. When you become the next Ori Allen don't forget the little people at the forums.:razz:

---

### Post by Mortuis on 2006-06-14
[QUOTE=catlett]I hope you don't mind but I followed the link in your signature to your blog. While being nosy [-X   I noticed this
 Just a tip that you may already know, use aptitude instead of apt-get when installing and removing.
Aptitude will resolve dependency issues where apt-get will just say there is a problem. All you do is aptitude install instead of apt-get install.
Aptitude will remove an application, add an application or hold an application back from upgrade to resolve. Simply if you run aptitude instead of apt-get you won't have dependency issues pop up because aptitude will stay on top of it. Also if you end up with a problem, run "aptitude update" and then "aptitude upgrade" and aptitude will go through everything and resolve any issue. Ay least it always has with me.
Just to give you my issue. I use the Debian mutimedia repository. Every now and again an update will come through that will bring on errors from update manager. I run aptitude upgrade and it takes care of it. Usually by holding a package at it's current state. Instead of trying to upgrade it along with the new package which is usually looking to connect with other updated packages.(if that makes sense:eek: )
Sorry this got long. Enjoyed your blog. When you become the next Ori Allen don't forget the little people at the forums.:razz:[/QUOTE]

Not at all, blogs are little ego boxes that give you a boost every time another visit is recorded. :-)

I've seen the word "aptitude" used regarding installation, but I guess I just assumed that was some kind of GUI application.  However, wikipedia has just informed me otherwise.  I'll have to check it out once I get my server back on the network. 

Do you use the same package names that are found when using the *apt-cache search* command?  Or does aptitude use a different system?

---

### Post by catlett on 2006-06-14
It uses the same packages. Everything for apt-get works for aptitude. It's just another front end. Put aptitude in the terminal. It looks cool when it comes up. You run it from the command line but aptitude can be called up in a way that is comparable to what "nano" looks like when you edit.
But to the question, aptitude and apt-get use the same packages and aptitude is run from the command line. Although aptitude has a terminal type of interface like nano/vi. I never tries aptitude from the server login. Try it and see if it comes up in a terminal bow. Obviously you can aptitude install from the command line but I'm talking about getting a user interface with aptitude in the terminal. If it pulls up the "window" for aptitude when you enter only the word aptitude from the server login,  that would be the best for you.

P.S. why am I goingh crazy I'll give you a couple of screen shots. Screenshot 1, aptitude command line upgrade. Screenshot 2, aptitude terminal window.

---

