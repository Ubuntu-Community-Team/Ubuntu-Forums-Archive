---
title: "BUILDING A PowerPC??"
date: 2015-01-17
forum: Apple Hardware Users
---

### Post by ravish2 on 2015-01-17
[FONT=Helvetica Neue]HI all,[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]I am a student from India and have been entrusted with task of designing a PowerPC based PC for a project.[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]I am a noob in this area and would require the help of gurus here to build it from scratch.[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]Please advice me on the same. Basically i need help in following areas :-[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]1. Understanding how does a Processor interacts with hardware i.e. how to program processor to take input from user. Will I have to learn assembly language or i can do it with C++?[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]2. How will i interface various hardware devices with PowerPC processor?[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]3.  Deciding on which Processor to choose and thereafter choosing its compatible hardware.[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]Please guide me and show me a path.[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]Waiting eagerly for your response.[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]Regards,[/FONT]
[FONT=Helvetica Neue]Ravish[/FONT]

---

### Post by TheFu on 2015-01-18
Dude - that is asking a computer engineering question to a bunch of software weenies.  I've been in IT and software and infrastructure architecture for over 25 yrs and wouldn't know where to begin to answer a question like that.  I suspect anyone who could won't be here. Entire textbooks have been written on each one of those tasks, individually.

If you don't use an existing, well-known, computing architecture, then you'll have to port any software tools over to your new system - all of them. This is not a small task.

Whether you can use C++ or not will mostly depend on how much RAM is in the system. If it is RAM constrained, a micro-C compiler might be all you can use, since C++ will add bloat to any software.

I think you should go and talk to your computer engineering adviser and ask for help. What is the budget for this? How many will you be making? How much time do you have?  Why PPC and not ARM (lower power) or MIPS or Intel? Those answers will lead to other core design considerations.

What is this to be used for?  Industrial machine management?  Desktops? Servers?  Door lock controls?  A worthless machine?
[https://www.youtube.com/watch?v=3il5xS-pnOk](https://www.youtube.com/watch?v=3il5xS-pnOk)  Enjoy.

---

### Post by ravish2 on 2015-01-18
Thanx TheFu for a quick reply :)

BTW..that video was hilarious :D

I need to build this machine for Real Time Processing of acoustic signals....No constraints whatsoever.

Can u suggest me some good processors to begin with which i can use for this?

[COLOR=#262626][FONT=Arial]Can I use multiple processors? If yes, then how to go about it??[/FONT][/COLOR]

[COLOR=#262626][FONT=Arial]How will i make multiple motherboards interact....and in which protocol/format??[/FONT][/COLOR]

[COLOR=#262626][FONT=Arial]My questions might be wrongly framed or my understanding of concepts may be off guys...am sorry for that and please bear with me.[/FONT][/COLOR]

[COLOR=#262626][FONT=Arial]Thanx a lot.[/FONT][/COLOR]

[COLOR=#262626][FONT=Arial]Regards[/FONT][/COLOR]

---

### Post by TheFu on 2015-01-18
Yes, that was a funny video.  My nephew got a simpler version of that box for Xmas last year. He had to assemble it to see it work. ;) He was highly amused.

Since I am not a computer engineer, I am completely outside my depth. Sorry.  Want to design an airplane or write GN&C code for spacecraft - call me. ;)

There is lots and lots of different types of acoustic processing. If it is highly specific, using a specialized chip would be better, cheaper, faster to deploy - look through the TI and Samsung catalogs.

Did a google search .... [http://defense.ge-ip.com/products/axislib-ppc/p3581](http://defense.ge-ip.com/products/axislib-ppc/p3581) came up. Doubt that is useful.

I've only seen PPC directly used in IBM AIX servers. Sorry. I'm unsubscribing. Way outside my knowledge, clearly.

---

### Post by este.el.paz on 2015-01-23
Just adding my $.02 . . . as TheFu says, this site is about getting ubuntu to run on apple hardware, but as someone who is interested in keeping PPC "on the radar" . . . I would suggest that you could probably find and buy a PPC computer for not too much money . . . and then "study" it . . . in vivo, or, in vitro . . . .  The AmigaOne series seems to be an extant PPC line, and that may be more money . . . but the Apple PPC options are likely "unsupported" and or "obsolete" . . . and depending on what you want or are willing to spend, you could have many choices--from "free" to "cheap" . . . .

Over on the Apple Discussion forum is the "OSX Technologies" sub-forum, you **may** or **not** be able to get some response there . . . there are less people even willing to talk about PPC these days . . . but, really the motorola processor is just fine . . . .

e.e.p.

---

