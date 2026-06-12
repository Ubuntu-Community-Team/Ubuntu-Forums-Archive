---
title: "loading ubuntu on dell inspirion with windows on it"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Zenmind on 2006-11-22
I have read a few places and not sure if the info was correct or valid - my wife has my old dell inspirion (8100?) and has win2000 on it and needs it for her job.

Can I load ubuntu on it and partitio the win with the ubuntu? or will it overwrite the win2000?  I have read that you can partition it off the CD - that there is some partiton app on it or the partition app is part of ubuntu installation.  Is that correct? and how do i do it?

If I write over the win 2000 I am looking at a divorce.

thank you.

---

### Post by saxsux on 2006-11-22
Yeah, you can partition it and keep Windows. I think the easiest way to do this would be to choose "Use largest continuous free space" when installing Ubuntu, but I'm not too sure...

---

### Post by Bachstelze on 2006-11-22
First : use the Alternate CD !!

It will let you resize the Windows partition and install Ubuntu in the free space (the "Desktop" CD will let you do that too but it stinks anyway :p).

---

### Post by outofnicks on 2006-11-22
A good search term would be "dual boot".

Yes, you can create a new partition above the Windows install without overwriting it, and yes there is a partition app on the CD. The answers are right in front of you when you are viewing the message list of "Absolute Beginner Talk", under the Sticky Threads.

[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

I don't know how old your computer is but one thing I know is that maximum amount of memory can make up for a lack of processor speed. I only have 256 mb on my 1.6 gig Dell, and I think I'd be better off with, say, 1 gig of RAM in an 800  mhz box.

---

### Post by Zenmind on 2006-11-22
not sure what you mean by 'alternate' CD. I have the Cd that I recieved from Ubuntu directly. whichever one that is. it is the dapper drake version for sure.

---

### Post by Henry Rayker on 2006-11-22
The alternate cd is one you would have to download and burn yourself.

The 'live' cd will work as well (that's the one you recieved in the mail).

If the situation is serious enough to warrant a divorce, I would suggest doing a LOT of reading, a lot of backing everything up and exercise EXTREME care. I've done about 4 or 5 partitioning jobs and Ubuntu installations, but my most recent one, I overwrote a "good" partition, due to a slight lapse in thinking...

---

### Post by Zenmind on 2006-11-22
Henry - a little bit of an exageration....but close! thanks for the replies.

---

### Post by tocleora on 2006-11-23
He's right, it can be hairy repartitioning if you aren't familiar with it.  I tried a parition app that came with knoppix (another distro) and I lost complete access to my partitions all together, something messed up, I had to completely reinstall windows.  So I got  Partition Magic as I've used it before and it worked very well.  Resize your Windows partition to allow space for Linux to install in, and then during the install process for Ubuntu you can tell it to use all available free space and also to have it automatically configure the partitions for you.  I would use something like Ghost or an equivalent to backup first though, just in case, and I'd still back up all important files and documents, e-mails, favorites, etc. to CD/DVD as well.  You can find information about Partition Magic here:

[http://www.symantec.com/home_homeoffice/products/overview.jsp?pcid=sp&pvid=pm80]("http://www.symantec.com/home_homeoffice/products/overview.jsp?pcid=sp&pvid=pm80")

And Ghost here:

[http://www.symantec.com/home_homeoffice/products/overview.jsp?pcid=br&pvid=ghost10]("http://www.symantec.com/home_homeoffice/products/overview.jsp?pcid=br&pvid=ghost10")

---

