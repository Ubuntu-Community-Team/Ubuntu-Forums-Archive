---
title: "customizing ubuntu - removing apps"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by brdohman on 2008-01-29
I am wanting to create a Ubuntu LiveCD that will be used on a public computer by public users.  To do this I am wanting to create a cd that will not allow users to use the terminal, telnet, or allow them to install new programs.  I need to make it so the LiveCD doesn't allow people to hack into the main network that the computers connect to.  I basically just want the user to be able to use the cd for these things

Run openoffice apps
Surf the internet
Use only the applications that I have installed
Not be able to use the terminal, or have telnet abilities.

The CD just needs to be very basic, not allowing advanced features that might allow the user to dig through the network, or to install any other software that could be used for hacking purposes.

I was wondering if it would be possible to create a user in my current ubuntu install, with limited abilities, and then create a livecd that will boot into that user directly, and then strongly password the root account, so it can't be hacked.  I will also need to disable access to folders on the cd, by the user (if possible) so they aren't able to access system folders to possibly launch software that i have removed from the application menu.

Any help would be appreciated, I might be making this question too hard, but am unsure about some of the ways to create this custom cd.

Thanks

---

### Post by Mark_in_Hollywood on 2008-01-29
Check out the Ubuntu Customization Kit at sourceforge:

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by corney91 on 2008-01-29
Another [link]("http://ibuild.livecd.net/") to check out.
Hope it helps.

EDIT: The Ubuntu Customization Kit looks to be more Ubuntu-oriented so you may want to go with that.

---

### Post by LRT on 2008-01-29
although this method may take a bit longer, if you want to COMPLETELY customize a linux distro i would go with LFS (Linux from Scratch).

[URL="http://www.linuxfromscratch.org/"]
http://www.linuxfromscratch.org/[/URL]

---

### Post by Mark_in_Hollywood on 2008-01-31
Since the original poster hasn't marked this thread as SOLVED, I'm giving one more link:

[http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd)

---

