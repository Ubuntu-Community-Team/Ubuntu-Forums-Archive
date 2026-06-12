---
title: "Gmail on Evolution"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by wintersenda on 2008-02-15
Hi,
   HI having trouble connecting Evolution with Gmail from work. Tried using pop and imap using 

[http://mail.google.com/support/bin/answer.py?answer=78799](http://mail.google.com/support/bin/answer.py?answer=78799) 

and having a look at some other posts however i am still getting the error.

"Could not connect to imap.googlemail.com: Input/output error"

 I have enabled pop and imap in gmail. Have tried gmail, googlemail, gmail:993 etc. If someone could point me in the right direction it would be much appreciated.
Enda

---

### Post by vikrant82 on 2008-02-15
Use IMAP.

Receiving Mail options:

imap.gmail.com
Security : SSL encryption
Authentication Type : Password 

Sending Mails : 
smtp.gmail.com
Security : TLS
Type : Login

Last Tab : IMAP Headers
Basic Headers(second option) works fine for me ...

Everything works like charm, I seldom need to go to my web gmail. :)

---

### Post by LittleLORDevil on 2008-02-15
I am a big fan of Thunderbird, G-Mail is as easy as putting in your login info for Thunderbird.

---

### Post by erginemr on 2008-02-15
+1 for Thunderbird. 

I remember having used GMail with POP/SMTP. Chances are that it will be less problematic for Evolution if you retrieve your mails via POP instead. You can enable GMail POP3 fuctionality with:
[http://mail.google.com/support/bin/answer.py?answer=13273](http://mail.google.com/support/bin/answer.py?answer=13273)

---

### Post by vikrant82 on 2008-02-15
POP works plain old easy. But my concern here is manageability. With POP I cant manage my mails at gmail inbox.

IMAP gives you all google labels in form of local mail folders. You can manage your mails better on gmail servers through IMAP.

Also with evolution you can have a unified google and personal calendar. You can get reminders based on your google calendar events and create events right from evolution.

Also With POP3, in case of gmail, mails are not always synchronized between your local mailbox and gmail mailbox. Lets say, you delete mail in your mailbox, that is not deleted at gmail servers etc.. Ofcourse you can create your local folders and filter them, but then they have no integration with gmail folders/labels. 

IMAP is the way for me. I can move mails between folders in my local box, and changes are propogated to gmail.

However note that deleting a mail from Inbox in evolution merely removes Inbox label from that message at gmail. You might want to delete it from "All Mails" folder also in your local mailbox to get it to trash in gmail box.

---

### Post by mbsullivan on 2008-02-15
Hi all,

wintersenda, have you solved your problem with the previous suggestions? If not, I can dig around and see what configuration I've got.

I've used both Evolution and Thunderbird with GMail, so...

> with evolution you can have a unified google and personal calendar

With the [lightning plugin]("http://www.mozilla.org/projects/calendar/lightning/"), Thunderbird can have a personal calendar, much like Evolution. Another [addon]("https://addons.mozilla.org/en-US/sunbird/addon/4631") extends this functionality to Google calendars (with read/write access), so the Thunderbird/Evolution debate really comes down to a matter of taste.

As for me, I prefer Thunderbird. This is partly based on the fact that I've found it to be less buggy, and also because I found IMAP to GMail to be god-awful slow through Evolution but not Thunderbird, for some reason.

Mike

---

### Post by vikrant82 on 2008-02-16
> As for me, I prefer Thunderbird. This is partly based on the fact that I've found it to be less buggy, and also because I found IMAP to GMail to be god-awful slow through Evolution but not Thunderbird, for some reason.

I just tried thunderbird with IMAP and those plugins, and I couldn't agree more. Switching from Evolution to ThunderBird. :)

---

