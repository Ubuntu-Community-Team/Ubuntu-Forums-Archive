---
title: "Where is Picasa installed?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by staib on 2006-10-15
Hi all,

I've only got 24 hours into the Ubuntu adventure and everything is up and running nicely (on a dual boot machine) - I have explored the Synaptic Package Manager (and opened it up to the universe and multiverse repositories) as well as Automatix, and have been impressed with the way they normally assign what I think of as shortcuts to the appropriate section of the Applications section.

But I have a simple newbie question - sometimes (an example is Google's Picasa graphics program) a program seems to download OK but I'm not sure where it ends up, or how to get a short cut onto the Applications launcher. Is there an equivalent folder to Windows' "Program Files" - where should I start looking (searching for "picasa" didn't help either)?!

Cheers,

Nick

---

### Post by bodhi.zazen on 2006-10-15
Open a termainal and type```
which <program name>
```

for example:```
which picasa
```

Programs are located in various locations:

[Linux Directory Tree](http://oreilly.com/catalog/debian/chapter/book/appa_01.html)

---

### Post by Perfect Storm on 2006-10-15
If I recall it correctly Picasa is installed under /opt

---

### Post by bulldog on 2006-10-15
In /usr/bin/ on my box:D

---

### Post by Perfect Storm on 2006-10-15
/usr/bin is where the launcher of the application is.

---

### Post by staib on 2006-10-15
Cheers all! :) 

Mucho appreciated!

Nick

---

### Post by catlett on 2006-10-15
Most applications will have there binaries stored in /usr/bin. Even if there folders are in /usr/lib or opt, there is usually a link to them in /usr/bin.
When you make a launcher (shortcut) browse to the filesystem and then to usr and finally bin. Select the binary that has the applications name (i.e. browse there abd look for picasa)
/usr/bin has most of the binbaries or at least links to them. /usr/sbin has the binaries for system applications like mount, useradd etc /opt holds third party applications that are added after installation but I only have a couple of apps there and they have links to /usr/bin
If you ever want to know where an application is stored, use the whereis commnad in the terminal
```
whereis picasa
```

---

### Post by staib on 2006-10-15
Thanks for the extra information... 

Even I will remember the "whereis" command!  Tried it with "Skype" and it worked a treat.

I think I installed Picasa via Automatix - but there may have been a problem. Automatix had been showing it as installed (even though I couldn't find it anywhere...).

I thought I would uninstall and then re-install (from Automatix again) but uninstalling generated an error message - and now Picasa seems to have disappeared from Automatix entirely - odder and odder!  Maybe it will come back soon!

Nick

---

### Post by Perfect Storm on 2006-10-15
Can you start it through the terminal (picasa that is)?

---

### Post by staib on 2006-10-15
No - I can't see it anywhere - even with the whereis command...

Automatix must have thrown a wobbly when I "installed" it yesterday - it showed up as installed but clearly didn't - as suggested by the error on trying to uninstall - what's odd is that it has (at least for me) now gone as a multimedia download option). Seems weird...

---

### Post by Perfect Storm on 2006-10-15
You can download and install Picasa manually here: [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

---

### Post by taurus on 2006-10-15
See if it's somewhere else...

```
sudo find / -name picasa -print
```

---

### Post by staib on 2006-10-15
Not there...

dad@dad-desktop:~$ sudo find / -name picasa -print
Password:
find: /proc/6936/task: No such file or directory
find: /proc/6936/fd: No such file or directory
dad@dad-desktop:~$

But as Automatix believes its installed, (and throws a fatal error trying to uninstall) I can't try to re-install...

Thanks for that other link AI - I'm up for the challenge :) 

Nick

---

### Post by staib on 2006-10-15
Hehe - worked a treat!  Thanks guys, this is such a cool OS - but it really helps having a forum like this 8) 

Cheers,

Nick

---

### Post by Bartender on 2006-10-19
Copied this from the Google Linux Picasa website...
"Starting Picasa
Start Picasa by looking in your Linux distribution's Graphics menu. If you can't find it there, give the command /usr/bin/picasa in a terminal window."

---

### Post by bocadoblues on 2006-10-24
Hello!
I'm new to the OS too. I have downloaded Picasa manually but I'm having some issues with it. I have xgl running and I guess it's kind of messing up Picasa... Well, I was not 100% happy with it anyway, since the Slideshow feature doesn't wor properly and I'd like to uninstall it. Here's the noob question:

- How do you uninstall Picasa?
Thanx for the time,


> **Artificial Intelligence said:**
> You can download and install Picasa manually here: [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

---

### Post by Perfect Storm on 2006-10-24
Well then you can looking forward for edgy + beryl, much better and it won't mess things up. :)

The gui way:
Go to System tab ---> Adminstration ---> Open synaptic package manager, push the search button and search picasa. When found right click it and pick completly uninstall. Then approve it.

command way:
```
sudo aptitude remove picasa
```

---

### Post by bulldog on 2006-10-24
You can try ```
sudo aptitude remove picasa
```

---

### Post by TiredBird on 2006-10-24
TRY is the operative word. I used Picasa for a while, then tried to remove it but it was everywhere. Several months later I'm still not sure I got it all.

For those who use Synaptic...

You can look at 'properties' on the right click menu for an installed app, or you can have the preference set that puts the 'properties' in tabs in the lower part of the screen. Using either method, there is a tab that lists installed files and shows where it installed them. Usually there is /usr/bin or /usr/lib/bin or something like that that is the binary but it also shows all of the other files, configuration, documentation, man pages, etc. 

In Synaptic at least, (I understand aptitude may be different), removing a package does not remove all the dependancies that were installed at the time of installation. It may have taken 80 MB with the dependancies to install a program but removing it only takes out 20 MB, leaving 60 MB of unused stuff still floating around in your system. 

Yes, Martha, there is a solution. Look at the history file and look at the list of programs that got installed when you installed application x. Remove those other programs too. If there's a simple way to get all of this at once I don't know it but I'm listening if anyone has any suggestions.

But Picasa??? Everytime it runs it creates more files. It seems to think it owns your system. That's an attitude I expect on Windoze but not on Ubuntu. Unfortunately, Google and some others that write for both platforms haven't learned that Linux users are Linux users, at least partly, because they want to control their own system, not have someone spoonfeed it to them.

---

### Post by bodhi.zazen on 2006-10-24
Yes aptitude is better then apt-get on the removal end. You would think synaptic would be better, but synaptic uses apt-get as a backend.

The problem is you need to have installed with aptitude to reap the benefits at removal.

I search for packages with synaptic, but install/remove with aptitude.

If you are in the need of some [url=http://ubuntuforums.org/showthread.php?t=140920
]CLEANING[/url].....

8-)

---

### Post by TiredBird on 2006-10-24
I followed the [CLEANING]("http://ubuntuforums.org/showpost.php?p=800462&postcount=1") link in bodhi.zazen's post and then followed the directions in the referenced howto. Fantastic. localepurge or whatever it was caused my Xubuntu system to hang a couple of times and I never did get it installed but the rest of the stuff worked like a charm. I particularly liked the orphan finder. I followed the directions for adding that to my Synaptic filters. Terrific. Thanks for the link!

---

