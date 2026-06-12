---
title: "[SOLVED] am I being hacked through Gaim/Pidgin?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-09-17
okay...this is really weird question I know...But am is it possible to be hacked through Pidgin?

I have these people (2 so far) that I'm *positive* I didn't add...and the strange thing is they will sign on and then immediately sign off before I can ask them anything...

But they have buddy icons and everything just like my regular buddies...even profiles...

It creeps me out.

Can someone shed some light on this?

---

### Post by uzybear on 2007-09-17
here's a guess from a total newb: could it be a buddy-of-a-buddy on one of your friends lists?

---

### Post by isaacj87 on 2007-09-17
hmmm...interesting...is this even possible?

---

### Post by Lacrimstein on 2007-09-17
I don't think it has anything to do with pidgin... most likely they hacked your im account.

---

### Post by isaacj87 on 2007-09-17
Yeah, I figured that my buddy list isn't local...probably some sort of service...

Like I said...it just weirds me out...

---

### Post by CaptainInsaneO on 2007-09-17
This has happened to me before, back when I used Windows and MSN Messenger. I had a chick from my old hometown show up on my list, and neither of us had any idea how the other one got there.

Good thing was, she turned out to be really hot and super cool and now we're really good friends. :lolflag:

---

### Post by misfitpierce on 2007-09-17
I would change your IM password to be safe and see if it stops. Friend prob has password or someone.

---

### Post by isaacj87 on 2007-09-17
> **CaptainInsaneO said:**
> This has happened to me before, back when I used Windows and MSN Messenger. I had a chick from my old hometown show up on my list, and neither of us had any idea how the other one got there.

Good thing was, she turned out to be really hot and super cool and now we're really good friends. :lolflag:

haha lucky b**tard

---

### Post by corevette on 2007-09-17
> **misfitpierce said:**
> I would change your IM password to be safe and see if it stops. Friend prob has password or someone.

Yes, definitely change your password, even if they have it or not, just to be safe.  Try logging onto [meebo]("http://meebo.com"), or some other instant messaging service and see if it does the same thing

---

### Post by FuturePilot on 2007-09-17
Might just be a spam bot, I've heard of that happening before.

---

### Post by rajan on 2007-09-17
gaim's password protection is really terrible. you need to make sure that you don't save your password in gaim even though it's a bit of a hassle. if you do save your password and you want to know why you shouldn't, type ```
gedit ~/.gaim/accounts.xml
```. look for your password there. it'll be in plain text. yes. that's right. your password is in plain text in a file that's not necessarily access-protected. i'm not sure if it's in that particular file or not, but it's somewhere in the .gaim/ directory. 


other than that, it's most likely not a hack. i can't really imagine someone would be really that interested in being on your buddy list just so they can sign off right away. maybe you're just that cool though. :)

---

### Post by isaacj87 on 2007-09-17
Thanks for all the responses guys...I actually went ahead and talked to one of the people and it was some girl that I have NEVER EVER met before....


It was really weird...but I going to try some of the suggestions...and I'm going to mark this as solved.

---

### Post by isaacj87 on 2007-09-17
> **rajan said:**
> gaim's password protection is really terrible. you need to make sure that you don't save your password in gaim even though it's a bit of a hassle. if you do save your password and you want to know why you shouldn't, type ```
gedit ~/.gaim/accounts.xml
```. look for your password there. it'll be in plain text. yes. that's right. your password is in plain text in a file that's not necessarily access-protected. i'm not sure if it's in that particular file or not, but it's somewhere in the .gaim/ directory. 


other than that, it's most likely not a hack. i can't really imagine someone would be really that interested in being on your buddy list just so they can sign off right away. maybe you're just that cool though. :)

hahaha maybe I am!

---

### Post by rajan on 2007-09-17
good to hear that everything is ok. hopefully that girl turns out to be as hot as the girl CaptainInsaneO met.

---

### Post by CaptainInsaneO on 2007-09-17
> **isaacj87 said:**
> Thanks for all the responses guys...I actually went ahead and talked to one of the people and it was some girl that I have NEVER EVER met before....


It was really weird...but I going to try some of the suggestions...and I'm going to mark this as solved.

HAHA!! It's a frickin epidemic, I'm telling you.

---

### Post by isaacj87 on 2007-09-17
I'm being completely honest here...

She actually is pretty hot...

Guess we ubuntu users are just lucky.

---

### Post by murt on 2007-12-08
> **isaacj87 said:**
> okay...this is really weird question I know...But am is it possible to be hacked through Pidgin?

I have these people (2 so far) that I'm *positive* I didn't add...and the strange thing is they will sign on and then immediately sign off before I can ask them anything...

But they have buddy icons and everything just like my regular buddies...even profiles...

It creeps me out.

Can someone shed some light on this?
The passwords in pidgin ase saved all NON-ENCRYPTED.
With just one command anyone who makes a script or a program that you run can take your password.
do this:
> cat ~/.purple/accounts.xml|grep password See, all your passwords comes?
Many people uses the same password for many places because its hard to remember all of 'em, wich i can understand. This is a serious problem that the Pidgin team HAS to fix.

---

