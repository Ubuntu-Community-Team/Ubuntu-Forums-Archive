---
title: "AV and other protection"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by supertails on 2008-02-03
Does anyone have any sudo commands or links to free protection software. I would prefer sudo commands though.

---

### Post by dcstar on 2008-02-03
> **supertails said:**
> Does anyone have any sudo commands or links to free protection software. I would prefer sudo commands though.

This makes no sense at all, "sudo commands" protect nothing.

What are you actually trying to achieve?

---

### Post by Luigi239 on 2008-02-03
There is no need for any protection software in Ubuntu and Linux in general. 99% of users never run and worry about such a thing, as there are not any mainstream viruses written for it.

(also, by sudo commands, I think you are referencing to using apt-get, the package manager (which installs and maintains software.) Sudo is simply added before the command to have you run the command as the root, or super user who has full controll over the machine.)

---

### Post by supertails on 2008-02-05
I've read in a book for ubuntu that windows emulators can install window virus on them. The book was talking about Wine, VMware, Xen and other emulators. Can they really install window virus?

---

### Post by kryth on 2008-02-05
On to the windows virtual machine I guess, but that wouldn't effect ubuntu at all. You can't get a windows virus on linux.  I'm guessing you could install windows anti-virus on the windows virtual machine.  As far as, wine goes I don't think you have any worries.

---

### Post by kryth on 2008-02-05
AVG does have a linux version.

---

### Post by supertails on 2008-02-05
Where can I get a Linux version of AVG? Do they have it on CD with every protection you can think of.

---

### Post by stchman on 2008-02-05
Generally viruses and spyware don't have any affect on Linux as nearly every virus is written for a Windows OS.  Even if someone writes some malicious code for a Linux box the code would have to somehow get executable permissions and then be executed.

Since Linux is locked down pretty tight the only thing that could be affected is the ~/ folder unless the person does sudo on the malicious code.

Too many things have to take place in order for viruses to do their work in a Linux box.  There are far too many unprotected Windows boxes out there to play with.

---

### Post by gn2 on 2008-02-05
Even when you deliberately try to run viruses, they don't always work.

Lots of info here: [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

You just don't need A-V software, Linux is not Windows.

Computer viruses should really be called Windows viruses.
They are species specific. 
Linux is immune because of it's biology.

---

### Post by supertails on 2008-02-05
People on Linux actually try to run viruses on their computer and the viruses can't do a thing. lol Linux is one bad dicator. Keeping all those virus as powerful as slop. :popcorn: Viruses are delicous. :KS I am a superstar and I don't care who you are. lol

---

### Post by stchman on 2008-02-05
A virus capable of doing harm on Linux would have to specifically written for Linux.  Windows viruses are targeted for Windows.  Also Linux has obscurity in it's favor.  A virus written for Ubuntu probably would not work on Fedora or Suse.  Each distro does things a little differently.

As I said before why would a virus writer target a Linux user (the average Linux user is pretty computer knowledgeable) when they can target the average PC challenged Windows user?  People who know nothing about PCs tend to do dumb things.  The average Linux user is usually convert that is sick of how M$ does things.

---

### Post by supertails on 2008-02-05
I agree with you on that. Have you ever used Solaris? I'm thinking of switching.

---

### Post by upthelum on 2008-02-05
Note: MOST viruses are for Winblows but why do MOST people seem to think Linux is immune? Any machine with an ip/mac address and web connection is a potential target. 

Is it not a myth now that no-one writes nasty code to attack Linux machines?

---

### Post by supertails on 2008-02-05
You are right that their is no purely safe computer but if 99% of all virus are for window that the other part of the 1% goes to Linux and after Mac it won't be that much left for Linux but I agree that Linux is not immune.

---

### Post by emarkd on 2008-02-05
Your ratio is off.  It's estimated that there have been 200,000 Windows viruses and lots of those are still out there.  There have been about 40 for Linux and NONE of them are still effective.  That makes the ratio 5000:1, not 99:1.

You should also know that the Linux A/V products scan for Windows viruses and only prevent you from passing on viruses that you're already immune to.

---

### Post by bodhi.zazen on 2008-02-05
If you are interested in learning a little about security, see this thread :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by JoshuaRL on 2008-02-05
> **emarkd said:**
> Your ratio is off.  It's estimated that there have been 200,000 Windows viruses and lots of those are still out there.  There have been about 40 for Linux and NONE of them are still effective.  That makes the ratio 5000:1, not 99:1.

You should also know that the Linux A/V products scan for Windows viruses and only prevent you from passing on viruses that you're already immune to.

I know, I love that.

And as far as saying that any computer with an IP address is a target is a little too simplified in my taste.  First, the obscurity angle is a little too overhyped.  Sure, it'd be less likely to work.  But if you targeted Linux users with whatever hook you're using, then you've solved that problem.  

The real issue is the problem of getting root priviledges and the lack of security holes to exploit.  For Linux, security problems are updated in hours or days instead of weeks or months in Windows.  But the way Linux is written you'd need the user **himself** to download, mark as excutable, input the sudo password, and run to get anything done.  There just isn't any way to run stuff without those steps being taken.  That is, unless the user is running as root.  And there's little to stop anything in that case.  

But even that's just theoretical at this point.  Because you could lilt around various sundry places on the internet as root in a Linux box with impunity since there's nothing out there to hurt you.  But the worst thing you can do is to think that you're untouchable.  So, I would suggest you read and apply this post by bodhi.zazen:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

EDIT:  Man, 15 minutes too late!  And from the source too.  With a cool new avatar no less.

---

### Post by supertails on 2008-02-05
Their is nothing to worry about then and that a AV will only check for windows virus and that Linux virus are not in effect.

---

