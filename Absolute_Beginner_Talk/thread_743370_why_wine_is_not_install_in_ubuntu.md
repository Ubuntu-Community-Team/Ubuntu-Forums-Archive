---
title: "why wine is not install in ubuntu?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by evertsfnic on 2008-04-02
why wine is not install in ubuntu?

I hate that, i want to used yahoo messenger and i can not do it.

I think if you already install wine in ubuntu (Like openoffice), it will be easier for a lot people to used your OS.  Right now ubuntu is great, but it needs to be better. 

I only come back to window for a few things.......

Thanks for taking the time to read. And Keep the good work.......

---

### Post by Crafty Kisses on 2008-04-02
First, you do realize Pidgin offers Yahoo services. Secondly, if you want to install Wine do the following: ```
sudo apt-get install wine
``` If you're installing Wine just for Yahoo Messenger it really isn't worth it, just use Pidgin.

---

### Post by twright on 2008-04-02
wine is not installed by default because most users do not need it. some think they do for simple things like messengers or msoffice but ubuntu provides better alternatives out of the box

---

### Post by Crafty Kisses on 2008-04-02
> **twright said:**
> wine is not installed by default because most users do not need it. some think they do for simple things like messengers or msoffice but ubuntu provides better alternatives out of the box

Exactly.

---

### Post by Northsider on 2008-04-02
> **Codename said:**
> First, you do realize Pidgin offers Yahoo services. Secondly, if you want to install Wine do the following: ```
sudo apt-get install wine
``` If you're installing Wine just for Yahoo Messenger it really isn't worth it, just use Pidgin.

Yea, Pidgin is the way to go...unless you just need that video chatting option:)

---

### Post by Crafty Kisses on 2008-04-02
> **Northsider said:**
> Yea, Pidgin is the way to go...unless you just need that video chatting option:)

Yeah I guess, but I'm getting the feeling in the near future Pidgin will have that option. :)

---

### Post by waspbr on 2008-04-02
the no video chat was a show stopper for me, although I really liked it.

then I found aMSN...

---

### Post by Crafty Kisses on 2008-04-02
> **waspbr said:**
> the no video chat was a show stopper for me, although I really liked it.

then I found aMSN...

aMSN never worked for me, tried everything I could, I would get these cryptic errors. :(

---

### Post by Cope57 on 2008-04-02
[**Pidgin**]("http://pidgin.im/") is a graphical modular messaging client based on libpurple which is capable of connecting to AIM, MSN, Yahoo!, XMPP, ICQ, IRC, SILC, SIP/SIMPLE, Novell GroupWise, Lotus Sametime, Bonjour, Zephyr, MySpaceIM, Gadu-Gadu, and QQ all at once.  It is written using GTK+.

You want video chat, use kopete

---

### Post by Crafty Kisses on 2008-04-02
> **Cope57 said:**
> [**Pidgin**]("http://pidgin.im/") is a graphical modular messaging client based on libpurple which is capable of connecting to AIM, MSN, Yahoo!, XMPP, ICQ, IRC, SILC, SIP/SIMPLE, Novell GroupWise, Lotus Sametime, Bonjour, Zephyr, MySpaceIM, Gadu-Gadu, and QQ all at once.  It is written using GTK+.

You want video chat, use kopete

Kopete is really good too. Never had trouble with that, I used it for a while, but I don't use a Webcam, so Pidgin is perfectly fine with me.

---

### Post by twright on 2008-04-02
skype is the best option for video in my opinion, it is proprietary but at least skype have made the effort to support linux

i tried ekiga but could never get it set up.

---

### Post by Crafty Kisses on 2008-04-02
> **twright said:**
> skype is the best option for video in my opinion, it is proprietary but at least skype have made the effort to support linux

i tried ekiga but could never get it set up.
I use Skype a lot, and that's really good for voice.

---

### Post by evertsfnic on 2008-04-03
thanks for your answers.
But i thought yahoo messenger in linux was with voice and video
I want a program  for talking to my sister in the state, she used yahoo messenger.............

---

### Post by evertsfnic on 2008-04-03
> **twright said:**
> wine is not installed by default because most users do not need it. some think they do for simple things like messengers or msoffice but ubuntu provides better alternatives out of the box
I have tried openoffice and it's great and kopete.
but i want a program for video and voice in that way i can talk with my sister in the state. she used yahoo messenger.

---

### Post by Xiong Chiamiov on 2008-04-03
It seems the most common app for voice chat on Linux is Skype.  Now, getting your mic to work, that may be the troublesome part (I haven't ironed it all out yet on mine).

---

### Post by Xiong Chiamiov on 2008-04-03
> **Codename said:**
> First, you do realize Pidgin offers Yahoo services. Secondly, if you want to install Wine do the following: ```
sudo apt-get install wine
``` If you're installing Wine just for Yahoo Messenger it really isn't worth it, just use Pidgin.

Forgive me, but don't you have to [add the wine repositories]("http://winehq.org/site/download-deb") first?

---

### Post by kpkeerthi on 2008-04-03
> **Xiong Chiamiov said:**
> Forgive me, but don't you have to [add the wine repositories]("http://winehq.org/site/download-deb") first?

Wine is already available in gutsy's [universe]("http://packages.ubuntu.com/gutsy/wine") repository.

The wine-hq's repo is optional unless you want to stay bleeding edge on wine.

---

### Post by loell on 2008-04-03
yahoo messy won't run in wine (properly).

---

### Post by twright on 2008-04-03
i'm not sure you will have any luck with webcams via wine:(

---

### Post by ugm6hr on 2008-04-03
> **evertsfnic said:**
> thanks for your answers.
But i thought yahoo messenger in linux was with voice and video
I want a program  for talking to my sister in the state, she used yahoo messenger.............

Perhaps suggest she use skype too.

---

### Post by forrestcupp on 2008-04-03
It's going to be a lot easier to get your sister to take a couple of minutes to download Skype and set up a free account than it is to set up Yahoo Messenger with video capabilities with Wine.  But you just said you want to 'talk' to your sister.  If you don't need video, just use pidgin; it supports Yahoo accounts.

As for the original question.  They don't include Wine because there is limited space on a CD for them to cram all of the apps that they think are important.  The goal isn't to get Ubuntu to be like Windows, but to be a viable desktop solution in its own right.  Then they include Wine in the repos for all of the people who need it.

---

### Post by ichi@YUKI on 2008-04-03
For those who are new to Linux like me, it seems important for us to let the computer run the way it usually did in Windows. However, I learned that that's just not the case. Wine is probably on of the first things I loaded into my system, and after just four days of my exposure to Ubuntu, I realized I never really needed it.

It's ok to think that you can use the same windows applications in Ubuntu using wine or whatever. However, based on experience, (visualboy, utorrent for example), these things just don't run smoothly in Ubuntu. Thus, I believe we're better off running the Ubuntu-prepared alternatives. 

I like Pidgin more than YM now.

---

### Post by loell on 2008-04-03
surprisingly, I wonder why only few people know this, you can actually do voice call with  a yahoo messenger user, by using gizmo. 


so to achieve Yahoo! voice and video use gizmo and (gyachi or kopete) respectively.

---

