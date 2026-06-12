---
title: "Sharing emails between my 3 pc."
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by Nevermore on 2005-11-27
I need to keep copies of work emails in different computers:
for example i need to keep copies in my office computer
copies in my home computer
and copies in my laptop
as well as attachment

at the moment i can't do that, since i have Win Xp at office computer with Eudora, ubuntu at home and in laptop with evolution (which i dun like being too similar to outlook).

I wish to install thunderbird, so that i can share emails from win to lin..
could someone give me please some hints about that? i suppose i have to samba the win machines...can i make a symlink called sync that would do all in batch?
Thanks

---

### Post by Kvark on 2005-11-27
Don't use POP3, it was designed specially for people who check their email from one computer only and use dail up for that computer. Thats why it keeps the emails on the local computer.

Use IMAP instead, it was designed for people who check their email from several different computers. It keeps the emails on the server so you have all your emails with you no matter where in the world you check your email from.

---

### Post by ssam on 2005-11-27
IMAP or webmail is the best solution.

another way to do it is to tell each email client to leave the email on the server for n days (where n is long enough that you will have check email on each computer by then).

do you really need to do this?

could you just use your laptop everywhere or have seperate email accounts (a work account and home account).

---

### Post by Nevermore on 2005-11-27
[QUOTE=Kvark]Don't use POP3, it was designed specially for people who check their email from one computer only and use dail up for that computer. Thats why it keeps the emails on the local computer.

Use IMAP instead, it was designed for people who check their email from several different computers. It keeps the emails on the server so you have all your emails with you no matter where in the world you check your email from.[/QUOTE]

the problem with imap is that not every server supports it and also the space online onto the server is not infinite..

---

### Post by ssam on 2005-11-27
[QUOTE=Nevermore]the problem with imap is that not every server supports it and also the space online onto the server is not infinite..[/QUOTE]

in those cases then one could set up a local IMAP server that downloads from the POP server. but that would be quite a job to do.

---

### Post by Kvark on 2005-11-27
[QUOTE=ssam]in those cases then one could set up a local IMAP server that downloads from the POP server. but that would be quite a job to do.[/QUOTE]
Yeah, that'd be some work to set up. It would be easier to get an email service that supports IMAP and set the old address to forward to the new address.

Or just keep juggling around with POP3 to check from all of the computers before the mail gets deleted from the server, but then you still can't check from a library or a friend's place.

---

### Post by Nevermore on 2005-11-27
actually what i am looking for is something that can synch my mail between the computers.
i mostly use my work computer for reading emails, and i only use the laptop when is absolutely needed too, if i could copy the mail from work to laptop when i want it would be perfect.
then i can bring also to home computer.
this is not gonna happen every day, but more likely every week or 15 days...

---

### Post by skirkpatrick on 2005-11-27
I have a dual-boot laptop that your system could be setup to be similar to.  I setup Thunderbird on Windows and told it to store all the user files (address book, mail, etc.) to a FAT32 partition.  Then I installed Thunderbird on Linux and made symlinks for the .mab files and mail folders.  Changes to the address book or emails from one OS is reflected in the other OS.  You should be able to do this using a USB drive instead of a hard drive partition.  Then you could carry carry it back and forth.  In fact, I've seen mention of setting up Thunderbird and Firefox completely on a USB drive so you can take your browser and email anywhere you go.  Check out the forums at [http://www.mozillazine.org/](http://www.mozillazine.org/).

---

### Post by ssam on 2005-11-27
[QUOTE=skirkpatrick]In fact, I've seen mention of setting up Thunderbird and Firefox completely on a USB drive so you can take your browser and email anywhere you go.  Check out the forums at [http://www.mozillazine.org/](http://www.mozillazine.org/).[/QUOTE]

i like that idea. of course you might need to sort out having windows and linux version installed on the same drive, but i am sure its possible.

just make sure you back it up somewhere, you wouldn't want to loose all you email.

---

