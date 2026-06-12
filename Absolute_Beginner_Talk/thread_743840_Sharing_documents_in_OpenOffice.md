---
title: "Sharing documents in OpenOffice"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-04-03
Hi all

So we recently switched to OpenOffice 2.3 as our Office suite when we moved to Ubuntu.

Few issues with the migration as one would expect, but one that has been causing problems is that there is nothing to stop multiple users opening the same file from our server.

In MS Office if someone has a file open, and then another user (there are ~20 of us) tries to open it, they get a dialog saying that 'User X is editing this file, what would you like to do' and then will open as read only.

In OOo, there is no such warning, meaning they can all open it and edit it to their heart's content.

This brings another problem, when one person saves their changes, but another user still has it open, all the first user's changes disappear.

Is there something I am missing, this is causing a lot of problems here (eg contact spreadsheets, one person is looking at it, another opens it and adds in a new contact, saves and then closes it....and then it is gone).

How do we get around this?

tks

Matt

---

### Post by calc on 2008-04-03
You need to enable 'FILE LOCKING' depending on what network filesystem you are using. I haven't actually had the need or tested it myself, but it appears that if you are using NFS for network file sharing then it should already be doing locking properly.

---

### Post by calc on 2008-04-03
If you are using something other than NFS for file sharing then changing the setting in:

/etc/openoffice/soffice.sh

to yes instead of auto may help resolve the issue.

---

### Post by tqprvn on 2008-04-03
on every workstation?

---

### Post by calc on 2008-04-03
Yea, it should just work if using NFS, it *might* work if using a different network file system but I am not sure. You can test on a couple and see if that fixes the problem, if it does then you would need to change that on each system.

---

### Post by niteshifter on 2008-04-03
Hi,

Open Writer / Calc / whatever

Click Tools, then Options.

In the tree view on the left, expand item OpenOffice.org

Click Security.

Check the box next to "Open this document in read-only mode"

Click OK.


That should do what you want.

---

### Post by tqprvn on 2008-04-03
> # File locking; possible values are:
# - yes:  enable file locking unconditionally
# - no:   disable file locking
# - auto: enable file locking, when the document is found on a nfs share
# If the environment variable SAL_ENABLE_FILE_LOCKING is set,
# the setting if ENABLE_FILE_LOCKING has no effect.

FILE_LOCKING=auto

this word 'unconditional' worries me....does that mean that all files will be locked always?

---

### Post by tqprvn on 2008-04-03
> **niteshifter said:**
> Hi,

Open Writer / Calc / whatever

Click Tools, then Options.

In the tree view on the left, expand item OpenOffice.org

Click Security.

Check the box next to "Open this document in read-only mode"

Click OK.


That should do what you want.

Hi there, thanks for taking the time to respond.

I dont want to make documents read only, just want to be warned if another user has a document open before we start editing it (and then subsequently lose the edits).

Does that make sense?

- Matt

---

### Post by tqprvn on 2008-04-03
> **calc said:**
> Yea, it should just work if using NFS, it *might* work if using a different network file system but I am not sure. You can test on a couple and see if that fixes the problem, if it does then you would need to change that on each system.
argh...damn linux....

> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

How do I do that again?

---

### Post by niteshifter on 2008-04-03
Are you sure? :)  You wrote:
> In MS Office if someone has a file open, and then another user (there are ~20 of us) tries to open it, they get a dialog saying that 'User X is editing this file, what would you like to do' and then will open as read only. 

Turning it "on" in OOo via the method I gave should do the same. Worth trying ...

---

### Post by calc on 2008-04-03
> **tqprvn said:**
> argh...damn linux....



How do I do that again?

Well NFS is the standard network file system for pretty much all non Windows systems and has been for around 23 years, which is longer than Microsoft's SMB protocol, so it isn't unusual to think a Linux system would be using that as its (N)etwork (F)ile (S)ystem. :)

To edit the file do this:

sudo vi /etc/openoffice/soffice.sh   (or whatever editor you are comfortable with)

---

### Post by tqprvn on 2008-04-03
> **niteshifter said:**
> Are you sure? :)  You wrote:


Turning it "on" in OOo via the method I gave should do the same. Worth trying ...
you mean turn this on for the time in which one user is working on the document, then turning it off again?

If we turn on read only, then save it, come back tomorrow, that doc is still set in read only mode, right?  So if - use same example as before - we want to add in another contact, we cant as the spreadsheet is locked....must unlock, add contact, relock, right?

---

### Post by tqprvn on 2008-04-03
> **calc said:**
> Well NFS is the standard network file system for pretty much all non Windows systems and has been for around 23 years, which is longer than Microsoft's SMB protocol, so it isn't unusual to think a Linux system would be using that as its (N)etwork (F)ile (S)ystem. :)

To edit the file do this:

sudo vi /etc/openoffice/soffice.sh   (or whatever editor you are comfortable with)
ahh sorry, my damn linux wasnt addressed at nfs things, was at the "I forgot how to do the sudo thing again and just wished that there was a gui for this stuff cos then I can read it"

---

### Post by calc on 2008-04-03
Sounds like what you really need is a database of some sort since those generally give you good locking for free. Editing a file over the network works as long as the programs doing the editing of the file all implement the same type of locking or if it is done at the filesystem level where the app can't go on its merry way and write to the file anyway. In this case assuming no one would ever modify the file with something other than OOo it might be safe, but someone could conceivably open it in some other editor, once other apps support ODF, that doesn't do locking and mess the file up for you again at a later date.

---

### Post by tqprvn on 2008-04-03
ya, that wouldnt really do it.  

It makes sense for the contacts example I have been citing, but for other documents no go. 

We are a PR company - so a with a press release for instance, we keep them all in a client folder, and if we have two people open it for editing/translating/whatever, the potential for a mess is huge.....we had exactly that kind of mess this morning with two people tweaking an invitation at the same time.

---

