---
title: "newbie and usenet and nzb."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by richieboy on 2007-08-18
i've become pretty handy with ubuntu thanks to everyone on these forums.  i'm new to usenet and downloading binaries, though.  i have pan installed and can read usenet posts. i have hellanzb installed according to this post :

[http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb).

but i don't understand what i'm supposed to do next.  step 10 of the above post says:

Download a NZB file and place it in:
Code:

/home/your-user-dir/nzb/daemon.queue/

what does that mean???  is an nzb file kind of like a torrent file?  do i download and nzb file and then open it with hellanzb?

sorry for being such an idiot but this stuff is all brand new to me.

thanks,

rich

---

### Post by felicity on 2007-08-18
NZB files are similar to a torrent in the sense that they aren't the file itself, but a set of "directions" for a program to use to download the files. You can find nzb files in newsgroups beside most full files, (using pan for instance) or (easier) download them from websites. Here's one site you can download them from, [http://nzbmatrix.com/]("http://nzbmatrix.com/"), but there are plenty of others.

Hellanzb automatically monitors a folder (you specify which folder it monitors in /etc/hellanzb.conf) so you just download or place the nzb file in that folder and nzb automatically reads it and starts downloading. Hellanzb is a great tool for usenet downloading, but it does take a bit of effort to configure the /etc/hellanzb.conf file.

---

### Post by richieboy on 2007-08-18
felicity. thanks.  on pan some binaries have yEnc at the end and some have par2.  are these nzb files?  and do you know how to stop pan from caching articles?  i can't find that option anywhere and i'm afraid of that stuff piling up.

---

### Post by felicity on 2007-08-18
No, nzb files are files that have the extension nzb. :) 

My pan has an option on the Behavior tab in the Preferences dialog to clear the article cache on shutdown. I'm using pan 0.132. If you're using the pan from the repositories  it may not have this option. You can get a .deb for the newest pan at [http://darrenalbers.com/Pan/]("http://darrenalbers.com/Pan/")

You can also always manually delete them from your hidden .pan2 folder in your home folder.

---

### Post by kellemes on 2007-08-19
> **richieboy said:**
> felicity. thanks.  on pan some binaries have yEnc at the end and some have par2.  are these nzb files?  and do you know how to stop pan from caching articles?  i can't find that option anywhere and i'm afraid of that stuff piling up.

You need the par2-files to be able to restore large binaries that aren't complete.. It's absolute magic, you download a 4 Gg movie but a portion is missing, the par2-files will fix the movie.

---

### Post by richieboy on 2007-08-19
thanks.  that was just what i needed.  thanks for the help.

---

