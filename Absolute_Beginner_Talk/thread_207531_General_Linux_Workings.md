---
title: "General Linux Workings?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-07-02
Ok let me see if I have this straight.

Linux is open source, it started as a combination of a kernel written by Linus Torvalds and as a set of scripts from the GNU project right? What exactly were those scripts/what did they do?

So as it stands right now, there are a variety of different distributions on the market. I got that much. But a distribution equals what exactly? Just a repackaging of common shared scripts? Or is there more to it?
As a newbie end user all I'm seeing is either the Gnome or KDE interface and all the same basic software being run from one distro to the next. So I'm having a hard time wondering what's different between them all. Even though I know there has to be differences, I just don't understand what they are. Please inform.

What exactly does the kernel do? The way I understand it right now it's basically the core that everything else attaches to in a modular system. Would I be right? Or is it something different?

Is the Kernel itself opensource? Do the different distros mess with it at all? Or is that just controlled by Linus? If that's the case do distros have to sit around and wait to add new stuff until the kernel catches up and supports it? What happens if the kernel never supports it? If that's just something that Linus says "eh, not important". 

Or are there diffferent Linux kernels? 
And if that's the case how does everything still work together?

Sorry for all the questions. Maybe there is a website somewhere you guys can point me to that will answer them. I've read about it's history I'm just still fuzzy on how it's all set up and works. Who does what and who controls what and how it all comes together.

---

### Post by molly_001 on 2006-07-02
[SIZE=2]I had those same questions when I started to research a Linux distribution.[/SIZE]
 
[SIZE=2]Nonetheless I was glad to read the short article below about the Portland Project.  In fact, learning about Portland Project was the clincher in helping me to decide to go ahead with becoming a new user of Linux at this time.[/SIZE]
 
LINK:
[http://www.desktoplinux.com/news/NS6247192959.html]("http://www.desktoplinux.com/news/NS6247192959.html")

---

### Post by 3rdalbum on 2006-07-02
GNU is a bit more than just a set of scripts. It provides the huge array of command-line tools, which in turn are used by the GUI layers. For instance, when you create a new folder, that's actually running a program written by GNU. But there is a mind-boggling number of programs written by the GNU project, some of which you will find very useful some day :-)

A distribution usually contains a whole heap of custom-written stuff for hardware support and user environment. For instance, the GDebi unpackager for Ubuntu was written by the Ubuntu developers. Many programs are modified slightly for certain advantages in some distros.

Your definition of the kernel is very abstract, but correct. The kernel is open-source, and the distros do fiddle with it a bit. This is especially true for the lightweight distros (not including Xubuntu), where often advanced hardware support is sacrificed for speed. Sometimes, bugs in the kernel are fixed by a distro developer, and the changes submitted to the kernel team for inclusion in the main code. But Linux generally has main control over what goes into the kernel, as distro developers don't really have time to add huge features to the kernel.

Everything works together... somehow! The bits that don't work together are made to work together by the distro developers.

---

### Post by Jucato on 2006-07-02
Well, first of all, don't be shy in asking questions. Every one's entitled to them.

Now on to the topics:

1. GNU/Linux: You're right, Linux is the kernel written by Linus Torvalds from Helsinki (but not entirely by him alone). But it was just a plain kernel, not enough to make an operating system, which what he was originally trying to make. He needed some other tools. On another side of the world, the Free Software Foundation (FSF) was also trying to make an OS, but all they had were the programs that were needed by the kernel, and lacked the kernel itself. To make the long story short, these two parties joined forces and produced the base of the Linux OS.

FSF's GNU didn't provide scripts. They provided essential programs that was needed by any kernel/OS, most notably, a compiler, which they called GCC or the GNU C Compiler. There are other programs that were included as well, such as EMACS (a text editor), but gcc was the most important thing, AFAIK.

2. Linux distributions: For a Linux OS to run smoothly, there are various parts that need to interact harmoniously: the kernel, the X server, the desktop environment/window manager, and the programs/packages. What Linux distributions do is to provide a Linux distribution customized to suit their customers'/users' needs and to make sure that those different parts of the OS work together, specially the programs/packages. Linux distributions are unique and customized in different ways from appearances to under-the-hood stuff. Most of the time, they have to modify certain programs or even the kernel itself, to make sure that these programs would work properly on their distribution. Other distributions also have custom made programs, like SUSE's YaST, Linspire's CNR, etc.

There are other things that makes one distro different from another, but these are the ones that I know about.

3. The reason why we have KDE and GNOME (and Xfce) is due both to some historical reasons, technical reasons, and the way the Free/Open Source world operates.
- historical reason: KDE was made first, but was based on a toolkit that was, at that time, not under a Free/Open Source license, like the GPL. This was a major issue for some people, notably those from the FSF. So they decided to make a completely different Desktop Environment (DE) and make a new toolkit from scratch. Thus GNOME was born. Later, though. Qt (the toolkit used by KDE) was released under a dual licensing scheme, which includes GPL. But by that time, GNOME was already well established and had won much support, so it didn't make sense to stop the project.
- technical reason: most important difference is that KDE's Qt is based on C++ and GNOME's GTK+ is based on C. There are other technical differences, but that might be reserved for a separate discussion.
- how the FOSS world operates: there's a saying among developers/programmers that goes "scratch your own itch", meaning, if something doesn't have what you want/like, try making one yourself. Although this accounts for much duplicity in the FOSS world, it's the freedom to do what you want or make what you need that makes the FOSS world go round.

4. The kernel
a. A kernel basically provides a way for software to communicate with the hardware and vice-versa, without having to know the specific details of the hardware. Think of it as a sort of phone operator/translator. The kernel is also responsible for handling the system's resources, like RAM, making sure to distribute it where it's needed. take note that not only Linux has a kernel. OS X, BSD, and Windows also have kernels, too.
b. Distributions sometimes (or probably usually) modify/customize kernels so that they could work smoothly on their distros. I'm not exactly sure though, but it makes sense. That's why even if a new kernel version/patch comes out, distros don't immediately have them available for download/update. 
c. The kernel, although started by Linus, is not solely written nor controlled by him. Even in the the process of making the kernel, many people were involved. And even now, although Linus is the main man, he's not the sole person responsible for the maintenance of the kernel. As for deciding which features to include, I'm not sure how the decision-making process is made. But you can rest assured that with many people involved, many views/opinions/suggestions will be taken into consideration.

Well, those are what I know. They may be wrong. I'm no expert. Just don't take my words as bible truth. :D

---

### Post by roxics on 2006-07-05
Excellent! Thank you so much for all the info. It really helps to clear things up.
I'm sure I'll have more questions in the future, but right now I'm good with what you gave me. 

Thank you.

---

### Post by Nequeo on 2006-07-05
Just a minor correction to Fenyx's otherwise excellent answer - GNOME did not create a toolkit from scratch. The GTK toolkit it uses was originally created for the Gimp. The 'G' in GTK stands for 'Gimp', not 'Gnome'.

Cheers,

---

### Post by Jucato on 2006-07-05
Thanks for that correction. I totally forgot that GIMP was already there when they started GNOME. :D

---

### Post by roxics on 2006-07-05
Ok I've got a couple more questions. Does linux and BSD both use the same terminal commands? 

What makes linux Unix based?
As in what defines something as being like unix?

---

### Post by Jucato on 2006-07-05
I'm not really familiar with BSD, but seeing that their UNIX based OS'es, they might share some similarities when it comes to commands on the terminal. I'm just not sure how much they are similar, because they might be using different "shells" (the command prompt program, so to speak). Linux uses *bash*, the "Bourne-Again SHell".

Regarding being UNIX based, here's a wikipedia article that could help. but being a wikipedia, take it with a grain of salt.
[http://en.wikipedia.org/wiki/Unix-like]("http://en.wikipedia.org/wiki/Unix-like")

---

### Post by Bloch on 2006-07-05
> As in what defines something as being like unix?

The various flavours of unix agree on some common standards called POSIX 
Linux and OS X are POSIX compliant - though I believe OS X breaks some of the standards.

A system that historically was derived from UNIX could still call itself a unix, but I guess for most users they mean something POSIX compliant

---

### Post by Jucato on 2006-07-05
And this would be the meaning of POSIX
**Portable Operating System Interface **(the **X** is for UNI**X**)

[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

---

### Post by IYY on 2006-07-05
> Ok I've got a couple more questions. Does linux and BSD both use the same terminal commands?

Mostly. The commands are not exactly the same, but very similar. In fact, BSD uses many GNU utilities, and the same shells.

> What makes linux Unix based?

It's not. There is no code whatsoever from the original Unix in Linux. The kernel was written from scratch by Linux, and the utilities have existed even earlier from the GNU project. Don't forget that GNU stands for "GNU is Not Unix". 

> As in what defines something as being like unix?

Already mentioned, read up on **POSIX**. That is the exact definition of being unix-like.

---

### Post by Jucato on 2006-07-05
[quote=IYY]It's not. There is no code whatsoever from the original Unix in Linux. The kernel was written from scratch by Linux, and the utilities have existed even earlier from the GNU project. Don't forget that GNU stands for "GNU is Not Unix". [/quote]

From [http://www.linux.org/info/index.html](http://www.linux.org/info/index.html)
>  Linux is an operating system that was initially created as a hobby by a young  student, Linus Torvalds, at the University of Helsinki in Finland.  Linus had an  interest in **Minix, a small UNIX system, and decided to develop a system that  exceeded the Minix standards**.

And from [http://www.gnu.org](http://www.gnu.org)
> The                        [GNU Project]("http://www.gnu.org/gnu/thegnuproject.html") was launched in 1984 **to                        develop a complete UNIX like operating system **which is                        [free software]("http://www.gnu.org/philosophy/free-sw.html"): the GNU system (GNU is                        a recursive acronym for “GNU's Not UNIX”; it is pronounced                        *guh-noo*, like *canoe*)

The fact that the GNU project even had to say that they were "not UNIX" means that they were, in some ways, similar to UNIX, hence the need to say that they are not UNIX. "not UNIX" here only means that they are not 100% identical to UNIX, but it doesn't mean that they don't posses any similar qualities.

---

### Post by IYY on 2006-07-05
> Linux is an operating system that was initially created as a hobby by a young student, Linus Torvalds, at the University of Helsinki in Finland. Linus had an interest in Minix, a small UNIX system, and decided to develop a system that exceeded the Minix standards.

This is not even true. "Linux" is not an operating system, but a kernel. You can use the naming liberally in every day conversation if you like, but when talking about the *history *of the system we must distinguish between the two. When Linus created the Linux kernel, it could work with the old Unix utilities, but it's the mergning with the GNU project that made it seperate from Unix and gave it the name GNU/Linux. Previously you could've had the Linux kernel and the Unix utilities, or the GNU utilities and one of the Unix kernels (as the Hurd was never finished).

> The fact that the GNU project even had to say that they were "not UNIX" means that they were, in some ways, similar to UNIX, hence the need to say that they are not UNIX. "not UNIX" here only means that they are not 100% identical to UNIX, but it doesn't mean that they don't posses any similar qualities.

No, you are misunderstanding this. While the goal was to make a system similar to Unix, and compatible with it, "not UNIX" means that it does not include any Unix code. Yes, GNU code usually does the same thing, and it does it in a similar way, but not a single line of code in it is actually from Unix.

---

### Post by Jucato on 2006-07-05
[quote=IYY]This is not even true. "Linux" is not an operating system, but a kernel. You can use the naming liberally in every day conversation if you like, but when talking about the *history *of the system we must distinguish between the two. When Linus created the Linux kernel, it could work with the old Unix utilities, but it's the mergning with the GNU project that made it seperate from Unix and gave it the name GNU/Linux. Previously you could've had the Linux kernel and the Unix utilities, or the GNU utilities and one of the Unix kernels (as the Hurd was never finished).[/QUOTE]

You also have to understand that some people, like Linus Torvalds or Linux.org, refer to the whole OS as Linux and the kernel as the Linux kernel, or just "the kernel". Of course, Richard Stallman and some other people, would prefer to use the term GNU/Linux for the whole OS. Whether which side is right is beyond the point and a subjective matter (although historically and technically speaking RMS is, of course, correct). The point is that Linux (or GNU/Linux) is a **UNIX based** OS. 

> No, you are misunderstanding this. While the goal was to make a system similar to Unix, and compatible with it, "not UNIX" means that it does not include any Unix code. Yes, GNU code usually does the same thing, and it does it in a similar way, but not a single line of code in it is actually from Unix.

No one, not me at least, ever said that being UNIX like or UNIX based meant that it contained UNIX code. When I said "similar to UNIX", I meant it to mean that it behaves/functions like UNIX, not that it has similar code. If you followed the link I gave about being Unix like, it says:

> A "**Unix-like**" [operating system]("http://en.wikipedia.org/wiki/Operating_system") is one that behaves in a manner similar to a [Unix]("http://en.wikipedia.org/wiki/Unix") system, while not necessarily conforming to or being certified to any version of the [Single UNIX Specification]("http://en.wikipedia.org/wiki/Single_UNIX_Specification").

And that specification/standard is POSIX:

> **POSIX** is the collective name of a family of related [standards]("http://en.wikipedia.org/wiki/Standardization") specified by the [IEEE]("http://en.wikipedia.org/wiki/IEEE") to define the [application programming interface]("http://en.wikipedia.org/wiki/Application_programming_interface") (API) for software compatible with variants of the [Unix]("http://en.wikipedia.org/wiki/Unix") [operating system]("http://en.wikipedia.org/wiki/Operating_system")... POSIX has been [backronymed]("http://en.wikipedia.org/wiki/Backronym") to **Portable Operating System Interface**, with the **X** signifying the Unix heritage of the API.

---

