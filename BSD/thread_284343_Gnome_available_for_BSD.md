---
title: "Gnome available for BSD"
date: 2006-10-25
forum: BSD
---

### Post by raqball on 2006-10-25
I just learned that gnome 2.16 is now available for BSD!

Downloading FreeBSD now and will give it a whirl!

I will post back with my findings :)

---

### Post by raqball on 2006-10-25
Ok, I tried FreeBSD, PCBSD, and DesktopBSD

I did not tinker with them much as I am spolied by Ubuntu and if it dont work out the box like Ubuntu does I will not spend much time tinkering.

BSD is NOT ready for primetime yet! All 3 of the above failed to get wireless working and all 3 failed to detect sound.

I was able to get wireless working fairly quick in all by using:

kldload if_iwi
iwicontrol iwi0 -d /boot/firmware -m bss
ifconfig iwi0 up

The problem is that new users will have a hard time figuring this out. Next up the sound issues:

Tinkered for about 10 minutes and gave up!

Back to good ol Ubuntu 6.06! BSD is just not ready for primetime in my opinion plus, I do not like KDE. I never got to try gnome out because I grew weary of tinkering with it and went on to the next BSD distro. None impressed me right out of the box!

EDIT:
I will say that setup was very easy in all 3 and that LAN worked right out of the box on all 3 distro's

---

### Post by xCM329 on 2006-10-25
BSD has been out for a longer time than linux.  You just have to make sure you have the compatible hardware.  Don't go insulting it just yet, it is much more stable than Linux and I find it superior.  You have to understand the differences.  Look at my post in Linux vs. BSD

---

### Post by raqball on 2006-10-25
I was NOT trying to insult BSD... I think it's a great os... I just dont think it's quite ready for the masses to drop windoze and use it..

I could have tinkered with it and got it working just fine, but dont think many novices could. AND... I really do not like KDE, but that is just me as I think it's to windozey like.

---

### Post by tseliot on 2006-10-26
AFAIK the new GNOME will use HAL also on FreeBSD. And that's great. It means automounting and all those things we are used to use in Ubuntu.

---

### Post by srt4play on 2006-10-27
> **raqball said:**
> BSD is NOT ready for primetime yet!

You sound like the folks who come in talking about how Linux isn't ready for the desktop.  In reality BSD is ready and is being used happily by plenty of folks.

---

### Post by raqball on 2006-10-27
No not really but if Linux works on just about EVERY system I have put it on and BDS has worked on 1 in 5 then you can do the math :)

Edit:

When you quoted me you forgot to include the **in my opinion** part :)

---

### Post by srt4play on 2006-10-27
So BSD doesn't do what you need it to do. That means that it's "not ready"?

Ok, let's do the math.  

you + bad experience = BSD sucks  ??

You said yourself that you didn't bother to tinker with it because you're spoiled by ubuntu.  Well, a lot of ubuntu installations wouldn't work perfectly without some tinkering.. so does that mean Linux is "not ready"?

---

### Post by raqball on 2006-10-27
> **srt4play said:**
> So BSD doesn't do what you need it to do. That means that it's "not ready"?

Ok, let's do the math.  

you + bad experience = BSD sucks  ??

You said yourself that you didn't bother to tinker with it because you're spoiled by ubuntu.  Well, a lot of ubuntu installations wouldn't work perfectly without some tinkering.. so does that mean Linux is "not ready"?

You are taking this WAY to personal and please show me where I said BSD sucks???? I have used BSD in the past of desktops and was happy with it. Do you really think a 1st time user changing over from windoze could get wireless and sound working in BSD? That was the jist of my post. I personally think BSD is great as long as you know what you are doing.

Please do not put words into my mouth (post) as I NEVER said BSD sucks!

---

### Post by xCM329 on 2006-10-28
BSD has been around longer and has been proven to be stronger than Linux.  Linux has more support for drivers, but that is because of its nature.  BSD is however more stable and can do everything linux can do (including running linux binaries).  Just because you had a bad experience with unsupported hardware does not mean that it is not ready for prime time.  Please eductate yourself in the field of the different *NIX OS's before you jump down BSD's throat.

---

### Post by raqball on 2006-10-28
> **xCM329 said:**
> BSD has been around longer and has been proven to be stronger than Linux.  Linux has more support for drivers, but that is because of its nature.  BSD is however more stable and can do everything linux can do (including running linux binaries).  Just because you had a bad experience with unsupported hardware does not mean that it is not ready for prime time.  Please eductate yourself in the field of the different *NIX OS's before you jump down BSD's throat.

Why is everyone from the BSD side so STUCK on themself like they are some type of PC GOD and everyone else is an idiot?

You guys are really turnung me off to ever try that os again! Best of luck with your bsd :)

---

### Post by raqball on 2006-10-28
Also,

Can you BSD'ers read what is actually typed or does it have to be in code for you to understand it? I can try using the biggest font they have here and see if that works...

I never said I had a bad experience with BSD, I said it did not work right out of the box!

I never said I could not get it working, I said I did not want to tinker with it!

Do you really think if you stood outside a store and handed 100 BSD disks out that joe and Jane smith could get it working and stick with it? I think not! I imagine 1 out of the 100 windoze user might stick with it, hence my NOT ready for prime time yet comment. If BSD want to gain users who know nothing it has to work out of the box or it will end up in the trash can... I know I wrote this in english but feel free to translate to code if it helps you understand it.

I am NOT a computer god, but I do have a degree in computer science...

Have a nice day! :)

---

### Post by hey_ian on 2006-10-29
BSD is really nothing for home PC use. It is stable and does not have such big software repos as Linux does - just perfect for server use, nothing more.

---

### Post by kazuya on 2006-10-31
I have not used BSD, but have read some on it. It is definitly a proven OS. Liking BSD is a matter of preference. For certain power users who perhaps may like to do the itigrity aspects of their OS and maintain a speedy feel about their system, I can see where BSD maybe preferred. As for most new users, with no knowledge or curosity, BSD may not fit the bill. The same could be said for the linux distros as well. 

I conclude by saying that they are both good in their different ways. I think the term primetime seemed insulting to the poster because, he would rather it was said that BSD generally takes more work on user part than Ubuntu to setup. Saying not ready fro primetime is like a put down in his book. Then again, it is the user's opinion.

So to each their own. I use gentoo-based, slack-based, debian-based distros. I may eventually try out PC BSD as well.

The slack system I use currently, which I am starting to prefer over Ubuntu uses systems similar or obtained from BSD. Having said that I dare not insult the collaborative effort of either side. They are all wonderful and totally ready for Primetime in my book. The users have to become intelligent enough to use the OS and contribute, hence they should just accept and use what they fell suit them at the moment.; But that doesn't give them the right to insult the efforts or put down the great acchievement of that other OS...

---

### Post by slimdog360 on 2006-11-02
I'll have to try out gnome next time I install freebsd. Though I think I'll wait till I get a new computer first, I've got ubuntu working just the way I like it. Not to mention the fact that I needed to follow two guides to get freebsd installed, up and running properly with kde. Its a mission I can tell you.

---

### Post by veganbabian on 2006-12-29
Hey, raqball, I am a NetBSD user and I know what you mean with some of the bsd-users think they are pc-gods...

In my opinion BSD is more unix than linux but it does not make me as a bsd user more elit.
I tried Ubuntu, and I work with it every day, but it is booring, its to "out of the box" for me.

No elitism, just using an outher operating system.

---

### Post by neowolf on 2006-12-31
> **raqball said:**
> I was NOT trying to insult BSD... I think it's a great os... I just dont think it's quite ready for the masses to drop windoze and use it..

I could have tinkered with it and got it working just fine, but dont think many novices could. AND... I really do not like KDE, but that is just me as I think it's to windozey like.

Its not supposed to be a mainstream desktop OS. ISP's use it alot because of its incredible stability. I'm looking forward to the Debian/BSD ports that being worked on, using apt-get and dpkg would make BSD alot easier I think :)

---

### Post by malaprohibita on 2007-01-06
> **neowolf said:**
> Its not supposed to be a mainstream desktop OS. ISP's use it alot because of its incredible stability. I'm looking forward to the Debian/BSD ports that being worked on, using apt-get and dpkg would make BSD alot easier I think :)

That would be awesome.

---

### Post by kazuya on 2007-01-08
I look forward to that.

---

### Post by justin whitaker on 2007-01-09
> **raqball said:**
> BSD is NOT ready for primetime yet! 

Whoa, what? I'm running PC-BSD on one drive, Ubuntu on the other, and I have to say...BSD is ready. Maybe not 100%, but no operating system is.

---

### Post by raqball on 2007-01-18
See next post

---

### Post by raqball on 2007-01-18
This forum sucks A$$... I get warned for telling these BSD IDIOTS that they are stuck on themselves? There you go mods... Ban me NOW!!!!!

---

### Post by IYY on 2007-01-18
> This forum sucks A$$... I get warned for telling these BDS IDIOTS that they are stuck on themselves? There you go mods... Ban me NOW!!!!!

This community is focused on being accepting and understanding. Insulting other operating systems, even if it's Mac OS or Windows, is not allowed.

---

### Post by raqball on 2007-01-18
I stated an opinion and I was attacked for it... ALL I said was that BSD was not ready for primetime... I get a PM warning me? LOLOLOL ban me now please... To Suse 10.2 I go.....

---

### Post by SlCKB0Y on 2007-03-10
> **raqball said:**
> I stated an opinion and I was attacked for it... ALL I said was that BSD was not ready for primetime... I get a PM warning me? LOLOLOL ban me now please... To Suse 10.2 I go.....

People take offense when you make statements like this. These same people are much more likely thinking that it is YOU who are not ready for primetime. That is, if you are not willing to at read the very very very good freebsd handbook. 

If you are expecting bsd to be just another linux distro, then yes you will find it hard, just as all those people who come to linux wishing it was more like windows will have a hard time.

---

### Post by handy on 2007-03-11
@**raqball**:  If you had of said ***from your experience***, or ***IMHO, BSD doesn't look like it's ready for primetime...***, you wouldn't have provoked as many rebukes as you did.  I think that perhaps you may have been a little careless in the use of language, which caused your statement to not truly reflect your meaning, which is so easily done in forums unfortunately. :-(

I am typing this from a PC-BSD box which I love using.  If Cedega worked on it I would not have another machine running Edgy.  (By the way, Edgy won't run properly on the machine that BSD is on, & BSD won't run on the machine that Edgy is on!) 

PC-BSD has access to well over 15,000 FreeBSD programs as well as being able to run Linux softwares too.

M$ used to use BSD servers to host Hotmail!  So, yep BSD is stable.

As far as **primetime** is concerned:  The way I see it is that anyone who is not using windows is in a lottery as far as their hardware support is concerned.  ATI graphic card owners & so many wireless users in particular are familiar with this problem.  

As it turns out, due to the [***_simpler & more open BSD license_***]("http://www.freebsd.org/doc/en_US.ISO8859-1/articles/bsdl-gpl/article.html"), the user is more likely to find proprietary firmware support in BSD, to an extent that could never be supported by Linux due to it's license.

Linux is great, so is BSD!

[***& Haiku is with us soon!!!***]("http://haiku-os.org/front_page")

Aren't we lucky!? :guitar:

---

