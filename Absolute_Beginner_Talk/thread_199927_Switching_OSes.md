---
title: "Switching OSes"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2006-06-19
Hi, I was looking for some general help and advice on switching to Ubuntu. I've tried the live CD (think it was Hoary) and Ubuntu seems to fit nicely with my needs. Plus it seems Windows 98 is losing support and I'll be damned if I'm giving MS more money to do exactly the same thing I do now give or take 1 or 2 things I'll never use.

I know Ubuntu has GIMP, but I find it needs photoshop to work with it. GIMP does somethings better (has better filters IMO and better for quick edits), but I just enjoy photoshop more for some reason. Is it possible to run photoshop 7 in Wine with reasonable performance? I'm no talking 12 gig images, nothing really beyond your average wallpaper size image, but still Wine seems picky so I figure I'll ask.

What games have been ported to Linux and still have good performance rates? I don't play that many games any more (HL2, NWN and Nethack is about it), but would be nice to know my options outside Sourceforge.

Is there any major differences between 32 and 64 bit Linux? My box could run either but I figure it's worth asking while I'm making a topic. If you run 64 are there many broken programs which only work in 64 or vice versa?

I'm not really too keen on the command line, I don't know why but I just never have. Is there any way to use stuff like aptget (Think I spelt that correctly), with a more friendly approach? I just don't trust going "leech this proggy for me" in a command line and also then I miss out on looking at all the alternatives and picking the one which best suits my needs instead of the most popular one being aptgot(not sure thats the correct term).

And finally, Wireless networking in Ubuntu. I've not got round to setting up a wireless network yet but figure if I upgrade my OS I may as well do it all at once and get the thing sorted all together. So what wireless networking cards does Ubuntu support straight out of the box? Hardwares really not my thing (mostly because I seem to find every sharp edge of a case and end up with no finger prints left) so the easier it is to get running the better really.

Thanks for reading.

---

### Post by aysiu on 2006-06-19
I can't answer all your questions, but I'll take a stab at some of them. [QUOTE=DiJEH]Hi, I was looking for some general help and advice on switching to Ubuntu. I've tried the live CD (think it was Hoary) and Ubuntu seems to fit nicely with my needs.[/quote] Just an FYI: Hoary is over a year old. I would go for Dapper, the latest version, which came out three weeks ago. > I know Ubuntu has GIMP, but I find it needs photoshop to work with it. GIMP doesn't need Photoshop. It's an independent application > GIMP does somethings better (has better filters IMO and better for quick edits), but I just enjoy photoshop more for some reason. There's a version of GIMP called GIMPShop you may want to look into. It's still GIMP, but since it's the interface and not the features you miss from Photoshop, you may want to look at GIMPShop. > Is it possible to run photoshop 7 in Wine with reasonable performance? I've heard you can. I've run Photoshop 6 in Wine. I think for CS2, though, you'd need Crossover Office instead of Wine. > Is there any major differences between 32 and 64 bit Linux? My box could run either but I figure it's worth asking while I'm making a topic. If you run 64 are there many broken programs which only work in 64 or vice versa? All I know is that there are a lot of packages that are not available for 64-bit yet, so 32-bit opens more doors to easily installable software.

> I'm not really too keen on the command line, I don't know why but I just never have. Is there any way to use stuff like aptget (Think I spelt that correctly), with a more friendly approach? I just don't trust going "leech this proggy for me" in a command line and also then I miss out on looking at all the alternatives and picking the one which best suits my needs instead of the most popular one being aptgot(not sure thats the correct term). You'll find that, of all the "user-friendly" distros, Ubuntu is the most command-line reliant. Still, most things can be accomplished through point-and-click. Take a look at this, for example:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

The command-line isn't that scary, though. Most of the time, you just copy and paste commands, and they do what you want. If you have questions about what a command does, just ask.

You'll see a lot of commands here, not because you *must* use them, but because they're better for support--easier to give support for, faster, offers better diagnoses of errors, etc.

---

### Post by mscman on 2006-06-19
> **DiJEH]I know Ubuntu has GIMP, but I find it needs photoshop to work with it. GIMP does somethings better (has better filters IMO and better for quick edits), but I just enjoy photoshop more for some reason. Is it possible to run photoshop 7 in Wine with reasonable performance? I'm no talking 12 gig images, nothing really beyond your average wallpaper size image, but still Wine seems picky so I figure I'll ask.
[/QUOTE]

I think Wine has some support for Photoshop, but you may want to check on [Wine's official Application Database]("http://appdb.winehq.org/") to see.

> What games have been ported to Linux and still have good performance rates? I don't play that many games any more (HL2, NWN and Nethack is about it), but would be nice to know my options outside Sourceforge.

It's really hit or miss with games and Linux.  Many of the very popular games are somewhat supported said:**
> Linux-gamers.net[/URL] or visit the [Gaming Central]("http://www.ubuntuforums.org/forumdisplay.php?f=93") section of the Ubuntu Forums.

No clue about 64 vs 32-bit...

> I'm not really too keen on the command line, I don't know why but I just never have. Is there any way to use stuff like aptget (Think I spelt that correctly), with a more friendly approach? I just don't trust going "leech this proggy for me" in a command line and also then I miss out on looking at all the alternatives and picking the one which best suits my needs instead of the most popular one being aptgot(not sure thats the correct term).

Synaptic is a great frontend to apt-get that's already built into Ubuntu.  You shouldn't even need the command line for it (except for rare occasions)...
That being said, the command line really is very helpful in many instances when using Linux.  Although it may seem a little daunting at first, you'll find that it makes many things a lot easier (and faster), including the installation of programs.  You should probably at least learn some of the basic functionality to be productive in Linux.

[quote]And finally, Wireless networking in Ubuntu.

I've had very good luck with networking in Ubuntu, particularly the latest Dapper release.  It seems to be one of the ONLY Linux distros that supports my wireless cards that I use, and they've been detected on install for both my desktop and laptop.  You may want to read around the forums to find out what cards seem to be having a lot of problems before you start purchasing.  Overall supports is very good.

> Thanks for reading.
No problem, that's what I do. :D

---

### Post by kb3hkg on 2006-06-19
Along with Gimp you may want to try other programs like Inkscape

For games many run natively now such as Unreal Tournament others run fine in Wine or if you really want performance Cedega, there are also open source games like Planeshift and Warsaw that a good too

if you have a 64bit processor then you will get better performance if you use an OS designed for it such as 64 bit ubuntu. As far as I know programs will run on either.

instead of command line apt-get there are GUI's like synaptic, kpackage, and adept out there.

For wireless any Atheros chipset seems to work well straight out of the box. These are made by a variety of companies.

---

### Post by MonkeyBoy on 2006-06-19
I dunno about some of the other stuff but regarding games check out: [http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games) 
[http://www.liflg.org/](http://www.liflg.org/) 
Enemy Territory Wolfenstein is a particularly good first person game and the mod entitled True Combat Elite, similar to Counterstrike, is even better.  There are loads of games about if you search the web.  

Regarding aptget, Ubuntu has a tool called Synaptic Package Manager which downloads and then installs things using a nice simple gui.  You need to enable some extra repositories for it in order to get hold of a lot of software but this is pretty simple.

The command line is still needed for some stuff but if you go here:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
you will find simple cut and paste commands to do a lot of useful things.

Ubuntu has good and simple support for some wifi devices at least so you should be fine so long as you get the correct wifi card.

Good luck!  Hope this is helpful to you.:)

---

### Post by DiJEH on 2006-06-19
Oops, double posted this part and can't find a delete button in editing.

---

### Post by DiJEH on 2006-06-19
Yea I know Hoary is a year old. Waiting for the latest CDs to ship since being on dial up right now is a nasty thing with large files. But then I'm using Windows 98 right now, it's not I'm exactly up to date any way.

I use Inkscape, GIMP and photoshop. Each has strengths in different areas, so I find using all 3 for different things is better than any one obviously. It's not the interface I miss, it's that Gimp is a git with brushs, where as photoshop it's easy to adjust brushs which is rather important to me, doing the sort of things I often do fixed brushs are just a lot of hassle.

Thanks for the help so far guys. Ubunutu doesn't seem so scary now at least.

Another thing I've thought of is MKV media files seem to be a lot of hassle in Windows, is it the same in Linux? I watch quite a few videos in .avi and .mkv, is there an easy solution to this in Ubuntu?

---

### Post by bruce89 on 2006-06-19
[QUOTE=DiJEH]Yea I know Hoary is a year old. Waiting for the latest CDs to ship since being on dial up right now is a nasty thing with large files. But then I'm using Windows 98 right now, it's not I'm exactly up to date any way.[/QUOTE]
No, but 1 year in Linux is a long time!
[QUOTE=DiJEH]I use Inkscape, GIMP and photoshop. Each has strengths in different areas, so I find using all 3 for different things is better than any one obviously. It's not the interface I miss, it's that Gimp is a git with brushs, where as photoshop it's easy to adjust brushs which is rather important to me, doing the sort of things I often do fixed brushs are just a lot of hassle.[/QUOTE]
Inkscape is easy to install, athough it will require downloading it.
```
sudo aptitude install inkscape
```
[QUOTE=DiJEH]Another thing I've thought of is MKV media files seem to be a lot of hassle in Windows, is it the same in Linux? I watch quite a few videos in .avi and .mkv, is there an easy solution to this in Ubuntu?[/QUOTE]
It depends on what video codec was used to compress them see - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

