---
title: "need some advice re 2nd hard drive"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by roscal on 2008-02-06
Hello fine linux people, I have been lurking here a while and have learned lots.
Thanks all.
I've been using Kubuntu Fiesty since last August, and absolutely love it.
The machine is second hand.
It has 2 80gig HD's.
It already had Kubuntu on it, from the previous owner, but I did a fresh install when I bought it.

So, I have my install on hda.

I never could figure out what happened to the 2nd drive, I thought it didn't work, but guess what?

I just mounted it up as hdb, mounted under media.

It's full of media contained in the home file, and has its own bin boot dev lib root sys and usr and var files etc under the tree for hdb. This is all stuff left over from the previous owner.

Can I just delete all these files and use the disc myself for storage or will it mess up my own install on hda?
Would it be best to just format it, and remount it. If so, I don't know how to format it.

I'm pretty green at this.
Thanks:)

---

### Post by jaytek13 on 2008-02-06
If you only installed on hda then there is nothing useful on hdb and you can feel safe just deleting everything.

---

### Post by jan quark on 2008-02-06
just download the gparted live cd

burn a cd and boot from it 

then you can format the disc to ext3 and and mount it 

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by roscal on 2008-02-06
That was fast, wow,:)
I did my own install on hda yes , never even acessed or mounted hdb untill now.
Thank you

---

