---
title: "Ok its the mp3 question.."
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by gryer7421 on 2006-08-21
I have recently decided to try linux again, my 1st few tries were problematic and frustrating.  this unbuntu and xubuntu have been alot easier. but I am having a hell of a time with just getting mp3/dvds to play.

I have tried a lot of links contained here in the forum and have hot a wall that I found very frustrating last time and again this time.

I install ubuntu/dapper.

I unlock the repositories, and ad a few more like plf and the restricted ones.

I drop to a command line and sudo su and proceed to get-apt update several times until its all successful.

So far so good.  Then I hit the links, there are MANY links describing mp3 support, calling for various libs, codecs, players and what not. But not one has worked so far.

Symptom : the mp3 “skips around” make a lot of harsh gibberish and stops.

I have installed alien, installed the win32codecs, xine, totem, their addons.

Made deb files out of various rpms, followed soooo many library installs 

Hell I even installed all vlc* packages…. No joy

So… I need exactly what is needed to get dapper (downloaded 3 days ago) out of the box fresh installed to play dvd files and mp3’s before I pull my hair out ;) ](*,)

also one last thing that is realy irksome... why is it there are so many "unavailable" packages or libaries?  i get installs that start well then come up and tell be thet a selected package is old or has been replaced... but then doesn't tell what to use.. very maddening...

---

### Post by taurus on 2006-08-21
Try xmms -> Options -> Preferences -> Audio I/O Plugins -> Output Plugins.  Play around with difference driver!!!

---

### Post by Shortgeek on 2006-08-21
Have you tried MPlayer? I don't know if it will work for you, but it plays my mp3's just fine. Also does Quicktime, AVI, and other useful things.

It's in the multiverse: mplayer-mozilla for a firefox plugin, mplayer for the player.

---

### Post by The Mekon on 2006-08-21
I have had great success with [Automatix]("http://www.getautomatix.com/")

It makes installing the "illegal" codecs easy.

---

### Post by gryer7421 on 2006-08-21
""I have had great success with Automatix It makes installing the "illegal" codecs easy.""

ok this i can do, but i want to learn more of the command line, then gui.. what packs/libs do i need ?  im trying to learn linux in  a little more depth than straight click and go.   its for personal learning as well as a job related command line experience...

---

### Post by Shortgeek on 2006-08-21
> **gryer7421 said:**
> ""I have had great success with Automatix It makes installing the "illegal" codecs easy.""

ok this i can do, but i want to learn more of the command line, then gui.. what packs/libs do i need ?  im trying to learn linux in  a little more depth than straight click and go.   its for personal learning as well as a job related command line experience...

The whole point of Automatix is to get things to work, while HIDING the command line stuff that you want to know about. It also does crazy things to your sources.list, and some things it installs ARE illegal.

But if you pay attention, Automatix can work. I wouldn't recommend it, though. Try EasyUbuntu (easyubuntu.freecontrib.org), if you want something like that.

If you are in the USA, do NOT, under ANY circumstances, choose the "Binary codecs" under "Multimedia", under EasyUbuntu, or LibDVD (or something like that) under Automatix. It's illegal here.

---

### Post by gryer7421 on 2006-08-21
ok i broke down and tried automatrix, looked at the logs and it was successful.. but the mp3 wil lstill not play.

i installed everything related to multimedia... whats really bugging me is that i got this to work under xubuntu *once* in the 4 installs...

the mplayer locks up, xmms cannot decode it.

any other thoughts... im frustrated atm...

---

### Post by gryer7421 on 2006-08-21
nevermind.... the whole install just crashed.. again.

i have to reinstall

---

