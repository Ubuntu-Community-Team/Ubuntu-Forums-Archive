---
title: "Evolution Mail - I'm missing something or it's crap"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by thewump on 2006-12-12
So.. 

I was really happy to see that there was a Linux exchange server client, but PLEASE tell me that I'm missing something..

I have about 200Mb of messages on my exchange server, and no matter what I seem to do, when I start EVOLUTION it takes about 1 hour to work out where it is!

There is a config option "automatically synchronize account locally" but I'm not sure if that is forcing this repeated download, or if it should run once then just do a quick sync on subsequent loads ( it doesn't ).

I also see that each FOLDER can be set to a state of "Copy folder content locally for offline operation" but as with the other sync there is no documented details about what this actually does.

So - can anyone help?  If this thing takes 1 hour to first sync folders, then download, then someone wasn't thinking very straight when the created the spec!

How is it supped to work?  What I am doing wrong?

TIA

Keith

---

### Post by Old Pink on 2006-12-12
Don't have any sync options checked, but set "Leave mail on server" as checked.

This way you simply download new mail, and ignore the older stuff.

If all else fails, [**Thunderbird**]("http://www.mozilla.com/en-US/thunderbird/") is better anyway.

---

### Post by thewump on 2006-12-12
That sounds like advice for someone using POP.. I don't think Exchange Server has that option, and I know for sure, that Thunderbird doesn't support Exchange server.

Keith

---

### Post by Rodneyck on 2006-12-12
There are several email clients for linux, but not many that offer exchange support.  I like Evolution, it's fast and efficient for what I need, but I also only use it for POP.

Here are some other solutions re MS exchange...

[http://linuxmafia.com/faq/VALinux-kb/ms-exchange-replacements.html](http://linuxmafia.com/faq/VALinux-kb/ms-exchange-replacements.html)

---

### Post by thewump on 2006-12-12
Sadly, it seems that Evolution is infact the ONLY client that works with Exchange server. The bynari client as far as I can tell is no more.

Most of the items on that list are about how to replace Exchange Server itself with a Linux solution, not how to connect to Exchange server from Linux.

I ALMOST had it, by installing CrossOver ( beta ) Windows emulator and running Outlook - it was fine, except that my Exchange server providor requires a screen that only seems to appear in Outlook Connections Tab after SP2 has been added to XP.. and that isn't part of Crossover ;-) Frustrated!

Seems like this is one of the last places that Microsoft have a strangle hold. It seems like the attention to detail of Evolution in this area is lacking.. In fact, I've read some rather negative things about it's post Novell purchase development, and for me you can tell how motivated a company is to develop something exelent in the small things.. Like their link to the Knowledge base at Novell.com goes to the root of the knowledge base, not to the Evolution section.. That's sucky!

Keith

---

### Post by Rodneyck on 2006-12-12
There is one last thing you might try. Search for portable programs. I know there is one for Microsoft Office 2003. These "portable" programs  run under WINE with great success. 

I have not tried the MS Office, although I know it exists.

---

