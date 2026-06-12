---
title: "Linux file server"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by flyingmonkey350 on 2006-07-29
Well since this is my first post I'm gonna take a bit of time to say a bit about my self before i get to my problem. Iv been using windows since i was in kindergarten and i will now be a senior in high school. Today was my first time ever running Linux at all so needless to say I'm totally lost. I started with running the desktop program at home and so far i really like it. But my main goal with Linux is to set up a file server. My sister is a teacher and she has problems with kids saving their work and other kids deleting their work. So my plan is to setup a file server in her class. My goal is for each student to have a folder on the file server that is password protected. I want the server to appear as just another hard drive on their computers so the students don't need to learn anything new in order to save their work. In her class she has 16 computers half of which are mac and the other half are running windows xp.

I'm sure ill probably get yelled at for asking this simple question and told to use the search function but i have been searching for over an hour but my problem is i really don't know what i should be searching for.

I have found a old computer in her class that i intend to use as the server so i burned ubuntu server to a CD and installed it on that computer. Needless to say i was a bit shocked when i realised that that the server version has no GUI and I'm greeted with a command prompt. Having never used a command line or Linux i now know what computer illiterate people feel like. I don't even know where to start. I probably do deserved to get yelled at for not searching more but if someone could at least point me in the right direction and give me an idea of what i need to do and where to begin that would be great. Oh and to add to the list of things i don't know how to do i barley know how to use a mac. I'm embarrassed to say that it took me at least 10 min to figure out how to turn it on (why do they make the power button blend in so much on the side of the computer). So i know this is gonna be quite a learned experience, having never used Linux, never made a server, never used a command prompt, and knowing basically nothing about macs also.

Thanks in advanced for any help after browsing these forums i have seen that you seem to be a very helpful bunch

---

### Post by Third Thoughts on 2006-07-30
It sounds like you have quite a task ahead of you. I don't have much experience with server stuff, so I can't talk you through much really, but I can point you to a couple of useful command line references just to get you started.
For a very barebones, glossary of commands check out
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
An incredibly extensive tutorial about everything Linux. This is several days worth of reading, but it has tons of information.
[http://rute.2038bug.com/node1.html.gz](http://rute.2038bug.com/node1.html.gz)
A less extensive, but still useful guide.
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
Hopefully that will get you started with simply getting around the system. Also, just to give you a thread along which to start researching, there is a program called Samba, that allows Linux to see Windows network shares. I'm not sure if it will be applicable to your situation, but it might be worth starting out at.

~Andrew S.

---

### Post by scxtt on 2006-07-30
i'd advise you to download the [alternate disk](http://mirror.cs.umn.edu/ubuntu-releases/6.06/) and reinstall ubuntu (this will give you a GUI) - you could do a **sudo aptitude install ubuntu-desktop** if the box has an internet connection (but that just might present more headaches) ... as far as getting the server to do what you want, i'd preliminarily consider this (after re-install):

1. create an account on the box for each student (real easy)
2. get samba set up on the ubuntu box (potentially annoying)
3. create p/w protected samba shares for each student (potentially annoying)

it's not hard, but setting up samba can be tedious {especially done by people explaining it to you over the internet} ...
3.

---

