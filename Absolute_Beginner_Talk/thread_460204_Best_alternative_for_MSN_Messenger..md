---
title: "Best alternative for MSN Messenger."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-05-31
Hey,
I use MSN Messenger alot, and gaim just doesn't seem to fit my need. Are there other good alternatives for MSN Messenger alone?

---

### Post by meng on 2007-05-31
What are your needs? That might help.
amsn, kopete, mercury are all possibilities.

---

### Post by sibot on 2007-05-31
anything close to the latest Live Messenger, a simple interface with all the features, like webcam et al.

---

### Post by jrusso2 on 2007-05-31
aMSN or Kopete

---

### Post by silentjudas on 2007-05-31
well nothing i know has good cpabilities excpet kopete and kmsn i think. lately though i havent been able to log into msn...and my cam doenst work cause the driver wont install...but either way, kopete has some good crap and i think kmsn is ok

---

### Post by gvoima on 2007-05-31
Personally I strongly recommend aMSN, it's a nice messenger :)

Are you using Feisty Fawn with Gnome (Ubuntu)? If so, I have a ready SVN .deb for it, just PM me.
(amsn_0.97-0+svn20070426~3v1ubuntu1_i386)

---

### Post by sibot on 2007-05-31
thanks alot! Anyhow, i got a small question. I'm installing Amarok from the application manager and it seems to be downloading some 36 files? i think it must be over 30 mb, is it normal?

---

### Post by sibot on 2007-05-31
KMsn would only work with kde enviorment? How do i find out which enviorment I'm working on? gnome or kde?

---

### Post by y-lee on 2007-05-31
aMSN is about as close as it comes. unfortunately it doesn't support **all **the features, but probably more than any of the rest. If I'm wrong someone correct me because I haven't tried some such as mercury. I personally love trillian (which supports most but not all of MSN features) but trillian is windows software and the full version is not free either, But I have switched completely to Linux so aMSN it is for now. lmao

---

### Post by sibot on 2007-05-31
Hmmm, I think I'll give aMSN a try, it sounds good.

---

### Post by sibot on 2007-05-31
Btw...just wondering, has anyone tried running MSN Messenger through Wine?

---

### Post by WinterWeaver on 2007-05-31
I like OpenWengo.

Looks and feels a lot like skype.
I can access my gmail, yahoo accounts.
It has webcam support.
It has good build over multiple platforms (windows, linux, macos)

One of my buddies installed the windows version (he only uses windows), and he instantly fell in love with it. ^_^

my 2 cents :P

EDIT: can also access your msn account :)

---

### Post by MentholLite on 2007-06-02
> **sibot said:**
> Btw...just wondering, has anyone tried running MSN Messenger through Wine?

I just tried this, but failed.

The Live Messenger installation file will detect that the OS is not XP and above and quit out itself. :(

---

### Post by Lord Illidan on 2007-06-02
> **sibot said:**
> KMsn would only work with kde enviorment? How do i find out which enviorment I'm working on? gnome or kde?

KDE applications work fine on GNOME. Amarok, KMsn, Kopete, etc. The only thing is that you have to download the KDE libs for them to work (this is handled by apt-get/synaptic automatically, so don't worry).

Can you see the Applications Places System at the top of the screen? If so, you are using GNOME.

---

### Post by blue_shift on 2007-06-02
> **sibot said:**
> KMsn would only work with kde enviorment? How do i find out which enviorment I'm working on? gnome or kde?

Nevermind, beaten to it :)

---

### Post by drowner on 2007-06-02
I think MSN is a terrible program.

Its got advertisements, at the bottom of every friggin message.

Thats not a good program, thats just anoying.

---

### Post by loell on 2007-06-02
HAh!! :KS

so is YM :p , so the lack of these messengers official support for linux, is good in some way,

though unfortunately, messngers are not just programs, they are essential communication tool to many.

luckily thanks to the individuals who made time decoding half of these protocols and develope an open source alternative. we can communicate with the other end (windows).

---

### Post by kilou on 2007-06-02
aMSN looks good but I hate the fact that the router firewall must be altered for the webcam to work :mad: I use messenger on my laptop to keep in touch with my family when I travel and really I can't change the settings of routers in a hotel, in an airport etc. That's really stupid IMHO to require this for the webcam to work. For now I haven't seen a place where aMSN works with the webcam without having to alter port forwarding on the router. It's not a problem of the built-in firewall of Linux, it's definitely caused by the router firewall. MSN on Windows never ask you to change the router port forwarding unless you already modified the settings yourself.

This is what prevents me from using aMSN now so I use MSN Live in XP instead....another reaon I cannot move to Linux completely :(

---

### Post by jrusso2 on 2007-06-02
> **kilou said:**
> aMSN looks good but I hate the fact that the router firewall must be altered for the webcam to work :mad: I use messenger on my laptop to keep in touch with my family when I travel and really I can't change the settings of routers in a hotel, in an airport etc. That's really stupid IMHO to require this for the webcam to work. For now I haven't seen a place where aMSN works with the webcam without having to alter port forwarding on the router. It's not a problem of the built-in firewall of Linux, it's definitely caused by the router firewall. MSN on Windows never ask you to change the router port forwarding unless you already modified the settings yourself.

This is what prevents me from using aMSN now so I use MSN Live in XP instead....another reaon I cannot move to Linux completely :(

Thats because the windows MSN uses upnp to circumevent the routers default safe configuration.  Upnp is a huge security risik

---

### Post by happy-and-lost on 2007-06-02
> **kilou said:**
> aMSN looks good but I hate the fact that the router firewall must be altered for the webcam to work :mad: I use messenger on my laptop to keep in touch with my family when I travel and really I can't change the settings of routers in a hotel, in an airport etc. That's really stupid IMHO to require this for the webcam to work. For now I haven't seen a place where aMSN works with the webcam without having to alter port forwarding on the router. It's not a problem of the built-in firewall of Linux, it's definitely caused by the router firewall. MSN on Windows never ask you to change the router port forwarding unless you already modified the settings yourself.

This is what prevents me from using aMSN now so I use MSN Live in XP instead....another reaon I cannot move to Linux completely :(

There's a workaround for that. On the main window, open debug mode with Ctrl+S and type/paste:

*set ::abook::demographics(listening) true*

For whatever reason, webcam will now work (or, it would with me!), but only for that session. Must be repeated  everytime you open aMSN. I don't know enough about programming to figure out how to set this permanently.

---

### Post by DougieFresh4U on 2007-06-02
> **sibot said:**
> Btw...just wondering, has anyone tried running MSN Messenger through Wine?




I use AIM through wine. But I have not been able to get any sound yet. Still working on that:(

---

### Post by kilou on 2007-06-03
> **jrusso2 said:**
> Thats because the windows MSN uses upnp to circumevent the routers default safe configuration.  Upnp is a huge security risik

I had disabled UPnP in XP with a known patch and MSN always worked the same when UPnP was disabled...

---

### Post by kilou on 2007-06-03
> **happy-and-lost said:**
> There's a workaround for that. On the main window, open debug mode with Ctrl+S and type/paste:

*set ::abook::demographics(listening) true*

For whatever reason, webcam will now work (or, it would with me!), but only for that session. Must be repeated  everytime you open aMSN. I don't know enough about programming to figure out how to set this permanently.

This "works" for me as well but the webcam laggs way too much to the point of being unusable :( Moreover I cannot send my webcam and receive the other one at the same time, it freezes aMSN all the time. And also it is not possible to easily start a video conference in aMSN: you need to send your webcam, ask for your contact's one...and then find a way to talk. That's just too complicated for me. Using MSN in XP through VirtualBox is much better but there again the webcam still lags...but much less than with aMSN. In plain XP, MSN is really smooth! I don't know if the laggs in Linux is a webcam driver issue though: mine is a Logitech quickcam Deluxe for notebook....

Definitely there are lots of improvements to be done with aMSN. I'm still using XP for videoconference because there is no true MSN or Skype (with video) equivalent in Linux unless your buddies are also under Linux.

---

### Post by sibot on 2007-06-03
Well, i tried out a couple of programs, and well none of them worked for me. Gaim, aMsn, etc. 
Right now I'm using Pidgin (Gaim's upgrade). And it seems to be working fine, except the fact that it doesn't have webcam support. Which is a must for me.

Well anyway, as posted by someone earlier in this topic, live messenger detects that we are not using windows OS, and stops the installation. I guess that would happen, since the bitter differences between Linux and WIndows. Recently Microsoft was planning to sue Linux over 32 patent violations. And I guess now winodws is working to make their applications only windows operable. So as i think, we should try and use the older versions of MSN, like 7.5, etc. Maybe they might work and it would absolutely give us MSN fanatics a chance to get the MSN experience on Ubuntu too.

Cheers! I will report back as soon as i try 7.5! if someone else tries it first, do post your valuation. 
Thanks for all the support!

---

