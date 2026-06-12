---
title: "all-in-one global configuration"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by doublemeat on 2007-10-03
Hi there, I'm pulling my hair out on where to execute a single custom global script from at user login.

I have a bash script called "startup".  I need it to be stored (and it is) in /data/system/bin, a custom folder with appropriate read/write/execute persmissions by all users.  In this script, I remap my MacBook keys, set environment variables, aliases, and load programs that all users need.  (E.g. beryl-manager.)

After some 40 hours of research and tinkering with it, much less hair, and this much closer to breaking up with my wife, I've given up.  Its time to cry out for help.  The requirement is to do everything necessary (and that is scriptable) for all users in one script.  (Rather than scattered about in a dozen "standard" auto startup scripts and config files...that Ubuntu variously doesn't seem to process even considering some are meant to execute at login and others on terminal launch.)

I'm having the following, seemingly unsolvable issues with my 'startup' bash script--and this is the primary enumeration of the problems I'm requesting help on:
[LIST=1]
[*]Aliases don't seem to work when defined here (in my startup script), even when the script is called with the ". " source modifier.
[*]PATH settings show up in a terminal's 'echo $PATH' command, but clearly are not honored/searched, either from the gnome shell or a gnome terminal.  (Again, even when sourced with ". ")  Yet when the same path is put in /etc/environment, not only does it also show up in 'echo $PATH' but also is actually honored.
[*]Other environment variable settings, e.g. for global RAR settings, similarly show up in 'echo $RAR' (etc.), but are not noticed by programs either from a gnome terminal or when launched straight from gnome.  (How can the variable be there yet not picked up?)  And again, the same variable works when defined in /etc/environment.  The way I define it in my startup script is in the form, e.g. *export RAR="-ep1"* etc.
[*]And some other illogical strangeness.
[/LIST]

The only thing that does work about my startup script are the calls to xmodmap to remap certain keys on my macbook keyboard (one customized key at a time--remember I only want ONE place to maintain non-default settings on a regular basis!--mainly for portability and personal sanity).  And calls to start beryl-manager and emerald also do work.

I've come to understand (please correct me if wrong) that:
[LIST]
[*]/dev/environment is the best (only?) place to **reliably** set PATH; but does not itself support variables (e.g. my required custom user-specific paths).
[*]It seems that alias statements only work when declared in one of the bash startup scripts (why are there so many!  ...And so many that aren't called!), possibly only those in ~ directory (still looking into this).
[/LIST]

So besides the first list of questions, there's also this huge question: *where in the heck is **one place** that I can ensure that this one single script executes for every user?*  And ideally, one that is not so fragile that an unhandled script error doesn't break the login (the latter being a very secondary concern).  I've tried the following, all with no success:
[LIST]
[*]Dropping a link to the script in /usr/share/gnome/autostart (and making sure permissions are at least rx for everyone).  Never gets invoked.
[*]Copying the bash script file itself in /usr/share/gnome/autostart (and making sure permissions are at minimum rx).
[*]Copying a ".desktop" file from ~./config/autostart (which does work), to /usr/share/gnome/autostart, then modifying it to call my startup script instead of whatever it was calling before.  Even after setting permissions to wide open and/or executable, the script will not launch this way.
[*]Calling from /etc/bash.bashrc.
[*]Calling from /etc/gdm/Xsession.  This is way too fragile and breaks the login process.  I can't seem to simultaneously call it from Xsession without errors occuring (thus requiring Gnome safe mode login), AND in source the script via the ". " modifier (perhaps because Xsession is a sh script and my startup script is a bash script?).  I can do one or the other though, but if it's not sourced from Xsession, then barely nothing "sticks" by the time the script finishes.  I think this is probably a similar problem sourced from some of the other places.
[*]/etc/profile.  I can't even remember why this doesn't work--this was the first thing I tried, spent 10 or 20 hours on it and missed my daughter's birthday, and moved on.  It seems this script does execute, but my explicitly called custom script never gets executed.
[*]
[/LIST]


Many thanks!  

Just as an offhand [OT] observation from a self-described "supreme power user" (and ex-programmer) but Linux newbie:  In the countless hours of research on this problem, it's clear that I am not alone in endless frustration over where to perform perfectly ordinary login-related stuff.  This particular confusion, frustration, and annoyance seems epidemic throughout the Linux community.  As a generalized observation, it seems that Ubuntu is great for rank newbies (it "just works" out of the box), and unix-like OS'es in general seem to be great for god-like pros and open-source developers...but totally sucks for "power users" that are not quite god-like experts, yet nevertheless cannot accept "don't touch it so that it won't horribly, irrovecobly break" that Linux seems to demand (otherwise it breaks).  Linux may be far more stable and tweakable than Windows (hooray), but it is exceedingly fragile, confusing, incredibly inconsistent, and illogical in terms of basic configuration and customization.  At least with Windows (gasp) you know the four or five global and user-specific startup locations (which admittedly is still too many), and more importantly, you know that they *all will work*, and *won't conflict* with each other!  (I realize there is a good reason for that: a fairly monolithic design and commercial evolution, vs. Linux' hodge-podge (and amazing) distributed open-source model.  But still.)  Because of Vista, I quit Microsoft and embraced Ubuntu (after first straying mistakenly to Mac--magnificent shell over unix but talk about a doubly proprietary trap!).  More and more though, I'm regressing back to XP just to get *some* work done.  Sorry, I know this is OT.  I've been going backwards in Ubuntu for the last three months--it works less well now that it did when I started (and I've installed it over a half dozen times).  And my personal relationships are suffering.  I really want this to work.  I have a future business dependent on me figuring this awful mess out.  I am becoming a convert to "free as in speech" in a big, big way, and once I get up and running I want to help (starting with sharing my MacBook install steps--more complete and straightforward than the other triple-boot macbook/ubuntu guides here and elsewhere).  But my hopes are flagging :(.  Linux--Debian and/or Ubuntu at least--seems absolutely riddled with a self-referencing spaghetti mess of legacy baggage.  Baggage that makes no logical sense whatsoever.  Microsoft is accused of breaking backwards compatibility often across Windows versions, but I think (they) may have a better balance of backwards compatibility vs. carrying too much legacy baggage.  Sorry for the long first-ever Ubuntu forum post.  Too much pent-up frustration, apparently!

Jim

---

### Post by funpop on 2007-10-03
hey there..

im not able to help you. just wondering: why do you need to have your custom settings applied each time you start your machine ? doesnt gnome/kde remember your settings ? 

suggestion: post your problems and questions, maybe your script too, in the programming subforum or the main support forum. im sure someone will give you a helping hand

---

### Post by doublemeat on 2007-10-03
> **funpop said:**
> just wondering: why do you need to have your custom settings applied each time you start your machine ? doesnt gnome/kde remember your settings ?

I didn't say I needed to apply them every time I boot.  My only requirement is that custom settings and configurations be in one place, rather than scattered across the system.  It just so seems to be that a script is the only way to reasonably encapsulate this.  And it also just so happens that in order to define enumerated keyboard mappings (in only one place), in the same script as doing other custom global stuff affecting all users, basically requires to "apply" them each time--not only each time I reboot, but login.

As far as posting the script itself goes, I'm happy to do that but I fear it would confuse the issue and waste people's valuable time.  I'm not interested in debugging the script (already spent enough hours on that), but figuring out what I presume are problems that have (hopefully) been solved by someone somewhere shomehow before, probably much smarter than me.  Such as, where to invoke this script from so that it reliably runs on every login, and the settings (e.g. aliases and env variables) defined in it are visible system-wide, including gnome terminals.

Hope that helps, and thank you for the reply!

---

### Post by coolen on 2007-10-03
Just a thought. This isn't the best solution, but better than nothing.
Try adding the script to System -> Preferences -> Sessions?
They seem to be pretty reliably honoured.

---

### Post by doublemeat on 2007-10-03
> **coolen said:**
> Just a thought. This isn't the best solution, but better than nothing.
Try adding the script to System -> Preferences -> Sessions?
They seem to be pretty reliably honoured.

Thanks.  I did try that, and yes it does work perfectly and reliably.  Actually I kind of mentioned that indirectly, by including "~./config/autostart" in the list of things I tried (which is part of what the "Sessions" GUI applet manages).

The fatal problem though, is that it's per-user.  I will be replicating this configuration not just across multiple users on my macbook, but across a half-dozen desktop machines, as well as friend and family's machines in the future (like most of you probably I have unwillingly become the defacto IT support for everyone I know--if I can use that to further the "free as in speech" agenda then hurray for us).  And in the near future, whatever solution I find to this mind-numingly simple yet frazzingly difficult to impliment requirement will be replicated across server farms.

So the solution absolutely has to be as self-contained, portable, and "drop-in" as possible (e.g. a monolithic custom bash script called from this mysterious "reliably executes" place in Ubuntu and features such as PATH export and alias defs "work").  Furthermore, I need to leave all the stock Linux startup scripts etc. as unmolested as possible, because it needs to work across various distros and upgrades, and I can't be overwriting or updating dozens of (originally) system-created files scattered across each system, or assuming much about them.

This personal requirement is frustratingly simple.  I'm amazed that there isn't at least one obvious and robust solution for such an "enterprise-ready" OS.  Since the days of...what was it, DOS 2.0?...you could do all that kind of custom stuff by calling a single "drop-in" .BAT file from AUTOEXEC.BAT (with a one-line modification in one place necessary on all machines calling it).  In Windows you can do the same thing by calling, say, "my-custom-startup-script.cmd" (or .vbs or .pl or .py whatever) from HKEY_LOCAL_MACHINE...Run, or from "...All Users/Start Menu/Programs/Startup", or from policy editor, etc. (And "permanently" modifying the registry to do so for all users is as simple as executing a three-line .reg file one time.)   All autorun locations work, and they all work the same in terms of how they execute (just differ in the ways in which they are defined).  You don't need to worry about how it's sourced, whether it's executing in an interactive terminal or not, login shell or not, etc.  (I realize that fewer worries like that probably also mean less flexibility--but at this point that's the last of my concerns!)  With Windows, you *do* need to worry about "interactivity" in terms of whether the script will run unattended or not, but that is *your implimentation decision*, not a seemingly arbitrary and inconsistent system constraint.

Anyway, thanks again!  I'll keep trying to find an answer.  I know alot of people have asked the same question without a good answer, so if someone ever does provide a good solution to this (or I figure it out myself), posting the answer here is going to help alot of people!

---

### Post by coolen on 2007-10-05
Well, for a solution to run at boot-time, there are two possibilities that present themself:
First, place the script in /etc/rcX.d
These scripts are run at different times during bootup/shutdown. There's a naming convention to follow. Scripts to be run begin with S and a two-digit number (not sure what the signicifcance of this number is, probably an order), and ones with K are not to be run.

Looking through, 0 is for shutdown, 1 is for singl-user mode, 6 is for reboot S is general startup...I'm not sure about the others (README files are no help), but this information shouldn't be hard to find. I know one is run when the X server starts, possibly three?

Alternatively, call your script from one of the bootup scripts.

Good luck :)

---

### Post by doublemeat on 2007-10-05
> **coolen said:**
> Well, for a solution to run at boot-time, there are two possibilities that present themself:
First, place the script in /etc/rcX.d
These scripts are run at different times during bootup/shutdown. There's a naming convention to follow. Scripts to be run begin with S and a two-digit number (not sure what the signicifcance of this number is, probably an order), and ones with K are not to be run...Alternatively, call your script from one of the bootup scripts.

Thak you.  I have actually looked into that but it seemed too scary (and odd) what with all the multiple subdirectories and links and whatnot.  Kind of kludged together and seems like it would easily break.  But trying it is a good idea, what do I have to lose.  I do believe I have a utility that manages the subdirectory business, you just put the script somewhere, though you still have to know what 0 - 6 is etc.

Controlling a scripts' execution through it's name, and subdirectory, seems like a fantastically kludgey and fragile solution--anybody with me?  Seems like something MS-DOS would have done in the late '80s.  Anyway, if it works, at this point I don't care.

RE other boot up scripts--that's part of the problem, not a single one seems to execute my script reliably (e.g. "really" set the path even though echo $PATH shows it is clearly set correctly but not searched or honored, or aliases are remembered...or they never actually run in the first place, etc.)

Thanks again.

---

### Post by coolen on 2007-10-06
Just wondering, where are you placing this script? I'm going to assume you've got the permissions set correctly: you're obviously no newb. Have you tried putting it in a standard path directory? Could be that path settings are handled differently at that point (security measure?).

Also, a little help with the run levels: it seems that X11's run level is 5.

---

### Post by doublemeat on 2007-10-11
> **coolen said:**
> Just wondering, where are you placing this script? I'm going to assume you've got the permissions set correctly: you're obviously no newb. Have you tried putting it in a standard path directory? Could be that path settings are handled differently at that point (security measure?).

Also, a little help with the run levels: it seems that X11's run level is 5.

Thanks.  The script is in a short but custom path.  That's a good observation about when the path gets set, but in general I try to call the custom script with a fully qualified path.  So far, that (by itself) hasn't been presenting a problem.  My only problem with putting the script in a standard place, is that I want my custom config (+ all the data that that means)--as an atomic, functioning, customized system--to be as portable as possible.  And not just to other Ubuntu installs, but other Linux/BSD installs as well (including Mac).  And Windows too!  I know the latter is a bit of a stretch, but it is actually working out fairly well.  Ultimately, "maximum simplicity" for this requirement is going to have to mean being a little non-standard on all systems, so I can just clone a single directory (and everything underneath it).  Anyway, that was a bit of a long answer.  Thanks for the thought and advice.

---

