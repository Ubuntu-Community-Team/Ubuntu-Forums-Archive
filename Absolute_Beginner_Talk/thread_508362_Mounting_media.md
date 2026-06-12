---
title: "Mounting media"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-07-24
I've read the review material from past forums posts
I posted details of my experiments in solutions [**here**]("http://ubuntuforums.org/showthread.php?p=3065420#post3065420")

But my problem remains:I cannot mount my media!

THE STORY SO FAR...I did a fresh install of Dapper on an old XP machine. Taking up the whole drive when I did so. I then upgraded to Edgy as this machine seemed to reject on boot Feisty...as i've not been able to get my Feisty CD to take. without activating a Feisty bug. 

It's  a great setup and I love it except for one major hitch: I cannot  mount either of my mp3 players -- iriver T30 and IFP -- nor my usb stick. In the past these worked fine on this machine with XP  (although I'd used Wubi with that and I couldn't mount the media while in Wubi/Ubuntu boot mode so I used the communication between Win and Ubuntu to sync to my Mp3 devices).

So, for me , this is very serious...and I'd like some direction as I find "mounting" the most obscure of Ubuntu categories.

My digital camera mounts fine....

So what procedures *step by step* do I need to  follow to work through this problem?

---

### Post by ravenwere on 2007-07-24
Can't help off from my knowledge base but does this link give any clues???

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/20773](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/20773)


What kernel are you using?

best of luck
r

---

### Post by ratbagradio on 2007-07-24
> What kernel are you using?

Kernel? Ubuntuspeak right? I haven't a clue! 

It came with the cd..

---

### Post by Mornedhel on 2007-07-24
> **ravenwere said:**
> What kernel are you using?

Isn't the pre-shipped Dapper kernel 2.4.27 ?

ratbagradio : If someone asks you again, tell them the result of uname -a (if you could please post it here, for that matter). It gives you information on your kernel and your OS. I found USB drives to automount perfectly under Feisty Fawn, and if your MP3 players are strictly of the external drive kind (the good kind), they should work as well. I cannot really help, as kernel fun is beyond my abilities.

---

### Post by ratbagradio on 2007-07-25
> ratbagradio : If someone asks you again, tell them the result of uname -a (if you could please post it here, for that matter).

? More unbutuspeak? "uname" means what? and "-a" is similarly obscure to me.

If you mean "username" it is "ratbagradio" on my machine. But that doesn't tell me how to "find" my kernal as it came , I assume,with the upgrade from Dapper to Edgy. Clean install.

I'll post anything here you ask of me but i gotta work out where it is to grab it from.

Similarly the "bug" page I was refereed to doesn't tell me clearly where to write in the new stuff. I've been on Ubuntu most of this year and have learnt a lot but  I don't know much in way of this stuff re kernals and mounting -- mounting especially as it is the most confusing aspect I've found of the whole Ubuntu universe.

Anyway all i want to top p mount my devices. I 've done it automatically before on Ubuntu  using the  same install protocol and CD .

IF the Feisty bug that closed down my attempts at installing  wasn't active  I could install Feisty in replace of what I've got now but I've found resistance. before . However if I try to install Feisty via the CD and it fails to take  can I get back to Edgy by default or do i have to go back to Dapper and upgrade?(as I don't have a  Edgy CD)
[I]
 And most importantly will such a route give me device mounting access?[/I]


I';m easy. I'll walk over hot coals for this....
es

---

### Post by ratbagradio on 2007-07-25
Gotcha. I went here
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
 and found the DIY

My kernel detail are:

[B]2.6.17-12-386
[/B]

---

