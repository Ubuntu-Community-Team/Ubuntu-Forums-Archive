---
title: "Make split RAR archive"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-09-08
I know this has been asked before, but I haven't been able to find an answer.  I'm usually decent with the command line, but this is just too strange for me! :confused::(:mad:

I need **very** specific instructions on **exactly** what to type if I want to:

-make a RAR archive...
-out of a folder in my home directory;
-(lets say it's called "folderA")
-split it into 100Mb pieces (or *just* under)
-call it "archiveA" and put in $HOME

please help!

---

### Post by mali2297 on 2007-09-08
I think this will do it:
```

rar a -v100M archiveA.rar folderA

```
(...assuming you have installed rar.)

---

### Post by ryanVickers on 2007-09-08
It looks like it's going to work, thanks!

I'll see when it's done :)

---

### Post by ryanVickers on 2007-10-15
well, the archiving worked fine, so I made a script to graphically guide you though creating the command, adding options, etc. ;)  Check it out! (signature)

---

### Post by go_beep_yourself on 2007-11-05
> **mali2297 said:**
> I think this will do it:
```

rar a -v100M archiveA.rar folderA

```
(...assuming you have installed rar.)

Why is it any more useful to have an archive split into many files rather than one?

---

### Post by ryanVickers on 2007-11-05
in case you need it in multiple pieces ;)

---

### Post by mivo on 2007-11-05
> **go_beep_yourself said:**
> Why is it any more useful to have an archive split into many files rather than one?

Sites like RapidShare and Mega Upload put size limits on the files you can upload.

---

### Post by go_beep_yourself on 2007-11-05
aw, i see. email puts limits on the size of files that you upload too. now i know how it is useful.

---

### Post by ryanVickers on 2007-11-05
yes, and lots of other things, like old memory sticks, CD's in the event a DVD drive isn't available, etc. :)

---

### Post by go_beep_yourself on 2007-11-05
> **ryanVickers said:**
> yes, and lots of other things, like old memory sticks, CD's in the event a DVD drive isn't available, etc. :)

That's not likely. I took my floppy drive out of my computer and beat it with a hammer. It's useless and obsolete. I have 2 dual layer dvd burners.

---

### Post by ryanVickers on 2007-11-05
well, *some* people don't!  (not me though, I do ;))

---

### Post by mivo on 2007-11-05
I now have the second desktop that came without a floppy drive, and I still feel it is really odd! Not that I have any use for it, but something is missing (not enough to buy one for a few bucks and put it in, I know ;)). But hey, there were ONLY floppies when I started with computers, and it was cool at the time too since several of my friends used "datasettes" still -- it would take years to my first HD .. with a whooping 10 MB! We've become spoiled.

---

### Post by go_beep_yourself on 2007-11-06
> **mivo said:**
> I now have the second desktop that came without a floppy drive, and I still feel it is really odd! Not that I have any use for it, but something is missing (not enough to buy one for a few bucks and put it in, I know ;)). But hey, there were ONLY floppies when I started with computers, and it was cool at the time too since several of my friends used "datasettes" still -- it would take years to my first HD .. with a whooping 10 MB! We've become spoiled.

It's hammer time!!! :guitar:

---

### Post by go_beep_yourself on 2008-01-07
> **mali2297 said:**
> I think this will do it:
```

rar a -v100M archiveA.rar folderA

```
(...assuming you have installed rar.)

I've figured out what this is useful for. Fat32 filesystems do not allow dvd size isos because they are too big. Emailing usually limits the attachment size, so send  10mb rar archives in several emails. I know there is more uses for this, but I can't remember them all now.

---

