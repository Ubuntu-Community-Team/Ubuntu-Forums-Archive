---
title: "Organizing my files (not a partitioning question)"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-10-14
I've got 2 windows pcs, a feisty pc just doing fileserving and some torrents, and 2 modded xboxes.  The 3 pcs are all full of hds.  I have media all over the place.  I'd like to get organized so the pcs and the xboxes can all mount something like this:

/movies
/tv
/music

And no matter where the movies are, they'd all show up in /movies... so 
/movies would contain, for example
 d:\media\movies\ on PC1
 f:\movies\ on PC2
 /dev/hda/movies/ on Feisty
 /dev/hda1/media/ on Feisty

and so on...

then I'd just be able to mount a "movies" 'directory' as a drive on the various devices I watch the media from... same thing for music, etc.

and what I'd *REALLY* like to be able to do is just dump movies into this virtual movies directory and have the filesystem or application or whatever figure out which physical device would be the fastest place to put it (i.e., check local drives first) and then which physical device had the most room for it without me caring which device it was on

Is this possible?  Any suggestions are appreciated.  Thanks!

---

### Post by aktiwers on 2007-10-14
I think you could go to Places => "Connect to server"
And create a Windows network to the specific folder(s).

Then make a playlist in your favorite Video player for all the files.

Rhythembox can add new files from specific folders you choose it, to the playlist on startup.

But by looking around on the forums, you offen get the idea that its not always an easy task to create a network between Windows and Linux, as Windows only likes to go in network with other windows pc's.

But I dont know..  I dont use Windows.

---

### Post by MatthewPlanchard on 2007-10-14
Well, I'm totally new to all of this, so I don't know of how much help I could be.

Symbolic linking, though, seems as if it might help you out here. You could create your /movies folder and then add symbolic links to all of your actual media using the cp command with the recursive (-r) and symbolic (-s) options active.

It seems like symbolic linking would work for the files on the windows drives as well, as long as you're using gutsy and can access your ntfs partition.

I don't know if you'd be able to access those folders from Windows, though, or if you'd only be able to get in from Ubuntu.

The second part of your question is by far the more difficult one. Basically you want something that looks at each drive's unused space and saves your media wherever the highest amount of unused space is, and you want it to do so automatically when you save something to your /movies folder.

I don't know of any program that could do that. I hope someone else does. It's really a good idea.

---

### Post by randomjohn on 2007-10-14
I think the symbolic links is what I'm going to have to figure out.  That will solve the organization part from a "read" perspective, but I'll still have to be careful of where I'm storing all my media.

I've actually got all of the various physical drives mounted all over the place (feisty drives mounted on xp, xp drives mounted on feisty, both kinds "mounted" in xbox media center, etc) and can read and write from any of them, whether it's a local or network disk.  I'm pretty proud of that one; it took a while to figure out.

Playlists definitely aren't going to cut it.  I'd have to do it for every playlist and probably for every device.  It's annoying enough to have to have all the xbox media center instances scan for new content separately to get the movie and tv information.

I got the idea from something called "unraid" which is apparently some sort of linux that boots from a usb drive and allows you to have a quasi-raid with whatever physical drives you want.  It's kind of cool, but I don't want to move all the disks into one box right now.

---

