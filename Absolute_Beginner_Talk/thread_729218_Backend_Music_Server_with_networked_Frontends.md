---
title: "Backend Music Server with networked Frontends"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by TheDeepFriedBoot on 2008-03-19
Hello
I am looking for a system that would allow me to have a back/frontend server with the music in a closet by the whole house amp and then have the other frontend systems around the house will control the music output on the system in the closet. I am trying to use Mythbuntu for this.  Does anyone know how to do this or what could do it? I have tried LinuxMCE but it seems a little overkill for what I hope to accomplish.

---

### Post by aidanr on 2008-03-19
If you want to change the music in one room and it changes the music playing in all the other rooms then I'd look into [mpd]("http://www.musicpd.org/") and [icecast]("http://mpd.wikia.com/wiki/Dependencies#icecast2"). If you want each room to be able to play different songs then I'd just set up a network share.

---

### Post by mcduck on 2008-03-19
MPD is most likely what you are looking for (and besides, it's one of the best music players around..)

[http://www.musicpd.org/]("http://www.musicpd.org/")

MPD and some clients are in Ubuntu repositories, and there are many more available so you sould be able to find a client you like. For examle, if all your machines are not running Linux (and you don't like the Windows/OS X clients available) you could use  a web-based client. For Linux clients I'd suggest trying Sonata at least, or if you like command line stuff, then ncmpc.

---

### Post by TheDeepFriedBoot on 2008-03-19
Well, considering im going to use MPD. Does it support WMA? If not, are there any good automated programs that can convert all my music w/o user intervention? 

Well, im installing an Ubuntu partition on the laptop that I used Windows Media Player 11 for the music. I never really learned how to use linux but im good with computers so I will try to teach myself. Does anyone foresee any issues that I may run into installing MPD as a first time user and what should I look out for?

---

