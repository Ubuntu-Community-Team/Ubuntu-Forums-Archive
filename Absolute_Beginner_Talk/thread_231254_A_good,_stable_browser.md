---
title: "A good, stable browser"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-08-07
Hello, up until now I have been using firefox but recently read an article on shashdot about it being a huge memory hog in exchange for speed. Even though it does not pose a big issue on my machine I don't like the idea of memory leaks. I just looked into epiphany but it does not seem too stable, for example: I opened up a site with flash and did not have the browser configured for flash so it just crashed rather than ask to install a missing plugin. In your opinion, what is a good, stable browser to use in Ubuntu? I was kind of thinking about checking out Opera but decided to ask here first on what you people thnk.

---

### Post by mcvos on 2006-08-07
I use Firefox now, but in the past I've been very happy with Opera. But when you have 200 webpages open at the same time, it still hogs an enormous amount of memory. With less excessive use, it's rumoured to be quite fast and possibly even light-weight.

---

### Post by Engnome on 2006-08-07
Opera! :D my favorite, consumes less memory while doing more things than ff.

They have .debs for dapper on their site.

---

### Post by orb9220 on 2006-08-07
Don't matter what browser you choose you are having problems with flash because all the sites are jumping on the falsh 9 bandwagon,

And adobe is slow to respond to linux users needs and are still waiting for linux version to catch up.

And the article is old about the memory leaks which are pre 1.5.0.3 issues which for the most part have been resolved in 0.4 and .0.5 yes there is still some and it is being improved.

Gnome has some called

Epiphany,Galeon,Mozilla-browser all in synaptic but they are limited and you will still have the flash problem.

Hope this helps.

---

### Post by Vlatko on 2006-08-07
i always prefer opera. even in windows. it's much faster, less resources and i just love the mouse gesture option. and the integrated email client. it rocks. :D

---

### Post by colo on 2006-08-07
Omg, I can't stand this any longer - there's so much bulls****hit floating around the web about memory usage, memory leaks and memory whatnot, and virtually EVERYTHING is coming from uninformed laymen who'd do better by not strinking a key at all. (This was not meant as an offense towards YOU, but those who keep on spreading this total garbage incessantly.)

As soon as a process is terminated, the underlying runtime libraries of the system the program links to immediately free() the memory it consumed. So if you feel like "firefox is hogging all my precious memory I don't need for ANYTHING else, really!", just close it, and restart it. By the way, I've been running firefox session for as long as 40 consecutive days without experiencing performance breakdowns of any kind.

As I've alluded to a few lines before, what are you using your memory for, anyway? If there's firefox running, let it take as much memory as it deems needed to provide you with a convenient browsing experience. Memory is not consumed just for fun, but for a reason - caching and buffering, for example. I'm _so_ sick of answering these "where's my RAM gone?"-questions over and over again. As long as you're not a developer or systems engineer eager to trim memory usage of projects you contribute to, you just should not care, mostly because of the fact you just cannot tell what's ought to be normal or best practise, and what's not.

On another note - I'm living without a flash-plugin for about three years now. Maybe you should try so, too - it's a relieving experience, really. Less annoying ads, animations, sounds... Flash is a rampant carcinoma in the tissue of the world wide web, and the less people use and depend on it, the better.

To finalize this and come to an answer for your initial question:
Stick with firefox. Its "Gecko" rendering-engine is fairly decent from a technical point of view, the browser is widely used and supported, and it's [free software]("http://www.gnu.org/philosophy/philosophy.html#AboutFreeSoftware") - that's the reason why you should be using it.
Opera, on the other hand, is gratis, but not free. Its code quality might be top-notch nonetheless, but there are moral implications you should take into account when opting - or not opting, which I recommend you to - for it.

Convenience must not win over freedom.

---

### Post by nexus_6 on 2006-08-07
<3 colo <3
to add some personal experience, i've never ever reached 350+MB memory usage on my 512MB(64M shared) laptop, even if desperately trying. use firefox.

---

### Post by MrHorus on 2006-08-07
> **mcvos said:**
> But when you have 200 webpages open at the same time, it still hogs an enormous amount of memory. 

Well with 200 pages it would do, yes but out of curiosity why do you need TWO HUNDRED web pages open at the asme time? :)

---

### Post by Colonel Kilkenny on 2006-08-07
Some people do have problems with FF and it's memory consumption so telling them that there is no really problem is quite stupid. And some of us don't wanna be restarting browser all the time..

I personally don't have that problem with FF and don't even use it much, because I prefer using the best browser (IMHO) which has been Opera for many years and seems to be in future also. But use whatever feels like the right one. Personally I won't give a damn if application is closed source as long it is outstanding piece of software engineering and beats the alternatives.

edit. open -> closed

---

### Post by tturrisi on 2006-08-07
fastest stable browser I ever used on a linux system is dillo:
[http://www.dillo.org/](http://www.dillo.org/)
There are also version called floating around called dillo-hacked that have more features.

---

### Post by David Corrales on 2006-08-07
> **colo said:**
> Omg, I can't stand this any longer - there's so much bulls****hit floating around the web about memory usage, memory leaks and memory whatnot, and virtually EVERYTHING is coming from uninformed laymen who'd do better by not strinking a key at all. (This was not meant as an offense towards YOU, but those who keep on spreading this total garbage incessantly.)

As soon as a process is terminated, the underlying runtime libraries of the system the program links to immediately free() the memory it consumed. So if you feel like "firefox is hogging all my precious memory I don't need for ANYTHING else, really!", just close it, and restart it. By the way, I've been running firefox session for as long as 40 consecutive days without experiencing performance breakdowns of any kind.

As I've alluded to a few lines before, what are you using your memory for, anyway? If there's firefox running, let it take as much memory as it deems needed to provide you with a convenient browsing experience. Memory is not consumed just for fun, but for a reason - caching and buffering, for example. I'm _so_ sick of answering these "where's my RAM gone?"-questions over and over again. As long as you're not a developer or systems engineer eager to trim memory usage of projects you contribute to, you just should not care, mostly because of the fact you just cannot tell what's ought to be normal or best practise, and what's not.

On another note - I'm living without a flash-plugin for about three years now. Maybe you should try so, too - it's a relieving experience, really. Less annoying ads, animations, sounds... Flash is a rampant carcinoma in the tissue of the world wide web, and the less people use and depend on it, the better.

To finalize this and come to an answer for your initial question:
Stick with firefox. Its "Gecko" rendering-engine is fairly decent from a technical point of view, the browser is widely used and supported, and it's [free software]("http://www.gnu.org/philosophy/philosophy.html#AboutFreeSoftware") - that's the reason why you should be using it.
Opera, on the other hand, is gratis, but not free. Its code quality might be top-notch nonetheless, but there are moral implications you should take into account when opting - or not opting, which I recommend you to - for it.

Convenience must not win over freedom.

First of all... chill out man. I know we all get frustrated from time to time if people ask the same questions over and over, but a decent and informative response will work much better than a rant 100% of the time.

About the Firefox thing, I do find that it usually takes a big chunk of memory after a while but most of it goes to caching so you can see pages already opened real fast if you go back to them. Some can even be preloaded.
In fact, in the linux world, memory is aggresively cached with user data to speed up the opening of programs and the overall experience. Good RAM is RAM put to use.

Concerning Opera, although it's closed source and whatnot I don't see any problem about using it. It's free and if it works wonders for you, go ahead :)
Same with flash plugins, you simply can't deny the fact that the web without flash wouldn't be the same place (and in a positive way, it does a lot of life to pages).
Personally I didn't find Opera easy to grasp and use from the start so I like my Firefox.

---

### Post by darrenm on 2006-08-07
I find Firefox 2.0 beta to be excellent with memory at the moment:

[http://www.mozilla.org/developer/#builds](http://www.mozilla.org/developer/#builds)

---

### Post by colo on 2006-08-07
Repeat after me: Ignorance is bliss.

---

### Post by andlinux21 on 2006-08-07
Dillo is very nice I think i will go searching for that dillo hacked he was talking about.:-k

---

### Post by robins_web on 2006-08-07
*On another note - I'm living without a flash-plugin for about three years now. Maybe you should try so, too - it's a relieving experience, really. Less annoying ads, animations, sounds... Flash is a rampant carcinoma in the tissue of the world wide web, and the less people use and depend on it, the better.*

Hear, hear! Flash, Shockwave and fancy tricks with Java or Javascript help websites draw attention away from the fact that they actually have very little content to hold you attention. They're a lot like television and the movies in that respect: if you don't have a plot, characterization, or decent dialogue, thrwo in a special effect.

If I come across a site that requires Flash or Shockwave, I simply navigate elsewhere.

Content and information should be what brings you to a site--not its presentation. If you want moving pictures, get an XBox or watch TV.

---

### Post by nexus_6 on 2006-08-07
for the sake of all of us, wouldn't it be more efficient trying to improve and integrate free software like firefox (which after all, everyone can at least try to work on) instead of supporting closed source apps without having any idea of how they work at all? 

ps.: yes, i dare to ignore the fact that this is not point of the discussion, kthx

---

### Post by davebgimp on 2006-08-07
> **darrenm said:**
> I find Firefox 2.0 beta to be excellent with memory at the moment:

[http://www.mozilla.org/developer/#builds](http://www.mozilla.org/developer/#builds)

The memory hogging is still a problem, worst being with OSX. From what I've heard and please take it with a grain of salt because I can't seem to find a link to support it - the memory-hogging issues with Firefox that occur in Linux builds and OSX will not be fixed until 3.0, sometime next year.

With that said, I use Firefox 2.0 on all my computers. I have some friends who get pissed at the memory problem, but in truth, it's never really affected my usage so I pay it no mind.

The curse/blessing with Firefox, for me is the extensions. I've become so addicted to certain ones that any other browser just won't do. I'm not sold on FF as much as I am addicted to it's extensions. ;)

As far as stability, it's really Flash that's been the problem for me. Currently, I have zero issues, but just a couple months ago, any flash on a page would crash FF.

---

### Post by mcvos on 2006-08-07
> **colo said:**
> 
As soon as a process is terminated, the underlying runtime libraries of the system the program links to immediately free() the memory it consumed. So if you feel like "firefox is hogging all my precious memory I don't need for ANYTHING else, really!", just close it, and restart it.

And if you think Windows is getting slower, just reboot it! Or reinstall, even. Thing is, these are all workarounds for software bugs. Well written software doesn't have to be restarted regularly because of memory leaks (unfortunately, memory leaks seem to be incredibly common nowadays).

And I prefer not to close my browser at all. I usually have a lot of weg pages open, many of which I'll probably need again real soon. (This is also how my Opera session accummulated 200 weg pages, but I admit that was excessive.)

> 
As I've alluded to a few lines before, what are you using your memory for, anyway?

For other processes. I usually have a couple of JVMs running, Eclipse, a whole bunch of tools for a variety of purposes. Memory can vanish quickly if you're not just a casual user.

Although for me, memory isn't the issue with firefox. My two problems with it are that it crashes occasionally (though not often) and that it doesn't always render XML properly. And the Ubuntu version renders some things in (x?)html differently (and worse) than the Windows version. But other than that, it's a brilliant piece of software.

> 
On another note - I'm living without a flash-plugin for about three years now. Maybe you should try so, too - it's a relieving experience, really. Less annoying ads, animations, sounds... Flash is a rampant carcinoma in the tissue of the world wide web, and the less people use and depend on it, the better.

I agree there. Flash is abused for the most horrible junk. The only good reason to use Flash is when the flash *is* the content. Games and animations are the only things that should be done with flash. But unfortunately there are too many sites that use flash for navigation, or for simple text-and-pictures content.

---

### Post by jis on 2006-08-08
Currently Opera passes Acid2 Browser Test unlike Gecko browsers.

---

### Post by mcvos on 2006-08-08
What is Acid2 Browser Test?

---

### Post by Linux4HumanBeings on 2006-08-08
For me Opera is much more slower than Firfox but Firfox sometimes unexpectdly quits for no reason. But you can always restore your session

---

### Post by Jagot on 2006-08-08
> **mcvos said:**
> What is Acid2 Browser Test?

[http://en.wikipedia.org/wiki/Acid2](http://en.wikipedia.org/wiki/Acid2)

---

### Post by powder on 2006-08-08
Ladies and gentlemen,

Firefox memory leaks only affect some users on some systems.  This only happens when firefox is left open for long periods of time (days).  Firefox using a large amount of memory does not mean you have a memory leak.  To this I say what good is memory if you're not using it?

Thank you.

---

### Post by Karlos on 2006-08-08
> *On another note - I'm living without a flash-plugin for about three years now. Maybe you should try so, too - it's a relieving experience, really. Less annoying ads, animations, sounds... Flash is a rampant carcinoma in the tissue of the world wide web, and the less people use and depend on it, the better.*

I totally agree. I find flash incredibly annoying thats why I use firefox.
it has an extension that will replace flash elements with a play button.
I also have adblock installed which cuts out most ads, which is nice.

in answer to the original post my favourite is konquorer its a very fast and stable browser. trouble is it works best in kde which is not very stable, I find it freezes up a lot and fills up my swapspace all the time so at the moment its gnome and firefox for me.

---

