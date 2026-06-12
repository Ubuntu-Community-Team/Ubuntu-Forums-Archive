---
title: "Upgrading Firefox?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by cutare on 2007-08-02
Hello everyone,

I am very new to Ubuntu and I have to say every day spent with this operating system is an enjoying challenge. I have one question, though: how do I install Firefox 2? My Ubuntu has Firefox 1.5 installed and I don't know how to upgrade it.

Cheers.

---

### Post by Hallvor on 2007-08-02
Are you using Ubuntu Dapper?

---

### Post by mike102282 on 2007-08-02
> **cutare said:**
> Hello everyone,

I am very new to Ubuntu and I have to say every day spent with this operating system is an enjoying challenge. I have one question, though: how do I install Firefox 2? My Ubuntu has Firefox 1.5 installed and I don't know how to upgrade it.

Cheers.

First I would enter the command in terminal sudo apt-get update
Then apt-get install synaptic
Then open Synaptic and search for Firefox and install

---

### Post by cutare on 2007-08-02
I am using Ubuntu 6.06, I don't know what Dapper is.

@mike102282: I did everything you said, Firefox is still 1.5 :(

---

### Post by laidback on 2007-08-02
Each release has a name as well as a number Dapper Drake is 6.06, Feisty Fawn is 7.04 and Edgy Eft is 6.10.

Is it possible for you to upgrade to 7.04. I'm running Firefox 2.0.0.6 (upgraded from 2.0.0.5 yesterday via auto updates). I'm finding 7.04 (Feisty Fawn) to be an improvement on 6.06.

---

### Post by Hallvor on 2007-08-02
Read this: 

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Dapper = Ubuntu 6.06

---

### Post by Seisen on 2007-08-02
You can try the directions here.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla")

---

### Post by Sunforge on 2007-08-02
Ubuntu releases a new version every 6 months. So far we've had:

4.10           20 October 2004                      Warty Warthog
5.04           8 April 2005                             Hoary Hedgehog
5.10           13 October 2005                      Breezy Badger 
6.06 LTS     1 June 2006                            Dapper Drake
6.10           26 October 2006                      Edgy Eft
7.04           19 April 2007                           Feisty Fawn 
7.10            Planned for 18 October 2007    Gutsy Gibbon 

So 6.10 and Dapper mean the same thing.

---

### Post by cutare on 2007-08-02
@Hallvor: I'm sorry for being such a newbie, but the instructions you provided seem extremely complex to me. Everyone is praising Ubuntu for the ease of installing software, so there must be an easier way for me to upgrade Firefox. Also, the wiki page states right in the beginning that various things will cease to function properly if Firefox 2 is installed using that method.

@laidback: you mean upgrading the whole operating system? Is all that hassle necessary just for upgrading the browser? I find it highly unusual. Also, I see from Sunforge's reply that Ubuntu 6.06 is barely a year old.

@Seisen: thank you very much for the link, but I'd prefer not to use third-party methods. As I said before, there should be an easier way to deal with this.

---

### Post by Hallvor on 2007-08-02
No problem. I am a newbie too.. :)The thing is that version 1.5 is frozen for Ubuntu 6.06 to increase stability. You will receive bugfixes and security patches, but not an upgrade from 1.5 to 2.0. I still use Ubuntu Dapper with version 1.5 because it has all the features I need, and I am also up to date with bugfixes and security patches. If the newer Firefox version 2.0 has features you can`t be without, you could upgrade to Ubuntu 7.04, with more bleeding edge software and perhaps a little more instability with it.

---

### Post by mcduck on 2007-08-02
> **cutare said:**
> @Hallvor: I'm sorry for being such a newbie, but the instructions you provided seem extremely complex to me. Everyone is praising Ubuntu for the ease of installing software, so there must be an easier way for me to upgrade Firefox. Also, the wiki page states right in the beginning that various things will cease to function properly if Firefox 2 is installed using that method.

@laidback: you mean upgrading the whole operating system? Is all that hassle necessary just for upgrading the browser? I find it highly unusual. Also, I see from Sunforge's reply that Ubuntu 6.06 is barely a year old.

@Seisen: thank you very much for the link, but I'd prefer not to use third-party methods. As I said before, there should be an easier way to deal with this.

6.06 is barely over a year old, but that also means that it's 2 versions behind already.

Anyway, there is no simpler way of installing version of Firefox that is not supported. The main problem here is that many other programs use Firefox's Gecko engine for HTML rendering, and Mozilla people refuse to provide Gecko as a separate package. So upgrading Firefox would upgrade Gecko, and so all the other programs using it should be upgraded too. And most likely there are more programs that depend on those, and they should also be upgraded and so on. There simply is no easy way to do this and still make sure that none of these upgrades results in any problems. Thus 6.06 still has the version of Firefox that it had in the first place.

Anyway, that's generally speaking the way how Ubuntu works. You get a new version with the latest and greatest software every 6 months, and after that no upgrades are provided for other than security reasons until the next Ubuntu version is released.

I really recommend upgrading to 7.04.

---

### Post by cutare on 2007-08-02
> **Hallvor said:**
> No problem. I am a newbie too.. :)The thing is that version 1.5 is frozen for Ubuntu 6.06 to increase stability. You will receive bugfixes and security patches, but not an upgrade from 1.5 to 2.0. I still use Ubuntu Dapper with version 1.5 because it has all the features I need, and I am also up to date with bugfixes and security patches. If the newer Firefox version 2.0 has features you can`t be without, you could upgrade to Ubuntu 7.04, with more bleeding edge software and perhaps a little more instability with it.

Wow, I have to say I am a little shocked. This is absurd. Where's the ease of use if Ubuntu forces me to upgrade the whole system just to get a newer Firefox? I suppose it's the same for every other piece of software in the repositories, and this is something I can't accept.

Is there any Ubuntu release that once installed will allow me to use it for at least two years but also to install whatever software comes up in the meantime?

---

### Post by cutare on 2007-08-02
> **mcduck said:**
> 6.06 is barely over a year old, but that also means that it's 2 versions behind already.

Anyway, there is no simpler way of installing version of Firefox that is not supported. The main problem here is that many other programs use Firefox's Gecko engine for HTML rendering, and Mozilla people refuse to provide Gecko as a separate package. So upgrading Firefox would upgrade Gecko, and so all the other programs using it should be upgraded too. And most likely there are more programs that depend on those, and they should also be upgraded and so on. There simply is no easy way to do this and still make sure that none of these upgrades results in any problems. Thus 6.06 still has the version of Firefox that it had in the first place.

Anyway, that's generally speaking the way how Ubuntu works. You get a new version with the latest and greatest software every 6 months, and after that no upgrades are provided for other than security reasons until the next Ubuntu version is released.

I really recommend upgrading to 7.04.

Sorry to ask, but how come it's so easy to upgrade Firefox on Mac OS X and Windows as opposed to Ubuntu? If they can do it, why can't Ubuntu do it?
Also, are you implying that Mozilla is at fault for this?

**Later edit**: if what you say it's true, Ubuntu can never be a replacement to Windows in my book. I was mislead by the word-of-mouth marketing, that says everything is so easy to install. I will replace Ubuntu with Windows XP as soon as possible, and that's a shame, because I was really looking forward to it. I would still like an answer to my questions, mcduck.

Thank you everyone, you've been helpful, at least that's true about Ubuntu: it has an awesome community.

---

### Post by BlackMeTaL on 2007-08-02
-

---

### Post by BlackMeTaL on 2007-08-02
> **cutare said:**
> Sorry to ask, but how come it's so easy to upgrade Firefox on Mac OS X and Windows as opposed to Ubuntu? If they can do it, why can't Ubuntu do it?
Also, are you implying that Mozilla is at fault for this?

**Later edit**: if what you say it's true, Ubuntu can never be a replacement to Windows in my book. I was mislead by the word-of-mouth marketing, that says everything is so easy to install. I will replace Ubuntu with Windows XP as soon as possible, and that's a shame, because I was really looking forward to it. I would still like an answer to my questions, mcduck.

Thank you everyone, you've been helpful, at least that's true about Ubuntu: it has an awesome community.

Linux is not Windows or OS-X, some things work different. You may better be off with Windows if you want full control over the versions of your software. Upgrading is a lot easier in Ubuntu so you could've just upgraded to Feisty and use Firefox 2 without problems.

---

### Post by cutare on 2007-08-02
> **BlackMeTaL said:**
> Linux is not Windows or OS-X, some things work different. You may better be off with Windows if you want full control over the versions of your software.

I am computer literate enough to tell the differences between different operating systems. I was merely implying Ubuntu does not stand to its fame. What good is it that I can easily install software, since my software choices are artificially limited by Ubuntu developers? It's more like "you can safely install whatever you want, as long as you install whatever we say you should install". Not acceptable, it's almost a form of vendor lock-in.

I still wish someone would answer my questions about what's so hard to implement an installation method similar to OS X (drag and drop .dmg files). If the answer is "just because this is the Linux way", I would have to say it's the wrong way for me.

---

### Post by Seisen on 2007-08-02
Well if you want to upgrade Firefox the supported way than upgrade to Edgy which I believe has Firefox 2.0. Actually it has the 2.0.0.6 version of firefox.

---

### Post by cutare on 2007-08-02
> **Seisen said:**
> Well if you want to upgrade Firefox the supported way than upgrade to Edgy which I believe has Firefox 2.0. Actually it has the 2.0.0.6 version of firefox.

You didn't get it either, I have a BIG problem with reinstalling/upgrading the WHOLE operating system just to get something trivial as Firefox 2.0.0.6. Even the sound of it pains me. It's miles away from what I expected from Ubuntu.

---

### Post by BlackMeTaL on 2007-08-02
> **cutare said:**
> You didn't get it either, I have a BIG problem with reinstalling/upgrading the WHOLE operating system just to get something trivial as Firefox 2.0.0.6. Even the sound of it pains me. It's miles away from what I expected from Ubuntu.

Then you're looking at it from a Windows viewpoint I think. The operating system is also just a bunch of programs working together. Upgrading system files and programs from one location is what I find an extremely powerful function. If you really want a certain version you can always compile from the source, but that would kind of defeat the purpose of the package manager.

---

### Post by mcduck on 2007-08-02
> **cutare said:**
> I am computer literate enough to tell the differences between different operating systems. I was merely implying Ubuntu does not stand to its fame. What good is it that I can easily install software, since my software choices are artificially limited by Ubuntu developers? It's more like "you can safely install whatever you want, as long as you install whatever we say you should install". Not acceptable, it's almost a form of vendor lock-in.
> **cutare said:**
> 
I still wish someone would answer my questions about what's so hard to implement an installation method similar to OS X (drag and drop .dmg files). If the answer is "just because this is the Linux way", I would have to say it's the wrong way for me.

You can install software very easily, as long as you don't mind that it's not always the latest version but instead one that has been tested to fully work with minimum problems with the rest of the OS and all the other programs.

It's matter of choice between stability and all the latest features.
Anyway, there are also Linux distributions that upgrade gradually instead of versions like Ubuntu. For example Gentoo allows you to always have latest versions of all software, usually as soon as they are released.

The choice is still yours, use the distribution that works the way you want. Myself, I think Ubuntu's 6-month release cycle is a great compromise between latest software versions and maximum stability.

edit: If the Firefox version and upgrading is such an issue, you could try Swiftfox. It's an optimized version of Firefox, and while the speed benefits are questionable it can be easily installed on your system while still keeping the old FF as well.  [http://getswiftfox.com/debian.htm]("http://getswiftfox.com/debian.htm")

What comes to mac/Windows-style installing of software, it's already done, check Autopackage, for example. But it's just not as good and easy way of the package-based system Linux uses so distributions (and most users) don't even want such thing. Mac/Win style program packages take more disk space, you need to update every piece of software separately, you need to find and download your software by hand from bunch of separate web pages and so on.

---

### Post by scrooge_74 on 2007-08-02
You can always go to Mozilla website download the source and compile it and get the lates version.

Remember the version you have of programs on a version of a distribuition are proven to work with not much troubles.

Newer versions of programs need to be adjusted to work with the rest of the system.

Firefox 1.5 may not have all the new little things, but it still works well for me.  Stability is an important issue for some people (like me).  One of my system is very stable using 6.06 so i dont need to messing around with it (same reason i use to have Debian stable).

Also for some apps there are backports (packages of new versions compiled for older systems)

---

### Post by Acglaphotis on 2007-08-02
You could have downloaded the tar file from mozilla and unzipped it on /opt. That way you could have Firefox 2. The thing is, you cant upgrade firefox on the **LTS** version. The lts version is not meant for it. You *can* have firefox 2 installed in /opt, but that doesnt erase the previous version of gecko if that is what you want. The lts version its for people who need (or want) stability and that means not always using the latest version of some packages.

---

