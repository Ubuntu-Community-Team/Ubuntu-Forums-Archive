---
title: "[SOLVED] Thunderbird got huge inbox 670meg but only got 15 messages"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-02
:confused: I did a clean up and its still staying at this huge size. What gives. I makes backing up home folder twice as long.

---

### Post by hyper_ch on 2007-10-02
right-click each folder and select "compress"... maybe that helps.

---

### Post by philinux on 2007-10-02
Thats just it though I've cleared out all my folders and emptied the trash. Weird Hardly anything in there now

---

### Post by philinux on 2007-10-02
Just found this doh 

[http://kb.mozillazine.org/Compacting_folders](http://kb.mozillazine.org/Compacting_folders) - nobody mentioned this and I've been running TB for yonks no wonder its huge. Of to compact see what happens

---

### Post by philinux on 2007-10-02
105 meg now - still quite big when I think of the amount of stuff in there.

---

### Post by conjur3r on 2007-10-02
I've been using this extension which automatically compacts after a configured amount of time.

[https://addons.mozilla.org/en-US/thunderbird/addon/1279](https://addons.mozilla.org/en-US/thunderbird/addon/1279)

---

### Post by erfahren on 2007-10-02
The Inbox of my main account in Thunderbird has 3 messages sitting there (easily totalling less than 100KB), yet the corresponding account's "Inbox" file in Thunderbird's Mail directory is 35megs.

Out of curiosity I opened that file up in gEdit and scrolling through it I noticed references to emails I completely deleted months ago. (My CPU shot sky-high scrolling through it!)

That might be the problem with yours. Apparently even though the messages are completely deleted Thunderbird is still keeping a record of them (maybe attachments too).

I don't know why that is. I've never noticed anything in Thunderbird indicating messages could be recovered after deleting from "Trash". That's the only reason I could see for that.

You could save the emails you want and then go to the ~/.mozilla-thunderbird/xxxxx.default/Mail/<accountname>/ directory(s) and replace the "Inbox" file (or whatever one) with just a blank,empty file. (In a fresh install of Thunderbird all those files ("Inbox", "Drafts", "Sent", "Trash", etc.) are just blank, empty files.)

Interesting observation in any event. Good to know!

---

### Post by ckempo on 2007-10-02
> **erfahren said:**
> ...Out of curiosity I opened that file up in gEdit and scrolling through it I noticed references to emails I completely deleted months ago. (My CPU shot sky-high scrolling through it!)

That might be the problem with yours. Apparently even though the messages are completely deleted Thunderbird is still keeping a record of them (maybe attachments too).

I don't know why that is. I've never noticed anything in Thunderbird indicating messages could be recovered after deleting from "Trash". That's the only reason I could see for that.

This is because until you compact your mail files, the emails are only "logically" deleted - that is, they remain ini the file (taking up space) but they are marked as "deleted" and get ignored by the program.

When you compact your mail file, this is a "physical" deletion - the data is actually removed permanently from the file *at this point* in time.

It's done this way for a reason - flagging something as deleted is a lot, lot quicker than physically ripping it out of the file each time you delete something.  Right click the folder and choose "Compact" - you'll notice it can take a while.  Imagine this kind of wait everytime you deleted a single message!

---

### Post by hyper_ch on 2007-10-02
If TB would be using the maildir format that shouldn't all be necessary.

---

