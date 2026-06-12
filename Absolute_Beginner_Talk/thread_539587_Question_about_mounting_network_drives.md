---
title: "Question about mounting network drives"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by rshel on 2007-08-31
Greetings. 

This is a noobie question.   I've been running ubuntu for a couple of years (now on Ubuntu 7.4).  I've managed to mount network drives, windows shares, etc.  But I have never understood, being a non-tech guy, something about network shares.  I have at home a Simpleshare Network Attached Storage (NAS) stand-alone hard drive connected through the router. My family access the shares from various OS's with little trouble.  On my Ubuntu machine I access the drive in two ways.  I have used the Connect to Server under the Places menu on the main menu, filled out the neccesary info on windows share, etc., and have the shares appear reliably on my desktop.  I can write to them and read from them as user.  I use the menu unmount command to unmount them.  But I cannot access them from terminal or from any program.  So I mount the same shares through fstab and directories created in /mnt.  When I do so, however, I cannot write to them except as root (I have never managed to change the permissions--access is denied or they simply revert to the original root ownership).  Anyway, I can live with it--life is too short.  But I am curious, what am I "mounting" to the desktop when I use the "Connect to Server" menu option and why is it that no program but the windows browser (Nautilus?) can access such mounted locations.  Is this a security thing in linux?

Just curious.  Thanks.  And by the way, if anyone has some easy to follow suggestions for how to change permissions on a Simpleshare Network Attached Storage device, I'd love here it.

Thanks

---

### Post by kidders on 2007-09-01
Hi there,

> **rshel said:**
> This is a noobie question.Your issue seems to be a common source of confusion.

> **rshel said:**
> I have used the Connect to Server under the Places menu on the main menu, filled out the neccesary info on windows share, etc., and have the shares appear reliably on my desktop. I can write to them and read from them as user. I use the menu unmount command to unmount them. But I cannot access them from terminal or from any program.Imagine you launch Firefox and open [ftp://ftp.ubuntu.com/](ftp://ftp.ubuntu.com/). You now have access to a remote fileshare. You *could* describe it as being "mounted", although strictly speaking, that would be inaccurate. It would also be naive to suggest that any other application would be in a position to access the share, simply because Firefox has opened it.

This idea is analogous to your Gnome question. Just because an application like Nautilus has opened a remote fileshare doesn't mean it has "mounted" it, and doesn't mean any other application can access it.

There are two observations to make about this:

**1: This kind of thing *does* work in other OSs.**
Take Windows or MacOS as an example. On those platforms, Explorer and Finder are just applications (just like Nautilus or Konqueror). The difference is that they are a sort of "standard" on their respective platforms ... applications can always assume they are there, and can rely on the mechanisms for interacting with them, so every single other application written for Windows and MacOS can interact seamlessly with them, giving you universal access to anything Explorer & Finder can access.

In the Linux world, this sort of high-level universal standard does not (and never will) exist, because it would deprive its users of the main reason many of them opted for the Linux platform in the first place.

**2: Mount things!**
Linux has something OSs like Windows lack, in that absolutely anything (eg a bluetooth OBEX facility on a phone, the contents of an optical disc, a remote share, part of your BIOS, or maybe a file with some sort of disk image stored in it) can be plugged into the root filesystem and accessed completely transparently, by becoming indistinguishable from the rest of your files. Thus, by dropping to a terminal and simply "cd"-ing from one directory to another, you could very well be bouncing between continents, in terms of where the data you're accessing is really stored. Since the system is so low-level, it is essentially impossible for an application *not* to have easy access to remote data ... even if the app wasn't originally written for Linux.

> **rshel said:**
> So I mount the same shares through fstab and directories created in /mnt.  When I do so, however, I cannot write to them except as rootNow, this is an entirely separate issue ... a more general problem that has to do with the way Linux manages access control. There are two angles on it...

**1: Embedded access control**
Every desktop OS in the world except Windows adheres to the same mechanisms for controlling access to files. This means that lots and lots of mounted filesystems contain embedded information about who can access what. Linux's default behaviour is to obey these instructions. 

**2: Other things**
A great many "mountable" things don't provide decent access control information, including ISO images, Samba shares, many WebDAV filesystems, and so on. Linux's default behaviour varies slightly from one example to the next, but the general rule of thumb is not to grant a level of access that might be somehow inappropriate.

Windows fileshares are particularly thorny, so I'll use them as an example:

Imagine you share a directory on one Linux box using Samba (so Windows boxes can access it), and you just happen to mount it on a second Linux box. As you play around with the share, access control information is being translated from the cross-platform *-nix standard into an alien standard, and back again. Since the two standards involved don't work quite the same way, some information is lost in the process, and becomes the subject of complicated guesswork, as Linux tries its best to fill in the blanks in a safe way.

> **rshel said:**
> I have never managed to change the permissions--access is denied or they simply revert to the original root ownershipIf the permissions you're trying to change don't physically exist, this won't work.

At a more superficial level, consider that accessing a network share usually requires some sort of login procedure. If you log in as user A, it's not normally appropriate to allow user B too much access to the share. During boot, /etc/fstab is processed as root, so root is the user that will be given proper access to anything that's mounted, in the absence of explicit instructions to do otherwise. As I mentioned, some filesystems contain such instructions ... other times they are inferred from your working environment. Of course, as if life wasn't complicated enough, some file sharing schemes use a concept called "root squashing", which means that server-side, attempts made by the superuser to access data are treated as though he were a privilege-less guest.

Anyhow, sorry for rambling! I hope this post sheds some light on the problems you've been having. In brief, my suggestions are...[LIST]
[*]Stick to traditional mounting where possible.
[*]Read a little about how to use /etc/fstab to log into remote shares as non-root users.[/LIST]Don't forget that you can use /etc/fstab to "prepare" mounts for later use, using the "noauto" mount option. Basically, once you've figured out the perfect set of mount options ... the ones that cause your remote fileshares to be mounted just the way you like them ... you can use /etc/fstab to save yourself the trouble of having to repeatedly re-type them, and reduce mount operations to a short, simple command such as "mount /media/windows". Your system will then look up /etc/fstab for references to the directory you specify, and perform the appropriate mount for you.

---

### Post by rshel on 2007-09-01
Thank you for the extensive, illuminating reply; you provided more information in that single post than I have gleaned from hours of web-browsing. 

My misunderstanding of the mounting procedures reduces, in part, I'm afraid, to my humanities background: an appreciation of complexity and nuance but a habituated literal-ness when it comes to word usage--and an assumption that in the cold, hard realm of computers things are either black or white (or, uh, 0 and 1?).  So when linux says it's "mounting" something, I assumed, with my dangerously little knowledge, that it was, indeed ,"mounting" it.  As you said, however, life is complicated. Obviously, there's mounting and then there's mounting. 

I appreciate you helping to clear things up.

rshel

---

### Post by kidders on 2007-09-01
Hehe no problem.

I imagine that when your box tells you it's mounting something it really is though. :confused: It would be odd for an app to use the term carelessly.

The sure way to know what's going on is to drop to a terminal and type "mount". That way, there's no mystery. Sometimes things like Gnome mount stuff (making things universally accessible), other times they don't ... only one way to be sure!

---

### Post by rshel on 2007-09-01
Kidders, thanks for the information and suggestions.

If I am in doubt, I will in the future use the terminal be certain about who or what I'm mounting.  

Let me make sure I've got this sort of straight.  There seems to be two different uses of the word "mount" deployed by Ubuntu/Linux here.  One usage refers to "mounting" a device or remote computer, etc., as a file system accessible by my Linux box, if I'm understanding you correctly, through samba, etc., with proper instructions in fstab.

The second usage refers to what happens when I use the Connect to Server menu choice in Ubuntu.  When I select this option and fill out the proper information in the dialog box, I "mount" a permanent link/launcher/automated script to a network location -- a "shortcut" in Winblows parlance -- on my desktop. When I click the link, I'm connected to the network.  As a network connection it is not accessible for programs on my Linux box, and the network connection is not permanently mounted, only the launcher/automated script that opens the connection is.  This is why the links show up on my desktop even when the network is inaccessible.   So when I "unmount" one of these links all I'm really doing is breaking the connection and removing the desktop launcher/link/script.   Is that more or less correct?  

Thanks again .  Cheers!

---

### Post by kidders on 2007-09-01
I'm not a Gnome user, so you'll have to try it out yourself to be sure. If I remember correctly, some filesystem & network related actions cause things to mount ... others don't.

In my opinion, the use of the word "mount" where no mounting (there's only one kind of mounting!) actually takes place is a bug, and doesn't exactly help people who are new to the platform. If you come across an occasion where Gnome calls something "mounting" that doesn't actually mount anything, feel free to report it to the Gnome devs.

When something is mounted, your entire system can see it, and it should be listed when you type "mount" into a terminal window.

I hope that's a little clearer. Sorry for being fuzzy.

---

### Post by rshel on 2007-09-01
No, no, no, you were very clear.  My own limited knowledge is the problem.  Thanks for explaining things.

Cheers

---

### Post by kidders on 2007-09-01
No worries. :-)

---

