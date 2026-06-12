---
title: "no serving hosts were found -- ubuntu networking in general"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by capty99 on 2007-04-26
okay, 2 completely different questions,
any help would be greatly appreciated.

1) what is up with the linux filing system. i understand /usr/lib/ is about equivalent to c:/programs, but beyond that im lost in a maze it seems and cannot find a good resource that explains it all to me. if you could point me in the right direction i would love you forever.

2) not really understanding networking with ubuntu, i can get it to work one way with windows ... so say if i set up a windows network i can get files from my windows pc to my ubuntu pc. but the ubuntu files dont seem to show up in the windows file manager. and when i have two ubuntu pcs together, i don't even see any kind of object representing they even see eachother.

well here is my specific question about number 2,
i just want to use XDMCP because my laptop is puny and my desktop is powerful.
BUT, when i follow the setup instructions, all i get is no serving hosts were found,
and don't know what to do to make them look for eachother in the right spot.
thanks.

---

### Post by Ecthelion on 2007-04-26
> 1) what is up with the linux filing system. i understand /usr/lib/ is about equivalent to c:/programs, but beyond that im lost in a maze it seems and cannot find a good resource that explains it all to me. if you could point me in the right direction i would love you forever.

Well I don't understand why you would want to look there...
Is there anything specific that you want...?

All the programs are put in the menus, and it doesn't seem a great idea to me to go messing in /usr/lib/
...So what are you exactly looking for?
What do you want to do?

> 
2) not really understanding networking with ubuntu, i can get it to work one way with windows ... so say if i set up a windows network i can get files from my windows pc to my ubuntu pc. but the ubuntu files dont seem to show up in the windows file manager. and when i have two ubuntu pcs together, i don't even see any kind of object representing they even see eachother.

So what you are saying is what...?That you can move files from your windows pc (using your windows pc) to your ubuntu, but once they are on ubuntu you can't see them (from your windows pc)?

I'm a bit lost in you explanations...

---

### Post by capty99 on 2007-04-26
thanks for the reply.

1) no,  i dont want to mess around with them,
but i do like to know whats going on with my pc, good to know where files are at and all that jazz.
i was a power user on xp for years but seeing it from the linux side is messing with my mind a little bit if you know what i mean.

2) if i go to places> network i see my windows network, and all the files that i am sharing on my windows pc can be accessed, viewed, downloaded etc.... but if i am in my network places on my windows pc, i can not see any of the files that i am sharing in ubuntu. better explanation?

my main concern is actually getting xdmcp working right now.... gonna reset my router config and start over see what i can do.

---

### Post by Wicca on 2007-04-26
If you want to share files between Ubuntu and Windows you need Samba.

See [http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO+samba]("http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO+samba")

When setup, you can easily right click a folder and choose Share Folder to make it accessible from a Windows box.

---

### Post by capty99 on 2007-04-26
yeah,
ive got samba.
doesn't seem to work for some reason.

---

