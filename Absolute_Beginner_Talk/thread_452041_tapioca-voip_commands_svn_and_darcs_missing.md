---
title: "tapioca-voip commands svn and darcs missing"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by rhageman on 2007-05-22
Hello Gurus,

Here is my second question.

I'm trying to get the parts together to generate a tapioca-voip client to talk to Google Talk.  I'm trying to follow the recipe given at [http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide) but I've run into a stumbling block.  There are four lines where the author is telling how to download the sources and he uses "svn" in two of them and "darcs" in the other two.

My install of 6.10 is complaining "-bash: svn: command not found" and "-bash: darcs: command not found".

Where do I get these?  Or, are there other commands to do the job?

One of the reasons I chose to do this project was because the author said he was demonstrating using 6.10.

Thanks for any light you can shine in here.

---

### Post by rhageman on 2007-05-23
Okay, I kept checking and found these in Synaptic:

darcs
darcs-buildpackage
darcs-load-dirs
darcs-server
darcsweb

svn-arch-mirror
svn-buildpackage
svncviewer
svnmailer
svn-workbench

I'm guessing that one or more from each section is needed.  Which ones?
Is there a standard suffix for identifying the root files of a command?

---

### Post by vtel57 on 2007-05-24
Subversion and Darcs are revision control system apps. I don't know where to get them, but here are a couple of Wikipedia articles about them:

[http://en.wikipedia.org/wiki/Subversion_(software](http://en.wikipedia.org/wiki/Subversion_(software))

[http://en.wikipedia.org/wiki/Darcs](http://en.wikipedia.org/wiki/Darcs)

Lots of info there, including the apps' home pages.

Luck!

P.S. Remember... GOOGLE is your friend. It took me less keystrokes to search Google for these two items than it did for you to post the query. ;)

---

### Post by rhageman on 2007-05-24
Good info Eric!!

I had tried a number of searches for svn and darcs - but - never found those...

Both sites had installable packages listed and used the apt-get command to install them.  It was very easy once they were found.

Thanks again.  Take care.
Bob

---

### Post by vtel57 on 2007-05-24
Cool! :)

---

### Post by rhageman on 2007-06-10
Erik,

This is a late follow up.  tapioca and company frustrated me.  Once I managed to get all the way through the tapioca install, it's gui decided that it wanted an older version of one module.

Someday, I may come back to play in the Ubuntu fields.  For now, I'm out looking at Mandriva and openSUSE.  Mandriva stubbed its toe twice when neither Live CD booted to an operating system.  Community there is still discussing the problem.  I have openSUSE 10.2 installed its Live DVD worked for both Gnome and KDE.  I decided to explore in KDE for a while at least.

Take care.  Thanks for the help and encouragement.
Bob

---

### Post by vtel57 on 2007-06-12
I just spent the past week installing and customizing Linux Mint, Zenwalk, and Vector Linux. I had to compile my own kernel for Zen (it's a long story), but all-in-all... three pretty decent distros. Give one a shot... not Linux Mint, though. That's just a green version of Ubuntu Feisty w/ commercial apps already installed. Maybe the Zen or Vector (both Slackware dirivatives). :)

Luck!

~Eric

P.S. I installed Mint, Zen, and Vector over my Fedora Core, SuSE, and Mandriva installations. I had already taken them as far as they could go.

---

