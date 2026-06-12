---
title: "FRUSTRATION!! Need help with so many things..."
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-08-21
I made the jump from XP to Feisty, and I'm feeling pangs of regret. In only the first few days, I've found things I really love about Ubuntu, but I've found a bunch of little buggy things that are driving me CRAZY.

At this point, I've determined that Ubuntu is ABSOLUTELY NOT for the casual/inexperienced user, and in fact is probably only really good for programmers and extremely advanced users. I'm not a n00b, and I'm not stupid, but I'm being made to feel both of those as I stab through this OS. It isn't a good feeling.

Now that I've let that steam off, I'm hoping someone can help me wade through the Ubuntu quagmire. I have a bunch of things I cannot, for the life of me, figure out how to solve.

Something you should know when you post your helpful replies (and I so hope some of you post those) is that you'll have to break things down into PAINFULLY simple, step-by-infantile-step language. God, I feel filthy talking that way - I've never had to ask for something like that before!

So, here's what I've run into:

-I managed to disable the touchpad of my laptop mouse (thank christ - I hate that thing), but in so doing, I lost my vertical scroll function. I miss it like crazy. I can't figure out which parameter in my xorg.conf to change to get it back (and as it stands now, I don't even remember how to open xorg).

-I think there's something screwy with my hibernate function. In XP, I had to wait a few moments coming back from a hibernate while it essentially booted back up. With Ubuntu, when I close the lid on my laptop, nothing seems to happen except that the screen goes black; when I open it back up, my workspace pops up instantly. Is this normal? If not, how do I get my machine to hibernate properly?

-Ubuntu won't play my m4a files. I used that encoder in iTunes when ripping CDs, and about half of my (rather substantial) collection is in that format. Now I have Rhythmbox, and it only placed mp3 files into my library. SOOOO frustrating...

-What on earth is a "pipeline"?

I know there's more, but I'm so frustrated that I'm not thinking very clearly. When I think of other issues, I'll post them here. In the meantime, any help you out there can provide will hopefully alleviate my impulse to hurl my PC out the window and tell everyone I encounter that Ubuntu is useless, NOT-user-friendly garbage. Somewhere inside me, I know that isn't true, but it sure feels like it right now.

Please help... *whimper*

---

### Post by Jimmyfj on 2007-08-21
Easy now - Don't hurl your computer out the window just yet. 

Try opening a terminal and write sudo dpkg-configure xserver-xorg and see if this doesn't get your mouse back. It'll reconfigure your xorg.conf file for you. 

Ubuntu isn't taht good with the power thing but that's being corrected in the upcoming release of Gutsy. Gutsy is much more user friendly for previous Windows users i can assure you. Fell free to ask for help eny time and welcome to Ubuntu.

---

### Post by Gone fishing on 2007-08-21
To manually edit the xorg.conf file try: sudo gedit /etc/X11/xorg.conf if you modify the file its always worth saving a backup of the original unmodified file. You can always get to the directory of the xorg.con file with root privileges by sudo nautilus /etc/X11.

To install multimedia codecs I just install automatix and let it do that and its always worked

---

### Post by r4ik on 2007-08-21
Pipeline please see,

[http://en.wikipedia.org/wiki/Pipeline_%28Unix%29](http://en.wikipedia.org/wiki/Pipeline_%28Unix%29)

Good luck !

---

### Post by dpar on 2007-08-21
> **Gone fishing said:**
> To manually edit the xorg.conf file try: sudo gedit /etc/X11/xorg.conf if you modify the file its always worth saving a backup of the original unmodified file. You can always get to the directory of the xorg.con file with root privileges by sudo nautilus /etc/X11.

To install multimedia codecs I just install automatix and let it do that and its always worked

gksudo would be better for graphical apps. See.....[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I prefer Add/Remove for codecs.:)

---

### Post by doctorbighands on 2007-08-22
UPDATE...

Thank you for the replies so far!

I still need to know which parameter to change in my xorg.conf file to bring back my vertical scroll function. I don't want to reset xorg back to defaults, because that would undo the progress I've already made (it would bring back TAPPING - yuck!).

I've decided that there simply is no suitable Ubuntu alternative to iTunes. I can't find ANYTHING that will play my m4a files! Incidentally, is an m4a the same as AAC?

I need to install Adobe Reader, but apparently the only Linux version is for RedHat. I've tried installing "acroread" based on instructions from several other threads and websites, and nothing works. All I really want is a .pdf reader that will allow me to use fillable forms. Whatever default reader I have won't let me do that.

The file installation process BLOWS in Ubuntu, by the way. If you're lucky enough to find the program you need in the repository, it's fine using Add/Remove. If it isn't in the repository, you need a friggin' masters degree in CS to get things done.

Still frustrated as hell...

---

### Post by igknighted on 2007-08-22
> **doctorbighands said:**
> UPDATE...

Thank you for the replies so far!

I still need to know which parameter to change in my xorg.conf file to bring back my vertical scroll function. I don't want to reset xorg back to defaults, because that would undo the progress I've already made (it would bring back TAPPING - yuck!).

I've decided that there simply is no suitable Ubuntu alternative to iTunes. I can't find ANYTHING that will play my m4a files! Incidentally, is an m4a the same as AAC?

I need to install Adobe Reader, but apparently the only Linux version is for RedHat. I've tried installing "acroread" based on instructions from several other threads and websites, and nothing works. All I really want is a .pdf reader that will allow me to use fillable forms. Whatever default reader I have won't let me do that.

The file installation process BLOWS in Ubuntu, by the way. If you're lucky enough to find the program you need in the repository, it's fine using Add/Remove. If it isn't in the repository, you need a friggin' masters degree in CS to get things done.

Still frustrated as hell...

Take 5 minutes, go grab a beer and calm down.

Then come back to your computer with the expectation that: 

1) you are learning something completely new.  It is not as simple as rhythmbox=itunes, there are funamental differences in what you are rtying to learn.  Be ready to embrace those as opposed to fighting them, or you will be pulling your hair out the whole time.

2) you are a complete newb.  Not in a mean way at all, but think about the first time (if you can remember) you used windows.  Its not quite that bad, but similar.

3) It works.  Just about everyone here uses linux regularly.  The overwhelmingly vast majority do not have CS degrees.  If you do #1 and #2, you will realize what I mean here.  It seems hard because it is new, but there is a beauty and a simplicity in the linux way which you will see if you take the time.

If you do not want to give 1-3 a shot, then save yourself and us a lot of time and headaches and use what is familiar to you and clearly already works well.  No one OS is for everyone, even linux.  If it is not for you then there is nothing wrong with using an OS that fits your needs better.

---

### Post by perce on 2007-08-22
> **doctorbighands said:**
>  
-I think there's something screwy with my hibernate function. In XP, I had to wait a few moments coming back from a hibernate while it essentially booted back up. With Ubuntu, when I close the lid on my laptop, nothing seems to happen except that the screen goes black; when I open it back up, my workspace pops up instantly. Is this normal? If not, how do I get my machine to hibernate properly?



The behaviour when you closed the lid is the normal default in Ubuntu. You can change it through system > preferencies > power management.

To hibernate go system > quit and you should have hibernate among your options if it is supported by your hardware. It works fine for most laptops, but unfortunately not for all. If you are one of the unlucky ones you can browse the forum for a solution, or wait for some next release: those things get eventually fixed.

About the touchpad, try system > preferences > touchpad, maybe you'll find the the options you need to change.

If you don't find these entries in the menu, right click on the Ubuntu logo on the top left corner, and you'll enter the menu editor.

I hope I helped

---

### Post by yellowband on 2007-08-22
i like rhythmbox, but i'm using amarok for my music right now, it may be worth checking out if you like the itunes feel.  

As for installing programs not in a repository, yes i agree it can be a hassle.  

Since you are usuing ubuntu, you might try looking for .deb versions of the software you want.  .deb are packages of files that take care of the dependencies for you.  

Sometimes you will want software that is not compiles yet, this gets a bit complicated, but notimpoossible:

if you download, say a file.tar.gz of your program from the internet:
- untar and uncompress the file: 
        ```
 tar -xzvf filename.tar.gz 
```
- look in the new uncompressed difrectory for an install readme or documentation.  Usually there is a conifgure script in there, so run something like
       ```
 sudo ./configure 
```
-Next compile your prrogram (change it from the text cource code into machine readable code)
       ```
  make 
```
-Finally, put the files where they belong on your harddrive
       ```
 make install 
```

---

### Post by em007a on 2007-08-22
These are pretty minor things so far. Walk away for a bit if you need to clear your head and then return with a positive attitude and things will get better. 

Just to let you know, my father-in-law knows almost _*NOTHING*_ about computers and he installed feisty on his own and is very happy. It goes to show that you don't have to be an advanced user to use Ubuntu. :)

Did you back up your original xorg.conf file? If so, print out a copy of the backup and the existing so you can compare them side by side.

As far as m4a, I typed in "m4a" in the search function at the top of the page and many links came up. I didn't have a lot of time to look, but there does appear to be relevant information in there. The search button will be your best friend for a while and of course there are plenty of friendly people here to help beyond that.

I'm at work using an XP box right now, so I can't check to see if acroread can be installed from Add/Remove or synaptic package manager.

Just be patient and keep an open mind. It will all come together for you.

Congrats on installing Ubuntu!

---

### Post by Paulmd on 2007-08-22
> **doctorbighands said:**
> UPDATE...

Thank you for the replies so far!

I still need to know which parameter to change in my xorg.conf file to bring back my vertical scroll function. I don't want to reset xorg back to defaults, because that would undo the progress I've already made (it would bring back TAPPING - yuck!).

I've decided that there simply is no suitable Ubuntu alternative to iTunes. I can't find ANYTHING that will play my m4a files! Incidentally, is an m4a the same as AAC?

I need to install Adobe Reader, but apparently the only Linux version is for RedHat. I've tried installing "acroread" based on instructions from several other threads and websites, and nothing works. All I really want is a .pdf reader that will allow me to use fillable forms. Whatever default reader I have won't let me do that.

The file installation process BLOWS in Ubuntu, by the way. If you're lucky enough to find the program you need in the repository, it's fine using Add/Remove. If it isn't in the repository, you need a friggin' masters degree in CS to get things done.

Still frustrated as hell...

Synaptic package manager shows a lot of things that aren't in add/remove. 

Many of your frustrations were also my frustrations.

Anyway to install acrobat, go to the terminal.
```

sudo pico /etc/apt/sources.list
```

add the following line
```

deb http://www.debian-multimedia.org stable main
```

save and exit

then again in the terminal

```
sudo apt-get update

sudo apt-get install acroread
```

---

### Post by perce on 2007-08-22
> **yellowband said:**
> i like rhythmbox, but i'm using amarok for my music right now, it may be worth checking out if you like the itunes feel.  

As for installing programs not in a repository, yes i agree it can be a hassle.  

Since you are usuing ubuntu, you might try looking for .deb versions of the software you want.  .deb are packages of files that take care of the dependencies for you.  

Sometimes you will want software that is not compiles yet, this gets a bit complicated, but notimpoossible:

if you download, say a file.tar.gz of your program from the internet:
- untar and uncompress the file: 
        ```
 tar -xzvf filename.tar.gz 
```
- look in the new uncompressed difrectory for an install readme or documentation.  Usually there is a conifgure script in there, so run something like
       ```
 sudo ./configure 
```
-Next compile your prrogram (change it from the text cource code into machine readable code)
       ```
  make 
```
-Finally, put the files where they belong on your harddrive
       ```
 make install 
```

I strongly suggest that he not install programs outside the repositories. This is not something for newbies: I remember when six years ago I deleted libc trying to install mplayer which was not in Debian repositories. There is not really much that is not in the repositories, and often you find .deb packages for Ubuntu for also for programs not in the repository, For pdf has you tried the default viewer? it's pretty good.

---

### Post by newlinux on 2007-08-22
for m4a, make sure you have installed gstreamer0.10-faac

```
sudo apt-get install gstreamer0.10-faac
```

I believe that is the codec. I can't check for sure right now cause I'm at an XP box.

Also, I think in Feisty if you open up a file using Totem it should search for the right codec and give you a list to select and install...

---

### Post by igknighted on 2007-08-22
> **Paulmd said:**
> Synaptic package manager shows a lot of things that aren't in add/remove. 

Many of your frustrations were also my frustrations.

Anyway to install acrobat, go to the terminal.
```

sudo pico /etc/apt/sources.list
```

add the following line
```

deb http://www.debian-multimedia.org stable main
```

save and exit

then again in the terminal

```
sudo apt-get update

sudo apt-get install acroread
```

That is a Debian repo... I would strongly advise AGAINST using it.  It would be like using a winNT driver on win98.  Might work, but eventually you'll run into issues.

The rough equivelent of debian-multimedia in Ubuntu is medibuntu, search on the forums for how to use it.

EDIT: The canonical comercial repo might be more appropriate if medibuntu doesn't have it.

---

### Post by logos34 on 2007-08-22
for m4a get amarok-xine.  It's the best engine (and the lightest to boot) -- plays just about anything (including my apple lossless .m4a files (.alac).  The amarok gui frontend is heavy though (hey, it's a kde app).  Audacious is a nice lightweight xmmms-like player that will do a noce job with its m4a plugins.   Follow the directions in the RestrictedFormats page for installing all the codecs you need.  That is a fantastic howto.

---

### Post by newlinux on 2007-08-22
acroread in Feisty:

[http://ubuntuforums.org/showthread.php?t=490459](http://ubuntuforums.org/showthread.php?t=490459)

---

### Post by Paulmd on 2007-08-22
> **igknighted said:**
> That is a Debian repo... I would strongly advise AGAINST using it.  It would be like using a winNT driver on win98.  Might work, but eventually you'll run into issues.

The rough equivelent of debian-multimedia in Ubuntu is medibuntu, search on the forums for how to use it.

EDIT: The canonical comercial repo might be more appropriate if medibuntu doesn't have it.

Ubuntu is based on debian. More like using a win95 driver on win98, which generally works. (98 isn't based on NT)

---

### Post by newlinux on 2007-08-22
> **Paulmd said:**
> Ubuntu is based on debian. More like using a win95 driver on win98, which generally works. (98 isn't based on NT) Yes, but the packaging is different, as it is from release to release in Ubuntu. Using debian packages not specifically meant for ubuntu (or a particular ubuntu release) can cause problems.

---

### Post by TeaSwigger on 2007-08-22
> **doctorbighands said:**
> I made the jump from XP to Feisty, and I'm feeling pangs of regret. In only the first few days, I've found things I really love about Ubuntu, but I've found a bunch of little buggy things that are driving me CRAZY.

At this point, I've determined that Ubuntu is ABSOLUTELY NOT for the casual/inexperienced user, and in fact is probably only really good for programmers and extremely advanced users. I'm not a n00b, and I'm not stupid, but I'm being made to feel both of those as I stab through this OS. It isn't a good feeling.

Now that I've let that steam off, I'm hoping someone can help me wade through the Ubuntu quagmire. I have a bunch of things I cannot, for the life of me, figure out how to solve.

Something you should know when you post your helpful replies (and I so hope some of you post those) is that you'll have to break things down into PAINFULLY simple, step-by-infantile-step language. God, I feel filthy talking that way - I've never had to ask for something like that before!

So, here's what I've run into:

-I managed to disable the touchpad of my laptop mouse (thank christ - I hate that thing), but in so doing, I lost my vertical scroll function. I miss it like crazy. I can't figure out which parameter in my xorg.conf to change to get it back (and as it stands now, I don't even remember how to open xorg).

-I think there's something screwy with my hibernate function. In XP, I had to wait a few moments coming back from a hibernate while it essentially booted back up. With Ubuntu, when I close the lid on my laptop, nothing seems to happen except that the screen goes black; when I open it back up, my workspace pops up instantly. Is this normal? If not, how do I get my machine to hibernate properly?

-Ubuntu won't play my m4a files. I used that encoder in iTunes when ripping CDs, and about half of my (rather substantial) collection is in that format. Now I have Rhythmbox, and it only placed mp3 files into my library. SOOOO frustrating...

-What on earth is a "pipeline"?

I know there's more, but I'm so frustrated that I'm not thinking very clearly. When I think of other issues, I'll post them here. In the meantime, any help you out there can provide will hopefully alleviate my impulse to hurl my PC out the window and tell everyone I encounter that Ubuntu is useless, NOT-user-friendly garbage. Somewhere inside me, I know that isn't true, but it sure feels like it right now.

Please help... *whimper*

Easy there - remember you had to learn from scratch with Windows, and Microsoft is taking in billions for what you're going to be getting for nothing but human generosity. That has to be good for some smiles and stress relief. And not a little of it is better than what Microsoft made, which should be good for some laughs when you think of it...

You'll figure it out and make yourself a nice groovy setup. I'll get to your list in a few, taking a tea break here...

---

### Post by Arthur Archnix on 2007-08-22
Lots of replies. So much to read. I'll just quietly add my two cents then disappear.

1. RE: Adobe. Start by not installing it. Ubuntu has a built in reader for pdf files. Better in many ways than Adobe (e.g. it's not 80 Fricken MB's to read a pdf, nor a resource hog). But anyway, since you've decided to try a whole new OS why not start by trying out the built in programs to do things? If after a few days you really, really want Adobe Reader. No problem. Lots of people use it. And you'll find a way to install it no problem.

2. RE: Can't play certain files. Ubuntu doesn't ship with the ability to play all the restricted formats, because they don't pay the corps to have the right to do that. So, you get a free OS on the one hand, but on the other had you have to do a few extra steps to get everything up to speed. All in all, some people call that a fair trade. I always start by running these commands:
```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```
Both those are directly ripped off from the [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), which should always be your first stop for help since the answers to so many questions are right there, and it's so easy!

3. The first rule of automatix is don't use automatix. The second rule of automatix is dont' talk about automatix. Or read the links in my sig for more, or search the net. It may be an essential program in a few months/years, but at the moment it has the minor and annoying habit of rendering a few machines unusable, which doesn't bother us to much since those people can't get online to come complain here, but still, we hate to see it happen.

---

### Post by likemindead on 2007-08-22
Don't give up! You've made the right choice--I promise! See how fast the community has responded? If you need specific help, try searching the forums. It's always worked for me. I have a basic, cursory knowledge of computers and I'm doing great with Ubuntu. Welcome to the FREE world....

---

### Post by TeaSwigger on 2007-08-22
> **doctorbighands said:**
> I made the jump from XP to Feisty, and I'm feeling pangs of regret. In only the first few days, I've found things I really love about Ubuntu, but I've found a bunch of little buggy things that are driving me CRAZY.

You never had any problems with anything in XP? Not even starting out? If not your experience is quite unique. You'll have to learn some new things on a different system, but you'll get it. Feisty is an awesome mountain of programming that definitely works and can do most if not all things XP can and some things XP can't.

Installing Feisty on my main PC was as easy as any installation of anything ever was, easier than installing XP. And it worked. It got complicated when I started wanting everything a certain way and expecting it to do a million things... but then it gets that way in XP. If and when you can do it in XP, and of course on XP odds are whatever it is it'll cost you $$ or $$$. Tradeoffs.

> Now that I've let that steam off, I'm hoping someone can help me wade through the Ubuntu quagmire. I have a bunch of things I cannot, for the life of me, figure out how to solve.

While you may have to do more "footwork" yourself, folks who are self taught users like yourself are here helping others for nothing. No calls routed to India at $40 or more per hour to tell you to reinstall Windows, either.

> Something you should know when you post your helpful replies (and I so hope some of you post those) is that you'll have to break things down into PAINFULLY simple, step-by-infantile-step language. God, I feel filthy talking that way - I've never had to ask for something like that before!

World's getting more "specialized" all the time. Don't feel inferior because you weren't born with intimate foreknowledge of computer software. :)

> So, here's what I've run into:

-I managed to disable the touchpad of my laptop mouse (thank christ - I hate that thing), but in so doing, I lost my vertical scroll function. I miss it like crazy. I can't figure out which parameter in my xorg.conf to change to get it back (and as it stands now, I don't even remember how to open xorg).

Oh yeah. Those pads. Drive me nuts. Haven't installed linux on my laptop yet though so guess I'll be learning the same thing eventually.

To open and edit xorg.conf, that I can help with. Remember it's a system file so to help keep it safe it requires you to have temporary admin control. You can open your file manager (Nautilus in ubuntu, Konqueror in KDE, Thunar in Xubuntu or whatever it is you're using) as root (for example enter the command "gksu nautilus") and go surf on over to the /etc/X11 directory for xorg.conf, and open the thing with gedit or whatever you like that'll edit text. You can open gedit or whatever you like that'll edit text with the command "gksu gedit" for example and open the /etc/X11/xorg.conf from there. Or you could open a terminal and enter "gksu gedit /etc/X11/xorg.conf" to edit it in gedit. Or enter "gksu nano /etc/X11/xorg.conf" to edit it right there in the terminal. More choices than your average state measures ballot, that's linux.

All this root / permissions stuff by the way sure annoyed me at first. But then it's also a good thing because it helps ensure Feisty is a safer, more secure system. So I'm getting used to it.

> -I think there's something screwy with my hibernate function. In XP, I had to wait a few moments coming back from a hibernate while it essentially booted back up. With Ubuntu, when I close the lid on my laptop, nothing seems to happen except that the screen goes black; when I open it back up, my workspace pops up instantly. Is this normal? If not, how do I get my machine to hibernate properly?

Can you bear it? :) ...bear? Hibernate...? Ah well. Another one I don't know about yet. But I can refer you to an article on the subject that might help you find your way:
Feisty Suspend Overview 
[https://wiki.ubuntu.com/FeistySuspendOverview](https://wiki.ubuntu.com/FeistySuspendOverview)
You might also search for more info on hibernation there at the wiki.

> -Ubuntu won't play my m4a files. I used that encoder in iTunes when ripping CDs, and about half of my (rather substantial) collection is in that format. Now I have Rhythmbox, and it only placed mp3 files into my library. SOOOO frustrating...

Please do check out this "sticky" thread about multimedia capabilities:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I'd suggest that any blame for any inaccessibility of m4a format software support should properly be placed at the feet of the people not allowing others to the license.

I don't use m4a's but if Amarok will play them, that's a great free audio player with library support. Beep-Media_Player / XMMS / Audacious are based on WinAmp and might play the files too.

> -What on earth is a "pipeline"?

As my crude inkling of it goes, it involves communicating some command or data from one thing to another. For more specifics open a terminal and enter "man pipe." All you could care to know. :)

> I know there's more, but I'm so frustrated that I'm not thinking very clearly. When I think of other issues, I'll post them here. In the meantime, any help you out there can provide will hopefully alleviate my impulse to hurl my PC out the window and tell everyone I encounter that Ubuntu is useless, NOT-user-friendly garbage. Somewhere inside me, I know that isn't true, but it sure feels like it right now.

Do feel free to ask any questions here. Don't get bothered, 'cause you'll get it, and don't let anybody's ol software turn you to being an ungrateful irascible grouch ;). Other Operating Systems only get harder (and, often, costlier) from Ubuntu. This stuff used to be horridly tough to use. 

Thousands of very clever cookies collaborated all over the place to craft this amazing mountain of programming to run our computers and do tons of cool and/or useful things, based in part on the freely given works of thousands more clever cookies. It's an inspiring testament to human endeavor. Look at it that way if you will and just smile at what people - including you - can do. :)

---

### Post by gnuman on 2007-08-22
First of all, I'm continually amazed at the quality of help that comes from these forums.

To the OP:

I remember being frustrated when I first switched to Linux.  I couldn't get the screen resolution correct.  And the touchpad had me selecting things all the time when all I wanted to be doing was moving the cursor.  I tried editing the xorg.conf, goofed things up and then couldn't get to the xorg_bak.conf that I THOUGHT I had made.... You get the idea.  I jumped from distro to distro just hoping that one would "just work."  Amazingly, it wasn't Ubuntu.  For my laptop, Mepis actually installed easier.  But, after I got more proficient with Linux, I eventually came to Ubuntu, even if I'd have to tweak a few things.

Just about any problem I experience was already documented online, either on these forums, or elsewhere.

I really truly believe that Amarok is superior to Itunes in many ways.  I had to tweak it a bit, but it is a lean, fast and powerful machine once it was set up right.  I've stopped using Photoshop and prefer GIMP.  Open Office is also excellent. 

If you install the synaptic touch pad configuration tool you should be able to disable the tap select or whatever it's called.  The scrolling should remain.

A long time ago when I decided to use Itunes to convert my large cd collection to mp3s, I luckily set the preferences to encode as MP3s.  I wanted maximum compatibility.  I hope you find a solution in that area.

Linux took some time and effort to get working, but I feel (I know this will sound weird) that this OS truly respects the user. 

Keep learning.

---

### Post by doctorbighands on 2007-08-23
> **gnuman said:**
> First of all, I'm continually amazed at the quality of help that comes from these forums.

I agree. I couldn't possibly agree more, in fact.

Let me take this opportunity to pause and offer some overdue, deeply sincere gratitude to all of you who've responded to this ridiculous thread I've created. I'm overwhelmed by you, and that's an extraordinary thing for someone so normally-disillusioned as I. Thank you very, very much.

I'd also like to say, for the record, that the open source philosophy is what initially attracted me to the Linux project, it's what finally gave me the push I needed to abandon other OS permanently, and it's what has cemented my resolve to keep that commitment. The whole project is truly a marvel. I appreciate every moment of effort on the part of all the "clever cookies" who made this thing what it is; in fact, I aspire to be one of those cookies one day.

Thanks again to all of you for the help. You don't know (actually, you very likely do) how refreshing it is to not have my "silly" questions flamed with backfires like, "Eff you, n00b - figure it out!" as is so common in Windows/Mac circles. Although "figuring it out" is precisely what I intend to do, it's very comforting to know there's such a huge community of folks who will refrain from reminding me of such in an unduly harsh manner, and will hold my pathetic hand when need be.

You rule, and - despite any preliminary judgment - so does Linux.

---

### Post by perce on 2007-08-23
> **doctorbighands said:**
> 

You rule, and - despite any preliminary judgment - so does Linux.


Thank you, and please give us a feedback on our suggestions, so that we can learn something too.

---

### Post by doctorbighands on 2007-08-23
Uh-oh. Something else:

At the suggestion of one of the kind souls here, I attempted the following command in the terminal:
[I]
sudo apt-get install gstreamer0.10-faac[/I]

My reply from the terminal was as follows:

[I]E: Type 'wget' is not known on line 45 in source list etc/apt/sources.list
E: The list of sources could not be read[/I]

I haven't messed with my sources.list file, I swear. Any suggestions?

Oh, also, I think there's something screwy with my arrow keys on the keyboard. Depending on the application, they're either unresponsive, sporadically responsive, or confused (e.g., pressing "up" moves the cursor left).

EDIT:

I tried to open Applications -> Add/Remove..., and the following nerve-wracking message popped up:

"FAILED TO CHECK FOR INSTALLED AND AVAILABLE APPLICATIONS

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

What have I done?!

---

### Post by heimo on 2007-08-23
> **doctorbighands said:**
> 
[I]E: Type 'wget' is not known on line 45 in source list etc/apt/sources.list
E: The list of sources could not be read[/I]


You'll need to fix that with text editor or perhaps Synaptic Package Manager (repositories). If you could show us what's in your sources.list, we can probably tell you what to change.

On a terminal window, you could run:
```
cat /etc/apt/sources.list
```

Or, to edit:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by aitorcalero on 2007-08-23
I completely agree with you. Do not install software manually unless you have more experience.
All of your problems seem to be easy to resolve, jusk asking the forum or searching them.

Think about this. Are your problems with Ubuntu more related that you are used to Windows or with Ubuntu itself. If have never used windows, will you find Ubuntu difficult to use?

I was also (and I am still) Windows User, but now I cannot conceive using other OS than Ubuntu

---

### Post by quinnten83 on 2007-08-23
> **Paulmd said:**
> Synaptic package manager shows a lot of things that aren't in add/remove. 

Many of your frustrations were also my frustrations.

Anyway to install acrobat, go to the terminal.
```

sudo pico /etc/apt/sources.list
```

add the following line
```

deb http://www.debian-multimedia.org stable main
```

save and exit

then again in the terminal

```
sudo apt-get update

sudo apt-get install acroread
```

I just tried adding that repository to my sources.list and it gave me an error about the public key, where do I get this (or any other )public key from. this is an error I frequently encounter.

---

### Post by perce on 2007-08-23
> **quinnten83 said:**
> I just tried adding that repository to my sources.list and it gave me an error about the public key, where do I get this (or any other )public key from. this is an error I frequently encounter.

I think (but I'm not sure) that this is only a security warning because debian-multimedia is not an official repository. This shouldn't worry you because, even if not official, it is maintained by a 
Debian developer. The problem is that it is a repository for Debian, so it could conflict with Ubuntu. It should not be a problem if you install only acrobat reader, but I'd remove that repository from your source list.

---

### Post by Paulmd on 2007-08-23
> **doctorbighands said:**
> Uh-oh. Something else:

At the suggestion of one of the kind souls here, I attempted the following command in the terminal:
[I]
sudo apt-get install gstreamer0.10-faac[/I]

My reply from the terminal was as follows:

[I]E: Type 'wget' is not known on line 45 in source list etc/apt/sources.list
E: The list of sources could not be read[/I]

I haven't messed with my sources.list file, I swear. Any suggestions?

Oh, also, I think there's something screwy with my arrow keys on the keyboard. Depending on the application, they're either unresponsive, sporadically responsive, or confused (e.g., pressing "up" moves the cursor left).

EDIT:

I tried to open Applications -> Add/Remove..., and the following nerve-wracking message popped up:

"FAILED TO CHECK FOR INSTALLED AND AVAILABLE APPLICATIONS

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

What have I done?!

I doubt it was you, but If you post the file, we might be able to fix it.  I think perhaps that a line that should be commented out, isn't. Comments are lines that are for humans to read, but are ignored by the computer. In that file, lines that start with '#' are comments.

---

### Post by gundumfx on 2007-08-23
well what i did is go to a google an typeup my prblem then i found this command here sudo dpkg-configure xserver-xorg so try to fix it from here but try not to screw up your computer

---

### Post by doctorbighands on 2007-08-23
Here are the contents of my sources.list file:

[I]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

wget
sudo
dd[/I]

Thanks in advance!

---

### Post by igknighted on 2007-08-23
Delete those last few lines (wget, sudo and dd).  I dunno how those got in there, but thats whats messing it up.

---

### Post by doctorbighands on 2007-08-23
> **igknighted said:**
> Delete those last few lines (wget, sudo and dd).  I dunno how those got in there, but thats whats messing it up.

Bam! Worked like a charm!

Thank you!!

---

### Post by doctorbighands on 2007-08-23
> **doctorbighands said:**
> I've decided that there simply is no suitable Ubuntu alternative to iTunes. I can't find ANYTHING that will play my m4a files!

Problem solved.

Solution: Amarok, as well as installing the "libxine" codec package. Now I can play mp3, m4a, wmv...anything! The interface isn't bad, either.

Crow officially eaten. :)

---

### Post by doctorbighands on 2007-08-23
I managed to install acroread using Synaptic. The default PDF reader that comes with Ubuntu just wasn't cutting it for me. I needed something that allowed me to complete fillable forms, and Acrobat Reader does that.

Another problem solved!

---

### Post by doctorbighands on 2007-08-23
My most frustrating issue remains: I can't get my vertical scroll function to come back. I know I've brought this issue up before, but I haven't been specific. I'll try to cover all the bases right now.

My machine is an HP Pavilion DV4000
The mouse is an ALPS Touchpad with synaptic driver

Here are the contents of the relevant sections of the xorg.conf file:

```

Section "InputDevice"
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"AlwaysCore"
	Option		"Device"		"/dev/input/event3"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"ClickTime"		"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"		"0.8"
	Option		"MaxSpeed"		"5"		
	Option		"AccelFactor"		"0.020"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"0"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"2"
	Option		"SHMConfig"		"true"
	Option		"TouchpadOff"		"2"
EndSection

```

Also, as a side note, the arrow keys on my keyboard still don't function properly, if at all.

---

### Post by doctorbighands on 2007-08-24
*bump*

I'd still love some help with the scroll function.

Anyone?

---

### Post by newlinux on 2007-08-24
You might get more help on that if you change the thread title or start a new thread... Wish I could help....

---

### Post by gnuman on 2007-08-24
> **doctorbighands said:**
> *bump*

I'd still love some help with the scroll function.

Anyone?

Have you installed:

" Touchpad
configuration tool for Synaptics touchpad driver of X server  
GSynaptics is a GUI configuration tool for the Synaptics touchpad driver of the X server.
This allows for modifications of the driver parameters on the fly.
Version: 0.9.7-3 (gsynaptics)
Touchpad integrates well into the Ubuntu desktop"

It can be found in the package manager (Applications/Add\/remove/Other)  (note it is not in system tools, but in the "other" category.)

If you install that, then in your System/Preferences dropdown menu you should now have "Touchpad" as a choice.  You will have three tabs "General/Tapping/Scrolling" that you can then set.

I apologize if you've already tried this--I didn't go back to the beginning of this thread before posting this.

Good Luck.

---

### Post by Paulmd on 2007-08-24
> **doctorbighands said:**
> My most frustrating issue remains: I can't get my vertical scroll function to come back. I know I've brought this issue up before, but I haven't been specific. I'll try to cover all the bases right now.

My machine is an HP Pavilion DV4000
The mouse is an ALPS Touchpad with synaptic driver

Here are the contents of the relevant sections of the xorg.conf file:

```

Section "InputDevice"
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"AlwaysCore"
	Option		"Device"		"/dev/input/event3"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"ClickTime"		"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"		"0.8"
	Option		"MaxSpeed"		"5"		
	Option		"AccelFactor"		"0.020"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"0"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"2"
	Option		"SHMConfig"		"true"
	Option		"TouchpadOff"		"2"
EndSection

```

Also, as a side note, the arrow keys on my keyboard still don't function properly, if at all.



Forgive me for making a guess: but 

```
Option		"UpDownScrolling"	"0"
```

0 is normally the same thing as off. Try changing it to 1. (Back up the file first)

---

### Post by Shibby73 on 2007-08-26
Hey doc,

Glad to see things are working better for you. I stumbled upon this thread looking for a solution to a PDF problem I am encountering.  I am trying to fill out an application for a fellowship in geriatrics... well I would really like just a "type writer" type of function that lets me type text onto the application (fill it out electronically) so I can later print the filled out PDF.

I see GIMP has the ability to kinda do this, but it is painfully cumbersome.

Any suggestions?

Thank you.

~Steve (smorrea)
(nospam)@stansgnosticus.net
replace nospam with smorrea

---

### Post by doctorbighands on 2007-09-05
First of all, as I understand it, your form needs to be created as "fillable". If it isn't, there's probably a way to convert a document into an image format in order to achieve your "typewriter" effect, but I leave that to you to figure out. I know you mentioned GIMP; that would be my best guess in this case.

If you find a way, I would be curious to know what you discover. Best of luck with your fellowship!

---

### Post by Johnny3 on 2007-09-05
Use the 32 bit. And do these installs
 12 Must Do Things After New Ubuntu Installation Fiesty Fawn

[http://ubuntuforums.org/showthread.php?t=515582&highlight=medibuntu](http://ubuntuforums.org/showthread.php?t=515582&highlight=medibuntu)

Should be a sticky in Absolute Beginner Talk
In terminal paste is shift+ctrl+v 
Makes it just about a easy as installing ms os. Just some copy and paste.
At 61 I did not think I would get Ubuntu to work so easy. Tried the 64 bit first. Couldn't get much installed 32 bit is the way to go first time to me
Johnny3
Gainesville,Fl

---

### Post by Shibby73 on 2007-09-06
> **doctorbighands said:**
> First of all, as I understand it, your form needs to be created as "fillable". If it isn't, there's probably a way to convert a document into an image format in order to achieve your "typewriter" effect, but I leave that to you to figure out. I know you mentioned GIMP; that would be my best guess in this case.

If you find a way, I would be curious to know what you discover. Best of luck with your fellowship!

Well I opened the PDF used KWORD and just typed over the areas I wanted to fill in.
I then exported it as a PDF.

---

