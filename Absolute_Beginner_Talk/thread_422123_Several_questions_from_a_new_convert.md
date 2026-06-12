---
title: "Several questions from a new convert"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by episodic on 2007-04-24
Ok - I have the 7.04 version.

In the last 3 days I've deleted windows. Figured out how to get my pixma printer working, configured multimedia, etc and have a perfectly good system running.

Is it safe to install KDE apps if you are not using KDE? I wanted to install KDE office to play around with it. Any problems here? I'm windows shy and don't want to mess my system up by installing and uninstalling stuff. Give me some hints about what you can and can't do. . .

The other thing. For the life of me I can't get my LIDE 20 scanner working. I did my research and found this to be a working scanner. It just doesn't work. Help.

Are the read write ntfs drivers safe to use? Thanks for comments here.


Ok  I have 2 harddrives. One is the main 200 gig harddrive that ubuntu is installed on. Before I installed ubuntu, I backed all of my files up on the 2nd 80 gig harddrive (ntfs). I like to keep my photos in two places at once. I use to use syncback on windows. How can I back my photos up effortlessly. I've already copied them to /home. I would like to leave the 2nd harddrive as ntfs should I ever find myself in a pickle and need to read it from windows. What are your suggestions?


Are there any photo programs I should be aware of? 

Under windows I used .8bf adobe plugins with gimp - can I do this under linux?

Finally - are there any good easy to use (non - command line) slide show apps to make slideshow video files from pictures?





TIA!

---

### Post by Wake Rider on 2007-04-24
> **episodic said:**
> Ok - I have the 7.04 version.

In the last 3 days I've deleted windows. Figured out how to get my pixma printer working, configured multimedia, etc and have a perfectly good system running.


Some minor things. I was trying out some software. One was checkgmail. I tried it, realized it only checked one account and uninstalled it. I can't for the life of me figure out how to remove it from the launcher menu - so under applications - internet - there is still the icon for check gmail. I tried reinstalling and uninstalling. I looked under system menu and didn't find it there either. So, how do I remove that?


The other thing. For the life of me I can't get my LIDE 20 scanner working. I did my research and found this to be a working scanner. It just doesn't work. Help.

Are the read write ntfs drivers safe to use? Thanks for comments here.

Finally - are there any good easy to use (non - command line) slide show apps to make slideshow video files from pictures?

TIA!

You were very brave throwing Windows away straight away!!! 

Anyway here is a link to get your NTFS Partitions mounted, both read and write:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c)

---

### Post by orb9220 on 2007-04-24
> Is it safe to install KDE apps if you are not using KDE? 

Yes I run Amarok and k3b in gnome.

> The other thing. For the life of me I can't get my LIDE 20 scanner working

At the moment scanners are brokin in 7.04 bugs have been filed wait for fix.

---

### Post by crispy_420 on 2007-04-24
What exactly do you mean by it is still there? Maybe I read it wrong but it is still in Applications -> Internet from your menu right? Did you do a complete uninstall? And you just want to get rid of it from menu? 

That can be done be right clicking on the menu at top (Applications   Places   System) and selecting edit menu. Then just go the offending entry and uncheck it. Now it shouls be gone from menu.

As far as scanner have you browsed [here]("http://www.sane-project.org/")?

Now for slide shows, here are a few tools I found via google:

[http://slcreator.sourceforge.net/](http://slcreator.sourceforge.net/)

[http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page)

I have not tried either so maybe you can and report back for other users.

Almost forgot NTFS support. It is good from what I hear and relatively safe/stable. But in my opinion, I would not trust it 100% for very critical data. But if you switched to Ubuntu all the way, why do you need it?

---

### Post by episodic on 2007-04-24
Ok, figured out the menu system. 

I downloaded and installed slccreator - it installed itself and apt took care of grabbing some 'gamba' files (runtimes I suppose). Anyway it was not installed in the menu. I went to the terminal launched it it gave errors in the terminal. It launched. Then it crased and burned. I went to synaptic uninstalled it and the gamba files.

Sigh. The other one (dvd slideshow) is command line. . .

---

### Post by episodic on 2007-04-24
BTW why isn't tuxracer in the apt repository?

---

### Post by jmagsho on 2007-04-24
> **episodic said:**
> BTW why isn't tuxracer in the apt repository?

If memory serves, it was replaced by planetpenguin-racer awhile back.   Same game, different name more or less.

---

### Post by crispy_420 on 2007-04-26
That is correct, they did change the name to that.

---

