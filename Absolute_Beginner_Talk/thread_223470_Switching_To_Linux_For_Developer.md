---
title: "Switching To Linux For Developer"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by jasonkostempski on 2006-07-26
Currently I'm a Windows user/admin/developer. I am thinking about making the switch to Ubuntu and I want to ask your opinions.

1: As a developer (desktop and web), with no additional box at the moment, should I install Ubuntu desktop or server on my machine?

2: I have read the program replacement post and [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) but I'm interested in your opinions on the best programs in these categories:

A: Development language for dynamic web pages (I use ASP.NET with C# codebehind in Windows).
B: Development language for desktop (I use C# in Windows).
C: IDE for web development.
D: IDE for desktop development.
E: Database (I've heard good things about MySQL).
F: Browser (I'll most likely use FireFox).
G: Media Player (I am hoping for something that will update ID3 info and download album art automatically like Windows Media Player).
H: Image editor (similar to Photoshop).
I: Image viewer (I'm thinking of trying Picasa).
J: Virtual Machine (does this even exist?).
K: Instant Messanger (AIM connection is most important).
L: Remote Desktop to Windows.
M: Remote Desktop to Linux.

---

### Post by mlind on 2006-07-26
> **jasonkostempski said:**
> Currently I'm a Windows user/admin/developer. I am thinking about making the switch to Ubuntu and I want to ask your opinions.

1: As a developer (desktop and web), with no additional box at the moment, should I install Ubuntu desktop or server on my machine?


If you want graphical desktop, then it's probably easier to start with Ubuntu desktop. You can always add features to either install, no matter which one you choose. This means installing server packages on desktop install, and installing desktop packages to server install.

> **jasonkostempski said:**
> 
2: I have read the program replacement post and [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) but I'm interested in your opinions on the best programs in these categories:

A: Development language for dynamic web pages (I use ASP.NET with C# codebehind in Windows).
B: Development language for desktop (I use C# in Windows).
C: IDE for web development.
D: IDE for desktop development.
E: Database (I've heard good things about MySQL).
F: Browser (I'll most likely use FireFox).
G: Media Player (I am hoping for something that will update ID3 info and download album art automatically like Windows Media Player).
H: Image editor (similar to Photoshop).
I: Image viewer (I'm thinking of trying Picasa).
J: Virtual Machine (does this even exist?).
K: Instant Messanger (AIM connection is most important).
L: Remote Desktop to Windows.
M: Remote Desktop to Linux.


There's no right answers here, but my personal picks would be:

A: Java, or stay with ASP .NET. I guess you can use Mono for that.
B: Python is very nice, but again you can do C# with Mono.
C: If you mean wysiwyg editor, then I dunno. Never used one myself. Maybe bluefish? I recall mozilla had some sort of editor too. 
D: Depends on language. If you plan to develop GTKish apps, then maybe glade.
E: Postgresql is my favourite. MySQL is okay too, simpler and maybe little faster.
F: Epihany vs. Firefox vs. Konquerror
G: Amarok, Rhythmbox, Banshee, Quodlibet.. hmm there's actually quite many of there (but nothing that compares to foobar2000 :()
H: Gimp (maybe incscape too?)
I: F-spot or Picasa
J: VMWare player. Search for forums for HOWTO
K: Gaim
L: VNC. TightVNC or UltraVNC maybe?
M: Same as above

---

### Post by cilynx on 2006-07-26
My personal opinions:

A: Perl or PHP
B: C, Perl, Python
C: IMHO, all WYSIWYG HTML editors suck.  This goes for Windows as well.  I've heard good things about Eclipse
D: Best to get to know the GNU toolchain.  Anjuta is ok.  Eclipse is ok.
E: I like MySQL
F: Firefox
G: Amarok.  Think iTunes.
H: Gimp for raster, Inkscape for vector
I: I just use EOG
J: vmware-server (free, lets you make your own VM's)
K: gaim
L: realVNC
M: realVNC, but remote desktop is kinda pointless when you can just forward X over ssh.

---

### Post by jasonkostempski on 2006-07-26
Thanks guys!

Just to clarify:

For A: I did mean server side code, dynamic generation of pages.
For C: I'm not looking for WYSIWYG (Yuck!). I'm looking for something with autocomplete for server side and client side code and maybe some automatic formatting/indenting.

Some additions to questions:

A,B: How useable is Mono? I have heard it is in somewhat of a premature phase.

B: C or C++ for desktop development? Cilynx suggested C but my experience with C (very minimal and in Windows only) has been that it's somewhat archaic and not very suitable for reasonably rapid development. As a C# developer with a VB past (never going back) I was leaning more towards C++. OOP is important to me as well. "You down with OOP? Yeah you know me!"

M: Is there a Remote Desktop client that will work with the Windows built in Remote Desktop server so that I will not have to install programs on machines I don't have physical access to but am allowed RD access?

---

### Post by cilynx on 2006-07-26
A: I use Perl / MySQL for my backend work.  I use SSI quite a bit a well, mostly to beautify URLs by referencing ugly Perl from inside SSI.  I really dislike the CodeBehind development model.  That's just my opinion.  I have to use it for work.

C: Vim can do anything once you get past the learning curve.  It's pretty steep though.  If you like buttons, look at gVim.  Bluefish also has nice HTML editing.

Mono: Good for "Hello World".  Not good for "Hello World; Buy My Stuff".

M: To the best of my knowledge, Win Remote Desktop is a proprietary protocol that has yet to be reverse engineered.

---

### Post by mlind on 2006-07-26
> **jasonkostempski said:**
> Thanks guys!

Just to clarify:

For A: I did mean server side code, dynamic generation of pages.
For C: I'm not looking for WYSIWYG (Yuck!). I'm looking for something with autocomplete for server side and client side code and maybe some automatic formatting/indenting.


I've mainly done .php and JSP content. My tools have been emacs and Eclipse (with WTP plugins). Like cilynx said, Linux has some quite powerful text editors, but learning curve is quite steep.. I'm not sure if Monodevelop has codegeneration features, I doubt it. Eclipse has, and you can use for C/C++/Python too, but Mono support is on very poor state.


> **jasonkostempski said:**
> 
A,B: How useable is Mono? I have heard it is in somewhat of a premature phase.


Well, it works okay. Dunno about server-side content though. F-spot and Banshee are Mono apps that are somewhat complex and seem to work.

> **jasonkostempski said:**
> 
B: C or C++ for desktop development? Cilynx suggested C but my experience with C (very minimal and in Windows only) has been that it's somewhat archaic and not very suitable for reasonably rapid development. As a C# developer with a VB past (never going back) I was leaning more towards C++. OOP is important to me as well. "You down with OOP? Yeah you know me!"


If you adore OOP and like to do desktop stuff for linux, then maybe Pyton is good language to start with.


> **jasonkostempski said:**
> 
M: Is there a Remote Desktop client that will work with the Windows built in Remote Desktop server so that I will not have to install programs on machines I don't have physical access to but am allowed RD access?


None (free) that I know of.. I've used VNC servers that don't need admin privileges to install on windows machines.

---

### Post by lxevolution on 2006-07-30
A: I'd use **PHP**, although I never tried any editors on linux. (PHP / Ajax is getting popular)
B: **Python** definitely for linux (I like java thoguh)
C: Quanta Plus? **NVU**? I have no Idea whether they have the features you requested since i used them once and like neither. (Dreamweaver pwns)
D: I like **NetBeans** (**Eclipse,** If you want something heavier)
E: **MySQL** all the way. (PHPmyAdmin is the best tool to manage it)
F: **Epiphany** is less heavyweight than firefox.
G: **Quod Libet** - You WILL like it. You WON'T use anything else after you try it.
H: Eh. **GIMP** is no match for photoshop. I run vmWare virtual machine windows to run photoshop.
I: The pre-installed ones are good enough for viewing.
J: **VMware.** 
K: **Gaim.**
L,M: **Vnc.**

---

### Post by hugmenot on 2006-07-30
L: Of course you can connect to Remote Desktop. It´s even installed by default. Look for Terminal Server Client in the Internet menu and select RDP for the protocol.
The command line version is called rdesktop.
M: FreeNX is very (very) responsive and you can suspend the session to resume it later on. It comes with the drawbacks of third-party software that is not specifically packaged for or included in the base distribution.

---

### Post by steve.horsley on 2006-07-30
> **cilynx said:**
> 
M: To the best of my knowledge, Win Remote Desktop is a proprietary protocol that has yet to be reverse engineered.

Crowd replies: "Oh yes it has!"

I've not seen a remote desktop server, but hte client for viewing windows boxes is called rdesktop, and ships with many distros.

---

