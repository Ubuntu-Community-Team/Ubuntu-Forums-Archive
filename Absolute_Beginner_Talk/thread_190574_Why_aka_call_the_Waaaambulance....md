---
title: "Why? aka call the Waaaambulance..."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by SC23 on 2006-06-06
First off.. many many props to the Ubuntu crew.. this is my second tip-toe into Linux.. last time was a few years ago (Mandrake) and the LiveCD thing was really really nice.. props and kudos..

Im an old fart. I cut my teeth on DOS 4.0. I actually work at a University supporting around 100 XP machines, a couple 2k3 servers.. etc.. so Im not a total n00b/idget.

There are a LOT of things I really like about Ubuntu... too many to list even though Ive only had it up and going for a few days now, however, I do have a pretty big whine.

As I go through the things that are important to me and search the forums for solutions and such, I continually see posts like this..

:: snip ::
> 
Herez how to install it:
first download the compressed file from a mirror of your choice:
Code:

[http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.3.tar.bz2?download](http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.3.tar.bz2?download)

Now do the following:
Code:

sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev make manpages-dev autoconf automake1.9 libtool flex bison gcc

Next do the following:
Code:

sudo perl -MCPAN -e 'install Bundle::LWP' sudo perl -MCPAN -e 'install Crypt::Simple' sudo perl -MCPAN -e 'install XML::Simple' sudo perl -MCPAN -e 'install Crypt::SSLeay'

All the above commands will configure your system and ask a bunch of simple questions which should be easy enough to answer (in my case almost all of them were defaults). They will install the perl modules.
Now do the following:
Code:

tar -xjf checkgmail-1.3.tar.bz2

:: snip ::

Why? Why oh why oh why...
To be honest, yes, I *could* learn it but I really really dont have the wanna-do-its. Yes, Im spoiled, yes Im lazy, yes Im a worthless piece of windows lazy crap I suppose.. still.. these solutions are pressing at best for mid-level users and I would think completely out of the question for the majority of the type of people I support.

Is it that there are so many divergences of the OS that it requires system-level terminal interactions to perform some of these solutions? And if so, does that mean that the community in general *requires* a more advanced PC user to fulfill  its mission of useability?

So theres my first whine on Ubuntu... My personal jury is still out as to whether this is in fact my savior from Vista as I am genuinely scared from a DRM/intrusive standpoint however overall I must say the things that work out of the box, apps and functionality are very very good so far..

---

### Post by Jason_25 on 2006-06-06
There is nothing to learn from those commands unless you want to.  You just copy and paste into the terminal.

The standard install process is to download a deb, right click it, choose install, and go.

---

### Post by bluenova on 2006-06-06
Or just:

sudo apt-get install gmail-notify

It'll give you something simlar without all that messing about

Or even easyer

Goto >Administratyion >synaptic package manager
search for gmail-notify
Right-click it and select 'install'
then click apply and your all set.

---

### Post by adwait on 2006-06-06
You don't need those commands to do those things. Either use Synatpic, select the program you want to install hit apply and you are done. Alternatively, download the file, right click and click install. That's all. People give the commands on the website because its easier for us to just give the command than explain how to do it with GUI. And its easier for the person to just copy paste instead of having to understand exactly what to do.

---

### Post by SC23 on 2006-06-06
I guess my post was a little unclear as I appreciate the insight into how to get the gmail checker thing working.. dont get me wrong.. but this was a more general issue with the requirements of terminal commands to complete some installations and functionality.. like my windows not mounting, etc.. (which I * did * go ahead and terminal command/fstab edit to make work)

I guess the real question is this..
Can everything be done gui if you wanted to?

---

### Post by [S|G] on 2006-06-06
Actually, it can be done using a gui. GParted should do the trick of mounting and unmounting, as well as changing filesystems and stuff. The thing is, the *standard* way to do things on *nix, historically, has been the terminal. There are apps to do most things in a GUI-based way, but they are either:

- Not as powerful and flexible as the terminal. But that also happens on windows; admin-oriented tools have CLIs that outperform their GUI counterparts
- Not standard. Meaning: different distros/desktop managers use different tools.
- Possibly not included by default.

Microsoft, like it or not, has gone a long way into software integration. I believe that currently linux distros are also moving towards that integration.

---

### Post by steve.horsley on 2006-06-06
[QUOTE=SC23]Im an old fart. I cut my teeth on DOS 4.0.[/QUOTE]
That makes you a youngster, still wet behind the ears.> 
I guess the real question is this..
Can everything be done gui if you wanted to?
No. GUI utilities exist exist for common operations, especially user operations, but to really get under the skin you need to go command-line. In the same way that regedit is needed to get at detailed windows configs, you sometimes need to bypass the GUIs and get closer to the real truth. Also, unlike windows, most GUIs are only a facade over a command-line program. And it's much easier to post a few brief commands than to post a series of click this, find that instructions, possibly with supporting pictures.

As for installing, generally use synaptic. I believe it's quite an ordeal to compile programs from source in windows too - somewhat more than it normally is in Linux. Of course, you wouldn't know that because in the proprietary world, nobody distributes the source code anyway.

---

