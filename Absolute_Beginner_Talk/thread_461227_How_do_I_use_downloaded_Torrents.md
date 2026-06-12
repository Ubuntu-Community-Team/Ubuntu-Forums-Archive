---
title: "How do I use downloaded Torrents?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by leo7068 on 2007-06-01
I installed Azureus.
I downloaded some torrents, but when I open them I get the following errors :

Azureus Error: Failed to access torrent file Ensure sufficient temporary file space available.

Open Error: 'file:///home/leo/Desktop/%5BisoHunt%5DNot a File0***.torren t ' could not be opened:
Not a File

Please help.

---

### Post by ajeffreys on 2007-06-01
Go into azureus, and choose open file in the file menu. Than browse to the where the torrent is, select it and press okay.

---

### Post by leo7068 on 2007-06-01
Should I take this as a general rule now: Always File>Open, because clicking files won't open the program they use?

---

### Post by kernel tom on 2007-06-01
i would just use KTorrent... you can always click files with that program,

I just don't like the way azureus works in ubuntu

---

### Post by Sethalos on 2007-06-01
One way is to make Azureus your default Torrent engine, after clicking on a torrent file  the prompt comes up; select the first option (Open With), click on the drop down box and select Other..then browse to /opt/azureus/azureus and that will make it the default, so now whenever you click on a torrent, you then just click ok when the command box comes up.

Another way is to download the .torrent file to your desktop and simply drag and drop it into the open Azureus window.

Having said that, KTorrent is much faster and in my opinion better than Azureus.

Seth

---

### Post by irish_flu on 2007-06-01
You sure it's not a problem with the hard drive (at least, one partition) filling up?  that's what the error message is saying, I gather.

I'm probably barking up the wrong tree, but just to be sure it would probably me a good idea to see how much free space you have in your disk partitions.

Go to the terminal, and at the command line type: df


Then, look at the "use" column and make sure none of them are at or near 100%.

---

### Post by Maxster on 2007-06-01
Im liking freeloader, maybee a little simple.

---

