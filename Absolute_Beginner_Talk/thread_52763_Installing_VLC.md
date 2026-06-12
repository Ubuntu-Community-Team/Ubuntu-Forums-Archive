---
title: "Installing VLC"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by whodat on 2005-07-28
Sup peoples,

I downloaded VLC its in a tar.gz file on my desktop, there is a lot of questions regarding downloading apps and how to install, but Im not getting the idea.

If I cant get an app throught app-get, then what should I do?

Sorry if this is a redundant question, but Im not getting this.

---

### Post by Xian on 2005-07-28
VLC is avaiable in Apt via the universe repository.
Just enable the [Extra Repos](http://ubuntuguide.org/#extrarepositories).

---

### Post by Sam on 2005-07-28
You must [add extra repositories](http://ubuntuguide.org/#extrarepositories), then open Synaptic (in System, Administration menu), and search for VLC. Synaptic is the interface to add new programs. You only need to compile from the source if it's not available in Synaptic or if you want to do some code modifications.

---

### Post by Declan on 2005-07-28
I'm not sure exactly what repository it is in, but I suppose that if you open Synaptic (in the System>Administration menu), and then go to Settings>Repositories and activate the two repositories that are listed there, but are unmarked ("universe" and "multiverse"), and then go to "Search" and type "vlc" into the space, it'll bring up the file(s) in question.  Select, and press "apply".  That should do it.

If you have the repositories enabled, all you have to do in the terminal would be:
"sudo apt-get install vlc".  Note: it is "apt" and not "app".  Advanced Package Tool, I think, and not APPlication.

Did it work?

Declan

---

### Post by Sam on 2005-07-28
3 answers in 2 minutes, 5 minutes after the first post... That is good support !

---

### Post by whodat on 2005-07-29
Thanks guys for the help.
I just back from work and tried what you advised by adding the extra repositories and it installed perfectly.

Thanks a lot again.

---

