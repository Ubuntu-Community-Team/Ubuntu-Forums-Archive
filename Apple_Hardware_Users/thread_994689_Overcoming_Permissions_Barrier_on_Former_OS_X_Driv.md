---
title: "Overcoming Permissions Barrier on Former OS X Drive"
date: 2008-11-27
forum: Apple Hardware Users
---

### Post by DrewT on 2008-11-27
I have a 250-gig drive in my Ubuntu machine that was originally used to offload data from a G4 running OS X. Because of my ignorance of  permissions hell, I stuck the drive in my Ubuntu machine without doing anything to make the G4 data accessible. I've been happily using the free space for months, but now I want to move those old files onto an external drive so I can format the whole 250-g drive as a Linux drive. Many of the files are unreadable with their current permissions, and therefore can't be moved. Is there a way to overcome this without pulling the drive and putting it back in my Mac? E.g., sudo Nautilus? (And if so, how exactly do I do it? The more elementary the instructions, the better -- I've made several attempts to fathom dealing with permissions at the command line level and I've come away with my head spinning every time.)

---

### Post by DrewT on 2008-11-27
I installed the gksu plugin for Nautilus (as described in the lengthy thread [here]("http://ubuntuforums.org/showthread.php?t=820564")). It installs a context menu in Nautilus that allows you to "Open [file or folder] as Administrator." This proves to be an awkward way to move files -- you have to open both the source and target folders as administrator, and it spawns extra windows along the way. The workspace rapidly becomes so cluttered with windows that you can easily lose your way (and perhaps make a mistake). 

But it works -- as long as none of the files you're moving are in the top directory of the source volume. The Open as Administrator option is not available when a volume is selected. So I'm still working on a workaround for that. I tried using sudo cp in the command line, but since I named these files in OS X I paid no attention to Unix naming protocols and Terminal refuses to recognize them as filenames. Is there a command syntax that will get around that problem?

Not sure it will do any good to post this here, but I'm having trouble understanding why permissions should be so rigidly enforced if all the user wants to do is move a file, as opposed to opening it. I guess it slows down a would-be spy who's trying to dump my files onto a thumb drive for sale to my competitors, but geez, this is my home computer here.

---

### Post by DrewT on 2008-11-27
Progress report ... (This seems to be a monologue but perhaps some future user will find it useful.)

I am able to move files using the Open as Administrator menu option so long as I stay within the window that opens with that command. I cannot (or cannot reliably) move files to another window, even if I also opened that window as administrator. At least I think this is the solution to the problem I last described. I am indebted for it to [this page]("http://www.psychocats.net/ubuntu/permissions"), which is one of the best-written bits of Ubuntu documentation I have yet come across.

---

### Post by cyberdork33 on 2008-11-29
you should be able to open two root nautilus windows and move files between them. Once they are moved to another partition, you can set the permissions differently.

just hit ALT+F2 and run 'gksudo nautilus' two times and there will be two windows. You can drag and drop freely between them.

---

