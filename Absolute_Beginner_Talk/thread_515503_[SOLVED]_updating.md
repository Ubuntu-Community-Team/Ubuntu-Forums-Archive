---
title: "[SOLVED] updating"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-08-02
so, this may very well be the noobiest question ever, but:

i have a WD my book drive (500gig) and a 80gig sata drive in my pc... i want to switch them out while the size of my file collection (i just got a netflixs account :) ) is still low.

my only question is this: can i update the kernel, and to new versions of ubuntu without having to wipe the drive clean?

will the files in my home folder remain intact even during updates and such?

i ask now, because i'm not sure when i'll be able to afford to buy a new 500gig book to keep as a backup.

---

### Post by Claus7 on 2007-08-02
Hello,

if I understood correctly you want to update the kernel without losing your data. Every time you do this, you should have in mind that something might go wrong and lose data. So it's better to keep some backup of your most important files first.
And have also in mind that the upgrades should be done one at a time and not from the oldest at once to the newest kernel version.

Have a nice update,
Regards!

---

### Post by colddayinapril on 2007-08-02
thanks.

also, what about updating versions of ubuntu?
like, from fiesty to the new one, when that comes out?

---

### Post by forestpixie on 2007-08-02
> **colddayinapril said:**
> thanks.

also, what about updating versions of ubuntu?
like, from fiesty to the new one, when that comes out?

not sure about that - but if you haven't installed yet - you would be better served by setting up so that your /home folder is on a separate partition  - ie making 3 partitions during setup - 1 for root, 1 for home and 1 for swap.

It will also help if you need to reinstall for any reason

---

### Post by Hospadar on 2007-08-02
I was able to go from edgy (6.10) to fiesty without have to reformat or loose data, so I would assume in the future that you would be able to do the same, and I regularly get kernel updates out of the repos without any troubles.

That said, if an update were going to cause data loss or problems it would probably be a kernel update or major version distro update.  If you see one of these you may want to either
a) wait a few days before installing it and see if any major issues show up on the forums
b) back up your most important data to some dvds before updating.

also, with kernel updates, if you update and stuff doesn't work right, you can always go back to the previous kernel with grub, or use a live cd to retrieve and back up the data, none of the updates should have the potential to mess up your filesystem so much that you wouldn't be able to get at the files with a live cd or an os on a different hdd.

Hope this helps!

---

### Post by colddayinapril on 2007-08-02
well, i actualy found a guy whos going to buy my wd drive. so, what i'm thinkabout doing is getting a WD raptor drive to be used for root, and a seagate barccuda for home (i hae enough memory that i don't really need a swapfile, and always turn it off)... that would solve the problem of updating.

so, my issue now is that i don't know how to set that up (root on one drive, hoem on the other).

can anyone point me to any guides or howtos on the subject?

---

### Post by forestpixie on 2007-08-02
I don't think you need to be putting root on a drive of it's own - unless of course it's a real small one , I think you have to make a symbolic link for the /home folder - I read somewhere, don't know how to do it though. 

As far as swap goes I would be inclined to have some - it won't use up very much room, perhaps the same drive as root - but if you haven't got it - sure as eggs are eggs :)

---

### Post by colddayinapril on 2007-08-02
hmm... well, how larg of a partition should i make for root?

after a clean instal, with nothing at all on the system, i'm only using 2 gigs... so, maybe 3 or 3.5?

so, i imagine that if i where to do that, i would just install onto a small partition, the install and run gparted to format the rest of the disk...


i'm sure i can find somethign writne on symbolic linking... but if you guys have any hanging around in your bookmarks, that would be cool to :D

---

### Post by forestpixie on 2007-08-03
I'm now not sure about the link thing (only been doing this for a short while) :(

Edit - this thread implies you can do it during install - [http://ubuntuforums.org/showthread.php?t=516356](http://ubuntuforums.org/showthread.php?t=516356)

Anyway - without knowing what HDDs you intend to use size wise - this what I've got, with 2 80Gb drives

8 Gb - root drive (forgot I wasn't installing Windows , it was late:) ) - of which I've got nearly 5Gb free - so If you did a 4Gb root that should be fine

67Gb /home folder 

1Gb swap - with 1Gb ram - and the swap gets used

two seperate partitions amounting to 80Gb

hope that helps you

---

### Post by colddayinapril on 2007-08-04
hmm... i was thinking it could be done during install... thanks for the input on the size of the root drive.

i'll look into swap more before i decide on that.

thanks

---

