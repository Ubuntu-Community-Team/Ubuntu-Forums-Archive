---
title: "Is open source safe?"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by Kvark on 2005-06-21
So random people from all over the world who don't even know eachother have added lines of code to open source software. What if someone somwhere added a keylogger to an open source program?

And when I as a user start the synaptic package manager and start putting checkboxes for everything that sounds cool. It's so easy and fun to try lots of random programs I don't know anything about. Is there a risk to get a trojan with all that unknown stuff?

I got a lot of authentication failed messages, should I be worried and cancel, or be calm and go ahead?

I added the universe and the mirrormax.net backports repositories so the questions goes for those too.

Hum, lot of text there. Mostly I just want to know if I can keep trying all the cool programs or if it is possible to get a trojan from the synaptic package manager...

---

### Post by sapo on 2005-06-21
People makes trojans cause they hate microsoft.. i ve been using linux for a looooooong time now... never caught a virus or something like it..

btw.. you should be carefull about non authenticated programs, but as long as its a good rep, i doubt that one thing like a trojan or maybe a virus would pass without nobody noticing it... a lot of people test the programs before puting them to download  :-P 

i m not afraid of installing anything here.. and never had a problem....

And believe me... linux isnt so easy as windows to make those things.. and people who uses linux are more interested in making those things to windows users  :-#

---

### Post by Burgundavia on 2005-06-21
I would be very careful with non-ubuntu repositories. They can contain exactly the kind of software you say. The only non-ubuntu repos I would trust, and only marginally, are the backports ones. 

That being said, all the work on most of these programs is open, so anyone could look for keyloggers/etc. The myth of "anybody can edit" is wrong. Usually, there are 2 groups of people changing the program:

1. The developer(s), usually a small group of people who trust each other
2. The packager(s), who makes any changes necessary to make the program work on that specific distro

Thus, the group of people who actually can add this stuff is pretty small.

There is also the reason of pride. Most FLOSS developers are quite proud of their accomplishments, and thus don't have a vested interest in installing malacious software.

So, it boils down to trust and social factors, mostly.

Corey

---

### Post by jeremy on 2005-06-21
> What if someone somwhere added a keylogger to an open source program?
Someone else somewhere else would take it out.

---

### Post by Kvark on 2005-06-22
thanks for clearing that up.

*goes wild with the synaptic package manager*  :grin:

---

### Post by nocturn on 2005-06-22
[QUOTE=Kvark]So random people from all over the world who don't even know eachother have added lines of code to open source software. What if someone somwhere added a keylogger to an open source program?
[/quote]

This is a scare tactic started by MS.   Most projects have a coordinating team that must approve changes to the source code.  Additionally, the source code is in the open, so it is being inspected by many more eyes then closed software is (making detection of a backdoor more likely).
Remember a year or 2 ago when MS had a breakin into their servers, how do you know that no backdoors were planted there?  How do you know that companies do not deliberatly plant backdoors for their own convienence or by government mandate?

Openness is the key to trust.

> 
And when I as a user start the synaptic package manager and start putting checkboxes for everything that sounds cool. It's so easy and fun to try lots of random programs I don't know anything about. Is there a risk to get a trojan with all that unknown stuff?


Everything that is in main is at least checked by the Ubuntu team (so it should be reasonably safe).  For universe, the case is slightly different, although the source is still available making it easier to detect such changes (and Universe is also controlled by Ubuntu, though less then main).
You can never be sure that software doesn't contain anything malicous, but the probability here is extremely low, much lower in fact then malicous content in commercial software where a producer even benefits from hiding it when discovered (bad press).

> 
I got a lot of authentication failed messages, should I be worried and cancel, or be calm and go ahead?


We cannot answer this without knowing the error messages, the packages in question and the repository they came from.

> 
I added the universe and the mirrormax.net backports repositories so the questions goes for those too.


When you add repositories, or download software of the net, you always put your trust in the packager or site (no matter which software it is).
So for each repo/site, you need to answer that question ("Do I trust this person/site?").

> 
Hum, lot of text there. Mostly I just want to know if I can keep trying all the cool programs or if it is possible to get a trojan from the synaptic package manager...

When you stick to pretty standard repos like main, universe, backports or marillat, I would say yes.

---

### Post by Kyral on 2005-06-22
A resounding YES! Like everyone else here has said, only trust "official" repos, like main, universe, multiverse, and backports (okay, backports isn't official, but its safe as far as I'm concerned). If you feel like you want to use another repo because they may have things that these don't (unlikely) at least use the ones from like KDE, GNOME, Enlightenment, etc, 'cause these are also the official repos from those groups, and not likely to be tainted.

---

