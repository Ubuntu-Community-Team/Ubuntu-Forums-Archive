---
title: "How to import address book from Thunderbird to Evolution"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-24
I am running Feisty and want to import my address book from Thunderbird into Evolution. Both applications are running in Feisty itself. Can someone tell me how to do it? 

Searching the Support Forum archives, I came up with one discussion where a script had been written to do it in 2005. But it was not explained how to use the script, and year later those writing in asking how to use the script received no answer. Here is the link: [http://ubuntuforums.org/showthread.php?t=54023](http://ubuntuforums.org/showthread.php?t=54023)

Please let me know the best and easiest way to import Thunderbird's address book into Evolution. Thanks!

---

### Post by swarup on 2007-08-24
Surely someone must know how to import the address book from Thunderbird into Evolution. Both applications in Ubuntu 7.04 (Feisty).

---

### Post by Depressed Man on 2007-08-24
Open up the address book in Thunderbird. Under tools there should be an option called export. Click that and choose a file (I think most work but try the one that ends in .ldif or something). Now save it somewhere (anywhere, though I'd save it to your desktop so you can delete it later). Open up Evolution, go to contacts, then file > import. Then click on that file. 

That should be it. After it's imported you can delete that file on your desktop (or wherever you saved it).

---

### Post by swarup on 2007-08-24
> **Depressed Man said:**
> Open up the address book in Thunderbird. Under tools there should be an option called export. Click that and choose a file (I think most work but try the one that ends in .ldif or something). Now save it somewhere (anywhere, though I'd save it to your desktop so you can delete it later). Open up Evolution, go to contacts, then file > import. Then click on that file. 

That should be it. After it's imported you can delete that file on your desktop (or wherever you saved it).

There is no option called export in the tools menu.

---

### Post by swarup on 2007-08-24
Somebody out there must know how to import an address book from Thunderbird into Evolution?

---

### Post by helios on 2007-08-29
Ah, another example of the award-winning, highly-touted and much bally-hoo'ed community forum support in Ubuntu.  Hey, an unanswered question of this complexity is understandable.  

That's sad...really fellas, the Mint guys had this question answered in 22 minutes.  Here is the solution should anyone need it.

In Thunderbird,
* Go to Address Book
* Select the address book you want to export, then
* Click "Export" from "Tools" menu (Tools --> Export)
* In the dialog give a name and a location to save the export
* Select either "Coma Separated" or "LDIF" as type
* Then click "save" to export

Now that exporting is compleeted, we can move into import these from Evolution

In Evolution,
* Go to Contacts Window View
* Click File --> Import
* Go ahead and select "import a single file" option when asked
* Select the file we created when exporting from Thunderbird
* Then import the contacts

Note: It's better to create a new address book to import the contacts, but it's rather your choice.

helios

---

### Post by swarup on 2007-08-30
Helios,

Many thanks for a very clear explanation. I knew there had to be a good way to do this. 

- Swarup

---

### Post by swarup on 2007-08-31
> **helios said:**
> Ah, another example of the award-winning, highly-touted and much bally-hoo'ed community forum support in Ubuntu.  Hey, an unanswered question of this complexity is understandable.  

That's sad...really fellas, the Mint guys had this question answered in 22 minutes.  Here is the solution should anyone need it.

In Thunderbird,
* Go to Address Book
* Select the address book you want to export, then
* Click "Export" from "Tools" menu (Tools --> Export)
* In the dialog give a name and a location to save the export
* Select either "Coma Separated" or "LDIF" as type
* Then click "save" to export

Now that exporting is compleeted, we can move into import these from Evolution

In Evolution,
* Go to Contacts Window View
* Click File --> Import
* Go ahead and select "import a single file" option when asked
* Select the file we created when exporting from Thunderbird
* Then import the contacts

Note: It's better to create a new address book to import the contacts, but it's rather your choice.

helios

I tried this, and it worked-- to a certain extent. That is to say, it transferred all the addresses. But the problem is the following. The addresses in my Thunderbird account were organized into several mailing lists. And those mailing lists were not maintained in the transfer. Rather, in the imported version in Evolution, there are no mailing lists at all. All the addresses are just listed as single addresses. It will take me two full days of full time work or longer, to reorganize all those addresses into their respective mailing lists. 

Isn't there some way to do the transfer in such a way that the integrity of the mailing lists is maintained? 

I did the export from TB as "Comma Separated". I don't know if it would have made any difference, perhaps, if I'd done it as "LDIF"?

Once this all happened, then I tried to see if I could just drag and drop the mailing lists from the TB address book to the Evolution Contacts mailing list. But of course, it wouldn't drag.

I'd also be willing to open the TB mailing list, "select all" and copy all the addresses in that list, then "paste" them as a group into the Evolution contacts mailing list. I tried it, but it wouldn't work either. --At least in the way I did it.

Any suggestions? solutions?

---

### Post by lathanial on 2007-10-10
Exporting ldif or csv files from Thunderbird and then importing to Evolution does work partially. It won't import company name for instance although the information is in the file imported. Does anyone know if there is a way to map the fields from Thunderbird to Evolution?

Thanks
lathanial

---

