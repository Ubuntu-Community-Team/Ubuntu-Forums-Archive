---
title: "What is .ICEauthority ???"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-30
What is all the fuzz about this .ICEauthority file and why does it cause problems to some people sometimes?

---

### Post by T700 on 2006-07-01
It is a file that coordinates some basic security and function permissions.  It can be damaged to a point where it is impossible to log on normally.  Most famously, this can happen by launching a graphical application using sudo instead of gksudo (or kdesu with KDE).  While it will not cause a problem with every graphical app or even every time, it is a real concern.

Paul

PS.  Have you really posted 1081 times in less than four months?  Wow; I'm quite the slacker!

---

### Post by user1397 on 2006-07-01
[quote=T700]It is a file that coordinates some basic security and function permissions.  It can be damaged to a point where it is impossible to log on normally.  Most famously, this can happen by launching a graphical application using sudo instead of gksudo (or kdesu with KDE).  While it will not cause a problem with every graphical app or even every time, it is a real concern.

Paul[/quote]ok thank you so much, I'll never start graphical apps in the terminal without gksudo!!!

[quote=T700]PS.  Have you really posted 1081 times in less than four months?  Wow; I'm quite the slacker![/quote]yep I have!  though that does not mean im an expert of any sort, I find myself learning new things every day! (i'm still a "noob")

and P.S. how did you know I posted that many times?  i chose to hide my beans!!!

---

### Post by woedend on 2006-07-01
T700 - i've heard similar claims and don't necessarily doubt the validity of the statement, but what exactly causes this?  naturally running graphical apps with sudo itself does not, I've done it a million times.  Is there a specific routine that changes this permission?

---

### Post by aysiu on 2006-07-01
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) explains a bit.

For some examples of it happening, here are a few that Google search for *sudo iceauthority* turned up:
[http://www.ubuntuforums.org/showthread.php?t=181867](http://www.ubuntuforums.org/showthread.php?t=181867)
[http://www.linuxforums.org/forum/misc/30916-how-find-what-changing-ownership-iceauthority.html](http://www.linuxforums.org/forum/misc/30916-how-find-what-changing-ownership-iceauthority.html)
[http://www.scoopal.com/node/19](http://www.scoopal.com/node/19)
[http://www.linuxquestions.org/questions/showthread.php?threadid=274995](http://www.linuxquestions.org/questions/showthread.php?threadid=274995)

---

### Post by Rui Pais on 2006-07-07
Hi,
i was thinking to start a thread on this subject when i found this one, so i'll bumped.

I remember read somewhere that the .ICEauthority file loose is permitions to root was considered a bug on gnome 2.6 (or 2.8, don't remember exactly...) and that was solved on the next gnome version. (Don't know, of course, if thats true) 
I got that problem looong time ago (when i used FC2) but never get one on any ubuntu from warty to dapper neither on any gentoo (i use both distros). I use exclusively sudo and don't get that kind od problems, as i said since FC2... and never even read about it until i read it hear, on Ubuntu Forum.

I search this forums for .ICEauthority (thats how i find these one) but at least the first ten or so of the threads only point to people suggest that. None show me that the thread starter solved the problem or even had any problem with .ICEauthority permitions.

I read the links that aysiu points, but they don't give any info on that. The [main one]("http://www.psychocats.net/ubuntu/graphicalsudo") its essencially a personal opinion from psychocats's page author. Some of the links there are dead, namelly one that most interested me refers a "full discussion on the issue" (that seems to point to same page on arch linux servers from Feb 2006 but not available anymore...) 
Btw, i get the reasons why gksudo firefox are diferent from sudo fiirefox, but i dont see the point in discussing gksudo vs sudo on that specific case, the point should be why start firefox as root powers? And/or the dangerous of starting GUI apps as root...

Can someone, please, point to some more technical discussion of the question? Or something that demonstrates that there is indeeed any real problem with sudo GUI stuff?

TIA.

---

### Post by aysiu on 2006-07-07
Thanks for notifying me about the dead link. I've changed it to point to the Google cache of that page.

One of the links is from May 2006. The other is from February 2006. I consider those pretty recent.

The only opinion I expressed was that we should recommend *gksudo* or *kdesu* for all graphical apps to send a consistent message of good practice. The rest is all factual--in a lot of cases, *sudo* with a graphical application will cause no harm, but, in some cases, it does. Why risk it? Just do what you're supposed to.

As for other links... unfortunately, I've searched around, and I haven't found any discussions more technical than what I've presented. All I know is that sometimes running *sudo* with a graphical application will screw up permissions or ownership for user configuration files, so it's best not to use it, except for terminal applications.

By all means, if you find some authoritative links on *sudo* v. *gksudo* please let me know, and I'll post it on the Psychocats page.

---

### Post by richbarna on 2006-07-07
> **aysiu said:**
> Thanks for notifying me about the dead link. I've changed it to point to the Google cache of that page.

One of the links is from May 2006. The other is from February 2006. I consider those pretty recent.

The only opinion I expressed was that we should recommend *gksudo* or *kdesu* for all graphical apps to send a consistent message of good practice. The rest is all factual--in a lot of cases, *sudo* with a graphical application will cause no harm.

By why risk it? Just do what you're supposed to.

I agree completely. I've already corrected two posts today. I think that some of the guides that the new-users are reading should be changed as well. 
And what's more, I was talking to one of my teenage student's computer teachers about sudo and gksudo and ice, and he told me that he knew nothing of the problem.
This guy get's paid to teach linux to new users.
I also heard that he was telling them to login as root as well.

---

### Post by Rui Pais on 2006-07-07
Thanks for a your so quick answer aysiu.

Yes, my problem is that 90% of the time one gives a suggestion on any problem on the forum need to advice sudo or gksudo (and some times the person who have problems can't even understand the difference.) So I want to know better the issue. I find myself weird advice something that i don't use or have any problem with.

The links you point refers a thread that someone suggest that that was the problem, but no answer from the person with the problem and two threads of people usinf old Fedoras from last year. Sorry, as i said have that problem with old FC too. But i don't see it anymore. Just like too know if someone can point me to some bugreport of that problem or some more detailed discussion.

Anyway, here, i started to advise people using gksudo, but, sorry, i'm felling in absolute that i'm just contributing to spread an unfundamented rumor...

Rui

---

### Post by aysiu on 2006-07-07
Well the Ubuntu book that's out (the only currently available one) uses *sudo* for graphical applications in all its examples.

I think it's just legacy. People see it, so they recommend it (I know I did). And **most** of the time, it's harmless.

If you do ```
sudo gedit /etc/apt/sources.list
``` your ~/.ICEauthority file isn't going to be *chown*ed.

But I, for one, am not going to keep an updated list of commands that will affect .ICEauthority and commands that don't.

---

### Post by aysiu on 2006-07-07
Here's one bug report:
[http://lists.debian.org/debian-qt-kde/2005/11/msg00349.html](http://lists.debian.org/debian-qt-kde/2005/11/msg00349.html)

I'll look for others.

**Edit**: [Here's](http://www.scoopal.com/node/19) another instance of *sudo* with a graphical app messing up .ICEauthority > My monitor has come back. It had exploded and gone for repair. So, I had been using my older and smaller monitor for a few days. But that doesnt stop me from fiddling around. Tatha wanted me to sniff out his IP. Not wanting to break the "never take the name of root in vain" rule, I used sudo to run the programs that I needed.

My monitor came back in the middle of this. So, I had to shutdown. Upon rebooting I got the mushy feeling that you get when looking at a brand new monitor rendering a Gnome login prompt in front of a bunch of Windoze users. I typed in my username and password, but got kicked out of Gnome before 10 seconds as the .ICEauthority file was not accessible.

I logged into a terminal. A brief

ls -l .E*

revealed that the file was owned by root. I remembered that I had encountered some errors while running a KDE applet in Gnome with sudo. So, I did what came first to me,

sudo chown sayanchak:sayanchak .ICEauthority

and logged out of the terminal. The rest went smoothly.

Lesson learned: Dont run KDE applets in Gnome with sudo. In fact dont run any graphical application with sudo. Just start a root terminal and run it from there if you dont want the user's .ICEauthority file to be locked up.

---

### Post by raptros-v76 on 2006-07-07
one bit of evidence that sudo does things differently is this
theres this kde app called netgo, that needs to be run with root
now, when i do sudo netgo, it starts up with the color scheme for MY USER. not with the root scheme, which i left default. but when i do kdesu netgo, the color scheme is the root one.

---

### Post by aysiu on 2006-07-07
> **raptros-v76 said:**
> one bit of evidence that sudo does things differently is this
theres this kde app called netgo, that needs to be run with root
now, when i do sudo netgo, it starts up with the color scheme for MY USER. not with the root scheme, which i left default. but when i do kdesu netgo, the color scheme is the root one.
Thanks for that, raptros. It's not just Firefox.

---

### Post by Rui Pais on 2006-07-07
> **raptros-v76 said:**
> one bit of evidence that sudo does things differently is this
theres this kde app called netgo, that needs to be run with root
now, when i do sudo netgo, it starts up with the color scheme for MY USER. not with the root scheme, which i left default. but when i do kdesu netgo, the color scheme is the root one.

Hi, 
yes things behave differently. No doubt about that. 
The link on previous posts of aysiu gives a good explanation of why.

The point was that if some GUI apps launched with sudo instead of quiet recent gksudo (or kde equivalent) will mess with permitions of the file .ICEauthority.
That was a known source of problems on the past. 
And maybe still is nowdays. I just ask for confirmation on that or a mention of a specific know case that happens.

[QUOTE=aysiu]But I, for one, am not going to keep an updated list of commands that will affect .ICEauthority and commands that don't.[/QUOTE]

No, of course, thats not the point to any user collect such a list :lol:
But one of the important things of Open Source *is* report bugs. So if an app do mess with permitions launched with sudo, that should immediattly be reported as a serious bug. Not deal with broken things is only asking for trouble. 

Thanks for the links. (You are quick!) I still haven't find nothing that convince me. 
I will continue to advice people on gksudo use but, i confess, just because that seems to be the preferred approach.

---

### Post by aysiu on 2006-07-07
Well, what I have seen evidence of is *sudo* with graphical apps changing ownership of certain config files.

You're right, though--no hard evidence of it affecting the .ICEauthority file in particular. Circumstantial evidence only on that one.

Nevertheless, it is good practice to use *gksudo* or *kdesu* for graphical apps, regardless of whether they affect app-specific configuration files or the .ICEauthority file. If only to just stop people from *ever* typing ```
sudo kate
``` it should definitely be considered a best practice.

I don't particularly consider the misuse of a command to be a bug, though. *gksudo* is made for graphical apps. *sudo* is not. So if *sudo* is used with graphical apps, and things get screwed up... that's not a bug. That's bad training.

It's like saying that most of the time when you use a hammer to pry out a screw that it pries out just fine and that it's a bug when the hammer accidentally rips the top off the screw. If you want to take a screw out, use a screwdriver. Just because a hammer works most of the time doesn't make it the right tool for the job.

---

### Post by Rui Pais on 2006-07-07
> **aysiu said:**
>  *gksudo* is made for graphical apps. *sudo* is not.

Sorry, i don't understand. Isn't that purely optional?
If i have a box with only fluxbox or enlightenment i don't even have gksudo...


edit: And if sudo <anyapp> change permition of a file that is a bug. It's not suppose to happen.

---

### Post by aysiu on 2006-07-07
> **Rui Pais said:**
> Sorry, i don't understand. Isn't that purely optional?
If i have a box with only fluxbox or enlightenment i don't even have gksudo...


edit: And if sudo <anyapp> change permition of a file that is a bug. It's not suppose to happen.
Well, everything's optional. If you have only Fluxbox or Enlightenment, there are a lot of things you'll be missing, and one will be launching graphical applications as root. *sudo* is a flimsy workaround, just like a hammer when you don't have a screwdriver.

It's like how if I install only IceWM, I use the terminal (instead of the run dialogue) to run commands. I don't have a run dialogue. Yes, things can be run from the terminal, but that's not the ideal... because when you close the terminal, the app closes, too.

If you think it's a bug, report it. In the meantime--until they make it so that every single application that launches with *sudo* uses the root configuration files and not the user ones... I will continue to urge people to use *gksudo* and *kdesu* for graphical applications.

---

### Post by Rui Pais on 2006-07-07
> **aysiu said:**
> Well, everything's optional. If you have only Fluxbox or Enlightenment, there are a lot of things you'll be missing, and one will be launching graphical applications as root. *sudo* is a flimsy workaround, just like a hammer when you don't have a screwdriver.

It's te first time i heard that sudo is a workaround.

> It's like how if I install only IceWM, I use the terminal (instead of the run dialogue) to run commands. I don't have a run dialogue. Yes, things can be run from the terminal, but that's not the ideal... because when you close the terminal, the app closes, too.

Thats what should happen to any app with adimnistrative powers. To be closed as far as possible.

> If you think it's a bug, report it. 

That was my point. Whats to report?

---

### Post by aysiu on 2006-07-07
> **Rui Pais said:**
> It's te first time i heard that sudo is a workaround. Well, for graphical apps, it is. That's what *gksudo* is for--for graphical apps.

> Thats what should happen to any app with adimnistrative powers. To be closed as far as possible. I'm not sure I follow you.

> That was my point. Whats to report? What's to report--you think *sudo* has a bug. Where to report it I think is what you're really asking.

[https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu)

By the way, apparently, there's at least one other way you can change the ownership on the .ICEauthority to root, but most of these situations involved some kind of non-kosher sudo-ing.
[http://www.ubuntuforums.org/archive/index.php/t-1583.html](http://www.ubuntuforums.org/archive/index.php/t-1583.html)
[http://www.redhat.com/archives/fedora-list/2004-March/msg02827.html](http://www.redhat.com/archives/fedora-list/2004-March/msg02827.html)
[http://lists.debian.org/debian-kde/2005/08/msg00079.html](http://lists.debian.org/debian-kde/2005/08/msg00079.html)
[http://www.kde-forum.org/post/46960/ICEauthority-keeps-going-back-to-root.html](http://www.kde-forum.org/post/46960/ICEauthority-keeps-going-back-to-root.html)
[http://forums.scotsnewsletter.com/lofiversion/index.php/t9048.html](http://forums.scotsnewsletter.com/lofiversion/index.php/t9048.html)

---

### Post by Rui Pais on 2006-07-08
Hi, 
thanks for your thoughts and concerns.

Bye.

---

