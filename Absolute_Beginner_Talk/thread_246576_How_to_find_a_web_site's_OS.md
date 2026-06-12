---
title: "How to find a web site's OS?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Old *ix Geek on 2006-08-29
This is embarrassing...I'm having a huge brainfart and cannot remember how to find out what OS a web site runs on.  Help, please?! ](*,)

---

### Post by hw-tph on 2006-08-29
Try [searchdns.netcraft.com](http://searchdns.netcraft.com/). In the resulting page you may have to scroll down for the information you're looking for.

Note that any web server admin can suppress the headers or make them appear like the site is running something else so don't take the listed response as a 100% truth.


Håkan

---

### Post by Paul133 on 2006-08-29
Web sites run on OS's? Cool! I love Ubuntu; You learn something new everyday.

---

### Post by Tomosaur on 2006-08-29
> **Paul133 said:**
> Web sites run on OS's? Cool!.

](*,)

---

### Post by asmith3006 on 2006-08-29
Why would you want to know this? Is there any reason other than wanting to hack it?

---

### Post by Old *ix Geek on 2006-08-29
> **asmith3006 said:**
> Why would you want to know this? Is there any reason other than wanting to hack it?
This is one of the most unnecessarily nasty things I've ever had said to me.  If you can't think of a plethora of reasons why one might be interested in the OS certain web sites run on, that's your problem.  Not that you deserve it, but my reason for having asked the question is simple: If the site in question (which has a lot of slowness and downtime) is running on something other than *nix, I'm going to suggest to TPTB that they switch to *nix servers.

To the others who replied with useful info, thank you.  I'm still interested in a command-line method of finding the OS type...and I could've sworn I used to know what that was. :confused:

---

### Post by az_human on 2006-08-29
> **Paul133 said:**
> Web sites run on OS's? Cool! I love Ubuntu; You learn something new everyday.

:-k

---

### Post by kpkeerthi on 2006-08-29
[www.netcraft.com](www.netcraft.com) and look for a text box top left.
EDIT: Didn't see that it was already answered. LOL!

---

### Post by NewWithoutClue on 2006-08-29
```

sudo apt-get install xprobe
xprobe --help; man xprobe

```

Nmap can also help.

Find namp's newest version at [http://www.insecure.org/](http://www.insecure.org/)

Paul

---

### Post by Jerome36 on 2006-08-30
> **asmith3006 said:**
> Why would you want to know this? Is there any reason other than wanting to hack it?

There's plenty of good reasons.  One might be if you want to do a little research about a company you're applying for a job with.  I've been asked in interviews if I've looked at, or researched their site and what not.  You can say "Yes, and I noticed your servers run FreeBSD.  I have a lot of experience with," blah blah blah...

---

### Post by Nytram on 2006-08-30
[QUOTE=Old *ix Geek;1438692]This is one of the most unnecessarily nasty things I've ever had said to me

Sir, you've lived a sheltered life.

Funny how popular this thread is... does it say anything about Ubuntu users... ;)

---

