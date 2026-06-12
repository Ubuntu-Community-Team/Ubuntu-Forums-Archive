---
title: "Installation.... Went reasonably well!"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by mafitzpatrick on 2006-06-10
Just thought I'd post experiences with the install here.  I've used Linux before about 6 years previously (tried Redhat mainly and KDE at the time) but left it after spending more time trying to make my computer work than actually doing work with it. 

After hearing praise about Ubuntu from the local LUG I took a look over here liked what I thought & downloaded and burnt the iso (actually, I spent about a month thinking about it).  I've just completed that install from the Live CD and and now writing from within Ubuntu itself.

Installation was a generally positive experience with some issues.

The biggest hurdle was the partitioning.  The instructions here could be clearer - even for me who knew what it was "supposed" to be doing.  For example the option to resize the partition picks a value & I could not for the life of me work out if that was optimum, minimum, or just plain random! There was no indication what space the Windows partition required to be viable - it allows resizing down to 0 & then errors out afterwards.

My guess is this is "advanced user" land really but a lot of people choose to dual boot. Maybe contiguous was the way to go, but there is little information about what these things mean in reality (graphically represented in some way).  The line "New partition size" is also a bit vague: Is that the "new partition" or the "new size" (i.e. the Linux one, or the resized Windows one).  A better phrase may be something like "Resize your current partition to:"

Anyway, I picked a size, it failed & the whole installation ground to a halt. It made like it was doing something (waiting icon) but the HDD & CD were silent for 1hr.  Quit and re-started. Second time round I just decided to remove the existing partition and that worked fine.  Downside being only then did I realise that I'd not backed up everything I thought I had!  Obviously this is my bad, but you have to see the funny side.

Overall, the whole installation process was rather slow. I don't know if this is a problem with my drive (and I suspect it is) but when it takes over 1 minute for a dialog to appear it's a stretch calling it a "Live" CD.  Inebriated maybe? Concussed? It's a nice idea - and well implemented otherwise.

I would have loved an option to bypass loading the desktop and jump straight into the install - especially after the 3rd time around!

Now it's installed.  Wireless/etc. all work fine and - as has been said by others - this was less painful that getting this setup working on Windows XP.  The effort that has been put in here is obvious - and a great credit to everyone involved. Only a few minor gripes remain now I've spent an hour or so fiddling:

[LIST]
[*]Firefox displays strange "squashed" fonts when (I think) Verdana is used on a page (e.g. Google front page).
[*]Not sure how to (as an admin) move backed up files into another users home.  
[*]How best to arrange files in the user dirs? Coming from XP I'm used to the whole My Documents thing - clearly the home directory is this but there is also the Desktop folder in the same place too. How do others do it?  Perhaps a default folder layout to get us started?
[/LIST]

Anyway, thats all for now... looking forward to seeing where this goes from here.  Thankfully, now I can't for the life of me look in the right place for the time I'll have plenty excuse for late night Ubuntuing.

---

### Post by userundefine on 2006-06-10
[QUOTE=mafitzpatrick]
[LIST]
[*]Firefox displays strange "squashed" fonts when (I think) Verdana is used on a page (e.g. Google front page).
[*]Not sure how to (as an admin) move backed up files into another users home.  
[*]How best to arrange files in the user dirs? Coming from XP I'm used to the whole My Documents thing - clearly the home directory is this but there is also the Desktop folder in the same place too. How do others do it?  Perhaps a default folder layout to get us started?
[/LIST][/QUOTE]
[LIST]
[*]I haven't experienced that specific effect, but you might want to check out [font rendering tweaks]("http://ubuntuforums.org/showthread.php?t=180647&highlight=font+howto") and then [even more improvements]("http://ubuntuforums.org/showthread.php?t=4456&highlight=font+howto").
[*]If you have the backed up files already, just ```
$ mv *files* /directory/for/backups
```If you don't have the backups, check out [this tutorial on the many ways to do backups]("http://www.linux.org/lessons/interm/c316.html").
[*]This comes down to personal preference, really.  In XP, I didn't have my documents in "My Documents" as XP defined it; I remapped that dir to another location on disk (different partition).  So, I just keep all docs (school, work, internet stuff, etc.) in a /docs dir in my home dir, with individual dirs for categories going on down.  Up to you, really.  It's your home, do what you want with it!
[/LIST]

---

### Post by ekarni on 2006-06-10
Welcome aboard!  Regarding your questions:

[LIST]
[*]Squished fonts:  do you have the MS True Type (msttcorefonts) package?  It may or may not help, but it's small and you'll probably want them in other places.  Look for it using Synaptic; if you don't find it, you probably need to enable the universe/multiverse repositories.  This is a very common how-to, check the wiki here:
[http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper")
[*]moving as admin:  if you are comfortable using the command line, just prefix the usual move command "mv" with "sudo", then type your user password when prompted.  e.g. *sudo mv file1 ~otheruser/*  Sudo is very common command that gives a user root privleges on a command-by-command basis.  There's a graphical way, but the only way I can think of to start it involves the command line (hah!).  That would be * gksudo nautilus*, where gksudo is a version of sudo for GUI programs.  Hopefully someone else knows a more elegant way...   
[*]Directory structure: very much depends on how your life and brain are organized.  I have about a dozen top level directories for my major projects, school files, photos, programs I download manually, and the ever-popular "misc."  It's a balance between keeping the top clutter-free vs. having to dig through a few layers to get where I want.  I never used My Documents under Windows, so this is nothing new for me.
[/LIST]

---

### Post by mafitzpatrick on 2006-06-11
Thanks for all your help..

Firstly, as to directories both of what you have described is what I've done. Mostly I was checking to make sure I wasn't doing something "horrendously wrong" - so good news all round.

Fonts I've tried to reinstall/etc. using the instructions (thanks) but it suggests a package connected to OpenOffice. After re-installing that there is still no Verdana font listed (in Firefox->Edit->Preferences...etc) which I assume is the problem. To be honest it just looks "different" to how it normally looks (not unpleasant) I'm just concerned given the large amount of web-dev work I do on my computer - I want to know how it's looking!

Thanks for your help so far folks - it's reinforcing the impression I got pre-install of a good community.  Hopefully I'll be able to give help myself soon enough!

---

### Post by ekarni on 2006-06-11
I just googled the problem - try this and see if it helps:
[Fonts]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Fonts")

If that doesn't help, have you tried using the Automatix script?  There's a sub-forum for it floating around here, I just don't have the link handy.

---

### Post by userundefine on 2006-06-12
[QUOTE=mafitzpatrick]To be honest it just looks "different" to how it normally looks (not unpleasant) I'm just concerned given the large amount of web-dev work I do on my computer - I want to know how it's looking![/QUOTE]
I'm not sure if this will speak to your issue directly, but as someone else doing webdev I found [this site]("http://typetester.maratz.com/") recently where you can test the output of tons of different fonts.  It's pretty cool.

---

### Post by mafitzpatrick on 2006-06-12
Ok, something very strange seems to be happening.

I've added the repository for the msttcorefonts (the Universe one) but they do not appear in the package list. If I take the url out of the config ( [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/) ) and browse down through the dirs ( [http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/msttcorefonts/](http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/msttcorefonts/) ) the package is sitting there waiting.

I know I can probably download & force it to install, but I'd like to find out what's causing it not appear.  Any thoughts?

Thanks for the other links I'll take a look.

---

### Post by mafitzpatrick on 2006-06-12
Ok, I figured it out - by following the instructions.

I had confused the list of package repositories with the selections of what to get from each repository (so I thought I had multiverse enabled for example).  Following instructions in another thread I double clicked the main repository (Ubuntu LTS) and checked all the 4 boxes underneath.  Worked a treat.

**Troubleshooting Instructions:**

Step 1. Read the manual in more detail.
Step 2. Refer to Step 1.

Live and learn - thanks for the help guys!

---

