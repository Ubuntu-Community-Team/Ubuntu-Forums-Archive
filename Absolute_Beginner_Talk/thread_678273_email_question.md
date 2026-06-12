---
title: "email question"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by greg m on 2008-01-25
is there a program that will move email from one linux os to another? i`m going to install 7.10 on a new (er) computer i have email on 6.1 , bsd, two other linux, and winblows xp. i`d like tham on one  computer, that i use just for email. if there is not a program, how can i do it?

thank you greg

---

### Post by seventhc on 2008-01-25
I'm not so sure about that especially since it's between different platforms. Couldn't you just save the folders?
or if it's on a network you might be able to store everything on the server then access it all from the one computer and bring it over to where you want. Not sure about a program though not without paying anyway.

---

### Post by greg m on 2008-01-25
where can i find the folders? i looked on one of the HD`s i have (each OS is on a HD) and i found the folder for what i think is thunderbird, but nothing was in the fouder. so it must some place else. 

thank you greg

---

### Post by PeterJS on 2008-01-25
What kind of mail server do you get your mail from? If it's an IMAP server it has copies of all your mail on it and you won't have to migrate anything just point the new client at it, and you're golden. If it's a POP server you're going to need to migrate your mail, which I can offer no insight on.

---

### Post by seventhc on 2008-01-25
I can't remember exactly where they are, but probably in a profiles folder maybe under mozilla/thunderbird or just thunderbird profiles something like that. Sorry it's been a long time since I've used thunderbird. If you can boot into each system Isn't there an export feature  in thunderbird for backing everything up?
look at this link it gives info for different systems. :) In ubuntu it will be in your home folder.
[http://home.att.net/~cherokee67/mailfldrloc.html]("http://home.att.net/%7Echerokee67/mailfldrloc.html")

---

### Post by smurphy_it on 2008-01-25
You could try exporting the information out of Mozilla Thunderbird.  At the very least you should copy out the profile/mail directory.  In your home folder should be a folder called [COLOR="DarkRed"][B].mozilla-thunderbird
[/B][/COLOR] (Which is a hidden folder).

Go into that folder, then go into the only listed folder there (random name dependant upon install) and in there will be a Mail folder.....

If you had a pop account on say sprint, then you would have a folder structure like pop3.sprint.ca.... copy out that entire folder structure... that should be all of your emails.

Next copy that folder structure into your new mail setup (assuming you will be using mozilla thunderbird again).

Otherwise, try exporting all of your emails out or saving them as documents.

---

### Post by jkzubu on 2008-01-25
Greg m -

I would follow the advice of PeterJS and use the IMAP.  Since you have multiple machines with e-mail that you want to consolidate (I think this is what you are asking), the easiest and quickest way I know  to consolidate these e-mails is to use the IMAP, because it is automatic.  If you have different e-mail addresses on each machine, I know this will work.  If you have the same email address on all machines, I think it will still work but you may have to be a little creative.

IMAP - Simply,  is a server-based mail system that will automatically place all of your e-mail messages (once you set the settings) to the server and automatically update all of your e-mail clients so they are all the same.  The mail resides on the server until you delete it.  If an email comes or goes or is deleted, all of your e-mail clients reflect the changes.  If all you want to do is get all of your e-mail in one place, you can always turn off IMAP once you have everything where you want it.

First - on each machine delete as much old e-mail as you can.  Not really a requirement, but strongly recommended.  The Google account you will need for this method has a 4GB limit.

Second - Google offers free e-mail with IMAP.  If you don't already have a Google account, you will need to set one up for this method.  Additional IMAP details available on Google.  Set up your new account and activate IMAP in the mail settings.

Third - Set up each of your machines mail clients to Google-recommended settings for IMAP.  See Google for Details.  You will obviously need to do one machine at a time.

Fourth - Allow Google to accept mail from your existing accounts (a/o email addresses).  Then allow, and go through the procedure to verify.  Then sit back and let the computer do all the work.  Repeat for each computer.

Once you new install is ready to go, configure the the new mail program to IMAP and the mail client will sync with the server.  That should pretty much be it.

JK

---

### Post by seventhc on 2008-01-25
If it's a google account and the mail wasn't deleted from the server then you don't have to do anything other than setting up the new machine for imap. All the mail should be either in your 'all mail' folder' or it will be in your inbox. either way the new imap set up can retrieve all of them. I use imap and never worry about going from one machine to another. The only thing I save are my mail config files since I use mutt. save mailcap and muttrc

---

### Post by greg m on 2008-01-26
thank you alll, i may be able to do it now. i hrad my email at my isp, take out most of the junk, some of the scams i`ll keep (they are funny) and i`ll trace them when i feel like it. i like os`s so i have email all over the place, until i stick with one main os. i was using ubuntu as my main computer, until i tried to add new vider drivers  ( i have to stop doing that , it`s the only problem i have with linux)


thank you greg

---

