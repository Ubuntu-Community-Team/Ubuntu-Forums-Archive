---
title: "Big Ol' Ubuntu Security"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by ubz on 2007-05-20
Hi, My first post to the ubuntu forums and yes I am 'an absolute beginner'.  I heard about ubuntu 3 weeks ago and have just installed it on 2 desktop pcs.

Yesterday I read this article:
The Big Ol' Ubuntu Security Resource 
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

I wonder about this suggestion:
Limiting access to the "su" program
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:
Code:
sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su

Is it advisable to run these chown and chmod commands?  If so, how would I change back to the ubuntu installation default?

---

### Post by aysiu on 2007-05-20
Are you running a server? [quote=Unsafe Defaults Page]While Ubuntu comes secure and ready to use, many people decide to offer other services on their computer, such as running an FTP server or Apache. The purpose of this page is to advise these users on the settings that they should probably change.[/quote]

---

### Post by starcraft.man on 2007-05-20
On the same vein of thought as Aysiu, are you behind a NAT router? (Hi there Aysiu, oh mighty cat god of the Ubuntu forums :p)

NAT routers would be any router you bought in the past 4 years I think.

A properly configured NAT router with WAN management disabled, and a strong 20 character random password will make your computer near invulnerable to internet attacks by stealthing your computer from the internet, it simply drops all unrequested data and pings. There is nothing better in my mind, no amount of security tweaks can improve upon it. It like the difference between leaving a box with treasure out in the street with treasure in it and a giant secure almost unbreakable lock, and making that chest invisible/immaterial. I pick the later, what you can't see or touch can't be harmed.

If you don't have one, I'd go and buy a cheap 40 dollar one, its the best investment any person connected to a DSL or other internet line can ever make in regards to security and then you won't need to bother with those tweaks. Course, if you are running a server then go right ahead and do that, I don't suppose you'll have much use for a router.

---

### Post by ubz on 2007-05-21
> **starcraft.man said:**
> On the same vein of thought as Aysiu, are you behind a NAT router?

Hi, yes I have a nat w/firewall router and am not running a server.

---

