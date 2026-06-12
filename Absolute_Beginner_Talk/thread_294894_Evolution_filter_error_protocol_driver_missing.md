---
title: "Evolution filter error: protocol driver missing"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by ubunovi on 2006-11-07
Hello out there,
I'm using "edgy" with Evolution 2.8.1. Most things working just nice. But now there is a problem: i invoked a local mail filter to work on a IMAP-Inbox. It's set up as follows (translations from German interface):

Search objects, that has
Subject includes: [list-identifier]
then
move to folder: Mailinglist_Folder.

Now I collected a number of incomming mails with [list-identifier] in their subject.
(1) The filter doesn't work on new incomming mail (yes, I activated that option in preferences of that account ;-))
(2) If I try to work with filter manually (mark all messages in Inbox, choose "Apply filters" from menu "Message"), I get this error message:

Fehler bei »Ordner wird gefiltert«.

Kein Treiber für Protokoll »email« verfügbar

Can anyone help, please!

Thanks
Frank

---

### Post by ltorgo on 2006-11-16
I have exactly the same problem with one of my computers. The other one works flawlessly. 

The one that fails is an AMD64, while the other is a 686 laptop (I'm adding this info as it is the only difference among them as far as I can see...).

Luis

---

### Post by ubunovi on 2006-11-16
Hello Luis,
I managed my problem by deleting all the rules and rebuild them from the right-click-context-menu over the subject of incomming mails.
This way everything works just fine for me.
Hope this may help you too.
Regards
Frank

---

### Post by ltorgo on 2006-11-17
Hi Frank,
Thanks for the tip! It also worked with me!... kind of odd though...

---

