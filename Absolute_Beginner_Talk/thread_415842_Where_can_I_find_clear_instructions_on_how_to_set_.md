---
title: "Where can I find clear instructions on how to set partitions using gparted.?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-20
I would like for you to look at the attachment and tell me what to do to set the primary partition to boot with WinXP. I still need to install WinXp after this partitioning. I lost my hard drive the other day via a power surge and failure and am having to reset partitions.

I have Feisty as my main OS on a separate hard drive. I need WinXP to do certain tasks not yet available in Linux. I won't go into that.

If you know how to work with gparted, please look at the attachment and tell me how to set **one partition...and an "ext"** if I need it for WinXP.
Edit: I see that it will not fill in the spaces with a screen shot. Sorry.
Edit: The second attachment shows how I have set the partitions. Is this the right way?

Thank you so much for your help.
kh

---

### Post by freebird54 on 2007-04-20
Basically decide how much space you want to devote to its exclusive use, and tell it!  By the way 0t he entries go in MB so 1000 = 1Gb (close enough).  For example - to give it 30 Gb (a reasonable amount) type in 30000 - and it will adjust that slightly to fit into a block neatly.

You could format it NTFS as well - that's the usual/better choice as far as XP is concerned - but it is easier to read it in Ubuntu with a VFAT32 setting if it matters.  I would use NTFS (but I only see XP every other week :)

Post back if more questions.

Oh - and the rest can be formatted ext3 and used by both - with a little for Windows.  Or it can be formatted VFAT32 and used by both - with no drivers needing to added wither end.  Your choice.

---

### Post by kittyhawk63 on 2007-04-20
[quote=freebird54;2494830]Basically decide how much space you want to devote to its exclusive use, and tell it!  By the way 0t he entries go in MB so 1000 = 1Gb (close enough).  For example - to give it 30 Gb (a reasonable amount) type in 30000 - and it will adjust that slightly to fit into a block neatly.

Freebird, could you look at my first post again. I put in another attachment. How does it look to you? I think maybe something is wrong but don't know what it is.
I will set it up as NTSF. I have it set as Fat32.

** Ok. From what you say, I need to do some more tweaking. I don't think I have it set right at this time. I will post my settings when I am finished "trying" to follow your instructions. They are clear. It is just my first time using gparted.**
kh

---

### Post by kittyhawk63 on 2007-04-20
Freebird54,

Or anyone else reading this.

How does this partitioning setting for WinXP look? See attachment.

Edit: I set the 1000.00 MiB also as ext3. Is that correct?
kh

---

### Post by n3tfury on 2007-04-20
[http://www.linux.com/article.pl?sid=06/07/20/1654251](http://www.linux.com/article.pl?sid=06/07/20/1654251)

you'll find what you need in that link.  your XP partition should be NTFS.

---

### Post by kittyhawk63 on 2007-04-20
> **n3tfury said:**
> [http://www.linux.com/article.pl?sid=06/07/20/1654251](http://www.linux.com/article.pl?sid=06/07/20/1654251)
you'll find what you need in that link.  your XP partition should be NTFS.

Thanks n3tfury. Taurus says NTFS is harder for Ubuntu to read. I am using WinXP on a separate drive and other than gparted will never use Linux to access WinXP drive. I will be setting it as NTFS.
kh

---

### Post by freebird54 on 2007-04-20
That was 1,00 Mb PER Gb... I suggested about 30,000 :)  That setup doesn't leave any room for XP!

OK?

---

### Post by kittyhawk63 on 2007-04-20
> **freebird54 said:**
> That was 1,00 Mb PER Gb... I suggested about 30,000 :)  That setup doesn't leave any room for XP!
OK?

I typed in 30000 and that is what it gave me. At lease that is what I think I typed in. I could be mistaken. Could you look at these attachments and tell me if I am getting closer.  Like I said before, I have never partitioned a hard drive before. Not sure which you looked at before. Sorry, the third one is no good.
kh

---

### Post by freebird54 on 2007-04-20
Nope!  Clear 'em all.  Create one at 30,000 for NTFS, create another eithr ext3 or NTFS for data.  Then format 'em.

If it is giving you too much trouble - you might have better luck from XP now that the drive has been cleaned up?  (empty it so that it is ALL unallocated)  that way the worst that would happen is that it would all be XP (and still readable from Ubuntu)

---

### Post by kittyhawk63 on 2007-04-21
> **freebird54 said:**
> Nope!  Clear 'em all.  Create one at 30,000 for NTFS, create another eithr ext3 or NTFS for data.  Then format 'em.
If it is giving you too much trouble - you might have better luck from XP now that the drive has been cleaned up?  (empty it so that it is ALL unallocated)  that way the worst that would happen is that it would all be XP (and still readable from Ubuntu)

Thanks Taurus. Sorry, I was called away for the last few hours. Thanks for your kind patience and your instructions.
kh

---

