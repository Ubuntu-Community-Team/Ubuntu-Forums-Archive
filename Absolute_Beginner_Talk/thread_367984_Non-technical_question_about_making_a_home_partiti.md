---
title: "Non-technical question about making a /home partition"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by thadiusdean on 2007-02-22
Now, I'd make a /home partition so if I reinstall Linux, all my stuff will still be there. But what about my installed programs? When I download applications and stuff they go to... some other folder. So if I reinstall, I'll still have my documents, etc. but lose everything else. I'd kinda like to go along with the norm and install programs where I'm suppose to put them but I'd still like to keep my programs.

Oh... maybe I can just keep the .deb and other install files...

Anyway. What would you guys do? What does your /home folder look like?

---

### Post by indytim on 2007-02-22
This should help you out to move an existing /home to a separate partition:

[Home Partition]("http://www.psychocats.net/ubuntu/separatehome")

If you're going to do a new fresh install, just pre-configure an extra ext3 partition for your new /home and manually select your partitions when you install the ops.

Hope this gets you there.

IndyTim

---

### Post by kidders on 2007-02-22
Hi there,

Traditionally, Linux users tend to have little interest in being able to hold onto applications the way you describe, for a multitude of reasons. For example:

[LIST]
[*]Many apps are architecture-specific, or can be *built* to be architecture-specific, for better performance. Some things can even be kernel-specific. In such cases, stability would become an issue on your new system, if enough about the operating environment were to change.
[*]If you consider some of the possible reasons why you might want to reinstall your OS, you might find that you wouldn't want to keep your applications after all. Say, for instance, someone intentionally damaged your system ... you could never be sure how safe it would be to run your apps.
[*]Unlike Windows software, and some Mac software, Linux apps tend not to come pre-packaged with all the possible system libraries & third-party dependencies they might need. If your new system were missing things, your applications wouldn't work properly.
[/LIST]

As a consequence, two things have happened in the Linux world:

[LIST=1]
[*]Files have become organised very much by purpose, rather than by application. An application's documentation will tend to live in one place, while its system libraries live in another. Configuration information almost always goes to yet another location, and so on. Although this means you always know exactly where to find what you're looking for, it makes gathering all the components of an application together very difficult. OS X works in a very similar fashion.
[*]Secondly, Linux software management has become incredibly efficient. After all, what other platform can offer you a way to identify, download & non-interactively install almost anything you want from a single location, complete with all necessary support applications & libraries, *and* help you keep them all up to date, regardless of whether they've each been developed by different people?
[/LIST]

To be honest, I would not recommend trying to hold onto your software between installs. If however you would still like to try, I would be more than happy to discuss the detail of how you might go about it.

It is worth noting though, that if there are one or two particular applications that you perhaps found very difficult to get hold of, or spent hours trying to compile/install, you *can* make special arrangements to hold onto it across installs. Many apps let you tweak their install-time configuration so they wind up in your home directory (ie a personal install), rather than being made available system-wide. Sometimes you have to compile the app from source to achieve this effect though. If, for argument's sake, you were a guest on someone else's Linux box, you would *have* to install your apps that way, since you wouldn't have the privileges to make system-wide alterations.

> What does your /home folder look like?I have a large number of .dotfiles and .dotdirs containing personal settings for system-wide apps, not all of which I necessarily have on my system at this very moment. In addition, I have full installs of a very small number of applications that are for my own personal use. I also keep all my personal data, with the exception of very large things like movies & music, which I store on a separate filesystem that I've optimised to handle bigger files better.

One other part of my desktop PC that I tend to treat specially is /etc. If (as I do from time to time) I want to try a different distro for instance, holding onto my /etc makes it far easier to reconfigure applications the way I want them. After all, it's not so much the actual *installation* of an app that is awkward ... it's setting it up afterwards that can take time.

Sorry for rambling on for so long! I hope this answers some of your questions.

---

### Post by thadiusdean on 2007-02-23
This answers my question exactly, thanks kidders!

---

