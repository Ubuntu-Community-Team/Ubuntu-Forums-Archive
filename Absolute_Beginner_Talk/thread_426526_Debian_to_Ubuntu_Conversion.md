---
title: "Debian to Ubuntu Conversion"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Chernevik on 2007-04-28
[This was probably misposted in the Installation Thread.]

I would like convert from Debian to Ubuntu, and would like some help finding resources to efficiently learn how do so in the smoothest manner possible. I'm happy to read what I need to read, but I could use some help finding the right resources.

I AM: a newbie running Debian for about two months. It works great but I would like to give Ubuntu a try, to see what all the talk is about and check out the latest and greatest.

I'D LIKE TO: convert to Ubuntu from Debian while retaining the system and user configurations we've established on Debian. These include:
- remote print service for a Windows XP computer (ie the XP box uses the printer attached to the Debian box),
- a few programs and scripts downloaded in user accounts,
- stuff like browser search histories,
- and so forth.

I'd also like users to have the same desktop they've been seeing under Debian, so my wife doesn't get frustrated at learning another new desktop. I think we're running "Nautilus" on Debian right now, but I'm not sure.

Before I convert I'd like to backup all of this and the Debian files so I can restore what we've currently got. I don't know how to do that either. For backup we have a linkstation nas, but maybe the debian os files should also be backed up to DVD/CD in case I have trouble booting up?

WHAT I'M RUNNING: I installed Debian 4.0 "etch" when it was in testing -- I haven't done anything to convert it to the stable version released earlier in April, though I've taken all the upgrades suggested by Synaptic, so maybe I'm already there. It is dual-booting Vista Home Basic (don't ask) -- we never use it but I'd like to retain it anyway. The computer is brand new but _very_ modest.  The print service is via Samba and I think CUPS, but maybe foomatic?

LAST: I'd almost prefer to do all this from the command line so I can learn how it works, unless some gui solution is much more efficient.

PLEASE HELP ME find resources to efficiently learn how to do all this; it'd be greatly appreciated. I've heard great things about Ubuntu, and if I get it to work I might be able to persuade a few people to give it a try themselves, or at least show them how it looks and works.

And THANK YOU for your time and expertise.

---

### Post by rickycodie on 2007-04-28
you'll be happy to know that ubuntu is debian based and also runs nautilus. i have not used debian but i read that many debian users are switching because of ease of use.  ubuntu also comes as a live cd so you don't need to worry about the trial period, and has a built in transferr manager(in 7.04 only) tahta will hep you make the transition. the only thing that i don't think is does is emails. all of your bookmarks and gaim and contacs should be able to be treansferred. try these links:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

[http://doc.ubuntu.com/ubuntu/desktopguide/C/](http://doc.ubuntu.com/ubuntu/desktopguide/C/)

that should get you started. if you need anything else google and here present the most ready options.

pleased to be helping,
ricky

---

### Post by CREEPING DEATH on 2007-04-28
is it set up with a /home partition?  If not, you're going to have to nuke it and reload.  There is an official method to install 4.10 to a Debian system, then 5.04, 5.10, 6.06, 6.10, 7.04.  The problem is distribution upgrades oftentimes fail on Ubuntu.  Ubuntu's main advantage is ease of set-up, if you have Debian going to your satisfaction I'd stick with it.

CD

---

### Post by rickycodie on 2007-04-28
i disagree i just updated and all i had to do was remove automatix. the reast of the upgrade went swimmingly.

---

### Post by Chernevik on 2007-04-28
My Debian installation does have a separate /home partition, but I admit I don't understand why that is important here.

So if I install ubuntu it will just pick up my existing configuration and network settings?

---

### Post by [S|G] on 2007-04-28
Some of your settings, such as your desktop layout, wallpapers, etc, might be preserved, but settings such as video settings and network settings will probably have to be made again. The point of having a separate /home partition is that you can format your root ( / ) partition and you won't lose your personal data.

---

### Post by Chernevik on 2007-04-28
Can't I retain the network settings by backing up the config files and using those after the ubuntu installation?

---

### Post by [S|G] on 2007-04-28
Well, backing up your /etc/network/interfaces should work, since they have the same layout

---

