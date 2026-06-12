---
title: "Transitioning"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by rcdeacon on 2007-10-16
Two days ago I installed the Gutsy Gibbon RC. I am currently seriously considering making a complete transition from another distro to Ubuntu. I have been a KDE user and there are some things I like with KDE but I have been somewhat impressed by what I have found with the RC. 

I am not a newbie to linux in general having been using linux off and on for a number of years but have within the last year "weaned" myself off windows completely. As I make this transition from KDE to GNOME and from another distro to Ubuntu I need help with the following: First, there is virtualization. I have been using virtual box to use a couple of windows programs that I need for my work. I would like to install virtual box and I did not find it in the repositories. There may be another alternative. Second, synchronization. I need to synchronize a Dell Axim X3 PDA. Currently I do this with virtual box using xp and outlook. I would like to become more linux focused and use evolution if it is possible. Also, I have an Apple ipod nano 2nd gen that I would like to sync. Third, is multimedia. I would like for DVD's, streaming video, streaming audio and such to be able to work. The other distro allows for most of these to work "out of the box" (excluding dvd's which require the w32 codecs).

There may be some other things but these are the most immediate. I appreciate the help and it seems at least to me that Gutsy is a GREAT improvement over Feisty which would never install or run live for me. Thanks again.

---

### Post by jayaramk on 2007-10-16
in order to use the windows aplication in ubuntu... u need a program wine.... its present in the repositories.......

or use this from the terminal

sudo apt-get install wine

---

### Post by rcdeacon on 2007-10-16
Thank you. I have actually had limited success with wine. I actually use E-sword which tends to play nice with wine and Logos Bible study software (libronix) which DOES NOT play well with wine that is why I had to resort to virtual box. I will once again try wine. Thanks again.

---

### Post by RomeReactor on 2007-10-16
Hi. VirtualBox shows here in Synaptic (System->Administration->Synaptic) also using Gutsy; maybe an update of the repository information will make them show up. Just in case, if for some reason it still doesn't show up, you can download the packages [from here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=names&subword=1&version=gutsy&release=all").

---

### Post by rcdeacon on 2007-10-16
Thanks, I didn't see it but I think I put a space between virtual and box during the search.

---

### Post by mivo on 2007-10-16
Just as a side note: If you do prefer KDE, there is always Kubuntu, too, which is also official and uses the same underlying system as Ubuntu. It's just KDE instead of Gnome. You are probably aware of this, but I figured I'd chip in this bit of information. :)

---

### Post by RomeReactor on 2007-10-16
Regarding multimedia and DVDs maybe [this]("http://ubuntuforums.org/showthread.php?t=577174") can help. If you also want the w32codecs package, you can find it [here]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb").

Optionally, you may want to enable the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu") (so you can install packages like libdvdcss2 and w32codecs through Synaptic instead of downloading them one at a time), but there doesn't seem to be a Gutsy repository yet, and I don't know if you can use the one for Feisty in Gutsy.

For the iPod, maybe [gtkpod]("http://en.wikipedia.org/wiki/Gtkpod") can help you, though I don't know if that's what you're looking for. You can find gtkpod in Synaptic.

---

### Post by rcdeacon on 2007-10-16
RomeReactor, you have been very helpful and I appreciate it. I will work on these later (time to go off to work).

---

### Post by shaft350x on 2007-10-25
I haven't gotten Libronix to work yet, but it has been a while since I actually tried, hopefully I'll have more luck next time around.

I did have pretty good results syncing my Palm0ne Tungsten|T5 with Evolution, I think like most the only thing was around "notes" but that wasn't a big deal for me.  I've since lost my sync cable and don't know if I want to plunk $30 for a new one.  This of course takes for granted that the Dell Axim is anywhere similar to the Palm, which it is not.  Just wanted to let you know that something kind of similar works and is quite a feasible option.

I've pretty much made the jump to Ubuntu myself, been a long time since I've logged into windows at all.  I kind of assumed the same was true for you, but best of luck on your continuing transition!

---

