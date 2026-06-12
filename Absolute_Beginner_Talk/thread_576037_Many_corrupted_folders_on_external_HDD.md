---
title: "Many corrupted folders on external HDD"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by NCLI on 2007-10-14
Well, I'm screwed. I plugged my 300 GB external HDD in to linux to transfer some files from XP. I access it, and realise I've forgotten some videos. I pull the USB cable out without unmounting, transfer the forgotten file from windows, plugs the drive back into myubuntu laptop, and voila; several folders are corrupted.

They are also corrupted when I try o access them from windows, and there seem to be 2 icons for my HDD on the ubuntu desktop. Here are screenshots of [the corrupted folders]("http://xs320.xs.to/xs320/07421/Screenshot.jpg") and [the extra icon]("http://xs320.xs.to/xs320/07421/Screenshot-1.jpg").

So, I guess this is where I beg for help :(

---

### Post by Gwasanaethau on 2007-10-14
Hmm. To be honest (and I don't want to trash your hopes too much), but I think you're screwed! I did it to a flash drive and had to format it to remove the trashed files. What I would do is save the files that aren't mashed onto the hard disc of one of the computers and then format the external drive. You should then be able to transfer as normal.

The moral of this story: **don't unplug a USB drive before it's finished synchronising**, ;) though you probably knew that already!

I feel for you dude, I really do!

---

### Post by NCLI on 2007-10-14
Cant say I didn't, but it's hard to break old habits after running windows for a year.

I'd hoped this would've been improved by now, but I'll hope others have more positive input :S
"Starts praying"

---

### Post by Gwasanaethau on 2007-10-14
Hehehe, tell me about it! :lolflag:

I think there's some way of getting the drive to automatically synchronise every time you move files to/from it (rather than waiting until you tell it to unmount). Unfortunately, I don't know how to do it myself. I think I might have read it somewhere in the forum before, though, in case you're interested.

(Says you: "It's a bit late now!")

---

### Post by az on 2007-10-14
Image the drive and then try to fsck  the filesystem of the image (mount is as a loop filesystem.)

Don't work on the original drive.

If that doesn't work you can always give data-carving a try - use foremost of photorec.  See [http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software)

---

### Post by NCLI on 2007-10-15
How do I make an image of my drive?

---

