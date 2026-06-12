---
title: "Icloud and Ubuntu"
date: 2011-10-13
forum: Apple Hardware Users
---

### Post by bash321 on 2011-10-13
will i cloud ever work on ubuntu or thunderbird???

is there a way??? for mail contacts and calendars..

---

### Post by scorp123 on 2011-10-14
You could use Dropbox ...

---

### Post by bash321 on 2011-10-14
dropbox doesn't have mail and calendar... and contacts.. it only stores files...

---

### Post by bash321 on 2011-10-15
I know how to get Icloud working on Ubuntu

If I could get some assistance in testing it would be great..

1. Hopefully my exchange icloud still works, not sure at the moment. but the IMAP Icloud Settings do work.
This probably would work on Microsoft Windows Xp.. if you have outlook 2007.
This Current configuration works on apple iphones and Apple OSX SNOW LEOPARD.

[http://support.apple.com/kb/HT4864](http://support.apple.com/kb/HT4864)

using the documentation provided by apple.
CALENDAR ICAL SETTINGS ALSO WORKS ON BOTH DEVICES.
TRY THESE SETTINGS ON SNOWLEOPARD OSX OR WINDOWS.. AS THEY WORK. THE ONLY PROBLEM IS MOZILLA OR UBUNTU?
THE CONFIGURATION SPECIFICALLY NEEDS SSL IMAP.
This is the IMAP Configuration. **Currently I do not know the Exchange push configuration**, but  THE IMAP CONFIG does work. 

2. You need to specify the write server configurations. 
the incoming server is:
imap.mail.me.com
port 993
*it will think you are a mobileme account I hope this is not a problem in the future..*
your username is just 
your user not the @me.com part...
example would be where it saids username...
email address: [email]john.smith@me.com[/email]
username: john.smith
**The Imap Authentication on a Mac computer is Password.**
this is where I am stuck on linux...
you may also need a CA Certificate for the settings to successfully work.
hopefully thunderbird would ask you. but I don't think it does at the moment.. or not very well anyway.. so.. thats another problem with linux and mac.


3. Smtp Settings
smtp.mail.me.com
username: same as before..
username: john.smith
do not put @me.com
it should then ask you for a CA Certificate... hopefully.. thats what it did on snow leopard. but it didn't work on ubuntu.

I need some help for people to test these settings to see if they work... as this is the mail problem with icloud on ubuntu at the moment. 
Bash.321

---

### Post by scorp123 on 2011-10-15
> **bash321 said:**
> dropbox doesn't have mail and calendar... and contacts.. it only stores files... And now guess where your mails and calendard entries get stored?? **In files.** Sync the right files via Dropbox (e.g. **~/.mozilla*** ) and voila, problem solved. Even works across platforms if you do it right: Linux, Windows, Mac OS X

That's how I've been syncing my stuff in the past 3 years ... loooong before Apple "invented" it. LOL.

---

### Post by bash321 on 2011-10-16
The Problem with Dropbox is that the syncing of files is relatively slow to icloud.

So I do not believe Dropbox is a better option.
Icloud is a whole lot quicker in speed even using the IMAP Protocol.

The Exchange Sync protocol that it uses for the iphone, mac os x lion, and windows 7 is instant sync and much quicker than wasting space on dropbox for a whole program, where that can be filled with important documents or files.

---

### Post by scorp123 on 2011-10-16
> **bash321 said:**
> The Problem with Dropbox is that the syncing of files is relatively slow to icloud. Can you backup that claim with hard benchmarks?? Dropbox only uploads changed portions of a file. I have several large files in my Dropbox account and have absolutely no problem syncing them across 8 or so computers that are in different locations.

And if you really really really want iCloud: you'd have to bug Apple about it. 

> **bash321 said:**
>  Icloud is a whole lot quicker in speed even using the IMAP Protocol.  No idea what you're talking about. And I seriously doubt you know that either. :lolflag:

IMAP is a protocol for downloading mails.
[http://en.wikipedia.org/wiki/Imap](http://en.wikipedia.org/wiki/Imap)

And how iCloud can be quicker than Dropbox ... I seriously doubt you've conducted any benchmarks. Sync a 100 MB, 1 GB and a 2 GB file from the very same computer using the very same Internet link ... yes, ***that*** would be a benchmark. Anything else here is just fanboyism on your part.

I am out here. Go bug Apple :lolflag:

---

### Post by DizzyTech on 2011-10-16
For [mail.](http://help.apple.com/icloud/index.html?lang=en#mmdd8d1d47)

**Contacts: ** Add a CardDAV account to your Address Book application.  The server URL is either [https://p01-contacts.icloud.com:443](https://p01-contacts.icloud.com:443) or [https://p01-carddav.icloud.com:443](https://p01-carddav.icloud.com:443).  Whichever works first.  Log in with your Apple ID and password.

**Calendar: ** Same deal.  This time, add a CalDAV account.  The server URL is either [https://p01-calendar.icloud.com:443](https://p01-calendar.icloud.com:443) or [https://p01-caldav.icloud.com:443](https://p01-caldav.icloud.com:443).  Whichever works first.

**Documents: ** Must be accessed via iCloud.com.

---

### Post by bash321 on 2011-10-17
I ll ask my question again as it was not clear enough.

I would like to use Apple Icloud Services on Ubuntu and have them sync with my email and calendar program Mozilla Thunderbird that is currently on Ubuntu. Is there anyway of integrating these services.

I have currently gotten the IMAP Protocol to work on Apple Mail and Windows Live Mail on Windows. from the apple support links above.
For some reason the imap protocol for incoming mail does not work in Thunderbird mail.

Bash.

---

### Post by bash321 on 2011-10-17
Thanks to Dizzy tech the mail settings do not work on my thunderbird.. which is 9.0 aurora daily build or 7.0 thunderbird on windows 7.. so I found another support topic about these settings on mozilla's blog site. mozilla messaging..
[http://getsatisfaction.com/mozilla_messaging/topics/icloud](http://getsatisfaction.com/mozilla_messaging/topics/icloud)
I will cross post the problems that I have been having..
I will test out the calendar settings and contacts..

Bash.

---

### Post by bash321 on 2011-10-17
dizzy tech settings for contacts and calendar do not work in thunderbird mail on ubuntu.

bash.

---

### Post by sokol99 on 2011-12-25
Dizzy's settings seem to 'almost' work for me in Evolution.  I don't get any errors searching for contacts when using the first path but the second gives me an error.  

... But I don't get anything back when searching either so...  Close?:confused:

---

