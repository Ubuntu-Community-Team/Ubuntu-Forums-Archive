---
title: "Problems when opening Mozilla Thunderbird"
date: 2011-09-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pauloz on 2011-09-15
Hello

I'm trialling Ubuntu 11.10 on my 1005HA netbook and when I open up Mozilla Thunderbird, I get the following message:

"There was a problem opening the address book "Ubuntu One" - the message returned was: Cannot open book: Could not create DesktopcouchSession object"

I'm not interested in having Ubuntu One because Dropbox is doing everything I need. When I try to delete the Ubuntu One Address Book I get the following message:

"Sorry - this version of EDS Contacts Integration does not support deleting Evolution address books. Due to the way that Thunderbird tries to delete address books, all of your EDS address books will appear to be removed from the address book manager.  Simply restart Thunderbird in order to have them return."

I've uninstalled Ubuntu One - can anybody advise what I must do to stop this message appearing each time I open up Thunderbird? Thanks.

---

### Post by vtzhang on 2011-10-15
I had this as well updating to 11.10.

Go into Evolution and delete the UbuntuOne address book. This might require re-installing Evolution though.

---

### Post by pauloz on 2011-10-18
> **vtzhang said:**
> I had this as well updating to 11.10.

Go into Evolution and delete the UbuntuOne address book. This might require re-installing Evolution though.
Thanks vtzhang - I was beginning to think I'd never receive a reply. I had to install Evolution and then deleted the UbuntuOne address book, but it looks like I'll have to leave Evolution installed but will continue to use Thunderbird, which is my preference.

---

### Post by Mr.Goose on 2011-10-19
With all due respect, (re)installing something you don't want just to get rid of intrusive messages that should not be there in the first place, hardly justifies marking this problem as "solved"!

Surely there must be a cleaner way of solving this?

Best wishes, G.

---

### Post by pauloz on 2011-10-19
Fair comment - I realise I'm treating the effect and not the cause and because this posting is 4 weeks old and I had not received any reply, and it has alleviated my problem, I felt obliged to mark it as "solved".

---

### Post by practic on 2011-10-19
Go into Thunderbird Add-ons and remove anything relating to EDS integration or CouchDB/UbuntuOne.

If that doesn't get rid of the error, go into Synaptic and search on "couchdb". Sort by installed items and remove everything related to that!

---

### Post by Mr.Goose on 2011-11-03
@ Practic. Thanks for the suggestion - it certainly put me on the right track. 

In my case, simply disabling EDS integration in the Thunderbird Add-ons Manager fixed it. Didn't actually need to uninstall anything.

For anyone else who is stumped by this issue. Hopefully this should fix it for you...
 
1. Click "Tools" -> "Add-ons" menu item.
2. Select "Extensions".
3. Select  "EDS Contact Integration".
4. Press the "Disable" button.
5. Click "File" -> "Quit" menu item.
6. Launch Thunderbird again.

Voila! Problem solved. I hope this helps someone. :)

@Pauloz, I'd be interested to know if this works for you?

Best wishes, G.

---

### Post by pauloz on 2011-11-04
> **Mr.Goose said:**
> @ Practic. Thanks for the suggestion - it certainly put me on the right track. 

In my case, simply disabling EDS integration in the Thunderbird Add-ons Manager fixed it. Didn't actually need to uninstall anything.

For anyone else who is stumped by this issue. Hopefully this should fix it for you...
 
1. Click "Tools" -> "Add-ons" menu item.
2. Select "Extensions".
3. Select  "EDS Contact Integration".
4. Press the "Disable" button.
5. Click "File" -> "Quit" menu item.
6. Launch Thunderbird again.

Voila! Problem solved. I hope this helps someone. :)

@Pauloz, I'd be interested to know if this works for you?

Best wishes, G.
Thanks for the posting Mr.Goose. I uninstalled Evolution and did what you suggested and it looks like that has worked fine.

---

