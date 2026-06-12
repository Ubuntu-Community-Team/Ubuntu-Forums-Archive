---
title: "Console Editor (or IDE) for C++ Projects"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by control_guy on 2008-03-17
Hello

I would like to know if there is a console-based editor (or IDE) for C++ projects with syntax highlighting, symbol search, etc. At the moment, I am using **nano** but it is getting difficult as the project grows. 

Mostly I work on Ubuntu Server, so I do not have and also do not want to install a gdm/grahpics front-end.

Can someone kindly suggest something?

Regards,

control_guy

---

### Post by jordanmthomas on 2008-03-17
vim or emacs may be what you want, but you'll need to do a lot of learning.
Also, there's a way to have nano use syntax highlighting, and it has very basic search functions (ctrl -w)
[http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting](http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting)

Good luck.

---

### Post by control_guy on 2008-03-17
Thank you jordanmthomas. I think I am leaning towards emacs. I just read on a website that once you have learnt it well, the productivity is comparable to using visual studio or eclipse.

I think I have some time on my hands to learn a good tool.

---

### Post by control_guy on 2008-03-17
I am really liking emacs. What an editor!! 
The doctor feature is good too :)

---

### Post by DrMega on 2008-03-17
Code::Blocks is the best I've seen. It has syntax highlighting, intellisense style code completion, a project outline view.

The downside is it isn't in the repository, but if you do a quick google for it, you'll find it has .deb files specifically packaged for Ubuntu.

---

### Post by Junglizer on 2008-03-17
> **control_guy said:**
> I am really liking emacs. What an editor!! 
The doctor feature is good too :)

I see you've chosen your path... Be wary of the rift that causes separation between *nix users.

---

### Post by raul_ on 2008-03-17
> **Junglizer said:**
> I see you've chosen your path... Be wary of the rift that causes separation between *nix users.

Too bad he chose the path of the dark side.

Just kidding :popcorn:

---

### Post by Junglizer on 2008-03-17
> **raul_ said:**
> Too bad he chose the path of the dark side.

Just kidding :popcorn:

I prefer Vim myself but chose to keep my mouth shut. I kind of see Vim as the "darkside" if nothing other then its -fg white -bg black by default, well in console.

---

### Post by control_guy on 2008-03-17
> **DrMega said:**
> Code::Blocks is the best I've seen. It has syntax highlighting, intellisense style code completion, a project outline view.

Is Code::Blocks console based? Can I run it without any graphic support?

Thanks.

---

### Post by DrMega on 2008-03-17
> **control_guy said:**
> Is Code::Blocks console based? Can I run it without any graphic support?

Thanks.

No. Sorry I didn't read your post properly (can't have had enough coffee at the time). I missed the bit where you said you wanted a console based solution.

Code::Blocks has a nice GUI, which unfortunately means you can't run it with gdm.

Out of curiosity, what is your aversion to installing a GUI? Is it a resource issue? the xubuntu-desktop package will install Xfce all nicely configured up for you, all in one command, and it doesn't use much in the way of resources.

---

### Post by jordanmthomas on 2008-03-17
> **DrMega said:**
> doesn't use much in the way of resources.
Not much for a desktop system, but for a server it can be a lot.
For instance, when I first boot my computer it uses 23 MB of RAM.  Once I load X (and I only use awesome window manager, nothing heavy) I am already up to about 150 MB (I have an integrated graphics card that steals 128 MB of RAM :( )
It can really be a significant difference.

---

### Post by control_guy on 2008-03-18
> **DrMega said:**
> Out of curiosity, what is your aversion to installing a GUI? Is it a resource issue? the xubuntu-desktop package will install Xfce all nicely configured up for you, all in one command, and it doesn't use much in the way of resources.

There are two main reasons:

1) The first is resource constraints, as also mentioned by jordanmthomas. I have only 256MB RAM and a 1GHz processor. The server runs some come computationally intensive real-time control tasks. A graphics system seems really unwanted here.

2) The server sits without any keyboard, display, mouse. No local man-machine interface. I always access it remotely through ssl. If I install a display manager, I would need to get into VNC-like stuff. Thats the last thing I want to get into.

Regards

---

### Post by DrMega on 2008-03-18
> **control_guy said:**
> There are two main reasons:

1) The first is resource constraints, as also mentioned by jordanmthomas. I have only 256MB RAM and a 1GHz processor. The server runs some come computationally intensive real-time control tasks. A graphics system seems really unwanted here.

2) The server sits without any keyboard, display, mouse. No local man-machine interface. I always access it remotely through ssl. If I install a display manager, I would need to get into VNC-like stuff. Thats the last thing I want to get into.

Regards

Ok. That makes a lot of sense.

Personally I would never develop directly on a production server, especially with a language as low level as the C family of languages (which allow you to very quickly and easily bring down a whole system, thanks to the super efficient "the developer knows best" approach to memory access.

If it were me, I would have my desktop machine with a nice GUI, and a nice IDE where I would do all my development and testing. Write and compile my apps as console apps, and when I'm happy they work correctly and are stable, copy them across to the server for deployment.

---

### Post by Junglizer on 2008-03-18
It comes down to personal choice really, though DrMega is right about code on a production server, though you could easily jail the home for the remote user. I learned all of my in Linux running off Knoppix cd's in computers with no hdd's and saved everything to a remote server, so even now, on my personally laptop, I do everything in the console. It only gets difficult when you want to view multiple header files or something.

---

### Post by DrMega on 2008-03-18
> **Junglizer said:**
> It comes down to personal choice really, though DrMega is right about code on a production server, though you could easily jail the home for the remote user. I learned all of my in Linux running off Knoppix cd's in computers with no hdd's and saved everything to a remote server, so even now, on my personally laptop, I do everything in the console. It only gets difficult when you want to view multiple header files or something.

Limiting the folders that the remote user can see won't protect you from crashing the server, or rendering it unstable if you have a mistake in your code (which is a normal part of the development and testing cycle) that does something like writing to a sequence of bytes in memory that have not been allocated. Or getting tied into an infinte loop that hogs all your CPU time.

---

### Post by jordanmthomas on 2008-03-18
> **Junglizer said:**
> It comes down to personal choice really, though DrMega is right about code on a production server, though you could easily jail the home for the remote user. I learned all of my in Linux running off Knoppix cd's in computers with no hdd's and saved everything to a remote server, so even now, on my personally laptop, I do everything in the console. It only gets difficult when you want to view multiple header files or something.

[http://www.brain-dump.org/projects/dvtm/](http://www.brain-dump.org/projects/dvtm/)
:)

---

### Post by control_guy on 2008-03-19
> **jordanmthomas said:**
> [http://www.brain-dump.org/projects/dvtm/](http://www.brain-dump.org/projects/dvtm/)
:)

Creativity knows no bounds....Thank you jordanmthomas 

emacs + dvtm .... awesome! :)

---

