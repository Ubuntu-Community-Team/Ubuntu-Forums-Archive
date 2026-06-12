---
title: "Problem in compiling file and glib"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by kukuku on 2007-05-27
Hi.

I attempted to compile a program for the first time, seeing how the Ubuntu Software Repository didn't hold Irssi in it. The INSTALL file gave directions as to:

```
./configure
make
su
make install
```

This far I can understand, but make command responded with an error.

```
make: *** No targets specified and no makefile found.  Stop.
```

It took a a little examining but it seems I have no glib installed. I copypasted one of the error lines to Google and this is what the conclusion seemed to be.

So I downloaded glib-2.12.12.tar.bz2 from the Gtk ftp, then used the commands listed in its INSTALL file. It ended up doing everything it wanted and placed me back to the prompt without error messages. Going back to compiling irssi didn't work yet, though. Make gave the following error:

```
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.12, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf.
```

From /etc/ld.so.conf I found only a single line of text, "include /etc/ld.so.conf.d/*.conf" - which I doubt I'm supposed to edit without knowing what to do. A little later I found myself editing /etc/profile with the purpose of adding these environment variables in there, but I'm not so sure this is what I want to do. First, haven't they already been assigned somewhere else? Would they just overwrite later what I put here? And secondly, it would probably need a reboot which I'd gladly avoid doing just for now.

Is there any hope left for me in compiling programs?

---

### Post by raja on 2007-05-27
Do you mean irssi ?. Because that is available in the repository.

```
raja@~>>aptitude search irssi
p   irssi                           - terminal based IRC client                 
p   irssi-dev                       - text-mode version of the irssi IRC client 
p   irssi-plugin-icq                - ICQ plugin for irssi                      
p   irssi-scripts                   - collection of scripts for irssi           
v   irssi-snapshot                  -                                           
v   irssi-snapshot-dev              -                                           
p   irssi-text                      - irssi dummy transition package 
```

---

### Post by Kobalt on 2007-05-27
Sometimes when you try to compile a program you face this situation : you have an unsatisfied dependency (GLIB - version >= 2.0.0 in your case). When it happens, just open up you package manager Synaptic and search for this package. Here you will need the package libglib2.0-0. If the package you need turns out to be already installed, then you need the -dev version of it, which means you'll be searching for libglib2.0-dev. Once you found and installed these dependencies, try the compilation again.

---

### Post by kukuku on 2007-05-27
> **raja said:**
> Do you mean irssi ?. Because that is available in the repository.

o_o;

I did check the repository, though only using the add/remove programs tool from gnome. I even tried it again, said that There is no matching application available.

The solution seems to be I'll have to learn to use that CLI version. ;)

> **Kobalt said:**
> Sometimes when you try to compile a program you face this situation : you have an unsatisfied dependency (GLIB - version >= 2.0.0 in your case). When it happens, just open up you package manager Synaptic and search for this package. Here you will need the package libglib2.0-0. If the package you need turns out to be already installed, then you need the -dev version of it, which means you'll be searching for libglib2.0-dev. Once you found and installed these dependencies, try the compilation again.

Ooooh. That one looks pretty useful. I hope the earlier installation attempts with glib I made won't make it a problem if I try to install that libglib2.0-dev library...

---

### Post by Kobalt on 2007-05-27
> **kukuku said:**
> 
The solution seems to be I'll have to learn to use that CLI version. ;)
You'd rather use Synaptic instead : System > Admin. > Synaptic Package Manager. It's a GUI for the apt-get command line tool, hence much more powerfull than Add/Remove.
You shouldn't have a conflict problem between glib and libglib2.0-dev...

---

### Post by kukuku on 2007-05-27
> **Kobalt said:**
> You'd rather use Synaptic instead : System > Admin. > Synaptic Package Manager. It's a GUI for the apt-get command line tool, hence much more powerfull than Add/Remove.
You shouldn't have a conflict problem between glib and libglib2.0-dev...

That sounds like a better option for Add/Remove Programs.

Thanks for all the advice! It all worked out in moments. :D

---

### Post by Kobalt on 2007-05-27
You're welcome.

---

