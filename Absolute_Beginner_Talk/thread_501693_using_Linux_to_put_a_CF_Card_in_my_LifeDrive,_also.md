---
title: "using Linux to put a CF Card in my LifeDrive, also RE USB card reader"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by PrettyInUT on 2007-07-15
Hi all - my quest for knowledge has led me here.

I am currently trying to put the Palm LifeDrive OS onto a compact flash card, because my microdrive died. Windows was woefully inadequate for the task, and so I am here, with my laptop all Ubuntu-ed out, and I'm stuck.

First, the page with information I am trying to follow:

[http://trac.hackndev.com/projects/palmld/wiki/ReinstallingPalmOS](http://trac.hackndev.com/projects/palmld/wiki/ReinstallingPalmOS)


When I try to use the git command as written on that page (git clone [http://git.hackndev.com/git/modrom.git](http://git.hackndev.com/git/modrom.git)) I get the following error:

/usr/bin/git-clone: 312: curl: not found
Cannot get remote repository information.
Perhaps git-update-server-info needs to be run there?

I have no clue what that means, but if I surf to the git file url, there is stuff there.

So then I figure "oh well, let's try the long way"...

I installed the programs they suggest at the top using the Synaptic Package Manager.

Unzipping the archive I downloaded from Palm works fine.

Cabextract worked fine, gave me a folder called Data1 with a bunch of stuff in it that I can't do anything with.

Making the folder called "data" was easy (duh), but once I was in there, and tried the command to unshield that information that I just extracted ('unshield ../Disk1/data1.ca' as written on the site) I get the following:

Unknown action '.' on command line.

Syntax:

        unshield [-c COMPONENT] [-d DIRECTORY] [-D LEVEL] [-g GROUP] [-G] [-h] [-l] [-V] c|l|x CABFILE

And then a page of all the various options for the unshield command.

Ummm, that's where I get a bit lost. I am a bare bones newbie - if you'd have asked me to do this fifteen years ago, no problem, I was a DOS baby, I could have figured it out. But a decade or more of Windows has petrified my brain.

What on earth do I need to tell my terminal to get it to open up those files to reveal the juicy goodness of Palm files inside?

Also of note is the fact that after I get my Palm stuff opened up and partitioned properly, I'm going to need to use my Compact Flash reader to get that onto my CF card - but when I plug it in, Ubuntu doesn't seem to see it - nothing pops up, and if I go to Places>Computer there is nothing there for a removable drive or CF card or however it might be listed. How do I get that working?

Thanks so much for looking!

---

### Post by rgarris on 2008-04-26
So ok, I hit the same snag. It seems that at some point hackndev moved their git server and did not update the howto.

the correct URL for the automatic way should read "git2.hackndev.com". I updated the wiki so if you try again, it should work.

[http://trac.hackndev.com/projects/palmld/wiki/ReinstallingPalmOS](http://trac.hackndev.com/projects/palmld/wiki/ReinstallingPalmOS)

Best regards!

---

