---
title: "Trepidation &amp; Tribulation"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Red.Heron on 2007-11-05
Okay, so... I haven't made the switch, and I'm kinda nervous about losing productivity as I switch over. I am using OpenOffice already, but I can't tell if there are things I'm missing.

I also need the following (none of which should be terribly difficult):

[LIST]
[*]Skype
[*]IRC
[*]LAMP for development of web-based software (currently using a WAMP for the same purpose)
[*]PDF reading/writing (dumping Acrobat for something free on Ubuntu would be nice)
[*]DTP software (the big issue, actually, since part of my business depends on this, since I'm working with trying to get a newspaper going and I need something that works similar to QuarkXPress or InDesign, both of which I've been using professionally for 13 years)
[*]A really well-done GIMP tutorial for a complete noob who understands Photoshop but is driven crazy by GIMP's UI.
[*]MP3 & CD playback software
[*]DVD playback software (or my wife's happiness is at risk)
[*]Subversion (for SourceForge)
[*]CVS (also for SourceForge)
[*]Windows font support for both Type 1 and TTF fonts, or a vector font editor of some variety (font support for Ubuntu isn't really there yet, even with the recent release of those fonts, and I actively use almost 600 of the fonts I have for design... and if this isn't possible, then I have to wait on the switch until I can afford VMWare.)
[*]LOTS of hand-holding while I make the switch (if I can).
[/LIST]

I think the two big issues are the page layout software and the font support. Once I can work around those, I'll be ready to take the plunge. I'm anticipating about a week of lost productivity, but after that it shouldn't be that big of a deal.

Thanks for any advice/help/humor you can offer.

---

### Post by kidders on 2007-11-06
Hi there,

Having scanned through your list, I would strongly suggest dual booting ... at least for a short period ... chiefly because good-quality, intuitive quarkxpress-like or indesign-like apps are not (at least in *my* experience) too easy to come by in the open source world. Although I've been a full-time Linux user for years, whenever I have anything design-related to do, I instinctively jump for my mac.

Anyhow, on to your list...
[LIST]
[*]**Skype** - Many users find bluetooth audio equipment and webcams a challenge, but once you get into the swing of how Linux does things, you should be fine.
[*]**IRC** - Easy. Your biggest problem will be choosing from a dizzying array of IRC clients hehe.
[*]**LAMP** - Ubuntu makes this very easy. Apps like apache & php tend to work far better on Linux than Windows, so you'll hopefully be quite pleased.
[*]**PDF reading/writing** - You can generate a PDF from any app that knows how to print. There are also some very nice console-based utilities for converting, generating & manipulating PDFs.
[*]**DTP software** - Since you're a long-time pro, I'm a little worried you may find what Linux has to offer a bit finicky & lacking in certain features.
[*]**A really well-done GIMP tutorial** - Gimp's UI *is* a bit ... ehh ... how shall I put this?!
[*]**MP3 & CD playback** - You should find Linux's software far more flexible than MS's.
[*]**DVD playback** - Again, no problem here, but some apps have glitchy or cheap-looking DVD navigation UIs.
[*]**Subversion** - No problem.
[*]**CVS** - No problem.
[*]**Windows font support** - Linux has great font support, but it's quite difficult to use, because you get so much control over virtually every aspect of how font conversions are done, how they appear on-screen, and how PDF generators treat them.
[*]**LOTS of hand-holding** - You've come to the right place! Generally, most Linux users expect people to read a little about a problem they're having, before posting questions on forums. For best results, try to ask reasonably specific questions.[/LIST]I hope that helps.

---

### Post by kebes on 2007-11-06
> A really well-done GIMP tutorial for a complete noob who understands Photoshop but is driven crazy by GIMP's UI.
There is a variant of GIMP called "Gimpshop" that basically tweaks the GIMP UI to make it more "Photoshop-like."

If you're already accustomed to Photoshop, you might prefer using that version of GIMP.

---

### Post by Red.Heron on 2007-11-06
> **kebes said:**
> There is a variant of GIMP called "Gimpshop" that basically tweaks the GIMP UI to make it more "Photoshop-like."

If you're already accustomed to Photoshop, you might prefer using that version of GIMP.

Hey! That's what I need!

One more issue to go, and then I'm no longer dual-booting.

Which, incidentally... how do I do that, or is there an option to do it on the CD? (Nervous about trying it and risking my partition... since I've never done that before.)

---

### Post by kebes on 2007-11-06
> **Red.Heron said:**
> how do I do that, or is there an option to do it on the CD? (Nervous about trying it and risking my partition... since I've never done that before.)
If I'm reading your question correctly... you're asking how to set up a dual-boot?


Short answer: The install CD will automatically set up dual-boot.


Long answer:

You just boot off the Ubuntu CD, and then start the installation. It will auto-detect Windows and during the partitioning phase the default option should be "Guided - resize master partition and use freed space". This basically means that it will shrink your Windows partition (to a size you can select), and install Ubuntu into the newly created free space (for this to work, obviously your hard drive can't be full!). Ubuntu will then install a "bootloader" that will give you the option of Windows or Ubuntu when you turn on your computer.

The "partitioning shrinking" operation will keep all your Windows data intact. That having been said, you should always **make a backup** of your data before beginning a dual boot install! (It's a good idea to have a backup anyway.)

If you want a nice guide for what the install process for a dual-boot is like, check out:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


(If your question was actually "How do I switch from a dual-boot situation to only having Ubuntu" then I apologize for my irrelevant advice!)

---

### Post by Red.Heron on 2007-11-06
> **kebes said:**
> If I'm reading your question correctly... you're asking how to set up a dual-boot?

Yes.

> **kebes said:**
> Short answer: The install CD will automatically set up dual-boot.

Awesome. :)

> **kebes said:**
> Long answer:

You just boot off the Ubuntu CD, and then start the installation. It will auto-detect Windows and during the partitioning phase the default option should be "Guided - resize master partition and use freed space". This basically means that it will shrink your Windows partition (to a size you can select), and install Ubuntu into the newly created free space (for this to work, obviously your hard drive can't be full!). Ubuntu will then install a "bootloader" that will give you the option of Windows or Ubuntu when you turn on your computer.

The "partitioning shrinking" operation will keep all your Windows data intact. That having been said, you should always **make a backup** of your data before beginning a dual boot install! (It's a good idea to have a backup anyway.)

Okay, back up my data... is there a reverse switch or something I don't know about? 

Just kidding. I do backups about once a month, excepting the last 2 because I keep forgetting to grab blank DVD's when I hit the office supply place.

> **kebes said:**
> If you want a nice guide for what the install process for a dual-boot is like, check out:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Oh, dude! That's freakin' awesome! Right down the line, what to expect. Thanks!!!

> **kebes said:**
> (If your question was actually "How do I switch from a dual-boot situation to only having Ubuntu" then I apologize for my irrelevant advice!)

Erhm... not sure how that could be interpreted from what I wrote, but I wouldn't call you a liar. I've had weirder interpretations of the things I've tried to write.

---

### Post by Red.Heron on 2007-11-06
> **kidders said:**
> [*]**DTP software** - Since you're a long-time pro, I'm a little worried you may find what Linux has to offer a bit finicky & lacking in certain features.

Someone at work just pointed out that we use TeX for some layout tasks, and that we have an InDesign plug-in that handles TeX for both importing and exporting (though nobody could seem to find that). And this same person said that TeX was actually developed on UNIX? Is that right???

If so, we may have a solution that's workable, because the first year I was working, we were using TeX to do math equation layouts because nothing else was as accurate. And I'm picky, too: I've been told that my tolerances are tighter than a mother-hugger (or... well, it **sounded** like that, anyway). And that's without a machine. So, if TeX is available on Ubuntu, I may be able to just go through with the whole thing.

Tried Google, came up with nothing about "TeX Ubuntu" specifically.

---

### Post by kebes on 2007-11-06
> **Red.Heron said:**
> Erhm... not sure how that could be interpreted from what I wrote, but I wouldn't call you a liar. I've had weirder interpretations of the things I've tried to write.

Hehe... sorry...!

> **Red.Heron said:**
> Someone at work just pointed out that we use TeX for some layout tasks. ... So, if TeX is available on Ubuntu, I may be able to just go through with the whole thing.

TeX is definitely available on Ubuntu. It's usually packaged with the "LaTeX" markup system. If you install LaTeX support, it will install the TeX packages, too. There are plenty of LaTeX programs for Linux.

It sounds like your TeX requirements are quite specific, so I'm not sure exactly which program to suggest... but as you mentioned, TeX was developed on UNIX, so there is plenty of support for it in Linux.

Hope that helps!

---

### Post by Red.Heron on 2007-11-06
> **kebes said:**
> It sounds like your TeX requirements are quite specific, so I'm not sure exactly which program to suggest... but as you mentioned, TeX was developed on UNIX, so there is plenty of support for it in Linux.

Hope that helps!

Oh, it does help! That's awesome!

So, this is me, looking around for what LaTeX and TeTex are, and if they can be used for what I need them for... might be a few days in response, but I'm excited!

Uh.... any good sites for that, or are the "top 10" in Google good enough?

---

### Post by Maestro23 on 2007-11-06
> **Red.Heron said:**
> Oh, it does help! That's awesome!

So, this is me, looking around for what LaTeX and TeTex are, and if they can be used for what I need them for... might be a few days in response, but I'm excited!

Uh.... any good sites for that, or are the "top 10" in Google good enough?

Might help:

LaTeX: [http://www.latex-project.org/](http://www.latex-project.org/)

TeTex:[http://www.tug.org/tetex/](http://www.tug.org/tetex/)

---

### Post by Ragnar Bocephus on 2007-11-06
I don't know much about DTP at all, but it would seem teTeX was discontinued awhile ago.  The replacement is [TeX Live](http://www.tug.org/texlive/)

---

### Post by Red.Heron on 2007-11-06
Thank you!

That significantly reduces the amount of reading I thought I'd have to do... yep, I think I like the community better than others.

:guitar:

You folks REALLY rock!

---

### Post by freesitebuilder on 2007-11-07
I used GPartEd to create my partitions before I installed, as I wanted a separate /home partition - several people here recommended that to me, as then I could upgrade without doing a complete fresh install and restore of my data. That's what I prefer - but I've seen just as many people saying they prefer the fresh install route. :)

---

### Post by Red.Heron on 2007-11-07
> **freesitebuilder said:**
> I used GPartEd to create my partitions before I installed, as I wanted a separate /home partition - several people here recommended that to me, as then I could upgrade without doing a complete fresh install and restore of my data. That's what I prefer - but I've seen just as many people saying they prefer the fresh install route. :)

What's the difference in partitioning the way you did? I mean, what changes in the way it works if you make a separate /home partition?

---

### Post by kebes on 2007-11-07
> **Red.Heron said:**
> What's the difference in partitioning the way you did? I mean, what changes in the way it works if you make a separate /home partition?

The advantage of having a separate /home/ partition is that you can reinstall Linux (even switch to a different Linux distro) without it affecting your user files. In fact, since most software settings are stored in files in your home directory, this means all your settings (Firefox bookmarks, program preferences, etc.) are all saved. As soon as you re-install the application, it has your old settings.

This also means you can backup/restore your user files and the OS state independently. So you can make periodic images of the root partition, and revert to an old image if you have to (without it affecting all your user documents).


Having a separate /home/ is indeed convenient (it's what I have, too). To do it requires a little bit of knowledge of partitioning: during the installation instead of letting it automatically partition, you enter a manual mode and specify what partitions you want, how big to make them, and how to assign them.


Edit: [Here is a tutorial]("http://www.psychocats.net/ubuntu/separatehome") for using GParted to make a separate /home, but you can also do it during install by using the manual mode.

---

### Post by Red.Heron on 2007-11-11
Okay, all installed, and I wasn't sure about partition sizes, but I gave my /home directory enough to play with (60% of the total HDD). I wasn't sure if the system would need more or not. I'm using an old 120gb hdd (5400 rpm... ugh! I need a new HDD next payday).

I'm having a slight issue with screen resoultions... expected, but I don't know what to do about it or where to read.

Also, is there an RPM installer that actually works? I've tried 5 of them already and I don't seem to be able to see any on the list that inspire more confidence than any other.

And now I just need Apache, MySQL, PHP, perl, python, Tomcat, Axis, Subversion, and Skype, along with a version of VMWare Player that works on the 64-bit platform (since I have an AMD Athlon 64 X2, which is a dual-core 64).

Geez... lots of stuff to learn!

---

### Post by hogwartsnigel on 2007-11-12
Just saying hi red heron. I've switched at the same time as you and although our paths are different, its cool to read a contemporary journy of discovering Linux (Ubuntu). KNow nothing of mysql etc come from a raphic design base myself and climbing the gimp mountain at present.
I think the whole linux community rocks for support and am so please that my last dual boot gave me boot load errors and as such I brave the uniboot. Never look back

---

### Post by Red.Heron on 2007-11-12
> **hogwartsnigel said:**
> Just saying hi red heron. I've switched at the same time as you and although our paths are different, its cool to read a contemporary journy of discovering Linux (Ubuntu). KNow nothing of mysql etc come from a raphic design base myself and climbing the gimp mountain at present.
I think the whole linux community rocks for support and am so please that my last dual boot gave me boot load errors and as such I brave the uniboot. Never look back

A lot of my own training is in graphic design as well. I also just installed GIMPshop by following the instructions at:

[http://delirial.com/archives/howto-gimpshop-on-ubuntu/](http://delirial.com/archives/howto-gimpshop-on-ubuntu/)

However, the installation command changed because I'm working on an AMD64 and I tested it: it seems to work fine, now that I have the 32-bit libs installed. The command line to install is this:

sudo dpkg -i --force-architecture gimpshop_2.2.11_i386.deb

What this does is to tell it to ignore the fact that I'm not on an i386 machine and go ahead with the install anyway. There was some definite negotiating going on in order to get it working right, but the end result seemed to work without much in the way of issues. There was just one thing I noticed, and that is that the "canvas" filter (under "Artistic") seems to take up an inordinate amount of cache space in the RAM, but since I'm not really a programmer this is for an unknown reason.

The menus at the top of the image (which you have to load first, before you'll see them in familiar-like fashion) are laid out basically the same as Photoshop, but with the GIMP's options instead. I dove right in and managed to get the images done I needed to today, and then I was able to save them and send them off without a single issue!

Well, we'll see... the people I've sent them to actually run full Photoshop, so I'm sure the fonts issue will be one I need to get handled soon.

But I still can't seem to get Skype working. It doesn't matter what I try: nothing works! I've tried wine and the Windows version, but it doesn't like that. I've tried the Feisty version, but Gutsy doesn't like it on the AMD64 platform. So, I'm at a loss for that, since that's how I keep in touch with most of the people I know (including a couple of fairly important clients).

If anyone can figure this out, I'd be really glad to hear about it!

Thanks,

--Red

---

