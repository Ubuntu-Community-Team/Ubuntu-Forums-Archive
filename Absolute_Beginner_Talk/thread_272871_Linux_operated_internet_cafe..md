---
title: "Linux operated internet cafe."
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by ton_cut345 on 2006-10-07
Hi,

New in linux. especially here in ubuntu. Im planning to open a business. an internet cafe business where people rent my computers. and im planning to use ubuntu, since the windows os is to expensive. 

my question is ubuntu linux is userfriendly? will it support windows base games like warcraft?. is OpenOffice.org 2 supports .doc file format just like ms office?. is it applicable to have this kind of OS in this kind of internet cafe? and also, can i set users account for limited access of files and program, like theres an anministrator account and a limited user account just like windows?

thanks for your help.. :D

---

### Post by aysiu on 2006-10-07
I'll try my best to answer your questions. Others may have to jump in.

1. You're a [Ubuntu 4.10](https://wiki.ubuntu.com/WartyWarthog) user (October 2004)--you may want to think about becoming a [Ubuntu 6.06](https://wiki.ubuntu.com/DapperDrake) user (June 2006). In a few weeks a newer version will be released too ([6.10](https://wiki.ubuntu.com/EdgyEft)--October 2006).

2. Ubuntu is user-friendly when set up correctly.

3. I don't believe it natively supports Windows-based games, but there's something called [Cedega](http://www.transgaming.com/index.php?module=ContentExpress&func=display&file=index&ceid=29), which helps to run some Windows games. You can read [some forum threads about setting up Warcraft specifically](http://www.google.com/search?hl=en&q=warcraft+site%3Aubuntuforums.org&btnG=Google+Search).

3. OpenOffice supports the .doc file format, but for some complex layouts or documents containing macros, [the support may not be there 100%. ](http://www.google.com/search?hl=en&q=openoffice+compatibility+word&btnG=Google+Search) If your business depends on people being able to have 100% compatibility with Word, you need to have Word, and you can probably install MS Office in Ubuntu using a helper program like [Wine](http://www.winehq.com/) or [Crossover Office.](http://www.codeweavers.com/)

4. Yes, you can use Ubuntu for an internet cafe.

5. You can definitely lock down user accounts in Ubuntu. There are a couple of tools available for kiosk modes: [*kiosktool*](http://extragear.kde.org/apps/kiosktool/) and [*sabayon* / *pessulus*.](http://72.14.253.104/search?q=cache:bpDWMW4Lu4EJ:www.linux-magazine.com/issue/70/Sabayon_Pessulus.pdf+sabayon+pessulus&hl=en&gl=us&ct=clnk&cd=4&lr=lang_en)

---

### Post by MiXor on 2006-10-07
Cool!!
My first thought when I read your question was "wow, this is so cool!!" I am a new Ubuntu user and I am enjoying it a lot!! Had no problems installing anything, and there are good tutorials on the web to install additional hardware. I strongly recommend anything from [www.psychocats.net](www.psychocats.net), it is clear and it works. Besides, you can use _Gnome Art_, which you can install with synaptic, to match the interface of your desktops with the style of your Intenet café!!

All the best!

Aline

---

### Post by steve.horsley on 2006-10-07
**will it support windows base games like warcraft?**
Linux support for windows games is not good although I don't know the details. Maybe others can say more?

**is OpenOffice.org 2 supports .doc file format just like ms office?**
Yes, OOo supports .doc files and .xls and presentations. Most (but not all) media codecs are also supported on Linux.

**is it applicable to have this kind of OS in this kind of internet cafe?**
I believe so. I think it will prove more reliable and less effort to maintain (after the learning curve) than Windows.

**can i set users account for limited access of files and program, like theres an administrator account and a limited user account just like windows?**
Yes. Linux/unix has always been that way - it's one of the common complaints by newcomers to Linux from Windows - why do they have to enter a password before they can do administration? Users only "own" their home folder and have no rights to make changes elsewhere without that password.

---

### Post by aysiu on 2006-10-07
By the way, I'm not sure what the laws are in the Philippines, but it's entirely possible that enabling certain multimedia (say the ability to play Quicktime files from Apple Trailers) may be illegal on Ubuntu.

It's usually not that big a deal for home use, but if it's a business you're running, you may be held criminally accountable.

---

### Post by wombat20 on 2006-10-07
Great idea!

I can answer "Yes" to most of your questions.

OpenOffice does support MS .doc .ppt and .xls formats, although there are some minor formatting issues.  It can also export to PDF.

You can definately setup user accounts with limited privileges easily - you could have the same "guest" account on all machines.  People won't be able to mess anything up except the icons on the desktop.  It would be nice if there was a way to restore this and delete anything left in the /home/guest directory when they log out, so the next user doesn't find their pr0n sitting there.  You shouldn't have to worry about spyware or viruses.

There's isn't an administrive (root) account as such, but some accounts can be allowed to gain root priviledges by entering their password.  Read this for more details.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The only thing that isn't easy would be getting commerical games to work.  You can run some through WINE or pay a bit for Cedega, but there's no guarantee that they'll all work and it might need a bit of fiddling.  These forums should help you.

Good luck!

---

### Post by wombat20 on 2006-10-07
It's also a fantastic way to expose the public to Ubuntu Linux. :)

---

### Post by loell on 2006-10-07
hi ton_cut345, :)

i could say that ubuntu is a viable alternative os for internet cafes, especially here in our locality (Davao) where the local government is stricter in implementing software licenses.

---

### Post by sabitha on 2006-10-07
i use ubuntu for about 2 years since Hoary and i satisfy with this. all just fine except billing sofware i haved try cclfox [http://ccl.sf.net/]("http://ccl.sf.net/") but i dont know what is wrong with this sofware i can't use it. cclfox make all my client computer lock on cclfox login screen. i hope ubuntu have a sofware to manage internet cafe 8)

---

### Post by Anonii on 2006-10-07
> **ton_cut345 said:**
> Hi,

New in linux. especially here in ubuntu. Im planning to open a business. an internet cafe business where people rent my computers. and im planning to use ubuntu, since the windows os is to expensive. 

my question is ubuntu linux is userfriendly? will it support windows base games like warcraft?. is OpenOffice.org 2 supports .doc file format just like ms office?. is it applicable to have this kind of OS in this kind of internet cafe? and also, can i set users account for limited access of files and program, like theres an anministrator account and a limited user account just like windows?

thanks for your help.. :D
Nope. Dont try to set up a net cafe for games, with Linux.
Yes, some games may run on Linux. Probably all you need. But they need tons of configuration and some of them are not functioning correctly. So if you dont want tons of angry customers to whine about how their Warcraft crashed when they tried to create a unit, avoid Linux.
If you, now, want a net cafe just for web browsing. Email, chatting, forums, music downloading etc. I'd strongly recommend Linux.

Good luck.

---

### Post by ton_cut345 on 2006-10-07
Yup. i heard about wine. actually here in philippines, government have these programmers or a developer who develop a bayanihan linux. wine is already there. pack with the installer. but anybody knows where i can download a free timer for clients? i would like to ask what is a kiosk modes?.

thanks guys for your help. :D

---

### Post by fragos on 2006-10-07
Don't know about games but I've been a Linux user for years and have regularly save my work in Word, Excel and PowerPoint format for others to use without any problems.  Install the Microsoft fonts from the Ubuntu repositories and you'll never have any issues.  I've had problems when someone gave me a document with Ariel Narrow with text boxes of defined sizes because there isn't a direct translation to a Open Source fonts.  In a normal document Ariel Narrow the pages may break a differently but everything will look fine.

---

