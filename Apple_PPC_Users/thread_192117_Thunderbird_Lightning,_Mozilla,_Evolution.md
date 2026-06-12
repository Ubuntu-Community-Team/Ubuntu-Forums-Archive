---
title: "Thunderbird Lightning, Mozilla, Evolution"
date: 2006-06-08
forum: Apple PPC Users
---

### Post by ubuntubrian on 2006-06-08
Several questions:
1. Is there a package for UbuntuPPC for Lightning0.1?
2. How can I import evolution mail, contacts, etc. into the Mozilla suite?
I'm sick of the junk filters on Evolution not working, even after all the configuring and I'd be haapy with the Mozilla suite if I can do the importing of Evolution.
Many thanks

---

### Post by diahrk on 2006-06-19
hi, it's actually as simple as that:

1. install thunderbird - create a profile. 
in case you have already installed & used it, backup your thunderbird config folder. (the ".mozilla-thunderbird" in your home folder). 

2. just copy your "Inbox", "Sent", "Drafts" &c. folders from your Evolution mail folder over the resp. files in your thunderbird account mail folder in ".mozilla-thunderbird".

that's it.

NOTE: that's the simple way - and it works! if you already got mail in your thunderbird account, you could give it a try and rename your evolution-files before copying (like inbox_evolution...). as soon as they show up in thunderbird, just copy the messages over to the folders you want them in...

good luck
dirk

---

### Post by ubuntubrian on 2006-06-21
Thanks-I'll give it a try. I'm a bit suspect as one of the guys in our LUG told the hair-raising story of losing all of his Thunderbird mail-all of it! He's quite adept and knows that it's nothing he did so I wonder if it's Thunderbird connected. Probably not since about 1/3 of all his home directories evaporated too!

---

### Post by ubuntubrian on 2006-06-21
I tried this and it didn't work. I copied my .evolution/mail/local/inbox into .mozilla-thinderbird/wierdnumbers-default/mail/localfolders/inbox.sbd and although the mail shows up in the directory it does not show up in the mail application. Help?

---

### Post by ubuntubrian on 2006-06-21
I finally copied each file in .evolution in the inbox directory and that worked. Now I'm trying contacts and found this:
fter a long session of searching and browsing I’ve found that the solution exists. And it is the easiest and most obvious solution out there.
Ryan’s Scraps managed to find somehow the most straightforward solution, which he himself admits to be almost hidden online for some reason:

Ryan describes Exporting Evolution Contacts to Thunderbird:

Locate the path to an obscure Evolution utility called evolution-addressbook-export (Simply write locate evolution-addressbook-export for the exact path)
This utility will export your address book to CSV format, which you can then import to Thunderbird or any other mail client.

It’s really simple once you know what to use and where to find it:
/usr/lib/evolution/2.X/evolution-addressbook-export --format=csv > contacts.csv

Now just import it into Mozilla Thunderbird (Addressbook – Tools – Import).

But I get a 'segmentation fault' error. Plus, where would the exports end up?

---

### Post by slight on 2008-05-28
For anyone unsure how to export calendars from evolution, you need to right click on the calendar name in the calendar view and select "save to disk". Took me a while, had to Google it, as I was expecting an export in the main menus. Make sure you include .ics in the filename as it's not automatically appended.

(Sorry to bring up an old thread but it came up for me in Google so it may for others too)

---

