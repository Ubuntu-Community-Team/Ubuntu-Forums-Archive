---
title: "Firefox flash9 plugin almost killed my CPU!!!!"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-02-11
I was reading a flash website and then left my laptop for a short time. When I came back the screen saver (blank screen) was on and I noticed a very loud noise coming from the fan. I logged back in to check the CPU temp with acpi -t .....and it was 87°C 	:shock: I then checked what was causing a high CPU usage and it was firefox. After closing firefox the CPU temp went down to normal levels around 50°C.

After experimenting a little bit I found that flash9 was causing an extremely high CPU usage. This is the last problem of a long serie on Ubuntu. I know it's flash and not Ubuntu that caused the problem but it seems there are just too much things that go wrong with linux for me. I'm now considering going back to XP because I cannot seem to get a useable system with Linux. I mean Ubuntu is great for a free software but I don't think that the Linux world can give me really what I need reliably, and this temperature issue on something as simple as a flash website just makes me mad because the idea of freezing a CPU that normally never gets hotter than 61-62°C just by leaving the computer on a flash website for a small time. Again this was not directly a Ubuntu problem but I need flash anyway and the fact is that everything I need works almost flawlessly on XP while it is clearly not in Ubuntu.

Anyway for the time being, if you have any solution for this temperature issue, please le me know. I have a Centrino Sonoma 1.86Ghz CPU and the fan goes on at 60°C...and it has never gone above 62°C even at 100% CPU usuage. I cannot understand why with firefox flash websites on Ubuntu the CPU gets to 100% usage too but the temperature can go way above 60°C........

---

### Post by shareMenaPeace on 2007-02-11
Do you play any 3D games? How is the temperature with an 3d  intense game?
What is the working temperature for this cpu?

Intel mobile pentium M can be up to 100 Celsius but normal max temerature s around 80 there are websites for this i searched mine cpu too. Well dont find the link rightnow...

---

### Post by %hMa@?b&lt;C on 2007-02-11
holy crap... my opteron is running @40 degrees celcius, and I thought that was warm.

---

### Post by kerry_s on 2007-02-11
You can try using the flash block extension for firefox, that way you can control flash. It gives you the choice to see only the flash you want to see.
-> [https://addons.mozilla.org/firefox/433/](https://addons.mozilla.org/firefox/433/)

---

### Post by kilou on 2007-02-11
My CPU has never got any hotter than 62°C in the past and that was with 100 % cpu usage too and a fan blowing at 60°C...so 87°C is clearly ususual and only happend with flash in firefox on Ubuntu. It is not a fan problem because further trial showed me that the fan starts to blow at 60°C too but is just not able to cool the CPU enough anymore (that's really weird) when on a flash website.

I don't find that flash block is a solution because what's the purpose of installing flash and then block it to "prevent" this problem? I need flash because I'm looking at job websites that have flash content. So I have to use XP to access these websites.......and this really makes me thing that Ubuntu is not for me because this flash issue is not the only thing that makes me require XP everyday. I need XP to run Excel 2003 with VBA because there are still some jerks with crossover and virtual machines such as Vmware or Virtualbox are not working efficiently with shared folders for me. I also need video in Skype or MSN to keep in touch with friends and this is not possible for linux versions and it is far too slow when using these apps in a virtual machine. My ricoh SD card reader is not recognized by Linux and the amount of time I had to tune the settings of my touchpad to have it work more or less correctly is just too much. So for now I'm booting more and more in XP.....and everything feels smooth and works.

---

### Post by kerry_s on 2007-02-11
Then, sounds like linux is not for you, maybe try again later when it catches up to your needs. You can still keep it to play with from time to time. Maybe even get a machine that's geared towards linux use, instead of built to run windows.

---

### Post by nickoli_02 on 2007-02-11
That's really odd... I wouldn't worry too much about your CPU being actually damaged due to operating at such high temperatures, there is internal circuitry built into most, if not all, CPUs to throttle the frequency and voltage in high temperature conditions in order to prevent the CPU from being damaged. In a very extreme case, the CPU will send a kill signal that either shuts down or restarts the system. Still, that's pretty crazy that flash would make your CPU that hot.

---

### Post by btolle on 2007-02-11
Maybe Ubuntu is not a good choice for you right now. I have no idea why Flash 9 would cause the heat problem but it seems to me I have read of other problems with Flash 9 running on XP. A search on Google Groups search will turn up a lot of links to posts about Flash 9 problems with both Firefox and IE7 so it is not entirely a Linux problem.

Before trying to switch to Ubuntu (or any other Linux distro) think about WHY you are trying to switch. If XP is serving you well I see no reason to change.

For me there are several factors that make me want to start switching over to Ubuntu. For one thing I am tired of having to reboot XP Pro weekly to keep it running and it still crashes periodically. And from everything I have read about Vista I have decided I don't even want to try to go there and such things as the DRM stuff in Vista is simply unacceptable to me. Besides, I am tired of having to spend money on hardware upgrades to just be able to run an operating system.

Sounds like you are dual booting so I would say that you might be better off to use XP most of the time and "play" with Ubuntu once in a while so you are ready to switch when XP is no longer supported and Vista is prohibitive with it's price, DRM, and other baggage.

---

### Post by scrooge_74 on 2007-02-11
Maybe playing with a lighter version of Linux could be interesting, maybe Xubuntu or DSL

---

### Post by kilou on 2007-02-12
Thanks for your replies. I must say I've always been quite happy with my XP install but basically I wanted to switch to Ubuntu to get some fresh air after 6 years of XP. I took a lot of time to tweak and setup my XP install and it is really working fast and without a single crash for a very long time but Ubuntu looks quite impressive....and beryl is awesome.

My problems are not related to a specific linux flavour, these are basically troubles that I would experience with any linux distros. I really like Ubuntu and much prefer it over K and Xubuntu for instance because Gnome is just what I like (although I'm a windows addict). 

I thought that Linux was really reliable because of all what people say about servers and companies switching to Linux but for me the use of Linux as a desktop environment is still not reliable and enough efficient to be really considered. For instance OOffice is nice but not when you need interoperability with Excel and you have to use macros. Even simplier tasks such as using date format are not translated correctly between OOCalc and Excel. Don't take me wrong, OOfice is great and really impressive and it would be a perfect choice if everybody was using it, but it's simply not like that at least not yet.

However with XP I'll just miss the possibility to surf the web without antivirus and firewall.......and this is maybe why I'm still a bit willing to try Ubuntu a bit more....but I'll have to watch out for those Flash websites :mad:

---

### Post by kerry_s on 2007-02-12
Like i said, you should try the flash block extension that way flash won't auto play, then if you want to play just click on the play button on the flash.

---

### Post by pvdg on 2007-02-12
kilou: Did you install the flash plugin from ubuntu repositories (multiverse) or by downloading from Adobe site? In either case, perhaps you should also ask Adobe about your problem; Flash is non-free binary-only sofware and is unsupported by the ubuntu team.

---

### Post by EvilMarshmallow on 2007-02-12
I can testify to the effectiveness of flashblock.  You know those websites that take 5 minutes to load a page because they've got half a dozen flash objects all over the place?  They load up in a big hurry when they can skip the flash objects.  I love it when a site uses flash for displaying advertisements... I automatically have them blocked for me!

Flash is a nice tool, but it's overused.

---

### Post by nickoli_02 on 2007-02-12
1. Linux is an operating system. Gnome is a desktop environment.

2. The reason why OpenOffice doesn't perfectly mesh with Microsoft Office is because Microsoft goes out of its way to ensure other products can't easily work alongside its own. Microsoft has done this for many, many years.

3. When you have a basic idea of what you're doing, linux is leaps and bounds more reliable than Windows. I've been using linux only for less than a year and I already know enough about linux to say comfortably that I have little reason to boot into my Windows partition. My windows is easily twice as slow as ubuntu, that's just sad (granted I'm not doing anything to try to make windows run faster, since I never use it).

Most of your issues with linux don't seem to be about linux at all. Keep an open mind and give linux a chance, once you find your feet in this new alien OS you may come to prefer it over windows.

---

### Post by kilou on 2007-02-12
pvdg, I installed Flash with Automatix2 and then also tried to install it from Adobe website but I always get the extreme CPU temperature with both version. 

Flashblock is nice but it won't solve the problem of CPU temperature. It is not better as simply uninstalling flash for me. As soon as I enable flash (and I'll need to because I use some websites that are based on flash) I will get high CPU temp that will force me to stop/start flash every now and then to allow the CPU to cool down. 

Honestly I cannot explain how I could get 87°C on my CPU!!! If I launch a 3D application that uses 100% CPU, the temp goes up max 62°C because the fan starts to blow at 60°C and always get the temperature down quickly, even if the CPU usage remains 100%. It's just as if flash was using 200% CPU power :confused: There is really absolutely no problem with the hardware, fan or bios settings because if I check with other softwares than flash, the temp doesn't go up as high as with flash, although CPU usage is 100%.....

Well honestly I must say that the linux world looks good but it has not the reliability that many people pretend. XP has been rock stable for me, of course I had some homework to do with it and set it up properly but it has never caused me any major issue. With Ubuntu it seems that every new thing can render the system unstable, even updates scares me because they sometime screw things up. 

I haven't seen anything about this kind of flash issue on Adobe website....but there are tons of post about flash producing 100%CPU usage in Ubuntu on this forum so it is not an isolated situation.

---

### Post by kaptainlange on 2007-02-12
It has been said already, but I think it is a valid point.  Linux may not work for the time being for your particular hardware needs.  It is a sad point that certain hardware just will not function correctly with Linux.  It is certainly not a fault of Linux that many hardware manufacturers don't build for Linux compliance, however it will translate as a shortcoming of Linux no matter who's fault it is.  I'm glad to hear you are not undaunted in giving Linux more of a try, just not going to be your primary system.

I wish you luck, and hope that that issue gets resolved soon.  It was mentioned elsewhere, but perhaps you should let Adobe know what this issue entails.  They may have some insight, or may even be able to fix that problem all together.

---

### Post by nickoli_02 on 2007-02-12
I agree with kaptainlange, I'm sure Adobe and the rest of the linux community would appreciate it if you report the problem to Adobe so they can look into it. Be sure to enclose your full hardware specs and the website you were visiting when the problem occurred.

---

### Post by geezerone on 2007-02-14
I understand where you are coming from and I use a mix of Ubuntu and XP but this community has to be one of the best around and [U,X,]buntu will get better and better. No doubt the introduction if V*sta will prove helpful in the Linux world with people peeved with DRM in MP11 etc...

Best Wishes! :-)

---

### Post by mcduck on 2007-02-14
> **kaptainlange said:**
> It has been said already, but I think it is a valid point.  Linux may not work for the time being for your particular hardware needs.  It is a sad point that certain hardware just will not function correctly with Linux.  It is certainly not a fault of Linux that many hardware manufacturers don't build for Linux compliance, however it will translate as a shortcoming of Linux no matter who's fault it is.  I'm glad to hear you are not undaunted in giving Linux more of a try, just not going to be your primary system.

I wish you luck, and hope that that issue gets resolved soon.  It was mentioned elsewhere, but perhaps you should let Adobe know what this issue entails.  They may have some insight, or may even be able to fix that problem all together.

That's true, but in my opinion if computer can't take 100% of CPU use for long times then there's some major fault in the cooling design of the hardware. If it's a desktop machine then some changes to CPU and case cooling are needed, and if it's a laptop I'd contact the manufacturer and tell them that their machine fails to do what it's supposed to do (and ask what are they going to do to fix it).

Computer that can't run at 100% CPU use for weeks is worth nothing for me. Luckily this far every machine I have owned has had no problems doing this.

---

### Post by atihimself on 2007-02-14
my traveling lap has pentium m processor and actually I've never seen it warmer than 75c although I love to play flash games when I'm travelling by train so... Imight be wrong but it might be graphic card issue,it might be incompadible with flas plugins.... maybe...

---

### Post by geezerone on 2007-02-14
> **mcduck said:**
> That's true, but in my opinion if computer can't take 100% of CPU use for long times then there's some major fault in the cooling design of the hardware. If it's a desktop machine then some changes to CPU and case cooling are needed, and if it's a laptop I'd contact the manufacturer and tell them that their machine fails to do what it's supposed to do (and ask what are they going to do to fix it).

Computer that can't run at 100% CPU use for weeks is worth nothing for me. Luckily this far every machine I have owned has had no problems doing this.

Interesting point and valid. The ambient room temperature has to be noted also with regards to cooling, as in a small room hot air out will just make the inside of the case hotter and hotter over a relatively short time with high CPU use (e.g. FPS gaming). 

Why not post your hardware setup including case, fans, GFX card, CPU and what CPU fan also?

---

### Post by dixon on 2007-06-14
I had the same problem with flash on my laptop. You should downgrade to Edgy. I have no idea why, but in Edgy I didn't have the problem with flash. I hope the next release(Gutsy Gibbon) will resolve this issue. :\ I'm still wondering if only us few people have this issue or the others just don't care :\

---

### Post by sylecn on 2007-08-25
I am having the same problem. When I was wathing flash based online video in FireFox 2.0, CPU usage goes high and OnDemand CPU freq which is usually 600MHz become 1.5GHz(Max freq).

Meanwhile the fan runs crazy, never stop a while.

I'm using a laptop computer.
Ubuntu 7.04
FireFox 2.0.0.6

---

