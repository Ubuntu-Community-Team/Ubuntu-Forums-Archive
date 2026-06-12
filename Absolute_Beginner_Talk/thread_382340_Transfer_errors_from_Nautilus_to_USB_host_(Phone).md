---
title: "Transfer errors from Nautilus to USB host (Phone)"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-03-11
Here's the problem: When I transfer files from Nautilus to my W810i Sony Ericsson phone (Mp3's, .thm or some ringtones) there's always a good chance that several files will wind up corrupted and not be usable. At times after a transfer, some files will show as being 0 bytes on the phone when the original file is something like 456 kb. That's just one scenario. 

The latest problem however, was the final nail in the coffin for me: Last week I uploaded a few Mp3's to the phone and seemingly, all was well. I later decided to delete those songs from the phone because I wanted to make file sizes smaller..whatever.  So just a couple days ago I uploaded another batch of songs and made a playlist out of them. I was checking out new free speakers which are made for the phone and things were sounding great until ....

The current song suddenly cut out in the middle of it, and was replaced by one of the songs which I had deleted last week ! I was baffled, truly. i figured that perhaps it was just an strange one time anomaly and let it go, only to skip to the next song, and have it happen again, but with a different song which had been deleted ! I looked with Nautilus all over the phone, and the memory card, but there was no trace of any of the files which were deleted. So what the heck gives ?

Apparently I'm not the only person whom has noticed and experienced this phenomenon, as more than one person on the Howard forums told me that the only way they knew how to resolve it, is to boot to Windows. This is hardly acceptable to me, but if it's the only way for now, it will have to be.  I'm really just unhappy about it though, and would like to know if something like this has been a known issue/bug within Ubuntu, and if it was perhaps being worked on, or is fixed in Edgy ? 

I wouldn't upgrade to Edgy if it was fixed, but would be nice to know that it was acknowledged as being a problem. Any advice or opinions would be helpful. 

Doug

---

### Post by shareMenaPeace on 2007-03-12
Try this

hit ALT F2 and type in```
 gksudo nautilus
```


than choose from the nautilus menu VIEW -> View hidden files

Now in the root path of the USB device you should see a ".Trash" folder - delete it.

---

### Post by Sweet Spot on 2007-03-12
I think that I had actually done that at one point, but just the files, and not the entire folder, which I'm assuming gets rid of those rogue files, and that's cool, but why does Ubuntu behave this way when transferring things to USB hosts in the first place ? (corrupting and such)  And is it a known issue ?

Doug

Alright, I deleted the whole folder this time, but looks like I had to delete two of them. The first was just Trash.username"  and the second was 'root.trash'  Got rid of both, but then noticed a message in Nautilus: 

"While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed."

Then I think this one appeared after deleting just the first trash:

--- Hash table keys for warning below:
--> &#65533;&#65533;&#65533;&#65533;q&#65533;8&#65533;&#65533;&#65533;q&#65533;8&#65533;-r&#65533;em"

Probably nothing to worry about I presume.

---

