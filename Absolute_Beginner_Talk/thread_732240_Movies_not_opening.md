---
title: "Movies not opening"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-03-22
Hey,

I found a drive in my computer that I had forgot about.  The reason why I had stopped using it was because windows XP froze massively during a re-installation and then it would never boot - even with the disk in - it's as good as ****, basically.  So I plugged it back in and went through it today (*which btw, on an off question I have one of the first major SATA mobos out there, the thing's ancient, 2 IDE and 2 SATA ports and I was having trouble unless I set it in the bios which made me wonder-- if SATA is always cable select depending on SATA1 or SATA2 - why do they still have jumper pins in the back?? - They don't do anything, b/c I was trying to force it as a slave and it would still try to boot it - it would only not boot it after I finally changed the boot order in the BIOS*) - I got all my old songs and such off there - found a few music videos - copied it all onto my local disk.  Though if I go to play SOME of the videos - I double click - nothing happens, kaffeine doesn't even attempt to load ---- I just logged out and logged back in - and now it works fine?  Any idea why something would not even attempt to load?  I've only noticed this with stuff from this drive...  If the RAM is full - would that make it not attempt to load?  I have been using a lot of RAM lately (for reasons unknown).

It seems like my computer's slower since I put that other hard drive in - but that doesn't make any sense unless I'm copying off of it (single core P4 3.0Ghz).  Anybody have any ideas?

Thanks in advance - I realize the question is rather ambiguous.

PS:  Do you think I would benefit from another gig of ram (if I check and see if my mobo (Abit IC7-G) can support it??)  It's always full - somebody once told me that UNIX systems don't use it like windows - that it'll be full until it needs to use it - then it'll clear the oldest stuff out - so essentially it'll always be full - but that's okay - the swap partition is only using a small amount (like 350k / 2gb swap part).  I'm not sure if another stick of ram will help - I am going to build myself another computer come end of summer - but until then - I'm not sure if I should try to give this another stick and see if it'll flow a lil better - or is it simply too much for too little?

Thanks :-\

---

### Post by Hoaxe on 2008-03-23
your post IS way ambiguous hehe, a little more detail would be appreciated, but anyways, 

i'm assuming worst case senario, so you have a bunch of videos, all of the same filetype and only SOME do not play at all, do not even load in fact. well, sometimes naming a file an avi, doesn't always make it one; 

some players can see through that and play it anyways, others can't. i can't speak for kafein because i've never used it [gnome guy my self] but try getting VLC and open it from there, see what that does.

as for your ram question, personally, i'm running on 750 mb of RAM, with full compiz-fusion "wow" power and i still run WoW with reasonable speed and graphics and i'm running on a similar chip as yours, 3.something ghz dual core. so do you NEED another stick of ram? not really, i certainly don't. blender and maya are passable on this same system [thanks if only to my 3ghz]  as well as gimp and other graphical apps.

linux, it's that good.
now if only someone could help me boot the damn thing on my laptop....

---

### Post by mikeyphi on 2008-03-23
Just a suggestion for tracking the problem: since all was OK after re-logging have you looked at memory/system usage using System Monitor whilst selecting movie files etc? Might give an indication of when/if your RAM is be used.

---

### Post by Syndacate on 2008-03-23
> **mikeyphi said:**
> Just a suggestion for tracking the problem: since all was OK after re-logging have you looked at memory/system usage using System Monitor whilst selecting movie files etc? Might give an indication of when/if your RAM is be used.

Which system monitor?  Something like Conky..or something like top?

> **Hoaxe]your post IS way ambiguous hehe, a little more detail would be appreciated, but anyways,

i'm assuming worst case senario, so you have a bunch of videos, all of the same filetype and only SOME do not play at all, do not even load in fact. well, sometimes naming a file an avi, doesn't always make it one said:**
>  but try getting VLC and open it from there, see what that does.

as for your ram question, personally, i'm running on 750 mb of RAM, with full compiz-fusion "wow" power and i still run WoW with reasonable speed and graphics and i'm running on a similar chip as yours, **3.something ghz dual core**. so do you NEED another stick of ram? not really, i certainly don't. blender and maya are passable on this same system [thanks if only to my 3ghz] as well as gimp and other graphical apps.

linux, it's that good.
now if only someone could help me boot the damn thing on my laptop....

Ha, I had trouble getting linux on my laptop too.

I didn't rename any of the files by extension - I do realize that they are encoded differently - and if I had these problems when I originally obtained them - then I would have just deleted them right away.  This is some new crap - but it's not just videos - last night it happened with a song.  Something about the data from that drive is tainted or something.  And you can't say it's permanent or something b/c as soon as I log out or reboot, it plays 100% just fine.

It's weird as hell, i can't make any sense of it.

Usually when it doesn't run w/ Kaffeine, I can still open it with VLC - but that's not solving the problem - it's not even completely circumventing it.

Mine's a 3.0 SINGLE core - not a dual.  I didn't even know they  made dual core +3.0.  So you have an ultimately kick-*** processor paired with 750mb of RAM?  With dual core +3.0's, I don't even see why you would remotely have problems with your setup.

Though I'm just trying to figure out if it'd be worth it to get an extra gig (i'd have to buy 2, I think, b/c I have 2 512's in there now, and I don't think I can put 512/512/1gb - think they gotta be in pairs or something) - or if the extra gig would be too little for rebuilding it in like 5 months.

---

### Post by Crash 0verride on 2008-03-23
I don't know were it would be for Kubuntu but on Ubuntu it is System->Administration->System Monitor

If you have ever tried windows xp or and windows version

It is like Task Manager (you know the thing that pops up if you hit CRL+ALT+DELETE)

---

### Post by mikeyphi on 2008-03-23
Quote: Which system monitor? Something like Conky..or something like top? Quote

Probably KSysGuard on Kubuntu

---

### Post by Syndacate on 2008-03-23
> **Crash 0verride said:**
> I don't know were it would be for Kubuntu but on Ubuntu it is System->Administration->System Monitor

If you have ever tried windows xp or and windows version

It is like Task Manager (you know the thing that pops up if you hit CRL+ALT+DELETE)

ha, I'm sorry, I use Gnome...ya it's kubuntu w/ gnome - lol

But seriously - this problem is getting RIDICULOUSLY bad.

It's like as soon as I touch a folder/file the countdown timer starts.  Then nautilus will just DIE.  It's nautilus that's crashing, not the whole system.  Then it can't preview the music icon for .mp3's, it can't show the preview picture for movies, if you try to open ANY folder it says "*The folder contents could not be displayed.*" and under it it says "*Sorry, couldn't display all the contents of "<FOLDER_NAME>*."

Then I double click on nothing - nothing works, if I right click - the "open with" dialog is all boxes 'n misc. characters.

Then I open up konsole/terminal - **ps -e** - **kill pID** - nautilus restarts automatically, and it's fine.

Though it's like as soon as I click one of these folders the countdown start, then nautilus just melts down...

---

### Post by Syndacate on 2008-03-24
Bump*

It just happened again today.

I was playing songs from the **** off my old hard disk.

The system monitor was on and CPU usage and ram usage were both perfect...

Seems like nautilus is the problem - but I don't know why it's doing it with only these files...it doesn't make sense...

---

### Post by Syndacate on 2008-03-30
Okay, it seems the problem is related to a different problem.

That would be when nautilus views too many files it eats itself.

This is apparently a known problem, I don't know how to fix it.

All I know is that when I view all of my music archives, it'll eventually toss an error saying that the contents of the folder cannot be displayed (then kaffeine won't open anymore).

In a forum someplace I read a suggestion by somebody else to soembody else about not showing previews on the icons - that just sounds stupid to me.

I keep hearing about "increasing the file handles" - or something along those lines - anybody have any input on that?

---

