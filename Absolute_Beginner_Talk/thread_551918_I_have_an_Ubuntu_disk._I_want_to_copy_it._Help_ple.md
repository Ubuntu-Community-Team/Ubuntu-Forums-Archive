---
title: "I have an Ubuntu disk. I want to copy it. Help please."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by penguinv on 2007-09-15
This should be so simple. 
-- I can download Ubuntu and then burn a disk with InfraRecorder.

But how do I take a disk I have (the professionally printed one, nice eh, lucky me) and copy it onto another disk?
--- InfraRecorder won't let me do it. I cannot have the source drive be the same as the target drive. I could do that with DOS diskcopy with the old floppy drives but not now. What's up with that?
--- I tried dragging the D: image to the Desktop, No. I tried copying it (submenu copy command) and pasting it to the Desktop. No. This "assumed" that I could then burn it (with InfraRecorder and it would be a workable bootable iso image.

I can find no documentation on this. I can't be the first person who wanted to get the same kind of image FROM A DISK that you can get by DOWNLOADING.Or can I?

Please help me and THEN put this information in the Ubuntu site.

Please actually take this question on!!! And thanks.

---

### Post by yabbadabbadont on 2007-09-15
Download the free/trial version of nero and use it's CD copy function.  It will let you have the source and destination be the same drive.  It will create an image of the disc to be copied on the hard drive and then prompt you to insert a blank media for burning.

---

### Post by chrome307 on 2007-09-15
To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

Open up TERMINAL and copy and paste in one of these commands:

**dd if=/dev/dvd of=dvd.iso** # for dvd
**dd if=/dev/cdrom of=cd.iso** # for cdrom
**dd if=/dev/scd0 of=cd.iso** # if cdrom is scsi


Ignore the** #** comments .... there just there to let you know what each one is for.

Once you've created your ISO image, you will find it in your HOME folder, simply right click and burn the ISO.

---

### Post by Dr Small on 2007-09-15
Why not have the drive mounted ?
I use this method several times, and had it mounted every single time...

---

### Post by yabbadabbadont on 2007-09-15
From the comments the OP made, I'm fairly certain that (s)he wants to do this in Windows...  ;)

---

### Post by penguinv on 2007-09-18
Thanks so far.
From Yabbadabbadont: I see how to do it in Windows. Thanks.

From chrome307: I dont see. I thought I put this in the ABSOLUTE Beginners so I would get the clearest directions. Oops, your version is not transparent to me.

OK we are doing it in Ubuntu, can I use the livecd or only on an installed system? How do I get a Terminal Window? (It took me forever today to get a telnet session going with an ISP wherein/on I have an account. It was under Something and then Connect to while I was looking at Terminal Applications.
And it didnt suggest port 22 for SSH the way putty (for Windows) does. I had to go into the windows application that works and do it from there. And what if I want a command line. I havent a clue on that yet but I didnt look. I suppose I can use the mail application in gnome instead of pine. Wow, I could evolve.)

And then, I'm a human not a robot. If you give me a bunch of lines to robotly use, I am absolutely not going to do it. Try explaining to me. I have heard of advice for a windows newbie that did terrible things to their drive. I am a newbie trying to learn. Not a paying customer that wants you to just get the job done.

So I prefer to hang with a different attitude. 

On the other hand, I can infer from your actions that you mean well, want to help me, are clear about the steps to be done and dont put all kinds of motivational or off topic things in your posts. Good stuff. 

Get me right, I would love to hear the explanation of those cryptic lines, or a link to where I could learn it. Since I saw InfraRecorder I was thinking in the GUI world. But using a shell would be dandy, if I could just figure out how to get one. Heh. I think I've been using tsch on that remote machine.

And thank you for your contributions all.

---

### Post by hyper_ch on 2007-09-18
penguinv:

Instead of others explaining to you what terminal commands do you could go and figure it out yourself. Google is a great place to start with... although I prefer the man(ual) pages --> open a terminal, enter "man COMMAND" --> you'll get a whole lot of info about it... press "q" to quit the man pages and the arrow/page keys to navigate through it.

In this example here, run this:
```

man dd

```

---

### Post by Overbyte on 2007-09-18
> **penguinv said:**
> 
From chrome307: I dont see. I thought I put this in the ABSOLUTE Beginners so I would get the clearest directions. Oops, your version is not transparent to me.


To open a Terminal Window (in Ubuntu), go to Applications, Accessories, then click Terminal.
Pop the CD in, then type that command.

dd originally meant "data definition" (according to UNIX history), but it currently doesn't mean anything. dd is used to copy data bit by bit from one place to another. In this case we'll use it to clone a CD.

To explain chrome307's command:

dd if=/dev/cdrom of=cd.iso

dd <- the command itself
if=/dev/cdrom <- the input, what you want to copy. In this case he points it to the CD-ROM.
of=cd.iso <- the output, this means it will copy the contents of the CD-ROM into a file called cd.iso.

So...the general syntax of the command, if you want to use it someplace else...
dd if=[source file] of=[destination file]

An ISO is a special file which is literally a bit-by-bit replica of a CD or DVD.
If you can't find it, it maybe is located in the root directory of "filesystem" (which is /). If not, it may be in your home directory.

Articles and Sources: [[COLOR="Orange"]here[/COLOR]](http://en.wikipedia.org/wiki/Dd_(Unix)) [[COLOR="orange"]here[/COLOR]](http://www.codecoffee.com/tipsforlinux/articles/036.html) and [[COLOR="orange"]here[/COLOR]](http://linux.about.com/od/commands/l/blcmdl1_dd.htm)

---

