---
title: "How are Fixes Released in Ubuntu?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by flowingfire on 2007-05-17
I'm curious how fixes are released in Ubuntu.  Every OS has bugs to work out...

So does Ubuntu release them in the Adept Manager like Windows releases fixes in Windows Update?  Does Ubuntu release special service packs?  

Do I have to do anything special in order to make sure bugs are fixed and all security considerations (if such a thing exists in Linux) are fixed?

All curiosities to me. :)

Thank you.

---

### Post by esoterica on 2007-05-17
Just watch your user bar, you'll get a little round sun looking icon thing that will pop in there and often fire off a balloon window telling you updates are available.

You click on it, it gives you a report of whats available and why, then the option to install it or not, very easy and a no brainer to use and figure out.

---

### Post by flowingfire on 2007-05-17
alright.  Thank you.. There's nothing else to it then?  Just click on the user bar flagrantly yelling at me to update and the bugs in the operating system will be fixed? 

Cool.

 Peace.

---

### Post by hyper_ch on 2007-05-17
If you are running Ubuntu (with Gnome) you should have the update notification automatically activated... on the top bar you should get some sort of a reddish/orange square that highlights "Updates available"....

It is all done through adept I think

However you can also use the command line. Open a terminal and enter the following code

```

sudo aptitude update && sudo aptitude upgrade

```
or
```

sudo apt-get update && sudo apt-get upgrade

```

The difference between apt-get and aptitude is basically, that aptitude install more software (also the recommended packages and not only the necessary ones - since I have enough diskspace, I use aptitude)

Basically the above code means the following:

sudo --> do as super user
apt-get/aptitude --> the command line package manager
update --> update the software repositiories and versions of available packages
&& --> after the first set of commands have been exectued, execute also the second one....
upgrade --> update the installed packages to the newest version available in the repositories

---

### Post by flowingfire on 2007-05-17
Hmm.. I'm running Kubuntu, *currently without Gnome too.  What does that mean as far as updates go?

---

### Post by esoterica on 2007-05-17
Security fixes definitely happen in Linux, you don't have to try and imply that lightly. Someone is feeding you a line of crap if they try telling you that Linux is more secure than this OS or that OS. (BSD is accepted and considered more secure by most people, but it's a headache to get working right and doesn't always play well unless your a hardcore devoted BSD geek)

People use to try and use that as a selling feature for Linux, complaining about how Microsoft always requires you to download updates and patches. Ha! Bastardo's, I run a CentOS Linux web server, keeping on top of all the patches, updates and security fixes on that thing seems like a never ending and never winning battle!

Don't get me wrong, I absolutely love my Linux web server and you couldn't force me to use anything else for it even by gun point, but for anyone to even remotely attempt to imply Linux doesn't have security problems, they are 100% FOS.

I've had Ubuntu installed a few days now and I've seen that little icon pop up several times already telling me updates were available. It's fine with me, I like getting updates, I look at them like mini christmas presents and feel a lot more comfortable knowing updates and patches are coming in regularly than the concern I'd have if I wasn't seeing updates coming in.

I didn't have to do anything to turn this feature on that I can remember, but you should have already gotten your first notice immediately after installing Ubuntu.

---

### Post by flowingfire on 2007-05-17
It's good to know that whole "Linux doesn't have as many security problems" line is bunk.  hehe.

I actually thought it might have less security problems because people say it's built differently and isn't as vulnerable as other OSes like Windows due to those architectural differences. :)

---

### Post by hyper_ch on 2007-05-17
flowingfire

well, the command line is the same for Kubuntu or Ubuntu or Xubuntu... I just don't know how "available updates" are being displayed in KDE... I'm almost sure there's a notifier... if in doubt, just open the command line terminal and enter those commands :)

I also like updates.. that makes me feel good :) you know I've been using Feisty since Herd 3 and there were daily updates... first thing in the morning I did was get up, turn on the computer, hit the update/upgrade command into the terminal and check what the devs have done during the last 24h :)

---

### Post by flowingfire on 2007-05-17
Kewl.  I ran the terminal commands and it feels gratifying. :) -- even if it didn't actually upgrade anything.  
Thx!
It must be a daily joy to be an Ubuntu alpha/beta guinea-pig. :)

---

### Post by hyper_ch on 2007-05-17
> **flowingfire said:**
> It's good to know that whole "Linux doesn't have as many security problems" line is bunk.  hehe.

I actually thought it might have less security problems because people say it's built differently and isn't as vulnerable as other OSes like Windows due to those architectural differences. :)

It is more secure by design because it was developped as a true multi-user system while windows is not... I think Vista is now the first attempt to actually correct that stupid thing that you need admin privileges for daily operations...
On WinXP, Win2000, ... you couldn't do anything without having admin accesss... and the switching was always tiring... you ahve to log out as this user... login as admin... do your changes... log out as admin... log back in as user... oh, you have forgotten to do something... log out as user... log in as admin ......

Linux has security issues but I tend to think most of those aren't as bad as on windows.... as said, normally you run windows as admin... otherwise the computer is just unusable... this means if any application in windows has a security issue it can affect the whole computer....

---

### Post by esoterica on 2007-05-17
I like the way you broke out what each aspect of the actual command does, that would be good if everyone did that in helping people learn and understand the commands.

Not to sound like I'm defending Windows, but I ran Windows for years at least since the days of Windows 3.11  and in my entire life I've never had it hacked or a virus, or at least a virus that was written well enough that it actually worked.

I did always run as Administrator myself in Windows like you said and for the reasons you said, however, for those that were doing it the recommended way you didn't have to ever actually log out then log back in as a different user, you could have instead used the run as command in windows (NT).

I like all operating systems myself, so I guess I'm not just one of those haters who will try to point out any flaw with any of them they can try and find and instead I tend to look at the reasons I like an OS instead of what I may not like about it.

With Ubuntu I'm having a heck of a time getting use to this sudo thing instead of root, su or Administrator, but I'm catching onto it. I do prefer to have the option to decide for myself what level I want to run my own computer at though rather than being forced to run at the suggested user level.

In fairness, Vista is pretty much the same way as Ubuntu is with sudo, but at times an even bigger hassle. I needed to run IPCONFIG /RELEASE then IPCONFIG /RENEW on my Vista system a while back and it was a nightmare. I had Admin rights already, yet it wouldn't let me do it. I did a runas Administrator command and tried and it asked me for the Administrator password. I only have a single password on that system and it was telling me the password wasn't correct. Finbaly I figured out through trial and error you have to actually start the command line itself in the GUI with runas administrator in order to be able to do any solid commands from the command line. That was a not very well documented pain in the butt that wasted a good half of my day just trying to do a simple command.

---

### Post by hyper_ch on 2007-05-17
well, normally if you don't know what a command means you can just type:

```

man program

```

That will give you the manual pages for that program explaning everything.....

---

### Post by flowingfire on 2007-05-17
:)
Esoterica: I solved that whole dilemma in Windows Vista by going to msconfig and disabling "user account control." 

Yeah, it was probably a bad move but I was so annoyed by the sheer intrusiveness of the OS it may have helped drive me here. lol

---

### Post by bikeboy on 2007-05-17
Don't think it's been mentioned yet, so I will do it. One great thing about updates in K/Ubuntu (and most Linux distros) is that not just the core OS and maybe office software gets updated automatically, every piece of software on the system does.

The only exception being things you've installed manually from source or other non-repository software. By the time you get to that stage I would guess you're pretty comfortable with what's going on and will know how to install the updated version of that software anyway.

---

### Post by 23meg on 2007-05-17
> **flowingfire said:**
> There's nothing else to it then?  Just click on the user bar flagrantly yelling at me to update and the bugs in the operating system will be fixed? 


Not all bugs; high-impact ones only, which rougly means including security vulnerabilities and showstoppers. Here's the stable release update policy:

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by esoterica on 2007-05-17
bikeboy, that is a very good point! I think someone has attempted to do this with Windows apps before, but it's never really caught on. I guess too many of them want you to pay for the software, then suck more money out of you by also then making you pay for update subscriptions. I absolutely refuse to use any software where they make you pay an additional fee for updates to fix their bugs, doesn't matter how bad I want the software. If software is reasonably priced and good I don't mind paying for it once, but to expect people to pay then on top of that for an upgrade subscription is just a bit too much.

I can't even remember now what that stupid Windows installer program was that attempts to find updates for all your software, but all it ever actually seemed to find updates for was itself.

Didn't an old selling feature of Linux also once use to be if you did get a bad program and it hosed up it would only affect it self and not crash your entire computer. I'd say that was a bit of a myth as well, I've experienced plenty of garbage open source apps on linux in the past that have caused the entire system to be hard booted to get running again.

I've even had older versions of RedHat before that after being hard booted you could never get it to run again at all, it would lock up at the lilo boot loader screen and just hang there. Hopefully that kind of stuff in Linux has since been fixed. I've had some really bad experiences over the years trying to get the desktop version of Linux to be stable and useable for me, so far Ubuntu has really been promising, though past horror experiences with other Linux distro's also has me treading very lightly in it right now.

---

