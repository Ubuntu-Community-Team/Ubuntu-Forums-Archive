---
title: "Random window closeing"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by avidsensei on 2006-09-24
i keep getting windows that close randomly.

mainly gaim but occasionally firefox or openoffice. you can immagine how fusteration this is working on something and then the window closes out and you lose all your data. anyone know a sloution to this problem?

---

### Post by kidders on 2006-09-24
Hi there,

Are you talking about windows closing or _applications_ closing? If it's the latter, they're probably crashing. Can you post any of the associated system messages?

---

### Post by avidsensei on 2006-09-24
i suppose that it is applications closeing.

there are no messages, its just like someone hits the x button

---

### Post by lonce on 2006-09-24
My swiftfox does that lately, but I have narrowed it down to one website that is doing it.

---

### Post by kidders on 2006-09-24
There must be *some* kind of message ... are you sure none of your system logs report *anything* after your app closes?

In the absence of any information to the contrary, let's imagine your programs are segfaulting. That would mean you either have a hardware failure (eg bad RAM) or a software bug. If (like lonce) you can identify specific conditions under which the problem occurs, the application's developers would probably appreciate a bug report.

If you can provide any further detail, I might be able to be more ... well ... helpful :-)

---

### Post by avidsensei on 2006-09-24
ok gaim is the most common crasher.
where would a log file be for it?

---

### Post by kidders on 2006-09-24
> **lonce said:**
> My swiftfox does that lately, but I have narrowed it down to one website that is doing it.

Hi there,

If you'd like to, you could investigate things a bit further. See what your system logs say, and then maybe take a look at the following:

Is the website crashing your browser on purpose?
Does the bug have more to do with your flash/java plugin than the browser itself, maybe?
Does the page behave itself in other browsers?

Depending on what you discover, perhaps there is a way you could use your popup blocker or cookie security settings, etc. to prevent the problem from arising.

---

### Post by kidders on 2006-09-24
> **avidsensei said:**
> ok gaim is the most common crasher.
where would a log file be for it?

Well, I'd check my dmesg and my system messages log from /var/log first. I'm not sure gaim keeps logs of its own (but I'm open to correction on that).

**Edit:** Are you using a beta version of Gaim?

---

### Post by avidsensei on 2006-09-24
no it is not a beta version, it is what installed with ubuntu.
there is an aweful lot of files in there im not sure which ones to start reading

---

### Post by kidders on 2006-09-24
Take a look at the end of the output of the "dmesg" command first. /var/log/messages contains a little more information though. The names of your system log files should give some indication as to their purpose ... see what you think might be relevant :-)

If an application crashes, it usually makes *some* sort of effort to say why. The trouble is that there is so much system information to wade through, important things can be hard to spot. If you can't find what you need on your own, I could take a look for you, if you'd like.

**Edit:** Do not post entire log files on here though ... they may reveal sensitive information!

---

### Post by avidsensei on 2006-09-24
to be honnest i have no idea what im looking for, i know there is a remote connect feature in windows. im sure ubuntu has something similar?

---

### Post by dmizer on 2006-09-25
do this:

open a terminal and type: gaim

then hit enter and run gaim until it crashes.  there will be a short little error output after this happens.  post that.

---

### Post by kidders on 2006-09-25
That's a great suggestion, thanks :-)

If I run an app with a terminal attached, and crash it on purpose, I get nice messages.

avidsensei: If finding out *why* your app is crashing proves difficult, it may not be that important anyway. I asked for the information because, on occasion, there can be a simple explanation for the problem.

---

