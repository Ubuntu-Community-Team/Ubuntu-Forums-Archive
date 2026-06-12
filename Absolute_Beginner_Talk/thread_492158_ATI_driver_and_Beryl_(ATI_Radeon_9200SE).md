---
title: "ATI driver and Beryl (ATI Radeon 9200SE)"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-04
Greetings to all, ):P

I have Beryl working with an ATI Radeon 9200SE video card using the default "ati" driver. However, I have not been able to prevent it from "eventually" going to a black screen. If I change "ati" in xorg.conf to "vesa" I can prevent the black screen, but I cannot use Beryl. If I turn on Beryl using "vesa," I will get a white screen. :(

My question: If someone with my card has got Beryl working without any screen problems, will you please post your solution? :idea:

Thanks so much. :)
kh

---

### Post by kittyhawk63 on 2007-07-04
bump

---

### Post by Golyadkin on 2007-07-04
I have a 9200SE in one of my pc's, and it runs Beryl fine, I never had to install any driver. It worked fine from a default install of Feisty. Never had trouble with black or white screens.

---

### Post by njknight on 2007-07-04
Hi I don't know if this is something you have looked at already but have you tried the Ati Nvidia script "Envy" which can be found here [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

His script did the trick for me when I was having difficulties setting up my system and I had been experiencing the "white screen" at log-on.

hope you get it sorted.

---

### Post by kittyhawk63 on 2007-07-04
Back from July 4th meal and visit with friends.

njknight,

Thanks for the link. I followed the instructions for the terminal inputs. Now I have to wait to see if it worked. Thanks again.
kh

---

### Post by kittyhawk63 on 2007-07-05
> **Golyadkin said:**
> I have a 9200SE in one of my pc's, and it runs Beryl fine, I never had to install any driver. It worked fine from a default install of Feisty. Never had trouble with black or white screens.

You are one of the blessed ones. Many of us have problems with the SE card as well as with ATI cards in general. There are even a few having problems with Nvidia cards. It is probably the way the card interacts with the computers we have the cards installed into. You and I could go down to a store and buy the same system, take it home, set up Linux using Beryl and have different results. What gives? It is because even though we have the same systems, we may not have the same electronics inside the computers. 

Computer manufacturers buy from different suppliers and may end up buying and installing different electronics to make up a computer of the same make and model. These differences can have a minor or major effect on how some programs work. That is where tweaking comes in. And if you're a noob, you may have some trying times ahead while you work out the problems. That is when the faint in heart may drift back to Windows. 

It took me several (4) months to get different distros of Linux to stop crashing. I eventually figured it out. It was simply changing "ati" in xorg.conf to "vesa."  It limited my resolutions choices, but it worked. But "vesa" doesn't work with Beryl. At least not on my computer. What I learned over the past months has helped me not to give up when I installed Beryl. I think (fingers crossed) that I have finally fixed the black and white screen problem as of yesterday....July 4th. How apropos. I have been online for over an hour. It is the first time since installing Beryl that I have not crashed within twenty minutes. Most times I was only getting five to fifteen minutes.

The only distro that I did not have to do anything to is SAM. It worked out of the box. Beryl was included. However, another SAM distro, SAM PCLinuxOS, is a different matter. I had a few things I had to tweak to get it to work on my computer.

I still keep coming back to Ubuntu. I have hung up my hat. I'm home. The major reason is this forum. Need I say more? Maybe. 99% of the people here really try to help. They are polite and really interested in helping each other out, especially helping the newbie. I wish that last 1% would take a clue. They can be real jerks to some newbie seeking help. The noob ask questions that for someone having used Linux for awhile seem elementary, but for the noob it is still unchartered frontier. Give these folks a break. They don't need some jerk giving them some smart alick answer. (Golyadkin, this is in no way directed toward you.) 

We have all been there as newbies and should try to remember what it was like. I have my keyboard that no longer has the little lifts underneath that raise the back up because of a frustrating several months with Linux. Slamming your fists on the keyboard will not fix Linux. I tried it. lol  

Anyway, Golyadkin, I'm really glad you have immediate success with your ATI card. I hope that it will always play nice with the other kids. :)
kh

---

