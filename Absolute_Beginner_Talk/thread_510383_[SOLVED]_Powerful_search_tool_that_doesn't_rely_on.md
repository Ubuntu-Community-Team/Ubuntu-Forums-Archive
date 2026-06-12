---
title: "[SOLVED] Powerful search tool that doesn't rely on working in the background?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Shadow ZERO on 2007-07-26
I am having trouble finding a file searching tool that fits my needs.  I was trying to familiarize myself with the OS, and i figured a good place to start would be to search for different file types that i knew were either installed into the OS or on my local storage drives.

First I tried Beagle, which came installed with my distro.  After looking through my available desktop background files, and selecting one, I decided to find out where they were stored, to get an idea of where Linux typically stores various files in the file system.  I was trying to find the .jpg and .png files that came pre-installed as desktop backgrounds.

Not only did Beagle fail to find any of the files that i knew for a fact were installed as a part of the OS, but i tried to search for various other file formats using wildcards (*.txt, *.mp3, *.jpg, etc.) that i knew there are plenty of on my storage drive.  No luck there either.  After deciding that Beagle was powerless without file indexes, i figured the only way to find anything and everything i search for was to index my entire file system (everything under "/").  7 hours later, Beagle still hasn't finished indexing, and although it is SLOWLY adding files, it is far from being complete.

I also tried using MetaTracker(aka Tracker) from the Ubuntu software repository.  I am having similar results, Tracker also seems powerless without its indexes, but i could not figure out how to manually add indexes with that program.

The find command(from the console) is definitely more of what i was looking for.  Problem with that is that sometimes i need to manage the files that i've searched for, even if i return thousands of results.  The console find command cuts off many of my results, and doesn't (seem to) allow me to directly interact with the files once they are found.

I'm using Linux Mint (which I highly recommend trying if you like Ubuntu), which is compatible with all of the Ubuntu software repository, but has far more out-of-the-box capabilities.  Is there a more powerful search tool for local files which doesn't rely on slow and painful indexing?  I would prefer something that doesn't use file indexes, and doesn't rely on running in the background to constantly update said indexes.  If i am forced to index my files, I want the tool to do so quickly and powerfully, using as much of my CPU and disk speed as necessary to get the job done ASAP, and then stopping completely once the indexing is complete.  This indexing for hours, running in the background all the time BS just doesn't cut it.  Something exactly like the "find" console command, but with a robust and feature-filled GUI would be splendid.  Anything like that around?

---

### Post by rich.bradshaw on 2007-07-26
locate is good, obviously no GUI, but why does a search tool need one?

sudo updatedb

will update the database, takes a few mins. Then

locate firefox

will show you every file that makes up firefox. Quite useful really!

---

### Post by Rocket2DMn on 2007-07-26
Any fast and effective search tool needs to have an index of the files, or else it will  have to scan the whole drive every time it searches.
This is equivilant to locating a single person in the population without the use of a phone book listing.

---

### Post by Shadow ZERO on 2007-07-26
> locate is good, obviously no GUI, but why does a search tool need one?

locate firefox

will show you every file that makes up firefox. Quite useful really!

Why does a search tool need simple but robust GUI?

If i search for *.mp3, i need my search tool to do a lot more than just "show me" where my mp3 files are.  I already know where they are, if i take the time to remember.  I need to be able to manage all the files that are returned to me by the search.  If i have thousands of mp3 files across a wide variety of different folders and drives, for example, i need to be able to see where they are all located, and compare file properties, within a single, non-redundant interface.  For example, if i have 20 different versions of the same mp3 track, spread out across several different folder trees,  I need to be able to quickly compare where each of them are located, what the bitrates and file sizes are.  I need to be able to compare properties of each different version of the same track or song, and also to be able to launch the files from the search interface, so I can manually figure out which one is the highest quality, and which ones might be duplicates or corrupt, if browsing the file properties alone doesn't reveal that info.  I can't imagine any text interface that will give me all of those capabiliites, without exponentially increasing the time and effort it takes to do the same functions with a simple GUI.

---

### Post by Shadow ZERO on 2007-07-26
I don't know why I post questions in forums at all... no matter what the forum is for, or the topic, I never get the answer i need... then I figure it out myself.:redface:

The program is called catfish.  It simply provides a GUI front end for other search tools, most importantly for me, the find and locate commands from the console.  No indexing required, just a quick power search with everything i need, and nothing i don't.

Hope someone else can make use of this thread.  Thx to those that replied :8)

---

