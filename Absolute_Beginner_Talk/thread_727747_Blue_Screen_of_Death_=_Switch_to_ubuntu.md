---
title: "Blue Screen of Death = Switch to ubuntu"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by cerpin on 2008-03-18
Alright, I've had enough! 

No more then ten minutes ago I got the BSOD, it happened while closing down World of Warcraft. although I think the problem might lie in a virus infection.

as a little bit of background story, last night I was looking through the Warhammer Alliance forums and I saw a topic about WoW that sparked my interest, so i googled it. To my dismay the first link on the subject sent me to a website that uploaded a Trojan to my computer. :sigh: i didn't need an anti virus to tell me that, the web page seemed bunk. ever since then I've had slow load times, bogged up connection, etc,etc everything that comes with a torjan. whatever though, I suppose that is somewhat my fault.

Virus or not, Im tired of BSOD. Ive had to reformat atleast twice in 2007 because of windows related problems
Anyway, back to the topic at hand, I am contemplating a full switch to Ubuntu on my desktop computer.

Only thing stopping me though, is Video games!
yeah I play World of Warcraft, and when it comes out Warhammer online. The way things are going though looks like I'm gonna keep the gaming to my laptop(dual boot ubuntu/vista).

which brings me to wine, what do you guys think about it? is there any "better" programs out there?

whatever, its happening soon. I dont want to worry about viruses!
or spending 70 bucks on a good antivirus!

Anyway, I was just wondering if you guys had any advice for me.

blah sorry bout my rant, oh and sorry if this wasn't the right place to post this.

---

### Post by bvanaerde on 2008-03-18
World of Warcraft can be played on Ubuntu:
[Howto: WOW with Wine]("http://ubuntuforums.org/showthread.php?t=579378")

Warhammer online wil probably be playable with Wine, but I guess it will take some time after the release.

edit
Apart from all this, I hope you'll have a great Ubuntu experience :)

---

### Post by fain on 2008-03-18
Wine for WoW works great!!! as for Warhammer, i dunno i haven't tried it yet in beta, but if it is popular enough support most likely would be on its way soon.

There are a few applications that help with wine called crossover office and cedega. I believe cedega has its own implementation of directx so it has better support for windows games but neither program is free like wine is :(

Savage 2 has a linux port coming out soon so you might want to check that out.
[http://savage2.s2games.com/main.php](http://savage2.s2games.com/main.php)

a site about linuxgames theres many more but i have to goto work
[URL="http://www.linuxgamingworld.com/"]
http://www.linuxgamingworld.com/[/URL]

happy gaming!!

---

### Post by hyper_ch on 2008-03-18
keep a small windows partition (30-40gb)  for the games only... no need to get there AV or firewall or .... as you will not run anything of crucial importance there... for all the rest, use Linux ;)

---

### Post by cj2003 on 2008-03-18
Other guides that might help you
[Ubuntu, Wine and World of Warcraft]("http://ubuntu-news.net/modules/news/article.php?storyid=3912")
and
[Install World of Warcraft in Ubuntu Fiesty Fawn]("http://ubuntu-news.net/modules/news/article.php?storyid=2507")

---

### Post by cerpin on 2008-03-18
Thanks for all the help guys, I've also been thinkin bout waiting for Hardy to be released. Any thoughts on that?

Im also abit worried about compatability issues. Im using a old Dell, still in good shape though. 

I need to look up  my hardware and find out if im going to have any problems. the only thing im worried about is my NIC

---

### Post by pdnick on 2008-03-18
Or in the meantime try out Avast Antivirus, nice little program you can check out at download.com...


And it's free!

---

### Post by Duck2006 on 2008-03-18
Run the live cd to see if things work, befor you install. 8.04 will be out soon.

---

### Post by piousp on 2008-03-18
If i were you, i'll wait for Hardy... while i use Gutsy Live CD to try everything out!

---

### Post by bilal.17 on 2008-03-18
wine and WoW work really well

---

### Post by Bölvaður on 2008-03-18
> **cerpin said:**
> Thanks for all the help guys, I've also been thinkin bout waiting for Hardy to be released. Any thoughts on that?

I think it is a good idea, but you should expect troubles the first days. It will probably still be rough around the edges, so do not worry if something doesn't seem to work at first.

And with the xp partition to play games on... strip it down and estimate the space that partition needs. I will not give my xp more than 20 gb out of my 300gb hd (and then I got second one with ubuntu on it)

---

### Post by scramasax on 2008-03-18
> **cerpin said:**
> as a little bit of background story, last night I was looking through the Warhammer Alliance forums and I saw a topic about WoW that sparked my interest, so i googled it. To my dismay the first link on the subject sent me to a website that uploaded a Trojan to my computer. :sigh: i didn't need an anti virus to tell me that, the web page seemed bunk. ever since then I've had slow load times, bogged up connection, etc,etc everything that comes with a torjan. whatever though, I suppose that is somewhat my fault.

I'm more a Mac/Linux user these days but here goes ...

Windows security:

1.  Don't surf on an administrative account.  That's number one.  Set up a non-privileged account for day-to-day use and only use the admin account for administrative tasks.  There are some programs that won't run on an ordinary user account, so you'll have to log into the admin account to use those, too.  Otherwise, don't use it.  Certainly, avoid surfing on it or use something like "drop my rights" if you insist on doing so.

[http://www.securityfocus.com/infocus/1848](http://www.securityfocus.com/infocus/1848)

Note, IIRC, you can also right-click on a program and use "run as" the admin user.

2. Be careful where you go and what you do.  Besides that do you use Firefox, and do you use the NoScript extension with it?  I'd recommend you do.  I'd certainly avoid letting any random website run JavaScript and other active content on a Windows machine.

3. Always be up-to-date with patches, and run some good security software.  NOD32 and Kapersky are good Av tools, but Grisoft AVG is free for home users and pretty good.  But, to emphasize, (1) and (2) are probably more important than AV software.

> Virus or not, Im tired of BSOD. Ive had to reformat atleast twice in 2007 because of windows related problems

That's more likely a badly written driver.  These days people writing malware aren't attempting to crash your machine but to sneak on it and use it for spamming, DoS attacks, etc, without disturbing you.

Badly-written drivers can cause BSODs, which is why MS has changed the driver model in Vista.  Of course, that means there's a dearth of drivers for a lot of hardware, because the existing ones for XP don't work.

> Anyway, back to the topic at hand, I am contemplating a full switch to Ubuntu on my desktop computer.

Give it a whirl.  Try a live CD first and check it supports your hardware.  It runs a bit slow off the CD, but you can get a feel for it.

****

Seriously, if you're sure you've been compromised, flatten the machine and reinstall Windows.  Once something's got on a Windows machine, it's very difficult to be sure a machine is clean again.  Providing the live CD indicates to you that Ubuntu will run fine for you, you can dual-boot Ubuntu against a known clean Windows install.

NoScript:

[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

### Post by cerpin on 2008-03-19
Well I've actually tried AVG before, the bad thing is it found a virus i had once, but it did nothing to remove it, so I have somewhat of a personal grudge with it. otherwise it is a nice antivirus.

And about Gutsy, Im using it on my laptop as i type lol. do you mean on my desktop? because ill probably give that a try and see how things work.
I am Definatley going to be waiting for Hardy to come out though. im kinda excited. about it.

also excited to try out wine, I need to do some investigating though.

---

### Post by cerpin on 2008-03-19
Dang thats for all the advice.

I'm gonna start using a non-admin acount on my desktop, well atleast until hardy.

Funny that you mention the javascrip, because thats what it was. wouldn't go away wouldn't let me exit firefox.  I did a scan with kaspersky and NOD 32. Also did an online virus scan, before those two. think it got rid of it, but like you said you never really know.

thanks for the noscript link too, ill set it up now, that and the separate account lol.

---

### Post by misfitpierce on 2008-03-19
WoW works great or fine as said. Warhammer youll have to test yourself or google for info upon.

---

