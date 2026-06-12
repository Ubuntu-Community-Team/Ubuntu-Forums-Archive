---
title: "where do I find an error log?  need to start detective work ..."
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by beauty on 2006-10-12
When I need to start debugging applications, where is the error log?  I mean, if I don't know where to start, there must be a generic error logger for stuff that goes wrong.

Specifically:  I can't burn an image to a CD.  I *have* burned data with the same CD writer.  Now, when I right-click the *.iso file and select "Write to Disc ..." I get the error, "Error writing to disc / There was an error writing to the disc"

I would run it in bash to see the errors, but since I'm right-clicking, I don't know what the bash command is.  I'll solve this in due time, but for starters -- where to look for error logs?

---

### Post by FizDev on 2006-10-12
Hmm.. don't know about a general log but, the log you're searching for is probably in /etc/var/log

Oh and for the parameters (for the right-click in console) execute your application in console with --help after. This should give you the basic parameters you need

---

### Post by beauty on 2006-10-13
Roger that FizDev!  Well I learned something already:  'console' means 'bash' to me.

I don't have the path you quoted, but I *do* have /var/log and /dev/log.  And I found a whole lot more, thanks!

```
root@ubuntuBreezyBadger:/# find -name log
./var/log
./usr/share/irssi/help/log
./dev/log
./dev/.static/dev/log
./home/...    (user files here)
./root/.synaptic/log
./root/share/apps/kconf_update/log
root@ubuntuBreezyBadger:/# pwd
/
```

I checked out /var/log/ and found all kinds of goodies (tried to attach).

So onwards and forwards:  
About the --help option in console,  I can't run in consule because I can't figure out what the durned command is.  I'm trying to burn files in Nautilus.  Instructions say to right-click and it burns the *.iso image.  I know this works because other users can perform the burn on this same machine.  I'm on the root list, but still can't burn the image.

Anyways, question being:  I'm right-clicking on this file, but don't know what command the right-click tries to execute ... so if I click around for 'help' it's all Nautilus stuff (naturally).  Oh, and I tried 

```
$ nautilus --help

```

just to make sure, but nothing relevant ... um, and the question:  how do I figure out the command, so I can run it in bash?

---

### Post by po0f on 2006-10-14
If you want to know how to burn an ISO image from the command line, read [this](http://www.sun.com/bigadmin/features/articles/burn_iso_images.html). 

Alternatively, if you don't mind having some Qt/KDE libs installed on your box, [K3b](http://www.k3b.org/) is IMO the best CD/DVD burning software for Linux.  When a recording session is completed, success or failure, it gives you the option to review the process.  It will be called "Show Debugging Output", which will show you the command line command used as well as the output of the command.  [Picture](http://websvn.kde.org/trunk/extragear/multimedia/doc/k3b/cdcopy_done.png?rev=511110&view=auto).

---

### Post by beauty on 2006-10-14
Nice info in the link ([http://www.sun.com/bigadmin/features/articles/burn_iso_images.html)](http://www.sun.com/bigadmin/features/articles/burn_iso_images.html))!

I got the CD burned - and I got some interestinger problems - but for now I want to get my baby steps figured out.  It still troubles me that I right-clicked in Nautilus and can't figure out what durned command is being executed.  Any ideas?

---

### Post by ReaderRat on 2006-10-14
> **beauty said:**
> Nice info in the link ([http://www.sun.com/bigadmin/features/articles/burn_iso_images.html)](http://www.sun.com/bigadmin/features/articles/burn_iso_images.html))!

I got the CD burned - and I got some interestinger problems - but for now I want to get my baby steps figured out.  It still troubles me that I right-clicked in Nautilus and can't figure out what durned command is being executed.  Any ideas?
I used the right-click trick and it worked first time - but I was not in Nautilus - the file was on my desktop.
Don't know if this makes a difference....:-k

---

### Post by Delkster on 2006-10-14
> **ReaderRat said:**
> I used the right-click trick and it worked first time - but I was not in Nautilus - the file was on my desktop.
Don't know if this makes a difference....:-k

It shouldn't matter, as the desktop is handled by Nautilus, and for files and folders it's technically just another folder in Nautilus.

Burning an ISO file in Nautilus has always worked for me (as long as the feature has been available). I'd guess that there may be a strange issue with the specific drive or something here.

The command run by Nautilus for CD burning is probably nautilus-cd-burner, although I don't know with what parameters.

---

