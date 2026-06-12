---
title: "Evolution Virus?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Stephen Shellard on 2007-06-28
I recently received an email from someone called Sonia Kone (soniakone01@orangemail.es.)  

I immediately spotted this as suspect and attempted to right click on it to either delete or mark as junk.  The result was a complete freeze of Evolution. I was obliged to force a quit.  

All other programmes seem unaffected, but on reloading Evolution, there is a long lead in before any activity is possible.  Then all subfolders appear to be working fine:  however, when I go to the inbox, the offending email is still present and I have been unable to delete it or indeed either delete or move any other items in the inbox:  each attempt, by whatever means, results in Evolution once again "not responding".   The email would appear to have taken control of my inbox.  

I should stress that I have made quite a few attempts at this, which have included a complete shutdown of the computer.

Help appreciated.

---

### Post by cogadh on 2007-06-28
How big is the e-mail? Is it possible that it is just trying to load it into the preview pane when you click on it and it taking a long time due to images?

The odds that it is a virus are extremely slim, Linux viruses are few and far between (only 12-14 viruses in the last 10 years).

---

### Post by Cirrocco on 2007-06-28
I'm willing to bet money that it's NOT a virus, and you're just suffering from one of the many bugs that Evolution is plagued with.

I use it at work because we're a Microsoft shop and it's the only client that will hook into a MS Exchange OWA server (please correct me if i'm wrong - I would love to try an alternative!!!)  and this thing crash 6-10 times a day.  I have to kill the backend processes before starting it up again.

Evolution is pants man.  use Thunderbird whenever possible.

is Evolution even open source?  I have my doubts about Novell products anyway.  SUSE is pretty cool but Evo looks like a remnant from the 80's.

---

### Post by cogadh on 2007-06-28
Evolution is Open Source, the Exchange backend for it is not.

---

### Post by Cirrocco on 2007-06-28
so, the Exchange backend process is closed source and Novell owns it?

---

### Post by cogadh on 2007-06-28
AFAIK, yes.

---

### Post by Beatbreaker on 2007-06-28
couldn't be a virus could it? has anyone else noticed it? maybe it's just a bug with the attachment

---

### Post by dasunst3r on 2007-06-28
The fact that Evolution is so unreliable is the reason why I have switched to web-based email (GMail) and Pocket PC synchronization (ScheduleWorld+Google Calendar).  If this message is tripping you up, disable the preview pane (someone fill in on how to do that, please), and then delete it (try Shift+Delete).

---

### Post by smoker on 2007-06-28
it will not be a virus, i always had this kind of problem with evolution also, now i use thunderbird, though there are plenty of other alternatives.

you could always save your emails and try to uninstall, and reinstall, and see if that helps

---

### Post by nocturn on 2007-06-28
I found evolution OK stability wise.  But when used on an Exchange Server, it does crash very often.

It works very reliable on my IMAPS server with GSSAPI auth (single-sign-on), so no complaints.
Also, Evolution handles very big mailboxes beautifully.

---

### Post by Anzan on 2007-06-28
I've had Evolution hang while loading an email (one of many in a nested folder) and crash a few times. (But it's not as if Outlook didn't do that too.)

I'm confident this was not a virus, Stephen.

---

### Post by Stephen Shellard on 2007-06-28
I can't determine the size of the file as any attempt to engage with it freezes the computer.  In any case, right clicking on the file would not load it, but does lead to things seizing up - so surely this shows that file size is not an issue?

As regards saving my mail, prior to deinstall/reinstall:  do I just save my *.evolution\mail *folder?  Couldn't I just identify the offending email by this back door folder (ie.without loading evolution) and delete it that way?   Actually I have had a look but am not really sure what to delete so haven't touched anything.

In general I have found Evolution quite stable - indeed I don't recall it freezing in this way on any prevous occasion and I have used it on a daily basis for the last 9 months or so.  

I used to use Mozilla which was very good, but I was attracted to the address books in Evolution which I use a lot.   

The only problem I have experienced really was setting up the junk mail filters, but these now work well.  There was a lack of helpful information, but forums sorted me out eventually,  though it was clear others had been having problems with junk mail set up.  Only other problem I have had has been minor quirks with setting up address books.  I haven't really used other features much.



Thanks for interest taken in this problem so far.

---

### Post by Stephen Shellard on 2007-06-28
Well I appear to have deleted the offending item.   Perhaps it was a large file or there was some other complication in opening it;  I have the view set to show a preview even when one does not double click on the file.  I selected the file but attempted no action - just left it.  When I returned to the computer, the preview had opened.  I then deleted the file with no problem at all.  Thanks for helpful suggestions and apologies to Ubuntu for doubting its resistance to attack.

---

### Post by Atomic Dog on 2007-06-28
I tried to use Evolution at work and it was just too unreliable.  Sent messages never appear in the outbox or sent items, crashes, freezes...ugh.

---

### Post by y6FgBn)~v on 2007-06-28
A lot of stability issues here as well with Evolution. It is more than likely the culprit here. I often why Ubuntu continues to use it in their distribution considering its current state.

---

### Post by drogers on 2007-06-28
I'm a noob and don't have time to read all of the replies but I thought I'd throw in my two bits since I've experienced the same thing.

My problem seemed to be with the 'preview' option, where you have the e-mail open at the bottom of the window. I hope that makes sense. I can't remember what the problem was but there was an e-mail that i received that lead to the same problem; evolution freezing up. So what I did was (after many attempts) was able to open evolution and have my mouse placed whereby I could as soon as possible, click on another folder or e-mail or whatever. So once I was able to have the preview of a different e-mail (which didn't freeze up the mail client) I then went into the view settings or whatever it was and changed it so that there was no message preview... It was just the folders on the left and the list of e-mails on the right and nothing on the bottom. So once that was done i was able to delete the e-mail. I guess you could go back to the preview thing but I never bothered. Sure it's a nice feature that I got used to in outlook but whatever... It is what it is...

hope this helped and hope it was relevant...

dr

---

### Post by poobuntu on 2007-07-11
I received the same email, and the same problem. After several lock ups in a row, I simply clicked another email as soon as I opened Evolution. Then I waited...... probably ten minutes. It eventually brought the email I clicked into the preview, allowing me to turn off the preview mode and then delete the offending email. 

Makes your day when things like this happen at just the wrong time.... what can ya do.

---

