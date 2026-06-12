---
title: "Does ANYTHING actually run on Wine?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-26
Hi,

I had a go at ***wine*** yesterday with some of my Windows applications like Winamp 5.24, WinRAR 3.6, Adobe Photoshop CS2 and Cool Edit Pro. After all the effort, I was very disappointed...

First, I ran ***winecfg*** and tried to set it up as I saw fit, which may actually not be the best setup.

Anyway, Winamp installed fine but it was INCREDIBLY slow especially when running wine in WinXP mode. Switching to Win98 improved things a bit but I was still not impressed. As for the actual functionality, it does play music but I didn't go through all the setting to check what works and what doesn't. For an application which is listed on the wine site as one that supposedly works on wine I must say that things could be improved A LOT. The good thing however is that there are very good Linux multimedia players out there so you don't really have to go to the trouble of installing Winamp on wine. ;) 

WinRAR also installed fine but then it just wouldn't run, the graphical interface I mean. The command line rar woked ok though. Good thing there is a linux rar available to install on one of the non-free repositories and that works very well! ;) 

Getting on to Adobe Photoshop, there is actually a screenshot of this running under linux on the wine website. My attempt was however unsuccessful... :-? It wouldn't even install... So I guess I'll stick to Gimp for now. ;) 

And finally, Cool Edit Pro didn't finish installing either...

This makes it... 4 tries -> 0.75 successes (0.5 x Winamp + 0.25 x WinRAR) - umm... not that good I guess...

Anyway, if anyone's got a better experience with wine  please let me know if there are some optimum setting and if there is any twitching that can be done. 

For now however I guess I'll stick to Linux applications in Linux and Windows applications in Windows. 8)

---

### Post by risbac on 2006-07-26
Your conclusion is saying it all. I understand that you may need some high-end applications like Photoshop, but to use Winrar and Winamp in Linux is clearly looking for problems. To me there are good equivalents on Linux, so it's better to spend some time trying some, then working with native applications.

I wish there were for all domains... If you want to edit videos, you are clearly in trouble. But sooner or later... : )

---

### Post by Ziox on 2006-07-26
since i used to be a gamer, i managed to run diablo II LOD using wine. Full screen caused the game to be extremely slow, but when i ran the game in windowed-version, it ran almost as smooth as in windows(tm)

---

### Post by GuitarHero on 2006-07-26
Why would you need Winrar?  And yes Winamp is good but so is Listen and AmaroK.  Photoshop I understand.

---

### Post by s_h_a_d_o_w_s on 2006-07-26
Exactly, you could just use xine or beep-media-player instead of winamp. For cool edit pro and photoshop, search on google, you might find it. For winrar, a substitute: unrar.

---

### Post by ovimunt on 2006-07-26
I didn't say I actually need to run any of those appications in Ubuntu, I still have WinXP installed on my computer for when I need Photoshop for example. 

I was only experimenting...

---

### Post by GuitarHero on 2006-07-26
Ah. Well Cool Edit Pro is a sound recording program right?  Try Audacity.

---

### Post by ovimunt on 2006-07-26
Cool Edit Pro is actually a professional and quite powerful sound editing tool.

It does quite a lot of stuff like removing noise from your old magnetic cassetes which you have decided to finally store in a digital format or you can get rid of sound artifacts on old vinyl discs and so on...

---

### Post by aysiu on 2006-07-26
Here's a list of some packages that work in Wine:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

I've tried and have successfully run in Wine... Internet Explorer (using the IEs4Linux script), Firefox, and FileZilla.

---

### Post by JoWilly on 2006-07-26
I always got wnirar working perfectly in wine, at least for the past year.

Photoshop CS/CS2 does not work; photoshop 7 does.

A nice app that I use regularly with wine and that is still missing in linux is dvdshrink.

Many things work with wine, even games like world of warcraft. But this doesn't mean everything works...

---

### Post by digivation on 2006-07-26
as to the DVDShrink problem, I hear (but havn't tried) that k9copy works ... you could give that a spin. [http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/)

or 

```
apt-get install k9copy
```

---

### Post by JoWilly on 2006-07-26
> **digivation said:**
> as to the DVDShrink problem, I hear (but havn't tried) that k9copy works ... you could give that a spin. [http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/)

or 

```
apt-get install k9copy
```

Looking at the screenshots k9copy seems to have improved since I last checked it out.

But can it re-author a dvd as dvdshrink does ?

And what about the quality ? Because at about ~60% shrinking the linux apps "were" not as good when I tried them.

---

### Post by Kilz on 2006-07-26
> **JoWilly said:**
> Looking at the screenshots k9copy seems to have improved since I last checked it out.

But can it re-author a dvd as dvdshrink does ?

And what about the quality ? Because at about ~60% shrinking the linux apps "were" not as good when I tried them.

K9copy is a good program. I use the 1.0.4 version. [Its available from this german repository.]("http://www.kubuntu.de/index.php?option=com_content&task=view&id=48&Itemid=70") It re-author's and the 1.0.4 is better than some of the previous versions on quality. But nothing is going to give you fantastic results with 60% compression. Thats why you re-author, to get rd of all the stuff you dont need to make it compress less.

---

### Post by echo $USER on 2006-07-26
Try GIMP instead of Photoshop.  It has a few less features but its like $500 bucks cheaper.

And for dvdshrink try xdvdshrink...

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

---

### Post by wog on 2006-07-26
From scoping out the WineHQ page I discovered there's still a long way to go as far as functionality. If you want something to work, you have to sign in and see if you can get error messages addressed to shore up functionality until your chosen application or game works properly.

Visual Basic functions work. DirectX functions only half work, and since most games these days are based largely on DirectX, that means a lot of games won't work.

I venture to say Wine will run nearly anything more than a couple decades old, with few exceptions. Okay, maybe a decade old... :p

---

### Post by orb9220 on 2006-07-26
I am using dvdshrink and xnview just fine. DVDshrink has no problems and rips dvd's about 10-15 mins faster than k9. 

 Xnview great acdsee like freeware they have a linux version but it sucks compared to the windows version.

 And I have tried k9 just a bit slower than shrink not as powerful,k3b it still has some issues alot of people still have problems with it. gnomebaker is ok but has troubles to. 

 Now amoraK 1.4.1 for kbuntu I use for my music collection and rocks. And I use to use Cooledtit and it does rock but have found an equivalent in linux. Video has some promising apps like Kino and such. I keep my eyes open until then.

 I think the word for the windows to linux tranisition is equivalent and on the fronts of Games,CD-DVD,Video,Audio linux isn't quite there.

 I was wondering why linux is lagging behind in these area's and the only reason I could think of is the Die-Hard Linux User's prefer the terminal and type in commands. I could be wrong but that is the only thing I can think of why no comparable gui stuff.

 Now I am not condeming the term but IT Is not the best alternative for everything unless you have fabulous typing and memory skills.

 And I am a converted xp user who now is in Ubuntu 6.894838 Days a week. If you are offended when I critize what I consider weak area's it is to make linux better. You are going to see more and more convert's that will be asking for more and more gui based solutions that may already exists in the term world.

---

### Post by JoWilly on 2006-07-26
> **Kilz said:**
> But nothing is going to give you fantastic results with 60% compression. 

Sure. What I was saying is if one app gives better results than the other when compression is difficult, I prefer to use it. Thats why I use dvdshink and not the linux apps.

But as I asked before, if the compression quality of the linux apps has improved since I last tried them, I might use them. Has anyone done a recent comparison at 60% compression ?

---

### Post by orb9220 on 2006-07-26
In dvd shring 60% compression setting means of Orig. so it is actually 40% percent of compression.

---

### Post by JoWilly on 2006-07-26
> **orb9220 said:**
> In dvd shring 60% compression setting means of Orig. so it is actually 40% percent of compression.


Yeah, we know that, you can rephrase it as you want.

The question was about comparing image quality, you have anything on that ?

---

### Post by orb9220 on 2006-07-26
Well my k9 copies are about the same as the dvdshrink ones. Except k9 takes about 10-15 mins more on same title. But the quality seems about the same.

---

### Post by JoWilly on 2006-07-26
> **orb9220 said:**
> Well my k9 copies are about the same as the dvdshrink ones. Except k9 takes about 10-15 mins more on same title. But the quality seems about the same.


Even with a lot of compression and the sharpness option set in the dvdshrink prefs ?

If so thats good news.

Thanks for your report.

---

### Post by orb9220 on 2006-07-26
I don't even use the sharpness option. And to clarify I play my movies on an older tv not a High quality HDTV or a huge 32" so you may see the difference on Higher quality gear.

---

### Post by JoWilly on 2006-07-26
> **orb9220 said:**
> I don't even use the sharpness option. And to clarify I play my movies on an older tv not a High quality HDTV or a huge 32" so you may see the difference on Higher quality gear.

Yeah, you said it.... I'm on a widescreen and don't like blockyness.

If it is not good enough in dvdshrink I shrink (re-encode) the movies with cce or procoder2.

---

### Post by Sandsound on 2006-07-27
All my homemade win-programs (made with Delphi) works fine under Wine, so does all my VST-instruments (use them for LMMS), even those who nead a dongle... ahem ;-) 

For audioediting i use Rezound, not as userfriendly as Audacity thou, but combined with LMMS it does all that I use to do in Cubase.

I have had some problems with Vocaloid under Wine, but nothing I cant work around. Rise Of Nations is the only reason why my Windoze-partition have survived.

---

### Post by Lord Illidan on 2006-07-27
Well, Winamp is not really that supported because XMMS, Listen, Amarok, Beep Media Player and the like beat the hell out of it, imho.

Ares works on Wine, that I can confirm.

Picasa works on Wine too...heh.
Starcraft and Warcraft 3 work on Wine if a little slowly.

Otherwise, yes, there's a lot to improve, but they are doing their best.

---

### Post by hw-tph on 2006-07-27
The only Windows-only program that I rely on is the game Championship Manager. It works equally well in Wine as in Windows (meaning - dog slow, but that's not Wine's fault!).


Håkan

---

