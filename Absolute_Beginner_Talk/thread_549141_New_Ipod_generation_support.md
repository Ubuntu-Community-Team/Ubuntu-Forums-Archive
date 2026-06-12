---
title: "New Ipod generation support"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Grimgoil on 2007-09-12
Hola, been looking around to see if any programs have been able to get the new ipods ready for use in linux and couldn't, so coming here to ask the sages if they know of anything thats working with them now - specificity ipod nano 3rd generation?
been using up untill now gtkpod though the last update there was in June.

---

### Post by mostwanted on 2007-09-12
My dad just got a new iPod classic 160gb. I'll see him in a few hours, so if it works / doesn't work I'll see to get back to you.

---

### Post by jw5801 on 2007-09-12
I have a relatively new video iPod and I use gtkpod. It works fantastically for me so give it a shot. Just opened it up and it has options for many different types of nanos so it appears like it has support.
```
sudo aptitude install gtkpod
```

---

### Post by atria on 2007-09-12
Nope, he is talking about the newest generation. I'm not sure if it works though and i am pretty hesitant to recommend it to my friends due to this fact.

Do update us if it works : ) 

Thanks!

---

### Post by mostwanted on 2007-09-12
I can confirm that the iPod Classic 160 GB is auto-detected by RhythmBox and I can see playlists and play the songs on the iPod harddisk on my computer. I tried synchronising, but that corrupted the iPod so it needed to have the software updated and all the content transferred over once more... 4 hours worth syncing, I feel so guilty now :(

We can conclude that reading from the iPod works, but adding songs (via RhythmBox at least) doesn't work.

---

### Post by Grimgoil on 2007-09-12
Nope, does not work with GTKPOD either, guess ill have to wait, or just dual boot with windows for itunes,

---

### Post by rlklee on 2007-09-12
The gtkpod devs are working on this issue.  Same goes for the classic 80 gig and the new nanos.  

-R.

---

### Post by horseglue on 2007-09-20
same problem, just got a 160 gig. i plugged it in, and it just corrupts the files, leaving me not able to see any of the files from the pod itself.
:p hope gtkpod does a fix  soon...
i dont have windows.s...

---

### Post by Adramelech on 2007-09-20
apple introduced a new encrypition thing on those new ipods to prevent 3 party applications to access the ipods, the good news is that is already cracked so you have to wait for the next release of the software to get the fix.

---

### Post by jw5801 on 2007-09-20
I love that... they refuse to release iTunes for Linux, and yet they actively try to prevent us from writing our own client so we may utilise their product.

---

### Post by stmiller on 2007-09-20
[http://amarok.kde.org/blog/archives/496-iPod-Classic-Will-Be-Supported.html](http://amarok.kde.org/blog/archives/496-iPod-Classic-Will-Be-Supported.html)

Support is in the works.

---

### Post by Tiggums on 2007-09-20
itunes's way of kicking us all in the how-do-ya-do's! I can't stand when companies force you to go with their software.  The good news is (like it's already been said...) that the crack has already been made, so just give it a little time.

---

### Post by littleiffel on 2007-09-22
I got my new IPoD workign with linux. get infos:

[http://www.backdot.com/?p=50](http://www.backdot.com/?p=50)

---

### Post by Linuturk on 2007-09-27
What dependencies are required for the svn checkout of libgpod ?

Can you go step by step littleiffel?

---

### Post by Linuturk on 2007-09-27
Can confirm mine worls via the latest svn of gtkpod and libgpod

---

### Post by GepettoBR on 2007-09-27
> **Tiggums said:**
> itunes's way of kicking us all in the how-do-ya-do's! I can't stand when companies force you to go with their software.  The good news is (like it's already been said...) that the crack has already been made, so just give it a little time.

This time they're trying to force more than that. It's either buy a MAC, use a buggy, slow iTunes in Windows or no iPod at all on Linux? Damn.

---

### Post by LowSky on 2007-09-27
I dont mind that apple wants user to use their software... but give linux users a native linux program... then I'll be fine

---

### Post by nuclearj on 2007-09-28
> **littleiffel said:**
> I got my new IPoD workign with linux. get infos:

[http://www.backdot.com/?p=50](http://www.backdot.com/?p=50)

Hey I went to that site and I do not know where to start to install the program to use for the new ipod nano.  Could you possibly help a brotha out?  And in laymens terms would be cool too!

---

### Post by Linuturk on 2007-09-28
Get onto #gtkpod on freenode. You'll have to compile gtkpod and libgpod from SVN from their site. They can give you a hand there.

Also, get your firewireGID. See the link you quoted for how to do that.

---

### Post by smbm on 2007-09-30
I've built some Gutsy packages from SVN of libgpod2 and gtkpod if anyone needs them pm me and I'll email them to you (due to size).

They were built with checkinstall so they are probably not the most bullet proof packages ever but they seem to work here.

---

### Post by nuclearj on 2007-10-07
> **Linuturk said:**
> Get onto #gtkpod on freenode. You'll have to compile gtkpod and libgpod from SVN from their site. They can give you a hand there.

Also, get your firewireGID. See the link you quoted for how to do that.

Ummmmmm, when you say "compile" do you mean install the .deb packages?

---

### Post by justinmiller87 on 2007-10-07
> **Grimgoil said:**
> Hola, been looking around to see if any programs have been able to get the new ipods ready for use in linux and couldn't, so coming here to ask the sages if they know of anything thats working with them now - specificity ipod nano 3rd generation?
been using up untill now gtkpod though the last update there was in June.
I posted a link to this about a week ago, it's how to get iTunes 7.3 working in WINE. Now of course, the latest version of iTunes is 7.4. You're welcome to try to install it from there, because as far as I know, 7.3 only gives support through the iPhone and 7.4 will allow the new iPods.

[http://ubuntuforums.org/showthread.php?t=566134](http://ubuntuforums.org/showthread.php?t=566134)

---

### Post by Linuturk on 2007-10-07
> **nuclearj said:**
> Ummmmmm, when you say "compile" do you mean install the .deb packages?

No, I mean compile the program from SVN. As far as I know, they haven't released the code for the next-get ipods. That's why I said to join their irc channel. They helped me get it done.

---

### Post by Niskyspy on 2007-10-11
I want ubuntu back on my comptuer but I guess I'll have to wait til we get software capable to work with the 3g Nano Video. :(

---

### Post by Linuturk on 2007-10-11
Just read the thread. You can get it supported. It just takes some work.

---

### Post by rbprogrammer on 2007-10-11
i havent had time to read the whole thread so if someone already suggested this, then i second it, i guess...

i have problems with my ipod on ubuntu as well.  especially with videos.... but it looks like this post can help: [http://ubuntuforums.org/showthread.php?t=566134](http://ubuntuforums.org/showthread.php?t=566134)

someone has supposedly found a way to use itunes on ubuntu with wine... so if you dont find any alternatives and your last resort is itunes, then try it.  i personally have not yet...

---

### Post by traviss0 on 2007-10-13
Alright, here goes....

I just bought an iPod touch.....I have been reading the net about getting it to work with Ubuntu. There seems to be one major problem that prevents me from doing anything...my iPod doesn't really mount.

I say "doesn't really" because an icon shows up but nothing really happens. I don't think it is actually mounted. It is not even charging. I activated it through windows and added a picture on it just to check. When I plug it in it opens up the window and shows a folder, I click on the folder but nothing happens and it just loops back and opens up the window again.

Am I missing something? I just want to get this recognized so I can complain later about not being able to get music on it.

I'm pretty sure it is not fully mounting (if that means anything)..

---

### Post by Pierre Lourens on 2007-10-15
Regardless of Apple's bitchiness, I hope that a reliable solution is released soon.  Compatibility with my iPod Touch is one of the main things keeping me on Mac OS X.

---

### Post by Grimgoil on 2007-10-16
Thanks to everyone for their suggestions, i've been using windows+itunes for a while now and just came back on to ubuntu (wont dual boot). so my ipod is loaded up for now and i would rather at the moment wait until there is a real actual full alternative before i start exploring.

---

### Post by Lady Owl on 2007-10-16
traviss0 - if your computer is old, it might use usb1, and that won't recharge like usb2... Although mine *does* show the contents etc. (haven't really tried anything else yet, as I have problems with sound system) I had to buy a separate recharger. Of course, it is handy when travelling, anyway.

---

### Post by omar_mandeel on 2007-10-18
Hello,

Can I please get a step by step guide on how to do this (screen shots a plus). I have put over 20 hours in trying to get this stupid iPod to work and it doesnt. I tried [www.backdot.com](www.backdot.com) but evidently Im too stupid to figure out how to update libgpod/gtkpod and I think somewhere in the process I managed to break something important. gtkpod, amarok, and rythmbox all give me the same thing: the music shows up in each other but not in the ipod. It is being transferred as indicated by the ¨memory meter¨.  And im not sure what format (00AJC2132 or 0x00 0xAJ 0xC2...) or where to put the FirewireGuid.

Its an 80GB iPod classic (Silver), the back says the model number is A1238, running on a Dell Intel Duo Core processor with Ubuntu (Feisty).

Also, anything about the iPodlinux project and this aggravating P.O.S. would be much appreciated.

Muchas Gracias

---

### Post by GepettoBR on 2007-10-18
As of now, the iPodLinux does not fully support Video iPod or the new Classic models.

---

### Post by omar_mandeel on 2007-10-18
Thanx.

Any word on getting the iPod to work all together?

---

### Post by Pierre Lourens on 2007-10-18
As of right now, I'm not sure.  It's been pretty experimental and speculative, and most people know as much (or as little) as you do.

I also want it soon though, I don't wanna boot into Mac OS X for my ipod touch.

---

### Post by eheitner on 2007-11-11
Hi-
I have the 80 gig 6th gen iPod. I have just installed the package for gtkpod today (11/11/07) and saw that it seemed to support sixth gen ipods, but I am still not seeing the music files show up on the ipod (ie, they show up when gtkpod or amarok opens the ipod, but not when the ipod is disconnected). 

This link, which was quoted upthread as a help source:
[http://www.backdot.com/?p=50](http://www.backdot.com/?p=50)

Seems to be broken now.

Is there another place which has a simple HOWTO for getting gtkpod to run on a 6th gen ipod?

Thanks.

---

### Post by omar_mandeel on 2007-11-12
Im curious. If I downgrade my iPods firmware, can I install ipodlinux or rockbox?

---

### Post by GepettoBR on 2007-11-12
AFAIK you can install Ipodlinux on the newer firmwares, it just won't support the new features.

---

### Post by omar_mandeel on 2007-11-12
AFAIK? (sorry Im a noob)
How? The ipodlinux website still says it has nothing for the 6th gen.

---

### Post by pacsum on 2007-11-12
If you don't like what apple is doing then why buy an ipod. Get a creative, hell they're even better from my point of view.

---

### Post by jw5801 on 2007-11-12
Rockbox is firmware in itself, so it will overwrite whatever is on there, as far as I'm aware anyway.

---

### Post by GepettoBR on 2007-11-12
> **omar_mandeel said:**
> AFAIK? (sorry Im a noob)

AFAIK = "As Far As I Know"

---

### Post by justinmiller87 on 2007-11-12
> **jw5801 said:**
> Rockbox is firmware in itself, so it will overwrite whatever is on there, as far as I'm aware anyway.
Not exactly. The firmware will let you load into either the Rockbox or iPod. If you turn it on, put it on hold at the Apple logo and it will load into the iPod default software.

---

### Post by jw5801 on 2007-11-12
> **justinmiller87 said:**
> Not exactly. The firmware will let you load into either the Rockbox or iPod. If you turn it on, put it on hold at the Apple logo and it will load into the iPod default software.

Ah ok, thanks for the clarification!

---

### Post by made72 on 2007-11-19
A new version of YamiPod is released, version 1.7
Changelog: added support for new iPods (nano and classic)

---

