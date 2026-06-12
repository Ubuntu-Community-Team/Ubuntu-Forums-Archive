---
title: "Virus's vs. Ubuntu"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Mission 10 on 2006-01-26
Just wondering how virus's can operate on Ubuntu, I can't blink without typing in my sudo password to access filesystem files. How is it that a system with firestarter closing all ports and stealthing can get a virus that can bypass the read/write protections offered by *nix boxes?

---

### Post by Madpilot on 2006-01-26
It can't, probably. There's only been a handful of *nix viruses, ever.

Why, do you think you've got something infecting your Ubuntu box?

---

### Post by Mission 10 on 2006-01-26
Just wondering, was checking out Ubuntu main page and saw the security notices and was wondering if/how a virus could work on Linux. I've never any problems with virus's at all with linux. Windows on the other hand...

---

### Post by frosty36 on 2006-01-26
Do you guys even have virus/spyware protection ... or a firewall?

---

### Post by qwazert on 2006-01-26
I use IPTables as my firewall and FIRESTARTER to configure it.
I also loaded the LINUX version of F-Prot as my Antivirus of choice...problem is, now that it's loaded I have no idea how to use it!
It doesn't show up in any of the menus and even a SEARCH for files doesn't show where it might be hiding...

...and as a typical Ex-Windozer, I keep right-clicking...hoping that the magical "**Scan with F-Prot**" will appear...but it doesn't. 

Any idea where I might find it and/or how I might use it?

---

### Post by ardchoille on 2006-01-26
You might be interested in this:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by Perfect Storm on 2006-01-26
[QUOTE=qwazert]I use IPTables as my firewall and FIRESTARTER to configure it.
I also loaded the LINUX version of F-Prot as my Antivirus of choice...problem is, now that it's loaded I have no idea how to use it!
It doesn't show up in any of the menus and even a SEARCH for files doesn't show where it might be hiding...

...and as a typical Ex-Windozer, I keep right-clicking...hoping that the magical "**Scan with F-Prot**" will appear...but it doesn't. 

Any idea where I might find it and/or how I might use it?[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

---

### Post by qwazert on 2006-01-26
I have no files named **xfprot** anywhere. Maybe I should try to RE-load it again?

---

### Post by Perfect Storm on 2006-01-26
you need to download xf-prot and compile it. It's not in the repo.

---

### Post by GreyFox503 on 2006-01-26
Unless you're running all kinds of unecessary daemons and services and opening ports, the risk of getting anything is really low.  Of course, if you download something yourself and execute it, anything could happen.  Just make sure you trust it.

That said, I've never had any problems running anything under linux.

I like this article:  [http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by frosty36 on 2006-01-26
hmmm....well I have McAfee Security Centre (firewall , virus scan etc) ; and was wondering if WINE could emulate it :p ... or have I got the wrong end of the stick :confused:

---

### Post by public_void on 2006-01-26
> hmmm....well I have McAfee Security Centre (firewall , virus scan etc) ; and was wondering if WINE could emulate it  ... or have I got the wrong end of the stick 

You don't need any of it really on Linux. Think about it, most viruses are platform specific, for exmaple one adds a registry key to start. How is it going to do that in Linux, if there is no registry. If it runs from home then it won't have persmissions to do anything serious to your file system. Even if you download from p2p and get a infected file, you won't suffer anything serious. But if you pass the file on a poor windows user might. IMO if your using p2p alot, then it might be worth it so you don't pass anything on.

---

### Post by hen3rz on 2006-01-26
> But if you pass the file on a poor windows user might. IMO if your using p2p alot, then it might be worth it so you don't pass anything on.
This is all I use anti virus on linux for. To help prevent the spread of viruses other wise there is really no point to have it on linux.

---

### Post by Jussi Kukkonen on 2006-01-26
[QUOTE=Mission 10]Just wondering how virus's can operate on Ubuntu, I can't blink without typing in my sudo password to access filesystem files. How is it that a system with firestarter closing all ports and stealthing can get a virus that can bypass the read/write protections offered by *nix boxes?[/QUOTE]
Easily. The virus is a binary executable attached to a mail in your mailbox. The mail says:
[INDENT]*Hey D00d! Check out these warez! Just run:*
$ chmod +x warez-0-day
$ sudo ./warez-0-day[/INDENT]
That's pretty much what all the unix viruses I've heard of do... It's not very smart or effective, but on the other hand it's very resilient -- the OS vendor can't patch user stupidity (like they could patch a hole in the email program).

Worms are another matter, and there your firestarter might have some effect.

---

### Post by MJN on 2006-01-26
Indeed - social engineering is one of the biggest enablers to spreading and executing viruses (virii?!) and in this regard Linux is no more secure than anything else.
 
Complacency probably comes a close second.

---

### Post by el3ktro on 2006-01-26
I have only a few networked services running (CUPS, Samba etc.). When you limit them to accept only connections from the local network, and when you only start those services you really need, there's no reason for a filewall imho. Besides that, my router has a firewall built in and I've activated some simple settings.

I'd only use a virus scanner on a Linux box if you constantly & often share files with Windows users, or of course when you run a Samba fileserver (or any type of fileserver).

The chance of getting infected by installing malware is virtually zero when you limit yourself to install only software from the default Ubuntu repos, or from any other trusted repos. If you need a program which is not in the repos, then stick with software that is well known, download the .tar.gz or .deb only from the project homepage itself, or via well-known sites like sourceforge etc. I think you can trust those. NEVER install Linux software downloaded from any P2P network (except BitTorrent) because since Linux software is usually free&open, there's no need to download them via P2P, and I would consider such an "offer" suspicious.

Tom

---

### Post by MJN on 2006-01-26
All sound advice, regardless what OS you use...

---

### Post by az on 2006-01-26
[http://reactor-core.org/stack-smashing.html](http://reactor-core.org/stack-smashing.html)
SMASHING THE STACK FOR FUN AND PROFIT

`smash the stack` [C programming] n. On many C implementations it is possible to corrupt the execution stack by writing past the end of an array declared auto in a routine. Code that does this is said to smash the stack, and can cause return from the routine to jump to a random address. This can produce some of the most insidious data-dependent bugs known to mankind. Variants include trash the stack, scribble the stack, mangle the stack; the term mung the stack is not used, as this is never done intentionally. See spam; see also alias bug, fandango on core, memory leak, precedence lossage, overrun screw.


One of the most commone vulnerabilities (a virus is a very narrow kind of vulnerability - there are many kinds of vulnerabilities) is a buffer underrun.  You can gain root access by smashing the stack like that.

Your best protection is to keep up to date with updates.

---

### Post by MJN on 2006-01-26
Don't you mean buffer *over*run...?!

(Although I suppose one could call a failed CD burn as a vulnerability... ;))

Mathew :)

---

### Post by az on 2006-01-26
Hi!  I'm mister Smarty Pants!

*bows head*


"buffer overflows", not "buffer underrun".  My bad.  






Where did I put my Geritol?

---

