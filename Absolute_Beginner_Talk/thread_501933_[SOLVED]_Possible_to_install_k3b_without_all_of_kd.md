---
title: "[SOLVED] Possible to install k3b without all of kde"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-07-15
just wondering if there's a possible way to install k3b without installing everything AND the kitchen sink that the repos want to install... i mean really... do i absolutely need kicker for this program... i cant find a decent lightweight cd burning app that doesnt rely heavily on either gnome or kde or both (i use xorg and fluxbox, so i try to avoid installing half of kde or gnome) so unfortunately, k3b it is (wich is a great piece of software none the less) but damn, all those dependencies... so my question ultimately is

if i download like a deb from the net somewhere do you think its possible to avoid half the crap apt wants to install, or is it likely that the deb is going to want teh exact same stuff

this wouldnt be an issue if it was just libraries, but i now have pretty much the kubuntu desktop installed on my machine for one flippin app

---

### Post by kvonb on 2007-07-15
Well that's odd, it should only install the necessary kde base libs.  I install K3B on every Ubuntu install and it has never wanted to install anything else.

Are you using the add/remove from the main menu, or via the command line?

---

### Post by FuturePilot on 2007-07-15
I think it's just one of the drawbacks of running an app from one DE in another. There should just be a bunch of KDE libs. I'm not sure why you're seeing Kicker as a dependency. I'm just seeing a big list of libs.

---

### Post by ramjet_1953 on 2007-07-15
If you want to run KDE apps on a GNOME desktop, there are core things that need to be downloaded. 

If you try to circumvent dependencies, things will not work.

I find that the convenience of having k3b and k9copy far outweigh the extra packages that have to be downloaded.

Also, once this is done, you can then also run other KDE packages like kate, as well.

Regards,
Roger :cool:

---

### Post by machoo02 on 2007-07-15
The only portion of KDE that k3b needs is kdelibs4c2a...not sure what other portion of KDE you are pulling it.  What happens when you try to apt-get install k3b?  Kicker....that does not seem right.

---

### Post by Nythain on 2007-07-15
command line and it pretty much asks for stuff i really dont want, like:
kamera, kcontrol, kdebase (bin and data), kdesktop, kicker, launchpad, a metric buttload of gnome stuff (why for a kde app i dotn know, but there's a ton of it), aspell and dictionaries (i REALLY wish that app wasnt a stinking dep for so many packages)... i mean this list goes on and on, totall it was like 90 effing packages

---

### Post by Nythain on 2007-07-15
> **ramjet_1953 said:**
> If you want to run KDE apps on a GNOME desktop, there are core things that need to be downloaded. 
Also, once this is done, you can then also run other KDE packages like kate, as well.

Regards,
Roger :cool:
not trying to install it on a gnome system, Xorg+Fluxbox...

ps... i have no need for any other kde apps, definately not kate... i just cant for the life of my find a suitable substitute for k3b... tried a few curses front ends (i love ncurses apps) but they pretty much blew, and anythign else i thought of (gnome baker, and xfburn) required an equal amount of JUNK, so i went with the best... just wasnt expecting all of kde to be installed

---

### Post by Nythain on 2007-07-15
ok, so i think i just figured out my problem... and here's a funny one, you ready for this...

i used aptitude like i always do and it just occured to me that aptitude by default im pretty sure wants to consider recommended packages as dependencies... is there a way to shut off this feature (like an aptitude conf somehwere) and or does apt-get do this also...

im so retarded at times

---

### Post by FuturePilot on 2007-07-15
Here is a complete list of the dependencies.
[http://packages.ubuntu.com/feisty/otherosfs/k3b]("http://packages.ubuntu.com/feisty/otherosfs/k3b")

Oh yeah. Aptitude might do that since it's probably pulling in the entire KDE desktop. I'd try apt-get

---

### Post by Nythain on 2007-07-16
ok, so that went much more smoothly
purged that crap with aptitude and reinstalled with apt-get, much much much smaller dependency list, like 14 or so vs the previous 90 :)

---

### Post by kuja on 2007-07-16
BUt of course, set it in /etc/apt/apt.conf. Use this to set it:
I don't use aptitude so I'm not quite sure how to set it, it will either be like this: 
APT {
  Aptitude::Recommends-Important "false";
  };

or this:

APT {
  GET {
     Aptitude::Recommends-Important "false";
  };
};

For more info read the manpage for apt.conf

---

### Post by machoo02 on 2007-07-16
> **Nythain said:**
> ok, so i think i just figured out my problem... and here's a funny one, you ready for this...

i used aptitude like i always do and it just occured to me that aptitude by default im pretty sure wants to consider recommended packages as dependencies... is there a way to shut off this feature (like an aptitude conf somehwere) and or does apt-get do this also...

im so retarded at times

I use aptitude all the time to install packages (including k3b) and I've never had a problem with so many extra dependencies.  Most of what you have listed are not dependencies, recommended, or suggested packages for k3b.

---

### Post by Nythain on 2007-07-16
hehe... most of them were deps, or recommended for other packages that were recommended for k3b.
like k3b recomended some kde pakcage and aptitude considered it a dep...
so
aptitude went and got all the deps and recomendations for THAT package...
wich led to
aptitude wanting to get more deps and reommendations for THOSE packages...
till it wanted to install pretty much the kubuntu-desktop (in fact i wouldnt be surprised if that metapackage wasnt a recommendation thrown in there somewhere)
but i did get it all figured out... ill just have to be more carefull how often i thrwo around aptitude vs. apt-get

still looking for a functional lightweight alternative... all i really need to do is burn data cd's full of mp3's (for my mp3cd player)... i know i can do it command line, but ls'ing through hundreds of directories and typing out hundreds of filenames in one command line is a bit tedious... tried tcdr or whatever, it wouldnt run, and cdw but it wouldnt burn the stinkin cd...

---

