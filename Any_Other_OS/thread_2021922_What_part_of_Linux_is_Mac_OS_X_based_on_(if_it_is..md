---
title: "What part of Linux is Mac OS X based on? (if it is...)"
date: 2012-07-10
forum: Any Other OS
---

### Post by linuxvstheworld on 2012-07-10
I use Mac and Ubuntu as my main OS' and I've noticed that some terminal features (Ex. PWD, CD, etc.) were both in Ubuntu **AND **Mac OS X. Any chance they're somewhat cousins in OS terms?

---

### Post by haqking on 2012-07-10
> **linuxvstheworld said:**
> I use Mac and Ubuntu as my main OS' and I've noticed that some terminal features (Ex. PWD, CD, etc.) were both in Ubuntu **AND **Mac OS X. Any chance there somewhat cousins in OS terms?

NO and Yes.

Linux is based from Minix a type of UNIX.

Mac OSX is based from BSD, which is UNIX.

---

### Post by linuxvstheworld on 2012-07-10
So Mac OS X Isn't directly related to Linux. But somewhat related to UNIX, along with Linux. Okay, that clears things up. Thanks!

---

### Post by haqking on 2012-07-10
> **haqking said:**
> NO and Yes.

Linux has its conceptual roots from Minix which is a type of UNIX.

Mac OSX is based originally upon from BSD, which is UNIX.


Edit: cleared that up a little

---

### Post by buzzingrobot on 2012-07-10
> **linuxvstheworld said:**
> I use Mac and Ubuntu as my main OS' and I've noticed that some terminal features (Ex. PWD, CD, etc.) were both in Ubuntu **AND **Mac OS X. Any chance they're somewhat cousins in OS terms?

Both OS X and Linux share the common heritage of Unix.  Both Linus Torvald's kernel efforts and the GNU folks work were motivated by a desire for a "free" Unix.  You need to read about the history of Unix for the context. Minix was a small teaching version of Unix created and published by Andy Tannenbaum. Tannenbaum's Minix book is an excellent intro to the software concepts used in Unix and all of its descendants.

The BSD versions of Unix, e,g, FreeBSD, can trace their lineage back to an early version of Unix developed at the University of California at Berkeley.  (BSD = Berkeley Software Distribution.) If you want to be pedantic, FreeBSD has a much better claim to being in the "real" Unix genome than Linux or OS X, but that's history at this point.

A decade or so ago when Apple decided to move to OS X, they chose a version of BSD as its underpinning. It was morphed (forked, essentially) into an OS called Darwin that was, and still is, freely available, minus all the GUI and other proprietary goodies from Apple that make OS X what it is.

The similarities you see in Terminal are because both Linux and OS X both use the same default shell command interpreters, BASH.

---

### Post by Bachstelze on 2012-07-10
> **buzzingrobot said:**
> 
The similarities you see in Terminal are because both Linux and OS X both use the same default shell command interpreters, BASH.

Actually, even if OS X did not use Bash, the commands (pwd, cd, etc.) would still be the same. As I am sure you know, those commands are not related to Bash in any way; that's a common misconception.

---

### Post by buzzingrobot on 2012-07-10
> **Bachstelze said:**
> Actually, even if OS X did not use Bash, the commands (pwd, cd, etc.) would still be the same. As I am sure you know, those commands are not related to Bash in any way; that's a common misconception.

True.  That seemed unnecessary in that little encapsulation.

---

### Post by Bachstelze on 2012-07-10
Also I forgot to mention, in most cases the commands are not *exactly* the same. As was said earlier, OS X's UNIX userland comes mostly from FreeBSD, while most Linux distributions use the GNU userland. In general, the FreeBSD versions of the basic utilities are closer to the original UNIX ones, whereas the GNU folks have added a lot of new features to their versions. (One example among a multitude of others is the [font=monospace]-i[/font] flag of [font=monospace]sed[/font] to perform in-place manipulations: it is a GNU extension, and thus only available in GNU sed, not in the version of sed that is in FreeBSD, and thus in OS X.)

---

### Post by schmii on 2012-07-10
Perhaps this explanation can help you with your understanding of Linux's roll in an operating system.  Linux is in fact, GNU/LInux, or as I’ve recently taken to calling it,  GNU plus Linux. Linux is not an operating system unto itself, but rather  another free component of a fully functioning GNU system made useful by  the GNU corelibs, shell utilities and vital system components  comprising a full OS as defined by POSIX. Many computer users run a modified version of the GNU system every  day, without realizing it. Through a peculiar turn of events, the  version of GNU which is widely used today is often called “Linux”, and  many of its users are not aware that it is basically the GNU system,  developed by the GNU Project. 
There really is a Linux, and these people are using it, but it is  just a part of the system they use. Linux is the kernel: the program in  the system that allocates the machine’s resources to the other programs  that you run. The kernel is an essential part of an operating system,  but useless by itself; it can only function in the context of a complete  operating system. Linux is normally used in combination with the GNU  operating system: the whole system is basically GNU with Linux added, or  GNU/Linux. All the so-called “Linux” distributions are really  distributions of GNU/Linux.

---

### Post by Bachstelze on 2012-07-10
Nice copypasta.

---

### Post by MG&amp;TL on 2012-07-10
> **Bachstelze said:**
> As I am sure you know, those commands are not related to Bash in any way; that's a common misconception.

[http://en.wikipedia.org/wiki/Shell_builtin](http://en.wikipedia.org/wiki/Shell_builtin)

If you wanted to be really pedantic, some are. But I'm sure you knew that. ;)

---

