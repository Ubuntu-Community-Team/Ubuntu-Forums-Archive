---
title: "Cant seem to install Warsow game"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by darkchest on 2007-01-16
I cant seem to start/install Warsow.  I downloaded it from the website, then extracted it.  From my search they say i should just double-click warsow and it would work, but mine just asks me if i want to RUN, RUN IN TERMINAL, OR DISPLAY.  None of the options seem to start the game.

From the wiki on the website, they talk about 'emerge' command, but the terminal says it doesnt recognize the command.  They also refer to the Gentoo distro, i dont know if that has anything to do with y it is not working.

If there is anybody who can help me out, i would highly appreciate it.  I have searched, and there is nothing i could find that helped me.  And if it had anything to do with the hardware requirements, how can i view my hardware components from ubuntu.

---

### Post by monkeydust on 2007-01-16
Hi darkchest

Not familiar with Warsow game, but will try and help.

What files are in that .tar.gz? (would download it myself, but it's 76mb big!)

Cheers

David

---

### Post by darkchest on 2007-01-16
warsow, warsow.freebsd_i386, warsow.i386, warsow.x86_64, wsw_server, wsw_server.freebsd_i38g, wsw_server.i386, wsw_server.x86_64.

Folders: basewsw, docs, libs

i have a amd64 by the way.

---

### Post by monkeydust on 2007-01-16
Ok I'm afraid I've not got a lot of ideas here.

Have you tried going to the terminal, entering the folder and typing

./warsow

?

How does it fail in the terminal - what message?

---

### Post by darkchest on 2007-01-16
when i type ./warsow, this was the reply.

./warsow.x86_64: /lib/libc.so.6: version `GLIBC_2.4' not found (required by ./warsow.x86_64)

---

### Post by monkeydust on 2007-01-16
Ok -- sounds like its missing a dependency

Power up Synaptic and install GLIBC 2.4

(sorry, not near an ubuntu machine right now, so can't look myself and give you more info)

Let me know how it goes

---

### Post by darkchest on 2007-01-16
Now im finding it hard to install GLIBC-2.4....It is not listed in the synpatic package manager.   I tried the sudo apt-get install glibc-2.4, it says not found.

i downloaded it from a site and there was a file that said configure.  so i typed ./glibc-2.4/configure... and this was the message it gave

checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for gcc... gcc
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... /lib/cpp
configure: error: C preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
signax@Signax:~/Desktop$ cd warsow/

i dont know wat the error is talking about.

---

### Post by monkeydust on 2007-01-16
"failed sanity check" ! I love *nix error messages. Especially the "printer on fire" error :-)

Sorry, it's late and I've got to get up early.

I've bookmarked this thread so I'll pick it up again tomorrow after work, if noone else has fixed it in the meantime.

I'll try installing Warsow for myself to see where it's going wrong for you.

What Ubunutu ver. are you running?

Night

David

---

### Post by darkchest on 2007-01-16
I am using Ubuntu Dapper.

 So see u 2mrw.  thx a lot for everything.

Night

---

### Post by Ragazzo on 2007-01-17
I just downloaded the game myself and it seems you don't need to compile anything. But you need to install the dependencies. For GLib-C, I'm not sure but I think the package name is libc6 in Synaptic.

---

### Post by darkchest on 2007-01-17
I checked my synpatic and found that libc6 was already installed.

---

### Post by monkeydust on 2007-01-17
Hi darkchest

Sorry can't help after all -- it won't install due to my graphics card.

Just a couple of last checks:

In Dapper, the LIBC6 may be too old (ver 2.3?) - No idea how to fix that? Perhaps force a refresh of the packages in synaptic and see if a newer one shows? If my memory serves me right it was complaining about not seeing version 2.4 ?

Now I'm no expert, but this page seems to suggest that Edgy has the required library:

[http://packages.ubuntu.com/edgy/libs/libc6-amd64](http://packages.ubuntu.com/edgy/libs/libc6-amd64)

Can someone confirm -- Am I reading that right? 

If so, maybe time to do an upgrade? (but backup!!)

Good luck!

---

### Post by darkchest on 2007-01-17
Thank you very much David....

I noticed that i have been installing stuff i dont even know are helpful or not.  Is it possible that later in my growing knowledge of ubuntu, i would be able to uninstall stuff (like how anything u install in Windows shows in the control panel).  I say this bcos these programs i install are not really application packages, so how would i know if i need it or not.

---

### Post by darkchest on 2007-01-19
Is there any requirement to let Warsow work.  If no solution, is there any cool 3d game that can be installed with a little more ease

---

### Post by moeFinley on 2007-04-07
[Nexiuz]("http://www.alientrap.org/nexuiz/")  :)

---

### Post by macbuzz on 2007-11-21
Warsow is in the multiverse repository.

sudo apt-get install warsow

---

