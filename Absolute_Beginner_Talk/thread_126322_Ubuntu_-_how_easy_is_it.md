---
title: "Ubuntu - how easy is it?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by IanWright on 2006-02-06
Hey everyone, I was just looking for any suggestions. I've never used Linux before, (except for installing SuSe once, and removing it again right after because I didn't know what I was doing!), but I have to use it shortly for my Uni project.

I need to use something called Netem, which it looks like I can control from a command line, later I need to program a GUI to interface with this somehow.

Well, what I want to know is whether Ubuntu is going to be easy to use to do this in? I had 1 person recommend it, but many others recommend Gentoo. Also, if I do install it, assuming I've got a network set up with it, can I then just go straight to a command line and start tapping in Netem commands for it to work, or do I have to set lots of other things up first?

I'm just wondering how long it'll take me to get a working system before i can start my project really. Also, I notice theres a Gnome and KDE? interface if I remember right, are either any easier to program GUI's for?

Any help is much appreciated! Thanks :)

---

### Post by Leo_01 on 2006-02-06
Ubuntu got a real small learning curve and it got a great and friendly forum!
i suggest ubuntu to all new linux users...

---

### Post by kabus on 2006-02-06
It doesn't sound like Gentoo is what you want. 
Ubuntu might be a good choice because it gives you a usable desktop out of the box.
You migh want to check first if all the specialist software you need is available from the repositories (otherwise installation can be a bit of a hassle) :

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Klaidas on 2006-02-06
Well, I am a begginer so far. I have tried out Mandriva, SuSE, Baltix, Gentoo, Kubuntu and Ubuntu. 

I find Ubuntu the best so far  and I recommend it :)

---

### Post by firehead on 2006-02-06
well i'm using kubuntu (which is just the kde-version of ubuntu) and it really is quite easy to use (easier on a desktop than on a laptop...depending on the type of laptop).
i wouldn't recommend gentoo either, because it's quite a lot of "hand-work" to install...maybe too much for a beginner (including me ;) )
[QUOTE=IanWright]Also, if I do install it, assuming I've got a network set up with it, can I then just go straight to a command line and start tapping in Netem commands for it to work, or do I have to set lots of other things up first?[/QUOTE]
Netem is already enabled in modern kernels (i.e. it is enabled in (k)ubuntu). you can just go to a console and start using netem with the command line tool 'tc' (but i don't know anything about any of these...sorry)
[QUOTE=IanWright]Also, I notice theres a Gnome and KDE? interface if I remember right, are either any easier to program GUI's for?[/QUOTE]
sorry,can't help you about that, but i guess they are quite similar...

---

### Post by annsachd on 2006-02-06
I have used just about all the distros and this is the best by far.

I've gotten just about everything working within a week and haven't put too much effort into it. 

The peope here in the forums are amazing. Friendly and really know their Ubuntu. 

BTW Gentoo can be a waste of time waiting for things to compile/recompile. Different philosophy over there.

Good luck with whatever you choose.

---

### Post by Ulysses on 2006-02-06
I surfed and I surfed and I surfed some more. I tried to download the software free (like they encourage you to do) and I couldn't burn the image onto a CD. Figuring that MS might have built some ultra-secret component into their download protocols (ignoring the fact that I am a complete idiot / that was not an acceptable explanation and not altogether believeable..ahem) I went to the ubuntu homepage and got them to send me 5 copies of the live and install CDs for free (I gave a donation to the cause though and have handed out 3 of the 5 copies for my friends to use).
My install started with me spending 1 week archiving all of my important data on CDs.
My install notes go like this
1/28/06
Howth Castle and Environs - erased 'entire' harddrive - may God have mercy on my soul
*20th anniversary of the challenger explosion/disaster
2:47PM @ 37% installing base system - thought it stalled. Scared me a bit
Name, user, password / standard stuff
Went about cleaning my basement. Found old, old, OLD floppies with old, old, OLD info on them that could be retrieved
4:13PM
EFFORTLESS install
Email is not working (I used stronger language in my notes) but I can fix that
Tried to recover data from 10y old disks and ubuntu not doing it
*actually, it managed to after all. Not bad. Had to learn what 'mount' and 'unmount' meant. Had to keep from giggling each time I mounted and unmounted anything on the desktop.
6:12PM
Spent time with my wife.
Came back downstairs. Ripping Prince's "Purple Rain" to the computer

The only problem I'm having is that I went out and bought a new, cheap printer (strictly for text and for printing to cue cards for my filing system) and I can't find a driver that works for it. It's a Lexmark Z730 if anyone can provide any kind of help. Really hate to take it back.

RAR

---

### Post by JeffV on 2006-02-07
Ubuntu is the second Linux I've tried, the first being Fedora Core 4.  I think Ubuntu is a lot easier and am completely hooked.  It's especially easy if you follow people's advice on the forums.

---

### Post by mips on 2006-02-07
[QUOTE=IanWright]Hey everyone, I was just looking for any suggestions. I've never used Linux before, (except for installing SuSe once, and removing it again right after because I didn't know what I was doing!), but I have to use it shortly for my Uni project.

I need to use something called Netem, which it looks like I can control from a command line, later I need to program a GUI to interface with this somehow.

Well, what I want to know is whether Ubuntu is going to be easy to use to do this in? I had 1 person recommend it, but many others recommend Gentoo. Also, if I do install it, assuming I've got a network set up with it, can I then just go straight to a command line and start tapping in Netem commands for it to work, or do I have to set lots of other things up first?

I'm just wondering how long it'll take me to get a working system before i can start my project really. Also, I notice theres a Gnome and KDE? interface if I remember right, are either any easier to program GUI's for?

Any help is much appreciated! Thanks :)[/QUOTE]

Ian,

Easy is a relative term and depends on experience, technical aptitude, mindset etc.

Having said that Ubuntu or Kubuntu is not 'the' easiest distro out there but in the same breath it is not the hardest either. I would rate it more on the easier side. The plus in Ubuntu's favour is the amount of support available and there I would rate it tops.

You should have a fully working system within about 30mins. You 'might' experience some hardware incompatibilities but those can be sorted out. 
I take it you will be doing a dual-boot Windows/Linux install ?

Wiki page- [http://linux-net.osdl.org/index.php/Netem](http://linux-net.osdl.org/index.php/Netem)
Author- [http://developer.osdl.org/shemminger/](http://developer.osdl.org/shemminger/)

Netem is installed by default in (K)Ubuntu so you dont even have to do anything in that regard. I just tested it and managed to delay the output of my ethernet interface by 100ms, only problem is I dunno how to turn it off :rolleyes: 

Do you have to write your own GUI ? Can you not use something existing that is GPL'd ???
[http://www.smyles.plus.com/phpnetemgui/](http://www.smyles.plus.com/phpnetemgui/)

As for the KDE(Kubuntu) vs Gnome(Ubuntu) thingy I suggest you maybe ask in the programming section or the developer channel on IRC. 
From what I've read kdevelop&Qt looks pretty good on KDE.

[http://developer.kde.org/](http://developer.kde.org/)
[http://developer.kde.org/tools/](http://developer.kde.org/tools/)
[http://developer.kde.org/policies/](http://developer.kde.org/policies/)

You might even get away with a scripting language.

Some additional info.

---

### Post by IanWright on 2006-02-07
Thanks very much for all the sugggestions so far guys, think I'll try it see what I think, and I'm intending to have a read up on the Gnome and KDE differences.

Thanks for all those links mips, pretty useful. Unfortunately I do have to write a new GUI, its going to be for very very non technical people as a demonstration set up, so they won't even know what packet loss is :P

I'll try posting in the programming section, so far QT has been suggested by a friend, so it looks like I might be using that option.

I'm sure I'll be posting soon, with many questions when I get stuck, but as you say, its a great and very helpful forum.

Thanks again!

Ian W

---

### Post by Robgould on 2006-02-07
If you have ever used VB or VBA, I would recommend using gambas for your GUI....will reduce the learning curve.

---

### Post by Dragonbite on 2006-02-07
Gentoo is great for ***_learning_*** Linux, but is not quite so easy (or quick) to set up and get running for the newbie (even somebody who's installed numerous times ;) ).

I've liked using Ubuntu because with little effort I got it up and running (hardware detection is great!) and had a system running and installed at least 2 new programs in less than 5 hours!

---

### Post by mips on 2006-02-07
[QUOTE=IanWright]Unfortunately I do have to write a new GUI, its going to be for very very non technical people as a demonstration set up, so they won't even know what packet loss is :P
[/QUOTE]

Lol, that kinda seems like a waste of valuable time/resouces.

---

### Post by Janzuka on 2006-02-07
The basic functions in Ubuntu using GNOME are easy to learn. When i started using Ubuntu as my first linux distro about two months ago, i rapidly learned to use the basic functions,but when a problem occures or i can't figure out something by trying and reading forums, i go to ubuntuforums.org to ask for help, and every problem i've had, has been solved.

---

### Post by IanWright on 2006-02-08
Part of a University project mips, to demonstrate communication links and the various effects in a practical way that people can understand (video streaming) for non technical users, or for students who are just moving into the field of communications.

---

