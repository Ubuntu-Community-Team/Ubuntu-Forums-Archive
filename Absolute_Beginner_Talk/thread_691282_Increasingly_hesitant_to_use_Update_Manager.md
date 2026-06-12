---
title: "Increasingly hesitant to use Update Manager"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by sjd on 2008-02-08
When I ran update mgr today, it returned a long list of updates.  As I usually do, I searched the forums/launchpad/etc to see if there were issues with the updates - it appears there may be at least a few.  The last time I was preparing to do an update, there was an issue with x-server that caused several people problems.  Fortunately, I waited.

Don't get me wrong, I truly appreciate the time and work everyone does to provide this wonderful alternative to Windoesnt and the apps for it.  And, I do not want to abandon Ubuntu/Open Source.  But, I am using it to support Windows clients (as well as Linux) and already have to boot into Windows for things I can't do (like MS Publisher files) which really slows me down.  Breaking Ubuntu entirely, by installing a bad update, would be my worse nightmare.  As a new user, it takes me longer to resolve even simple issues.

What I would like to know is if others have developed a way to reliably determine whether or not to install an update and/or if there is an 'update blog' somewhere that posts notices related solely to update manager related issues.

At this point, for me, it's a hit and miss proposition - hoping to notice a bug or issue before installing the update and continually monitoring to find out when it's safe to install the update.  It's not too bad when there are only a few pkgs in the update, but today's list is 15 items long.

Thanks for any suggestions/ideas.

---

### Post by HappyFeet on 2008-02-08
i usually do the security updates right after install, then take my time installing the "recommended" updates. my theory is, if it aint broke, dont fix it. then, once i install a few of the recommended updates, i shut off all updates. 

but everyone has their own way of doing things and different opinions about what is good and what works. trial and error seem to be the best teacher.

---

### Post by emarkd on 2008-02-08
Maybe I'm just lucky, but the only problems I've ever had after an update was getting VMWare kernel modules reinstalled after a kernel update.  And that's with three Ubuntu boxes in the house.  Are these problems you're having related to some propietary binary bit, maybe?

Also, if your Linux box is critical, consider the LTS release.  It's going to be more stable because it uses more established software.

Reading back over this, I don't think I came close to answering your question, but I guess I'll post it anyway :)

---

### Post by sirzepp on 2008-02-08
So far, updates have only caused problems with my NVIDIA drivers.  Since I don't use the restricted drivers, every time I install a kernel update, I have to re-install the NVIDIA drivers.  It takes about 15 minutes...

Other than that...I've not had any difficulties.

---

### Post by Sidewinder1 on 2008-02-08
I know exactly how you feel. I'm terrible with syntax and the terminal. I do the same as you, when I'm notified of an update, depending on it's description (kernel upgrade,etc.), I'll wait a day or two; search the forums for 'upgrade' and read.copy/write down the solutions. I also love linux and am very appreciative of all of the work the developers put into it. I think the plethora of hardware configurations in conjunction with the hand complied drivers and such makes it darn near impossible to have a major update with absolutely no problems. I am also learning alot. Now, if I can just figure out how to get back into update manager and reconfigure it to check for updates; I had it turned off for this last one; which went flawlessly, by the way...

---

### Post by timzak on 2008-02-08
There was just an update to Adobe Flash, that on 64 bit machines, broke flash.  See in the 64 bit forum for details.

---

### Post by eggdeng on 2008-02-08
I follow a rule of thumb which basically consists in not installing any package with the word linux or anything with xorg in the name, *unless I have a good reason to do so*. Bit rough and ready but it works for me.

---

### Post by mikewhatever on 2008-02-08
Hi there, just as others, I do not know of a place to check the reliability of Ubuntu updates. Not being a developer, I humbly assume that each and every update is tested to the point when it's considered safe to release to general public. Is there an analogy to what you expect for Windows or Mac? ["Dear XP users, we are glad to report that our latest security updates will break your system with the probability of 1 to 5."] I've never seen something like this.

Other then reading reports, there are two ways I can think of, to make updating relatively painless. One, install Ubuntu in Virtual Box and test every update that comes out. Two, back up your root and home.

I've been very lucky to update with no problems, don't know why. The only time there was an issue, was after a kernel update in 2007, but reinstalling nvidia with envy fixed it in 10 minutes.

---

### Post by r4ik on 2008-02-08
i just update and most of the times all go's well.
The flash update is always a bit of a surprise but since i am om 32 bit it went okekidoki.

---

### Post by nodegamra on 2008-02-08
I felt the same way when I made the switch.
I never had any problems with any updates!:)

---

### Post by TheDilettante on 2008-02-08
Sidewinder: go to System -> Administration -> Software Sources and then the Update tab.  One of its settings is the frequency of updates.

---

### Post by LowSky on 2008-02-08
here is my theory about operating systems

Windows is like American Cars, Big, cheap, breaks easily, but easily repaired, doesnt last longer than 5 years ...ex. chevys

OS/X is like Japanese cars, Light, tested and always inproved, barely lets you down, harder to fix but not a catastrophy, should last a good long time.. ex. .toyota

Linux is like European cars, built for the speed, but can be used anywhere, newest of the new in technology, but not as stable and requires you to be your own repair man or know a good one, but will last forever if properly maintained.. love seeing those old VW and Vovlos...lol

as for your question, if it work dont update it unless you really think it willl improve something, or switch to a more stable linux, like debian.

---

### Post by Whiffle on 2008-02-08
> **LowSky said:**
> here is my theory about operating systems

Windows is like American Cars, Big, cheap, breaks easily, but easily repaired, doesnt last longer than 5 years ...ex. chevys


My 14 year old, 205,000 mile chevy takes offence to being compared with windows...


As far as update manager goes, I only use it if something isn't working.  I'll check every once in a while for updates that might improve things and install those, otherwise I leave it alone.  I did update before going on a trip once, and it did its thing, I shut it down, all was dandy.  I boot it up the next day...Grub error 22.  I was not happy about that at all.  They really really need to do more testing on critical updates, and make sure they install right.  If you watch the questions on the forums, you can kind of tell when a new update came out and went wrong.  This weeks winner is a kernel update that went wrong for some people by putting the the wrong thing in for their root partition.

---

### Post by darco on 2008-02-08
I dont mean to hijack this thread but my only question in regards to the update manager is, do I have to download everything thats posted? Sometimes I see things related to KDE when I use Gnome, so I dont know what to do because other times you get error messages that certain dependencies are missing blah blah when trying to install a program. So I basically d/l everything. Also I cant seem to hide certain downloads  anyways like I can do in Windoze so by leaving behind those packages , they just build up and you have to deal with them everytime you check for newer updates.... :confused:
dr

---

### Post by emarkd on 2008-02-08
Those KDE packages you're seeing are probably libraries for some apps you have installed.  With the proper libraries, KDE apps run fine on Gnome.  Whereas Windows apps are usually completely contained except for the core win32 dll's, Linux uses lots of shared libraries.  It's more efficient to code, more efficient to store on your hard disk, and more efficient upgrade.  Patching one library fixes a bug in every app that uses that library.

If you want to prevent a certain package from getting updated, you can select it in Synaptic, the click on Package > Lock Version

---

### Post by jrusso2 on 2008-02-08
> **LowSky said:**
> here is my theory about operating systems

Windows is like American Cars, Big, cheap, breaks easily, but easily repaired, doesnt last longer than 5 years ...ex. chevys

OS/X is like Japanese cars, Light, tested and always inproved, barely lets you down, harder to fix but not a catastrophy, should last a good long time.. ex. .toyota

Linux is like European cars, built for the speed, but can be used anywhere, newest of the new in technology, but not as stable and requires you to be your own repair man or know a good one, but will last forever if properly maintained.. love seeing those old VW and Vovlos...lol

as for your question, if it work dont update it unless you really think it willl improve something, or switch to a more stable linux, like debian.

My 89 Camaro still runs great after 19 years.  It doesn't like being compared to Windows either.

---

### Post by TheDilettante on 2008-02-13
Nor does my '94 Cherokee with 140,000mi...

---

