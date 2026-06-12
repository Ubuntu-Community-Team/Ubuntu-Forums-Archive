---
title: "evolution - export feature?"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-06-21
I'm switching e-mail clients (testing out Mozzlia-Thunderbird), anyway, just wanted to see if anyone knows a way to export from evolution?

I do not want to have to re-type all my contacts...

Any thoughts?

---

### Post by Haegin on 2005-06-21
[QUOTE=garnertr]I'm switching e-mail clients (testing out Mozzlia-Thunderbird), anyway, just wanted to see if anyone knows a way to export from evolution?

I do not want to have to re-type all my contacts...

Any thoughts?[/QUOTE]
 try saving them all as v-cards (on the contacts page FIle>Save AS VCard for each contact) dont know how many you have though so if you have hundreds this may be tedious (but better than typing them all in again)

---

### Post by jeremy on 2005-06-22
You can select them all, Ctrl+A, then export the whole lot into one .vcf file.

---

### Post by tonywhelan on 2008-06-10
To import Evolution address book to Thunderbird

I had program aborts when tried to use evolution-addressbook-export --format=csv so could not export to CSV, and importing CSV into Thunderbird seems to scramble fields anyway.

The most reliable method (doesn't scramble the fields) is as follows:

In Evolution, choose the address book you wish to export. Right-click and choose Properties, then click the "make default" checkbox.
Now in a terminal, run the command: ```
 evolution-addressbook-export --format=vcard > giveitaname.vcf
```
This will export the currently-default contact list to a single VCARD (vcf) file.

Now you need to add VCF import capability to Thunderbird:
See this site: [http://nic-nac-project.de/~kaosmos/morecols-en.html](http://nic-nac-project.de/~kaosmos/morecols-en.html)
Download the addon and install in Thunderbird. Then when you create a TB address book, you can select it and then go to the Tools menu.
There you'll have an item called Actions for Contacts, then click Import VCARD/VCF. 
It takes a minute to do the work but the results I got were perfect.

---

