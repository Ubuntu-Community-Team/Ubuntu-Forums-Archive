---
title: "I'm in Panic mode! I just deleted ..."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by jason442 on 2007-12-15
I need help bad!... I just accidentally deleted my Music folder on my NTFS mount. Its about 80 gigs of music!! I I don't know how I hit the delete key!!....ubuntu doesn't even confirm a delete!? Please help... Can I recover this?

---

### Post by Ribar on 2007-12-15
Did you use rm -r command? If so there is not much hope but i let the experts chip in maybe there is still a way to retrieve the folder ;)

---

### Post by jason442 on 2007-12-15
I was using the explore browser window and hit the delete key :)

---

### Post by jason442 on 2007-12-15
That was supposed to be a :(

---

### Post by mellowd on 2007-12-15
Yes you can, the most important thing is to NOT write or move anything to the disk.

When an OS deletes a file it's still there it just deletes the reference to it. If you write anything to it the OS will use this space so wiping out anything that was there.

This is by far the most important step

---

### Post by mellowd on 2007-12-15
Then download this: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It's a free source program and don't be put off by the name, it also is able to detect mp3's and many other mutimedia type files. I've used it and it works very well.

---

### Post by sloggerkhan on 2007-12-15
it might be in the recycle bin still.

have you checked the .trash folder?

---

### Post by jason442 on 2007-12-15
> **sloggerkhan said:**
> it might be in the recycle bin still.

have you checked the .trash folder?

Nope...It went straight to deletion

---

### Post by jason442 on 2007-12-15
> **sloggerkhan said:**
> it might be in the recycle bin still.

have you checked the .trash folder?

Thanks for the help! I'll get to work!

---

### Post by jason442 on 2007-12-15
> **mellowd said:**
> Then download this: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It's a free source program and don't be put off by the name, it also is able to detect mp3's and many other mutimedia type files. I've used it and it works very well.

Thanks for the help! I'll get to work!
__________________

---

### Post by sloggerkhan on 2007-12-15
Just to be 100% clear: you hit the delete key and it did not move the files to a hidden .trash folder?
And you're using nautilus?
Because on my machine, if I hit the delete key, not matter how big or how many the files, they always go to a hidden .trash-$username folder on the same drive.

---

### Post by Brindled on 2007-12-15
> **jason442 said:**
> I need help bad!... I just accidentally deleted my Music folder on my NTFS mount. Its about 80 gigs of music!! I I don't know how I hit the delete key!!....ubuntu doesn't even confirm a delete!? Please help... Can I recover this?

hmm, i'm not sure about your load of ubuntu and how you have your settings, but my load, by default, does delete things to the /.Trash-(user) folder before a final deletion on my NTFS drive. even then, you have to ok the trash bin deletion. 

it should still be on your NTFS drive's trash bin.

just sayin'

edit: yeah, what sloggerkhan said.

---

### Post by Kingsley on 2007-12-15
> **Brindled said:**
> hmm, i'm not sure about your load of ubuntu and how you have your settings, but my load, by default, does delete things to the /.Trash-(user) folder before a final deletion on my NTFS drive. even then, you have to ok the trash bin deletion. 

it should still be on your NTFS drive's trash bin.

just sayin'

edit: yeah, what sloggerkhan said.

Well, I'll be damned. I accidentally hit the delete button on a movie in my NTFS partition a week ago and thought it was gone forever. Now, I've found it and other stuff in the volume's trash folder. Thanks for the info.

---

### Post by rsambuca on 2007-12-15
It is still there.  Just open the root directory of the partition where the music folder was using the normal Nautilus File Browser.  Then select View - Hidden Folders.  You will find the deleted folder inside a folder called .Trash-<yourusername>.  You can just retrieve it from there.  Anything you delete on an ntfs partition goes to these hidden folders where you can retrieve them from.  If you want to open up the hard drive space, you can delete them from this hidden Trash folder.

---

