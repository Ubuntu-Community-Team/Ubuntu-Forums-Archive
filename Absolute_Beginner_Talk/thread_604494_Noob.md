---
title: "Noob"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Jumpmasterrt on 2007-11-06
Hello everyone. I've finally decided I'd like to try my hand at Linux by using Ubuntu 7.10 on the recommendation of my brother-in-law. I've got it installed on a clean machine (no other OS) with a P4 3ghz, 1.2g ram, 80gb HD.

Just as stated, it works right away. No tweaking really necessary.

So, where should I start? I need to learn about the Linux kernel first I would think, then Debian. So what are some good resources to learn? Practical exercises would help me out too. 

I've not done programming since back in the 80's on an Apple IIe. Real basic ;)

I've got a strong command of PHP, HTML and other web languages. I'm rusty on Basic Cobal and Fortran not that any of those would even be useful.

Thanks for any help you offer.

---

### Post by hyper_ch on 2007-11-06
Well, I learn on a need-to-know basis... e.g. I want to do something, don't know how, then I'll try to find out...

What do you want to do with your Linux?

If you're interested in the technical details, maybe first learning about the file system organization, package management, shell (scripting)...

---

### Post by Pumalite on 2007-11-06
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)

---

### Post by Jumpmasterrt on 2007-11-22
> **hyper_ch said:**
> Well, I learn on a need-to-know basis... e.g. I want to do something, don't know how, then I'll try to find out...

What do you want to do with your Linux?

If you're interested in the technical details, maybe first learning about the file system organization, package management, shell (scripting)...
What do I want to do? Good question. I'm not really sure. It works so well that it doesn't need improving, so I guess I just want to know how it works and then be able to completely customize it for myself.

There are some things I'd like to be able to do like make Win or Mac programs that I use available for that machine... but that's a long time from now.

A good place to start I guess would be a simple program install like Thunderbird.... unless there's a nice little deb package that does it all for you. I need a manual install package to learn with.

Pumalite... those references are exactly what I needed. Thanks

---

### Post by bobpur on 2007-11-22
There are some books out there that may help you. There are several out there just for Ubuntu. I have "Ubuntu Hacks" and "The Official Ubuntu Book." I got both of them from Books-A-Million. Try to stay current with the books as they are soon outdated by the distros they represent.
                                       Good Luck! ABN!

---

### Post by Jumpmasterrt on 2007-11-23
Yeah, I started reading something that was the equivelent to "the idiots guide to linux" and got lost.

The Unix Kernal and command line structure is the basis right? So when the install sets up it's directories as /dev, what does dev stand for? What's the difference between root and usr? Is that like the "windows" and "program files" dir's in MS?

Like Hyper_ch said, I probably need to start at the VERY beginning..... so I'm off to look for Unix references so that Linux makes sense :D

---

### Post by hyper_ch on 2007-11-23
I didn't say you need to start at the very beginning but on a need-to-know basis...

When you have tools like apt-get available for installing software from centralized repositories, does it matter much to you - in the beginning - where the actual binaries, config files, docs et al. go? I don't think so...

For the files system, have a read here:

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by bobpur on 2007-11-23
The books I mentioned were specifically about Ubuntu. I thought that would bend the learning curve in your favor.

---

### Post by Jumpmasterrt on 2007-11-28
> **hyper_ch said:**
> I didn't say you need to start at the very beginning but on a need-to-know basis...

When you have tools like apt-get available for installing software from centralized repositories, does it matter much to you - in the beginning - where the actual binaries, config files, docs et al. go? [/url]

When I said "like you said" I was referring to learning the file systems.... not starting at the beginning.... but that's not what I said (are you confused yet? :) )

I'm a little more anal retentive than most people, so to me learning WHY something is happening is just as important as getting it done. So yeah, even though the software comes in nice packages, it still matters to me where everything came from and is going. Do I NEED to know? No, but I WANT to know. That way when I screw something up, I know why or how. 

That's really the whole reason I installed Ubuntu. Not because I hate MS, but because I want to learn to do it myself.

Bob, the books were helpful but even with Ubuntu you kinda need to know what the author is talking about when they're speaking Linux.... which I didn't.  This again is because I want to learn the actual programming not just the operation of Linux.

---

### Post by Tomosaur on 2007-11-28
Explanation of the Linux filesystem: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

If you're inclined to use the terminal (a great way to learn what's going on under the hood - then just hit alt+f2 then type 'gnome-terminal'.

Most thorough way to learn? In the terminal, hit 'tab' twice, then press 'y'. This will show you all of the commands and programs you can use. Type 'man <command>' to find out more about each individual program (No all programs / commands have a 'man page', but most you're likely to use will do). For example:

```

man rm

```

Will bring up the man page for the 'rm' command (rm is the command you use to remove / delete a file.)

Have fun!

---

### Post by Pumalite on 2007-11-28
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by Jumpmasterrt on 2007-11-28
> **Tomosaur said:**
> Explanation of the Linux filesystem: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

If you're inclined to use the terminal (a great way to learn what's going on under the hood - then just hit alt+f2 then type 'gnome-terminal'.

Most thorough way to learn? In the terminal, hit 'tab' twice, then press 'y'. This will show you all of the commands and programs you can use. Type 'man <command>' to find out more about each individual program (No all programs / commands have a 'man page', but most you're likely to use will do). For example:

```

man rm

```

Will bring up the man page for the 'rm' command (rm is the command you use to remove / delete a file.)

Have fun!Now THAT'S what I'm talking about!!! 

Puma.... you too. Thanks :D

---

