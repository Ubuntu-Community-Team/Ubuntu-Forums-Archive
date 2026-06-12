---
title: "MOL on Hardy Heron"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by mfox on 2008-05-25
Almost a year after [this thread]("http://ubuntuforums.org/showthread.php?t=565388"), I attempted to get MOL running on my PowerBook G4 Al with Tiger/Hardy dual boot. I followed frog_pilot's instructions, up to the svn command, but at the one prior, the result ended with "Checked out revision 145." When I then tried the autogen, I got:

Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed

That's as far as I got. Any suggestions?

---

### Post by frog_pilot on 2008-05-25
did you install the suggested developer-packages?

look at the mol website if the hardy-kernel is already supported.

try the mol version from the ubuntu repos (synaptic). Almost a year ago I used 7.04. the feisty mol packages were totally outdated, thats why i had to compile my own version.

But at this time I was stuck at making **wired** network available for osx in mol and sharing data between ubuntu and osx. i didnt find a way to mount a linux partition to write on it from osx-mol.

since this time i frequently restart my system. :popcorn:

---

### Post by mfox on 2008-05-25
I did install the developer packages you suggested in that older post.  Unfortunately, there doesn't seem to be an up-to-data MOL website, and there is no mention of Hardy on the Source-Forge site.  I also tried installing MOL from Synaptic (Hardy repos). It would install MOL, MOL Linux driver and MOL OS9 driver but not the MOL OSX driver due to a dependency problem.  You have to configure MOL with the startmol command.  The startmol-x command won't work because the driver isn't configured, but when I issue the startmol command, I get vertical lines on my screen as well as a stall.  But I wonder if the problem isn't the lack of a config file - ironically there is one for osx, but not os9; at least I didn't find one.

---

### Post by mfox on 2008-05-27
I just did a package update and then tried once again to configure MOL with the molvconfig command.  This time I got the same stalled screen and lines all over my display, but when I recovered, I noticed the following command on the Terminal: "Running MOL video configurator on VT9" followed by a blinking cursor.  Many minutes later, I got the Bash $ back.  Unfortunately, when I ran startmol I still got a message "no video modes have been configured. Please run molvconf ....".  Does the VT9 message give a clue as to what I can do to make this work?

---

### Post by ayenack on 2010-04-13
Has anyone got MOL to work and if so can you put an how-to up for me.

I'm running 9.04 on a PowerBook G4 12" 1.5GHz

Thanks for any help.

---

### Post by mfox on 2010-04-14
I don't know if this helps any, but I never did get MOL to work on Ubuntu back in 2008.  In the end, I gave up on PPC Ubuntu for that reason, and found two other distros that it worked on: Debian Lenny and openSUSE 11.0.  I have since relegated my PB G4 to just making PowerPoint presentations, and I don't use the distros on it anymore.  What I do remember was that with those two distros, I didn't have much trouble getting MOL to work.  I found good instructions on the net and just followed them.  Perhaps whatever Debian did to MOL to make it work with the "newer" kernels (2.6.27 at the time) was picked up downstream by PPC Ubuntu.

Good luck with your project!

---

