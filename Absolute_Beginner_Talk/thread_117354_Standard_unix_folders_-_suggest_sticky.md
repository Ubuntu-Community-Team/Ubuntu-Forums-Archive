---
title: "Standard unix folders - suggest sticky?"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Garyu on 2006-01-14
Hey, maybe some moderator could make a sticky topic about this...

In windows there are some standard folders that most people are familiar with. When you install something it ends up in "c:\program" or "c:\program files" as default unless you specify it yourself. There is the "My documents" folder, and the "c:\windows" for OS-specific files... But in Linux things seem to end up all over the place, and I don't know where to look for what...

So, could someone PLEASE make a list of standard linux folders and what ends up where and maybe even why or how to tweak it so that I can get a better chance at understanding the basics of the file system organization?

I know for instance some binaries are in /bin, but then there is also /usr/bin and and /local/bin and /home/bin (or something like that) and all kinds of different bin-folders... what goes where and why can't I have just one /bin for everything like in windoze? Maybe this doesn't matter to a lot of people but to me it just seems like a big mess and I want to keep my hard drive organized...

In a recent topic someone said to go to [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) but the info there takes a lot of effort to digest... I'm looking for the easy path to convert from windows to linux... so something that is easier to understand from a windows-user point of view and not so technical.

oh, and also... where are the files equivalent to the windows registry?

---

### Post by matthew on 2006-01-14
Start here: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by savio_mit_glug on 2006-01-14
Hi !
           I'm new to GNU/Linux myself. I too was confused about the filesystem. Then I came across this pdf e-book:
         [www.tldp.org/LDP/intro-linux/intro-linux.pdf](www.tldp.org/LDP/intro-linux/intro-linux.pdf)
          It helped me understand linux a little  better. Hope it helps you too.

EDIT:  Well, If you are a complete newbie, (who isn't, at some point in their lives?) maybe you could consider the book "Linux for Dummies". I started with that one. Though it was good for a newbie, I still feel it has more humour than information !
Regards,
Savio.

---

### Post by Garyu on 2006-01-14
*sigh* still not what I wanted...

As I understand /bin is about the same thing as the commands in command.com? And if I install new software it ends up in /usr/bin? If that is the case I would like a short introduction like so:

/bin        - Common commands like those in command.com (dir, cd, etc.)
/usr/bin  - Installed software like C:\Program files\
...

and in such a list I would not want such as /tmp which I am (probably?) very unlikely to use, at least not until I am a bit more proficient at dealing with this OS.

The purpose is for instance to know where to look if I install something using Synaptic and it does not show in the menu automatically (like most games I have tried to install, they just disappear somewhere). Also, when I started using MS DOS and DR DOS I learned a lot from just looking at the basic commands and trying them out. In Linux I don't even know where to start looking for many basic commands. Now thanks to the above comments I know I should start looking in /bin, but this is not very obvious to a newbie like me. Also, the man and --help things are useful - if you know about them, but all of this stuff is something I have stumbled upon when reading forum threads... There should be an easy accessible guide to things like this...

---

### Post by matthew on 2006-01-14
<I'm saying this with a friendly tone, not demeaning nor belittling in any way, with my only goal trying to help you become adept and proficient as quickly and easily as possible.>

The problem is that unix/linux is nothing like windows and so any comparison is shaky at best (it's also older by more than 10 years...unix first appeared around 1970). There is no exact analog for many things so it just isn't possible to say X in Windows = Y in unix/linux. Seriously, you are better off starting from scratch than trying to learn based on comparisons--the comparison method will only serve to confuse and frustrate you.

You might find this to be interesting reading: [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")

EDIT: I just noticed you added to your most recent post so in a moment I will respond to the final paragraph above...hang on
.
.
.
Here you go...some more links to help you out
[The Linux Guide for Windows Users]("http://www.psychocats.net/essays/linuxguide.php")
[Linux Newbie Guide: Shortcuts and Commands]("http://www.unixguide.net/linux/linuxshortcuts.shtml")
[Filesystem Hierarchy Standard]("http://www.debian.org/doc/packaging-manuals/fhs/")
[LinuxCommand.org]("http://www.linuxcommand.org/")
[Linux commands]("http://www.ss64.com/bash/")

---

### Post by savio_mit_glug on 2006-01-14
Great article, Matthew!
Savio

---

### Post by Garyu on 2006-01-14
Matthew - you are an angel. :)

Yes - I understand that Linux is not Windows. I am not trying to get a guide to turn Linux into Windows. What I want is an easy way to understand the basics before I start to dig deeper. Even though these OSs are very different to the core, which I already knew, there are always some similarities and what I want is an easy way to start where I can implement the knowledge I already posess (you don't read the manual every single time you buy a refridgerator, do you? you just want to know how to open the door and put things in it, until it isn't working like it should and you want to fix it - then you read the manual).

Anyhow, in the links you provided in your last post I got many things that I was asking for. GREAT! But I still think that this is something that should be more readily available. :P

---

### Post by matthew on 2006-01-14
Garyu: :)

---

### Post by Sgood1971 on 2006-01-14
[QUOTE=Garyu]The purpose is for instance to know where to look if I install something using Synaptic and it does not show in the menu automatically (like most games I have tried to install, they just disappear somewhere).[/QUOTE]

I know this wont solve your original question, but for finding apps that dont show up in the menu, here are a few tips that help me.

1. In synaptics, right click the package, choose 'properties' and look at the 'installed files' tab, it will show you where everything was installed to. (This only works after the package is installed.)

2. In terminal, type 'whereis <packagename>' without the quotes, it will also tell you where the package was installed to.

3. Install the Debian Menu, a lot of apps appear here when they don't appear anywhere else.

Hope this helps in some small way.

---

### Post by hen3rz on 2006-01-15
> Start here: [http://en.wikipedia.org/wiki/Filesys...archy_Standard](http://en.wikipedia.org/wiki/Filesys...archy_Standard)
That wiki page was extremelly helpful. I was getting annoyed going through folders looking for apache2.conf then trying to find my way back to the www folder thanks heaps.

Also is there a search feature in nautilus that im missing. Im looking for something that will let me search all my files and folders for the times when i forget were that .conf file was..

---

### Post by matthew on 2006-01-15
[quote=hen3rz]Also is there a search feature in nautilus that im missing. Im looking for something that will let me search all my files and folders for the times when i forget were that .conf file was..[/quote]It should be in your menus. Places->Search for Files...

---

### Post by hen3rz on 2006-01-15
Uhhh thank you.

Im so blind :???:

---

### Post by matthew on 2006-01-15
[quote=hen3rz]Uhhh thank you.

Im so blind :???:[/quote]No problem. We all have those moments.

---

