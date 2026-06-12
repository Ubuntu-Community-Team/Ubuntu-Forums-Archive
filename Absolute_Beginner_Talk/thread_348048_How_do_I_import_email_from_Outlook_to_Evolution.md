---
title: "How do I import email from Outlook to Evolution?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by NoVista on 2007-01-28
I need to get my mail from Outlook Express into Evolution Mail.

Since Evolution can't import these files directly, how can I do it?

Has no one been able to do this?

---

### Post by mips on 2007-01-28
Did you even try to google *Outlook migration to evolution* ?

Well I did it for you and there are many hits.

This one looks good:
[http://www.novell.com/documentation/evolution26/index.html?page=/documentation/evolution26/evolution26/data/outlook-migration.html](http://www.novell.com/documentation/evolution26/index.html?page=/documentation/evolution26/evolution26/data/outlook-migration.html)

---

### Post by A*p on 2007-01-28
Sorry I have no experience with outlook but this maybe is a possible solution. If your mail serer has the possibility of using imap you could maybe copy/sync your mail to be stored on the server then grab it all again in evolution.

---

### Post by Woodgar on 2007-01-28
As an alternative, you can "trick" OE into saving a bunch of emails [in plain text format](http://www.codeconscious.com/outlook-express/exporting-from-outlook-express.html) that you can then import at your leisure.

---

### Post by FryerFox on 2007-01-28
What I have done in the past is pull the email into Windows Thunderbird and then copy the MBOX files over to Evolutions directory.

It is much easier to migrate data from Thunderbird to Evolution since they both use MBOX format.

See:
[http://www.cyberciti.biz/tips/moving-outlook-email-data-to-linux-evolution-mail-client.html](http://www.cyberciti.biz/tips/moving-outlook-email-data-to-linux-evolution-mail-client.html)

---

### Post by NoVista on 2007-01-28
Yeas, I did Google it, Outlook EXPRESS though, and not Outlook, two diff progz.

Copying the folders over manually from Thunderbird worked like a charm.

Oddly, I never came across the easy fix. I had even posted on this once before.

Thank you all, I can now be free of Windows as my main OS.

This is good :D

---

### Post by linux_believer on 2007-01-28
I had the same problem. What I found out is that Evolution cannot import a PST file. What you will have to do as somebody suggested is install thunderbird on your windows system then port the data. Once you have it in thunderbird you can put the file on disk and Evolution will read it. Evolution is great in comparison to outlook.

Have fun

---

### Post by aysiu on 2007-01-28
I've moved this from the Cafe, because it's a support request, not discussion.

I've also retitled it to more accurately describe your problem.

---

### Post by Ubuntu Joe on 2007-02-08
Nice work fellas . . .

---

### Post by sicofante on 2007-02-19
I haven't been able to find any way of moving email from Outlook into Evolution KEEPING ALL OF MY FOLDERS AND HIERARCHY the same and IMPORTING ALL OF THEM AT ONCE and not one by one. This is something trivial with Thunderbird and that's the reason I'm using it, but I'd love to move now from Thunderbird to Evolution in one easy step. No success so far.

Does anybody know which mail format is Evolution using? I know it's mbox in Thunderbird.

---

### Post by mar225 on 2007-02-19
I fought that problem dor a week and the best I could do was to forward all the emails from OE to a friend and then have her send them back and brought them into evolution. 

Might be the long way around but it worked for me.

---

### Post by sicofante on 2007-02-19
I can't do that with almost 4GB in emails... Besides all dates would be changed.

---

### Post by muguwmp67 on 2007-02-27
I also had a huge outlook mailbox with lots of directory nesting.  Thunderbird crashed each time it tried to read it.  I ended up importing it into outlook express.  Then I installed thunderbird in windows and imported from outlook express to thunderbird.

I have my windows partition mounted, so I could find:

/media/sdb1/Documents and Settings/<user>.<PC Name>/Application Data/Thunderbird/Application Data/Thunderbird/Profiles/<profile code>/Mail/Local Folders

Under that, I copied the entire contents of the folder containing the .sbd file to:
~/.evolution/mail/local

I opened evolution and the folder was displayed with all of the nesting intact.  All of the messages were marked unread, but this can be fixed by right clicking the folder in evolution and selecting 'mark read'.

---

### Post by tiver on 2007-05-26
> **FryerFox said:**
> What I have done in the past is pull the email into Windows Thunderbird and then copy the MBOX files over to Evolutions directory.

It is much easier to migrate data from Thunderbird to Evolution since they both use MBOX format.

See:
[http://www.cyberciti.biz/tips/moving-outlook-email-data-to-linux-evolution-mail-client.html](http://www.cyberciti.biz/tips/moving-outlook-email-data-to-linux-evolution-mail-client.html)


This was a great help since Evolution E-Mail seems to support more than Thunderbird.

But could anyone help me to locate the directory of Evolution E-Mail ~/.evolution/mail/local ? I cannot find it, even not under /home. 

Thank you a lot!

---

### Post by hartdg on 2007-08-12
> **muguwmp67 said:**
> I also had a huge outlook mailbox with lots of directory nesting.  Thunderbird crashed each time it tried to read it.  I ended up importing it into outlook express.  Then I installed thunderbird in windows and imported from outlook express to thunderbird.

I have my windows partition mounted, so I could find:

/media/sdb1/Documents and Settings/<user>.<PC Name>/Application Data/Thunderbird/Application Data/Thunderbird/Profiles/<profile code>/Mail/Local Folders

Under that, I copied the entire contents of the folder containing the .sbd file to:
~/.evolution/mail/local

I opened evolution and the folder was displayed with all of the nesting intact.  All of the messages were marked unread, but this can be fixed by right clicking the folder in evolution and selecting 'mark read'.

**Muguwmp67** this is **ABSOLUTELY INSPIRED.** I've spent a long (4 day) weekend researching this topic and the sticking point holding up migration of my e-mails from Outlook is that Evolution File / Import will only allow import of one file at a time. 

There are many other people who have struggled with this issue.

This little gem of wisdom should be incorporated into the official Ubuntu document on migration from Windows as well as included in the Evolution  documentation.:guitar:

Man am I stoked - this is the cherry on the ice cream of my weekend! Thanks again.:KS

Kudos also to Evolution for the way it so gracefully and speedily updates it's indexes and incorporates the new folders.

I was also quite impressed with the way Thunderbird extracted my MS-Outlook 2003 (2GB of e-mails spread over about 8 .pst files and 120 folders). It took several hours but completed the job.

Dave

---

### Post by overmark on 2007-10-24
I agree with hartdg, that was awesome. Just did it then and worked perfectly. It should be added as a "How to" or "solved".

Thanks for saving me hours of heart ache.

Mark

---

### Post by overmark on 2007-10-24
Tiver ~/.evolution is a hidden directory under your home directory. Go to view in file browser then check "show hidden files"

---

### Post by ahzadjali on 2008-06-14
Lately, i installed Ubuntu ver8 as a dual boot. I find this distro fantastic and easy to use vista alike. But again as old windows user, there are few migrations i face hard to crack.

1. Outlook PST files migration to Evolution.

Read few posts but i still find it bit harder to migrate my PST to evolution. Is there some thing straight forward tool to migrate.

---

