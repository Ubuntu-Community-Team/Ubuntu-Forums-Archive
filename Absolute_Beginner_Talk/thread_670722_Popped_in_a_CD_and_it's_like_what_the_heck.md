---
title: "Popped in a CD and it's like what the heck"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by joshlemer on 2008-01-17
Ubuntu 7.10

I popped in a CD and it's not working on any of my audio apps. It's recognising there's a cd, and and it has all the names but it's not playing. For example, in Rhythmbox music player, whichever song I click on there appears a red circle with a horizontal white line just to the left of it. In sound juicer cd extractor, a window comes up with that red circle again, saying :

Error Playing CD,
Reason: Resource busy or not available

Then another window comes up with that same red circle with the white line saying:

Error playing CD.

Reason: Internal GStreamer error: state change failed.  Please file a bug at [http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer](http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer).

Sound Concerter says this when I try and double click audio CD in the window that pops up when you select "ADD FOLDER":

The folder contents could not be displayed
VFS error: Invalid parameters

So yeah I was just wanting to know how to do that. I bought a book about Linux, specifically Ubuntu 7.04(couldn't find a 7.10), it said this about installing MP3 support for audio apps:

The easiest way to install playback and encoding support for just about any format, and for most of the applications I will be discussing in this chapter and throughout the book, is via Automatix(Applications>System Tools>Automatix). Once Automatix is open, click Codecs and Plugins in the left pane of the window and then check the boxes next to AUD-DVD Codecs and Multimedia Codecs in the right pane. Once you've done that, click the start button at the top of the window, and the download and installation processes will begin. Be forewarned that this is a somewhat hefty download, so have a little patience at hand if your internet connection is a slow one.

That's all fine and dandy but in Applications>System Tools, there IS NO automatix!! Oh boy! I don't know if it's because the book was written for 7.04 or because I just am doing something wrong, but I'm really confused.

By the way the book is:

UBUNTU FOR NON-GEEKS 2ND EDITION
a pain - free, project - based get - things - done guidebook by Rickford Grant.

---

### Post by sumguy231 on 2008-01-17
Automatix is a rather controversial third-party utility which installs nifty things but isn't necessary and (allegedly) may break things. You can accomplish the same thing in Gutsy by installing the ubuntu-restricted-extras package in your package manager or like this:
```
sudo aptitude install ubuntu-restricted-extras
```
(Make sure you have Mulltiverse enabled in software sources. Ask for more details.)

I don't know anything about Rythmbox but in the time being until you get it fixed you might try Amarok which is a great media player and uses a different engine so might actually work.

---

