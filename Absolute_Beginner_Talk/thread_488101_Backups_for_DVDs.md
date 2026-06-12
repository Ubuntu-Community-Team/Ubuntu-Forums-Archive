---
title: "Backups for DVDs"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-06-29
I have a bunch of commercial DVDs which I've purchased over the years, mostly of Jazz concerts.  I'd like to be able to not only make a backup of each, before the original media starts to fail, but also to keep them on disk and watch them from there.

I gather there is some controversy about the legality of this, although I've also often heard that one has the right to make a backup copy of something one has purchased.

Since I'm not going to be doing anything but watching them myself, I feel that I'm within the spirit, if not the letter, of the law.

So, what's the best way to get a css scrambled DVD onto a hard disk in a format that's playable by, say, VLC?  VLC has no problem playing ISO files that aren't scrambled, so I presume if I can get around the scrambling I'll be good to go?

Or is ISO an inefficient way to store this material on disk?

Also, is there a recommended file system, or tweaks to ext3, which would lend itself to mult-gigabyte files being used almost exclusively in read mode?  (The "almost" is because I obviously have to write them to the disk at least once.)

I don't particularly care about editing them, stripping out menus, or modifying them in any way.. I'd just like to to enjoy them as I do now, but on disk.  I think this would improve the experience a bit too, as I get occasional pauses which I, perhaps mistakenly,  attribute to the DVD drive.

I've got lots of horsepower, memory, and disk.. over a Terabyte in fact, and I'm planning on dedicating one 500G drive to my concert movies and perhaps to music CDs as well.. those are subject to the same risk of media failure and I'd like them backed up as well.  Perhaps I should have two partitions, set up differently, for movies and for music?

What's the best way to do this?

Thanks,
Bob

---

### Post by DBStevens on 2007-06-29
K3b under tools > dvd copy look at the check boxs you'll figure it out.

---

### Post by RTrev on 2007-06-29
> **DBStevens said:**
> K3b under tools > dvd copy look at the check boxs you'll figure it out.

Got it.. it works.. thanks!

---

### Post by carusoswi on 2007-07-05
> **DBStevens said:**
> K3b under tools > dvd copy look at the check boxs you'll figure it out.

Can you clarify?  I did not get it.

Thanks.

Caruso

---

### Post by DBStevens on 2007-07-05
You need to make certain the create iso is checked and the delete upon closing is not.

After the copy is done you can then rename the iso and put it anywhere in your filesystem you desire.

---

### Post by ramjet_1953 on 2007-07-06
If you want to compress your DVD 9's onto DVD5 disks, I have found [COLOR="Blue"]k9copy[/COLOR] to be excellent.

It makes a copy which is virtually indistinguishable from the original.

I found that it is best to only use k9copy to create the iso, though and then use k3b to burn it.

Although both programs are KDE applications, they work fine under GNOME, but just take a little longer to start-up than when running them under KDE.

Regards,
Roger :cool:

---

### Post by carusoswi on 2007-07-06
> **ramjet_1953 said:**
> If you want to compress your DVD 9's onto DVD5 disks, I have found [COLOR="Blue"]k9copy[/COLOR] to be excellent.

It makes a copy which is virtually indistinguishable from the original.

I found that it is best to only use k9copy to create the iso, though and then use k3b to burn it.

Although both programs are KDE applications, they work fine under GNOME, but just take a little longer to start-up than when running them under KDE.

Regards,
Roger :cool:

Thanks for the clarification.  I had not been aware of K9Copy.  I did download and install it.  Have made two iso files thus far - have not tried to burn them to DVD yet.  One more question (please excuse my ignorance): What is the difference between K9 and K5?

(well, two more questions, actually): Also, I now have two ISO files located on my desktop.  So, to make a backup DVD, all I need do is copy that ISO onto an empty DVD, right?

Thanks for your help.

Caruso

---

### Post by Perfex on 2007-07-06
use gnomebaker, etc to burn the .iso (image) to disk , if you burn it another way you will just have an .iso on the disk

---

