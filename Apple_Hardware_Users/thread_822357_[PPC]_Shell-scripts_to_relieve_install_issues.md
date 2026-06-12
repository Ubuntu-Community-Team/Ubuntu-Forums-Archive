---
title: "[PPC] Shell-scripts to relieve install issues"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by stream303 on 2008-06-08
Here's a thought to help out new users faced with xorg.conf and yaboot.conf editing - maybe we can come up with some shell scripts or maybe just simple sed / awk one or two-liners that can be issued at the cli after the second-stage yaboot boot: prompt based on the specific model specs?

I guess that means that the guy that suggests it has to write it. :)  I might take a stab at it, but wonder if there are any shell script gurus out there that might want to take on a project like this?

I suppose the yaboot.conf scripts might only consist of changing the "append=" line, and xorg.conf for at least the right horizontal and vertical freqs etc, and leave the other tweaks alone - the user can then apply that themselves once their system is actually usable.

I guess you could say I got a little inspired by me recent foray into Knoppix.  Now that would be cool, a PPC Knoppix!

Back on track, any thoughts on automated shell scripts or one-liners to ease installation woes?

#1 To help avoid abuse would be to make them simple enough for peer-review, and the standard warning to users that you should *never* run any posted script or command unless you know what it does.

---

