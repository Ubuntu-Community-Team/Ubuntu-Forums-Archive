---
title: "Outlook to Evolution"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by ~J~ on 2005-10-10
Hi,

Does anyone have any walkthroughs or know of any on the web that will show me how to successfully (and pain free!) convert my Outlook emails/calendars/contacts/notes/etc so I an import them all into Evolution?

Starting to making a firm transition now over to Ubuntu and this is one of those hurdles that's preventing me.

---

### Post by matthew on 2005-10-10
This is what I did. Install the Mozilla suite on Windows. It is capable of importing your mail and so on from Outlook. Once that is done, save the mbox file it creates and transfer that to Ubuntu. Evolution will import mbox format mailboxes.

There have been several threads in these forums on this and a search for them will probably lead you to more detailed step-by-step instructions if you need them. Good luck!!

---

### Post by loupy on 2005-10-10
There is also a package in the repository called readpst.  You can use that to do the conversion it was quite simple.  It does not work on outlook 2003 PSTs, but in outlook you can create a new PST in 2000 format and copy everything over to that, then run readpst.

---

### Post by ~J~ on 2005-10-10
Great suggestions, many thanks!

---

### Post by micrologix on 2006-04-02
[QUOTE=loupy]There is also a package in the repository called readpst.  You can use that to do the conversion it was quite simple.  It does not work on outlook 2003 PSTs, but in outlook you can create a new PST in 2000 format and copy everything over to that, then run readpst.[/QUOTE]

I have installed the readpst program, can you please tell me how to execute it, thanks.

---

### Post by hotani on 2006-04-12
You'll have to pay a visit to the CLI.

// show help:
shell> readpst -h 

// this is what i ran on mine
shell> readpst -o /export-dir /path/to/MAILBOX.PST

// more info: 
shell> man readpst

Actually, now that I've tried this I wouldn't recommend it. I exported the file fine, but when importing to Evolution it hung so bad I had to force quit it. Now it won't open at all. Good times.

---

