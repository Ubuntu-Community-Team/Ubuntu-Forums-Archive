---
title: "Evolution and &quot;leave mail on server&quot;"
date: 2009-11-01
forum: Apple Hardware Users
---

### Post by rpras on 2009-11-01
Hi folks:

I have a feeling this may be a FAQ.  If this has been answered before, I apologize; my searches did not find a satisfactory answer -- please point me to it.

I am trying to set up Evolution on Karmic running on my 600MHz PowerPC iBook G3.  While setting up my accounts, I did not find an option to "leave mail on server."  Is this the default behavior in Evolution?  If not, where do I set it?

TIA

---

### Post by ChrnoMaster on 2009-11-01
When you open Evolution, go to **Edit > Preferences > **(select your account)** Edit > Receiving Options Tab**. You should hopefully find it there.

---

### Post by rpras on 2009-11-02
> **ChrnoMaster said:**
> When you open Evolution, go to **Edit > Preferences > **(select your account)** Edit > Receiving Options Tab**. You should hopefully find it there.

No -- don't have any such option.  Any other pointers?

---

### Post by sevenbluesuns on 2009-11-03
i am having the same issue. have attached a screeny of what that path shows up with.

ed. Could the fact that this is with a gmail account have anything to do with anything?

I have an imac which receives mail using thunderbird and leaves mail on the server, and i'm trying to setup evolution on my laptop which has ubuntu to receive all that mail so that i have all my mail on both machines.  I haven't put in my password yet because i don't want evolution to wipe out the server of all my mail.

halp

---

### Post by itkeepsrepeating on 2009-11-10
Same problem here. 

As far as I can tell by the help files, it says if you wanna use multiple clients on the same mailbox, to use evolution, and then set up message rules to forward everything to the other mail client directly via a file. 

Nothing I saw in there addresses multiple machines, same mailbox. 

I bet there's a preference file somewhere we can just edit to fix this, but it should be in the gui as well. Anyone know where that file is?

Alternate suggestion for someone more knowledgeable than me: I know Ubuntu's package choices aren't meant to be bleeding edge releases, so perhaps a repository for a more-updated evolution version?

Thanks in advance...

---

### Post by rpras on 2009-11-11
Okay -- the version of Evolution in Karmic is 2.28.1.  The window for "Receiving Options" looks like the one posted above by sevenbluesuns.  The older versions of Evolution did have the option to "Leave messages on server."

The good news is that Evolution is not wiping out my messages  from the server -- at least not for my Gmail account.  I have not checked if this behavior holds with other e-mail services.

Guess "leave messages on server" is now the default.

---

### Post by linuxopjemac on 2009-11-11
You can edit at:
Edit->Preferences->Edit Mail account->Tab Receiving Options
[IMG]http://mac.linux.be/Ubuntu/mail.png[/IMG]

---

### Post by rpras on 2009-11-11
> **linuxopjemac said:**
> You can edit at:
Edit->Preferences->Edit Mail account->Tab Receiving Options
[IMG]http://mac.linux.be/Ubuntu/mail.png[/IMG]

Is this on Karmic with Evolution version 2.28.1?  I've checked several times, but don't get this screen at all?  What protocol is your e-mail server using?  I have a gmail account set up that uses IMAP protocol and I get a different "Receiving Options" window.

---

### Post by linuxopjemac on 2009-11-12
ok, that could be the difference, I have a POP account...It's the same version though...

---

### Post by tuwe on 2009-11-12
> **rpras said:**
> Is this on Karmic with Evolution version 2.28.1?  I've checked several times, but don't get this screen at all?  What protocol is your e-mail server using?  I have a gmail account set up that uses IMAP protocol and I get a different "Receiving Options" window.

if you have imap the mail always stays on the server.

---

### Post by linuxopjemac on 2009-11-12
Gmail has the possibility to read its mail with POP settings.
[http://email.about.com/od/accessinggmail/qt/How_to_Access_a_Gmail_Account_with_any_Email_Client_via_POP.htm](http://email.about.com/od/accessinggmail/qt/How_to_Access_a_Gmail_Account_with_any_Email_Client_via_POP.htm)

---

### Post by itkeepsrepeating on 2009-11-13
> **tuwe said:**
> if you have imap the mail always stays on the server.

Perhaps with Gmail, but not with my mail. It's a DreamHost server, and if I check it through the web interface, read mail stays in the box until I delete it, obviously. But when I check it with Evolution, it deletes everything it downloads. I cannot find a setting to correct this. I am willing to manually edit a file, if pointed at the correct file.

---

### Post by rpras on 2009-11-14
> **tuwe said:**
> if you have imap the mail always stays on the server.

Thanks!!  That is good to know.

---

### Post by rpras on 2009-11-14
> **itkeepsrepeating said:**
> Perhaps with Gmail, but not with my mail. It's a DreamHost server, and if I check it through the web interface, read mail stays in the box until I delete it, obviously. But when I check it with Evolution, it deletes everything it downloads. I cannot find a setting to correct this. I am willing to manually edit a file, if pointed at the correct file.

Oh -- that must be so annoying.  Actually, I get the same behavior on my MSN/Hotmail account.  Not much of importance goes there, so I did not mind losing some e-mail.  However, if this were to happen to my GMail account -- that would not be good.

As far as I know, my MSN account also allows downloading e-mail via IMAP.  So, the behavior must be controlled by a server-side option.

More details are most welcome.

---

### Post by Stoneface on 2010-07-14
> **itkeepsrepeating said:**
> Perhaps with Gmail, but not with my mail. It's a DreamHost server, and if I check it through the web interface, read mail stays in the box until I delete it, obviously. But when I check it with Evolution, it deletes everything it downloads. I cannot find a setting to correct this. I am willing to manually edit a file, if pointed at the correct file.
I have the same issue. I use Evolution 2.30.2 on Maverick Meerkat. In the past I was able to use POP and leave messages X days on the server, but with the latest version of Evolution this is no longer possible. All messages will be removed from my hosts server as far as I understand (have not taken the risk yet) In Thunderbird I can leave messages forever on the server which I prefer. I am trying IMAP now as I use Evolution as a secondary api to access email anyways. So far I have not been able to get any headers, but that is a different issue. I wonder why Evolution removed the POP option to leave messages x days or forever on the server. See screenshot of Evolution's current receiving options tab:

---

### Post by silvagroup on 2010-09-22
This is bad and has been a weak point for Evo. yes imap works great but for pop this has been a real crippler and inconvenience with Evo.
And from the previous post the feeble option for leaving on server for set days now gone really brings Evo to a low as a pop client.
I am currently using Unison to keep my Evo synced to my laptop because of the lack of the "leave on server until I delete", not the optimum but it works, but I wouldn't need to do that if Evo did it the right way as Tbird does. Of course tbird is not a PIM so it's not a solution if a PIM is required.
If any one has any word of wisdom or a PIM that does it all please let us know !!!!

---

