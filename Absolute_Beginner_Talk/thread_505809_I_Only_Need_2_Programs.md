---
title: "I Only Need 2 Programs"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-07-20
Hi I have an old Laptop where I only need maximum two programs to run. (nothing more) I need a music application, in this case rhthmbox to stream music, and maybe a browser.

The idea is to use the laptop as streaming audio server and connect it to my speakers, then whenever someone turns it one could be a friend of mine,  girlfriend, or parents it would boot straight into the music app, and the user wouldn't be able to touch anything else.

And then if I (adminstrator) would need a web browser at some point I could run that, but I don't need anything else. How would I go about doing that. Much of it is also to save system memory to make the laptop run faster.

I'm running gnome.

---

### Post by farueulogy on 2007-07-20
Is this what you want to achieve:
[I]
User turns on their computer and from there remotely turns on your computer to access the music stored on it and play it at their end.
[/I]
The first issues is if you need it to be able to be turn on the "server" remotely. I can't think how you'd do that. I always figured servers were always on.

The second issue is audio programs where you can stream out. I know winamp had an interesting feature where you could access your music remotely - But obviously that's no good as it's a windows app unless there's some clever way around that using wine - a windows emulator.

(Don't stress about a browser, any OS worth it's salt will run one and Ubuntu comes with Firefox: the browser preference of many.)

---

### Post by kasperbs on 2007-07-20
> Is this what you want to achieve:

User turns on their computer and from there remotely turns on your computer to access the music stored on it and play it at their end.
Yeah thats pretty much it. Except - don't worry about turning the server on or off. It streamed from my own personal computer so its nearly always on anyway. But yes thats what I need and nothing more, how do I delete everything else in Gnome and minimize the number of processes to only those needed by Rhythmbox?

---

### Post by xpod on 2007-07-20
Depending on how old it is (specs???) you could install distros like puppy,dsl.tinyme or even wolvix..amonst others.

All great little disrtos in their own right although i`d say puppy & Wolvix were a lot quicker on the c600 i have with 128Mb & 700Mhz,great for just a browser and mediaplayer......and remote access of course.

All i need the old Dell for is so my 2Yr old can do her LInux,letters & numbers and her xtartan with her 6 Yr old sisters as well as watching her Twennies & teletubbies vid`s:)

I`ve been watching a minimal Ubuntu installation thread with interest as all i need are the basics too on the ole thing in question

[http://ubuntuforums.org/showthread.php?t=480714](http://ubuntuforums.org/showthread.php?t=480714)

EDIT: i use an nfs share on my main machine to share multimedia with the others on the same network although their all Linux too.
I also use shh to occasionally share with a machine my son uses on a seperate network

---

### Post by farueulogy on 2007-07-20
If you go to

System> Administration> System Monitor> Processes

you can get a look a what's going on. Looking at mine now the majority of items are actually using 0% cpu. I don't think you'd need to slim down the system.

Have you tried running the server idea you've got going or are you still trying to work out streaming?

---

### Post by louieb on 2007-07-20
Easiest way 
1st do server install from alternate CD.
2nd Add minimum  Gnome install
3rd. Add whatever  applications you want. The  update manager will take care of any needed dependencys. 
If you need help with the first two search the forum lots of threads for doing just that.
This is what I used when I set up a P3 433mhz as a test server. [HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")

---

### Post by kasperbs on 2007-07-20
I found this post on [another forum]("http://www.linuxquestions.org/questions/showthread.php?p=2823826") and it sees to be what I'm looking for, wont you agree?

It's just how do I do it, otherwise I have been told not to post anything else than U/Ku/Xu/EDU/buntu stuff here, so otherwise [this one]("http://mail.gnome.org/archives/rhythmbox-devel/2007-February/msg00050.html") looks pretty good as well, I just miss some clues to have I would get started actually doing it.
> Is this what you want to achieve:

User turns on their computer and from there remotely turns on your computer to access the music stored on it and play it at their end.

---

### Post by xpod on 2007-07-20
@louieb

That seems exactly what i was thinking about myself.The small distros are great and all but i like the sound of that minimal gnome idea.
I`ll have a go tommorow mabey...cheers:)

---

