---
title: "Welcome to the accessibility forum!"
date: 2006-06-07
forum: Assistive Technology &amp; Accessibility
---

### Post by Henrik on 2006-06-07
With the release of Ubuntu 6.06 we have some basic assistive technology components in place, but there are still rough edges and work to be done. I hope that this new support forum can help new users of Ubuntu get set up with a working system and where needed help work around some of the known limitations in the current offering.

This should also be a useful place to give feedback about where we are at currently and what feature enhancements we need for future versions. More technical discussions about new feature development will likely continue on the mailing list, in the wiki and the specification tracker in launchpad.

And finally, I'd like to thank the forum staff for setting up this forum section for access questions!

---

### Post by matthew on 2006-06-07
Although I do not need any of the accessibility functions let me say that I am thrilled to see it being worked on and even happier to have you here inviting discussion and comments. Welcome!

---

### Post by munch on 2006-06-07
[QUOTE=Henrik]With the release of Ubuntu 6.06 we have some basic assistive technology components in place, but there are still rough edges and work to be done. I hope that this new support forum can help new users of Ubuntu get set up with a working system and where needed help work around some of the known limitations in the current offering.

This should also be a useful place to give feedback about where we are at currently and what feature enhancements we need for future versions. More technical discussions about new feature development will likely continue on the mailing list, in the wiki and the specification tracker in launchpad.

And finally, I'd like to thank the forum staff for setting up this forum section for access questions![/QUOTE]
Henrik -

My father has been using 4.10 - as an emacspeak workstation for about a year now... ubuntu was the easliest of many distro's i attempted to setup - it was one of the reasons that i am now a ubuntu user.

Getting an old man who hasn't typed for many years from going blind at an old age was much harder then setting up the code... (emacspeak & eflite)

---

### Post by linbetwin on 2006-06-08
This forum section is a great idea. I absolutely hate mailing lists!

---

### Post by lizardking on 2006-06-08
good thing! I think accessibility is so important...

---

### Post by vladozan on 2006-06-11
When i was using the MS Windows i was using the Magic software to enlarge my screen and I can't find anything at least from a half as good as that in linux world. What magnifying software would you recommend?

---

### Post by linbetwin on 2006-06-11
[quote=vladozan]When i was using the MS Windows i was using the Magic software to enlarge my screen and I can't find anything at least from a half as good as that in linux world. What magnifying software would you recommend?[/quote]

If you say you can't find anything as good, then you've probably tried gnopernicus (with gnome-mag) and kmag.

Gnopernicus/gnome-mag renders more poorly than kmag, but it can follow keyboard/cursor focus in some applications, something that kmag can't do. But kmag renders images perfectly.

---

### Post by richbarna on 2006-06-11
I have a friend who is blind and also works for a foundation that researches technology for the disabled.

Only yesterday we were discussing the accessibility functions on Ubuntu (from wiki.ubuntu.accessibility).

He currently uses "JAWS" screenreader with Windows Xp and has told me that it is the best software available.

This week I hope to set up a testing partition with Dapper, to give Gnopernicus a try-out.
One thing to bear in mind is that anything designed for blind people by sighted designers is not "accessible" 90% of the time.

I am hoping that I can provide some feed back at a later date.

My question is, Do the Gnopernicus developers have blind people to test their software ?

---

### Post by Henrik on 2006-06-11
Gnopernicus with gnome-mag provides a reasonable basic set of magnifier and screen reader tools, but it's far from great. Fortunately there are new developments on the way. 

You can already install the Orca screen-reader (gnome-orca package) which will be moreflexible than Gnopernicus. See: [http://live.gnome.org/Orca/](http://live.gnome.org/Orca/)

For magnification we are working on a new compiz based system that should greatly out-perform gnome-mag and kmag. See: [https://wiki.ubuntu.com/Accessibility/Specs/compiz-mag](https://wiki.ubuntu.com/Accessibility/Specs/compiz-mag)
[http://www.poweroftwo.de/wiki/index.php/Soc-xmag](http://www.poweroftwo.de/wiki/index.php/Soc-xmag)
[http://www.alphaworks.ibm.com/tech/mcm](http://www.alphaworks.ibm.com/tech/mcm)

Gnopernicus will gradually be replaced with these tools over the next 6-12 months. I'm sure Gnopernicus has had some blind people involved, but i don't know. Certainly Orca was started by a blind coder, now joined by three others. And we have several visually impaired people on the Ubuntu team.

---

### Post by vladozan on 2006-06-11
[QUOTE=Henrik]Gnopernicus with gnome-mag provides a reasonable basic set of magnifier and screen reader tools, but it's far from great. Fortunately there are new developments on the way. 

You can already install the Orca screen-reader (gnome-orca package) which will be moreflexible than Gnopernicus. See: [http://live.gnome.org/Orca/](http://live.gnome.org/Orca/)

For magnification we are working on a new compiz based system that should greatly out-perform gnome-mag and kmag. See: [https://wiki.ubuntu.com/Accessibility/Specs/compiz-mag](https://wiki.ubuntu.com/Accessibility/Specs/compiz-mag)
[http://www.poweroftwo.de/wiki/index.php/Soc-xmag](http://www.poweroftwo.de/wiki/index.php/Soc-xmag)
[http://www.alphaworks.ibm.com/tech/mcm](http://www.alphaworks.ibm.com/tech/mcm)

Gnopernicus will gradually be replaced with these tools over the next 6-12 months. I'm sure Gnopernicus has had some blind people involved, but i don't know. Certainly Orca was started by a blind coder, now joined by three others. And we have several visually impaired people on the Ubuntu team.[/QUOTE]

I triede gnopernicus before i installed ubuntu on hard drive. i experienced a problem of a square where the magnified picture of my screen was, but i had problem when i went with mouse into this square.

i will try the other software and i can share my experiences.

---

### Post by TheMuso on 2006-06-12
[QUOTE=Henrik]Gnopernicus will gradually be replaced with these tools over the next 6-12 months. I'm sure Gnopernicus has had some blind people involved, but i don't know. Certainly Orca was started by a blind coder, now joined by three others. And we have several visually impaired people on the Ubuntu team.[/QUOTE]

Hi all. I am one such vision impaired person involved with the Ubuntu Accessibility team. I have been working on Ubuntu accessibility for well over a year now, and what has been done in that time can be seen in the dapper release.

For those who are curious, I use Linux completely, for everything from web browsing to email, to writing documents. I use the console, and the Speakup Screen Reader with a hardware speech synthesizer. There are plenty of tools available on the console to be able to do the things I do. I hope to be able to use GNOME a lot more one day, as the various screen reading technologies are improved. My biggest hopes lie with Orca, due to its scripting capabilities for individual applications.

Feel free to either email me or privately message me if you have any questions regarding full-time Linux use, and I will do my best to answer any questions you may have.

---

