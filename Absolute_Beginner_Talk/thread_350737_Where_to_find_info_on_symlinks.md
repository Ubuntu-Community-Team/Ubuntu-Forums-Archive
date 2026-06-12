---
title: "Where to find info on symlinks"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-01
I'm looking for info on symlinks. I've looked through the Ubuntu Guide ([http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)) but didn't turn up anything. The man page is much help. 

What I want to do is link to a file on a FAT32 partition. When I try using the "make link" command in the context menu, I get an error "Operation not permitted". I get the same error even running Nautilus as root. 

I have X File Explorer (XFE) on the system and can make a link while running as a user. I can delete the link in XFE but not in Nautilus even as root. 

As an experiment, I was able to make a link (while running as user) on the desktop to the aforementioned link on the desktop. However, even as root I cannot delete it. I can only delete this second link in XFE. 

My meager understanding lead me to think that symlinks could easily link to files on other partitions even ones using other file systems. My experience with XFE shows they can be made and work but I haven't had any luck except with XFE (which as a file manager is a bit funky).   

 So, I need some info on symbolic links, how they work, what restrictions there are on using them, and generally more info than I have about them.

---

### Post by Stochastic on 2007-02-01
To my knowledge you can't create a symlink for files on a fat32 partition.  I could be wrong however.  Possibly you could create a link on your desktop  and then edit the link to point to the other partition.  What does google turn up on the subject?

---

### Post by Patrick K on 2007-02-01
Here's what Wikipedia says:
"Systems can use symbolic links to refer to files even on other mounted file systems."

Most all other info I found was in geek speak that didn't make much sense to me.

---

### Post by dcstar on 2007-02-01
> **Patrick K said:**
> 
..........
My meager understanding lead me to think that symlinks could easily link to files on other partitions even ones using other file systems. My experience with XFE shows they can be made and work but I haven't had any luck except with XFE (which as a file manager is a bit funky).   

 So, I need some info on symbolic links, how they work, what restrictions there are on using them, and generally more info than I have about them.

I have Symlinks on my Gnome desktop to FAT32 files, and they seem to work ok (for me!).

I create mine by Right-clicking a file and using the appropriate function, then moving the created link off the Windows file system to where I want it to reside.

AFAIK you should be able to use Symlinks ("Soft" links) to any mounted filesystem, just as you would with a "Hard" link on your local drive.

A Symlink is basically a pointer to a file accessible from your system, and most apps these days can treat these as with any "normal" directory entry that references a local filesystem.

---

### Post by Buck2348 on 2007-02-01
I cannot make links to files in fat32 in Nautilus by right-clicking and choosing "make link."  ("Operation not Permitted")   But I can from the command line:  ```
ln -s path/to/file link_name
``` This makes the link in the current directory.  Tomorrow I'll try to figure out why the nautilus way doesn't work.

Buck

---

### Post by Patrick K on 2007-02-01
that's what I thought. However, I get the errror message whenever I right click and select "make link". I don't get any other options but to retry, which bring the same error back, or cancel. I get the same error even as root. 

I just noticed this in the terminal window:
> ** (nautilus:12943): WARNING **: No description found for mime type "application/x-extension-ini" (file is "sd.ini"), please tell the gnome-vfs mailing list.
** Message: Hit unexpected error "Operation not permitted" while doing a file operation.
I don't know what this means but I guess I should tell the gnome vfs mailing list.

---

### Post by Buck2348 on 2007-02-01
I found one thing--I can middle-click and drag a fat32 file somewhere else--such as the Desktop.  The context menu that appears when you drop it has an option "Link Here" and it works.  I don't understand why the right-click menu won't let us make a link, but I never saw much use in making a link in the same directory, unless you need the linked file/directory to use an alias.  Of course you can drag and drop it somewhere else.

I found this > It's of type FAT32, so Linux functionality such as symbolic links won't work on it [here ]("http://www.geocities.com/epark/linux/partition-share-HOWTO.html").   But as I say, the links I made work just fine.

Buck

---

### Post by Patrick K on 2007-02-01
The middle button works, thanks for pointing that out. I wonder if the context menu item is for a hard link, which cannot span different partitions or maybe it's file systems, I'm not sure. Anyway, the middle button tip will work fine.

---

### Post by phil_n on 2007-04-21
> **Buck2348 said:**
> I cannot make links to files in fat32 in Nautilus by right-clicking and choosing "make link."  ("Operation not Permitted")   But I can from the command line:  ```
ln -s path/to/file link_name
``` This makes the link in the current directory.  Tomorrow I'll try to figure out why the nautilus way doesn't work.

Buck

Just a guess at an obvious reason, which you may have already checked... Nautilus creates the link in the same directory as the file, whereas if you use ln, you can create it wherever you like. If your windows partition is locked read only then Nautilus won't be able to create the link. However if you can write to your fat32 drive then I don't know why you can't create links. I have to say what's really needed is a wizard in Nautilus that creates links so that newbies and people migrating from Windows can make recognisable shortcuts from File->New->Link, rather than the way it's set up at the moment. I may just find out how to raise that as a feature request.

---

