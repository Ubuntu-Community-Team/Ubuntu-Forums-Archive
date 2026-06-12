---
title: "How is Linux so Secure?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by t-nine on 2007-04-29
I just wanted to know how Linux is so secure?

---

### Post by riminicat on 2007-04-29
Who would waste there time hacking into linux, and making virus's for it?

---

### Post by Iceni on 2007-04-29
Well, there are several reasons. One of them is the idea that the used is not root (administrator). System-changing operations are not allowed until you type your root password, making it very hard for unauthorized code to change things.

Windows have actually adepted this idea with vista, but not as well imho. Feels very annoying.

---

### Post by Findoo on 2007-04-29
Many people actually, if you consider that it is used on servers alot, hacking linux can gain alot of information. The simple answer to your question is that it's opensource, and not windows. Because the opensource community work together and release regular patches, the code is more up to date. Windows is only unsecure because they own something like 90% of the market, and are full of holes due to the fact that its closed source, therefore people who notice bugs cannot fix it themselves.

---

### Post by lepz on 2007-04-29
This is pretty good [http://www.theregister.co.uk/security/security_report_windows_vs_linux/]("http://www.theregister.co.uk/security/security_report_windows_vs_linux/")

---

### Post by 3rdalbum on 2007-04-29
Also, Linux doesn't treat a file according to a "filename extension" like .jpg or .exe.  It actually treats it according to what's actually in the file. Try taking a text file and putting a ".mp3" extension on it, then double-clicking it. Gnome warns you that it's not an MP3, that it's actually a text file. Features like this can decrease the probability of maliciously-crafted files which can cause attacked programs to execute code.

The other big thing is the execute permission. If you download an executable file from the Internet and then try to double-click it, it won't run - permission denied. If you want to run it, you have to assign it execute permissions. This stops many "Windows user"-style attacks where a user is sent "Angelina Jolie NUDE!!!.jpg.exe" through e-mail, and then the user runs it. Because if a user knows so little about computers that they will run such an obvious virus, they're not likely to know enough to make the file executable in the first place!

---

### Post by gilgongo on 2007-04-29
I don't think GNU/Linux has anything that makes it inherently more secure than Windows. Yes, permissions are generally better managed, and memory use is arguably more secure on some systems. But malicious use of a system (these days) involves rather more sophistication than even a strict permissions model would prevent. There's nothing about Linux that can prevent exploits occouring if the system is unpatched, for example. The same applies to Windows. At the end of the day, Windows has a higher profile - therefore it is in effect less secure.

---

### Post by az on 2007-04-29
> **gilgongo said:**
> At the end of the day, Windows has a higher profile - therefore it is in effect less secure.

I dissagree.  Linux is a high-profile target in the server space, and that would be a more profitable and less tedious target than individual desktops.  Linux holds it own in terms of a favorable security record when compared to similar sized deplyments.

It's hard to compare server security to desktop security, since you can run apache and PHP on a windows mache, and lots of people do.  Php is the least secure portion of the LAMP server stack, but is nevertheless a very popular part of running a database-driven website.

So is a GNU/linux desktop more secure than a windows desktop?  I think so, and it has nothing to do with marketshare.

Windows is binary compatible with itself.  That obliges it to have to work around a lot of problems instead of actually fixing them.  The free-libre open source method of developing software is not binary compatible, but source compatible.  This is a pain, since you as a user usually have to compile from source to get the latest version of something to work you your system (your system was compiled with a different toolchain than others, which makes it not binary compatible)  But, your distribution is what is responsible for providing you with a binary version of packages.

This means that there is a centralized repository of software and that not just anyone can upload stuff there.  This provides a layer of security.  Since the software in the reposities are send there in source form, it is very hard for someone to conceal any malware without getting discovered.

Another advantage of the compatible-on-the-source-level but not binary compatible is that the software can adapt very quickly.  Many people credit the flexibility of free-libre open-source software to the development model.  It is like a pure form of the laws of the market.  Out of the possible solutions to a problem, the most popular one will usually prevail.  Since not one entity controls the software, this means that the software is usually what the market wants it to be, and not only what one person or company would want it to be.

Add to that the transparency of the software (you can know at all times exactly what your computer is doing and it is not a "black box" which mysteriously churns away, doing who-knows-what with your data, I would say the fact the GNU/linux is free-libre open source adds a lot to making me feel safe.

---

### Post by benson444 on 2007-04-29
Here's an interesting article:

Which was already posted by lepz. Doh!

---

### Post by kerry_s on 2007-04-29
> **t-nine said:**
> I just wanted to know how Linux is so secure?

It's not, security is a myth.

---

### Post by t-nine on 2007-04-29
Neat... So Linux should be good with P2P's?

---

### Post by bobplano on 2007-04-29
linux is also more secure because you have to know more/know what you are doing otherwise you'll most likely screw up your computer

---

### Post by LaurelLynn on 2007-04-29
Linux is secure because it is based on an os that was designed over thirty years ago with security in mind. Its primary use has till now been in multi-user systems where security has been of paramount concern. Thousands of programmers have been going over the source for decades looking for holes. It can be made insecure, especially by the user any os can, but it starts with a much stronger position.

Windows evolved from a small completely insecure base. Even when security started to be a concern, it continued to be ignored for years. Security didn't sell upgrades. Upgrades which dragged along a bunch of poorly thought out code that was left unchanged (printing and peer to peer networking come to mind). They also constantly changed and moved around the os features so that they could convince people to upgrade. Features are there one edition, gone the next, or in a new location (win98 option to install backup, XP Home Edition gone, moved to a cabnet file only opened by installing another program, reserved for XP Pro just another $100).

When I first read about the ActiveX security model over 10 years ago, I was rolling on the floor crying out "We're all doomed! The internet is doomed!"  (literally).  Then I had another rolling episode when they integrated support for it throughout their entire OS and all their applicatitions. THAT is why I believe Windows is insecure, to crush Java, they made an os that seems to open the door to internet code and says "come on in, make yourselves at home".  Ever since they have been trying to shoehorn security into the os, to make up for years of neglect.

At least that is how it lookes to me.:(

---

### Post by aysiu on 2007-04-29
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by t-nine on 2007-04-29
Wow. 
[off-topic]-And, is there any good theme sites for Ubuntu, Feisty Fawn?

---

### Post by ubuntu27 on 2007-04-29
> **t-nine said:**
> Wow. 
[off-topic]-And, is there any good theme sites for Ubuntu, Feisty Fawn?

Here: [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by t-nine on 2007-04-30
Thanks :D

---

### Post by LaRoza on 2007-04-30
I know someone who was sick of his friend saying Linux is completely so he wrote a virus for him, which randomly changed the root password.

Who needs enemies with friends like that?

The virus probably doesn't work anymore, and if it where unleashed on the internet I bet it would not last as long as the Windows viruses.

---

### Post by jrusso2 on 2007-04-30
I bet you had to run that virus as root.

---

### Post by Toufik on 2007-04-30
> I bet you had to run that virus as root.
Not specially, you can do that with a buffer overflow. You tell the chip you need 1ko of memory to store whatever you want but actually use more! The extra-byte might be something to can be nasty :)
See [http://en.wikipedia.org/wiki/Buffer_overflow](http://en.wikipedia.org/wiki/Buffer_overflow)

---

### Post by LaRoza on 2007-04-30
I just know it was an email attachment, and his friend clicked on it.

It was Fedora core 5, I believe.

---

### Post by az on 2007-04-30
> **jrusso2 said:**
> I bet you had to run that virus as root.

The permissions model is not the be-all and end-all of security.  A vulnerability is something that can allow someone to escalate their priviledges and do things as root.

One example is a buffer overflow.  Another example is sloppy use of temporary files.  If you can predict what temporary file will be used by a process with root priviledges, you can create that file yourself and try to make the root process do stuff for you.  One clever method of crashing a system is to create symlinks to important files.  If a root process wants to write to a temporary file, but that file already exists and it's a symlink to /sbin/init or something, you have a crashed machine since the root process will overwrite the symlink target with whatever was supposed to go to the temporary file...


I'm sure there are plenty ways to get things done on a system without actually being root.

---

