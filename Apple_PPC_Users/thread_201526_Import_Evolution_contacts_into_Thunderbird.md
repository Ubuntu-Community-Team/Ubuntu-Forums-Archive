---
title: "Import Evolution contacts into Thunderbird"
date: 2006-06-21
forum: Apple PPC Users
---

### Post by ubuntubrian on 2006-06-21
I finally copied each file in .evolution in the inbox directory and that worked. Now I'm trying contacts and found this:
"After a long session of searching and browsing I’ve found that the solution exists. And it is the easiest and most obvious solution out there.
Ryan’s Scraps managed to find somehow the most straightforward solution, which he himself admits to be almost hidden online for some reason:

Ryan describes Exporting Evolution Contacts to Thunderbird:

Locate the path to an obscure Evolution utility called evolution-addressbook-export (Simply write locate evolution-addressbook-export for the exact path)
This utility will export your address book to CSV format, which you can then import to Thunderbird or any other mail client.

It’s really simple once you know what to use and where to find it:
/usr/lib/evolution/2.X/evolution-addressbook-export --format=csv > contacts.csv

Now just import it into Mozilla Thunderbird (Addressbook – Tools – Import).+

But I get a 'segmentation fault' error. Plus, where would the exports end up?

---

### Post by ubuntubrian on 2006-06-22
I tried many approaches and finally used kmail as the import tool. kmail can import almost any format and export as a different format so I imported vcards and exported .ldif file and then imported that into Tbird. I'm using Plan as my calendar.

---

### Post by towsonu2003 on 2006-09-25
this one helped me a lot.thanks :)

---

### Post by kkuzia on 2006-09-26
> **ubuntubrian said:**
> I tried many approaches and finally used kmail as the import tool. kmail can import almost any format and export as a different format so I imported vcards and exported .ldif file and then imported that into Tbird. I'm using Plan as my calendar.

I am trying to use Kmail right now, but for some reason, I cannot find any option in it to import contacts (heck, I cannot even get the address book to open since the button is greyed out).  I can find the import messages option, just not contacts.  Am I missing something obvious? ](*,)

---

### Post by towsonu2003 on 2006-09-26
> **kkuzia said:**
> I am trying to use Kmail right now, but for some reason, I cannot find any option in it to import contacts (heck, I cannot even get the address book to open since the button is greyed out).  I can find the import messages option, just not contacts.  Am I missing something obvious? ](*,)

From which program to which program are you trying to migrate?

---

### Post by tagra123 on 2006-09-26
MoreColsForAddressBook is a Thunderbird extension that adds several nice features including vcard import.

[http://www.extensionsmirror.nl/index.php?showtopic=3831](http://www.extensionsmirror.nl/index.php?showtopic=3831)

---

### Post by kkuzia on 2006-09-26
> **towsonu2003 said:**
> From which program to which program are you trying to migrate?

Trying to migrate from Evolution to Thunderbird (if at all possible).

---

### Post by Stefano Fonzarelli on 2006-11-14
I worked around the same problem today! I didn't know about the Thunderbird plugin, but it probably does it in about the same way.
Manually, it works like this:


To make it easy, I will specify the steps from scratch:

1 - export an addressbook from evolution to a vcard

2 - open the exported vcard ( a .vcf file) in the program Kaddressbook

3 - export the addressbook again form Kaddress as a .csv file

4 - open the .csv in a spreadsheetprogram such as OpenOffice or Excel

5 - you now see the fieldcontents in rows A to ..

6 - IMPORTANT!!! fill all culomns that are completely blank with an X. Thunderbird has trouble importing files with columns that are not filled to any extend.

The next steps a a bit more tedious. Thunderbird does not keep the same order in Fieldnames. You can see this is you run the import routine and get to the point where you can mark/unmark the fields that are to be imported. Marks on the left, fieldnames in the middle and the expected contents on the right.
If you don't change the order and or deselect unused fields (like the ones you filled with X-es previously) you will get the "f-ed up" results as described by Phil.

It is advisable to write a list of all the optional fields that Thunderbird uses in its format in its subsequent order. And list of your own corresponding fields is also handy. 

So choose step 7 or 8 to get the results you can actually use.

7 - insert, delete and move columns in the spreadsheet, to make shure that you have data for all the fields that Thunderbird expects it. And make sure none of the columns is completely empty can't state it enough)

8 - remove all columns with information you don't want to import

The final steps:


9 - select all the rows and columns you need (no more, no less and use the SAVE-option to export the data as a .csv-file again. Use another name as the one before, so you can mess it up as many time as you want to.

10 - choose import, addresses from within   Thunderbird and take the steps to the point where you have to mark/unmark the fields. Luckily Thunderbird will remember you previous selection, so you only have to deselected sooo much one time.

11 - mark the fields for import and optionally move fields up and down to sort them. (whether or not this is necesary depends on the method you chose earlier.

12 - click finish and .... Voila! (if the results are not correct, you made a mistake somewhere. Try and analyze where you went wrong. You are bound to find out soon enough.)

Good luck,

Steven

Can anyone help me with the mail-import. Importing about a 1000! mails one-by-one is just too much.
There must be another way. Moving around files in the .evolution/... directories is getting me nowhere.

---

### Post by dmBriarwood on 2006-11-16
Can you really say "Voila" after a 12 step procedure to transfer contacts from one open source mail application to another?  Absolutely no offense meant at all Steven, I'm just completely flabbergasted at how completely lame the import utilities are for t-bird.  (I realize that T-bird is Mozilla which isn't Ubuntu - but my brush gets broader the more frustrated I get).  I want to get t-bird working on my Ubuntu 6.06 as evolution is broken - it can import lickety split from Outlook or Outlook Express - where's the love for us Ubuntu fans who struggle for days to get things like 1440x900 monitor resolutions to work on three year old video cards, or dreaming of one day syncing my palm pilot with some sort of application on ubuntu (it was this attempt I suspect that broke my evolution).  I'm embarrased to say my Ubuntu distribution is as flakey as my old Windows 2000 box!  Screen locks, kernel panics - at least Microsoft gave us the blue screen of death!  Ubuntu acts like it was turned to stone.  I used to love working on my Ubuntu distro - it was the backbone of my computing work - now it has been supplanted by a more dependable 3 year old laptop running XP.  

Sorry - I'm full of bile.  As I run into these ridiculous problems, basic,, basic configuration issues on standard hardware with the most common (reputedly the best open source software packages available) I'm becoming more and more discouraged.

---

### Post by pediatracancun on 2007-06-09
The easiest way I've found is by using the following link: [http://labs.brotherli.ch/vcfconvert/](http://labs.brotherli.ch/vcfconvert/) 

Save your Evolution contacts with File - Save contacts as vcf card.

Then using the above link, just chose the vcf card file, and it will transform it into a ldif file, which can be read by Thunderbird.

---

### Post by gerbman on 2007-09-27
> **pediatracancun said:**
> The easiest way I've found is by using the following link: [http://labs.brotherli.ch/vcfconvert/](http://labs.brotherli.ch/vcfconvert/) 

Save your Evolution contacts with File - Save contacts as vcf card.

Then using the above link, just chose the vcf card file, and it will transform it into a ldif file, which can be read by Thunderbird.Is anyone familiar with a better process of importing ldif files into the "Personal Address Book" than the one at the bottom of [this]("http://www.unit.villanova.edu/pc/address_book.html") page? That procedure works, but it's an awful lot of work for such a trivial operation.

---

### Post by tonywhelan on 2008-06-10
> **tagra123 said:**
> MoreColsForAddressBook is a Thunderbird extension that adds several nice features including vcard import.

[http://www.extensionsmirror.nl/index.php?showtopic=3831](http://www.extensionsmirror.nl/index.php?showtopic=3831)

I just found this same extension today and it worked perfectly when importing VCF format address books produced by Evolution.

The author's website is [HTML]http://nic-nac-project.de/~kaosmos/morecols-en.html[/HTML]
Download the addon and install in Thunderbird. Then when you create a TB address book, you can select it and then go to the Tools menu.
There you'll have an item called Actions for Contacts, then click Import VCARD/VCF. 
It takes a minute to do the work but the results I got were perfect, without any mangled or misplaced data.

---

### Post by Sukarn on 2008-06-18
> **tonywhelan said:**
> I just found this same extension today and it worked perfectly when importing VCF format address books produced by Evolution.

The author's website is [HTML]http://nic-nac-project.de/~kaosmos/morecols-en.html[/HTML]
Download the addon and install in Thunderbird. Then when you create a TB address book, you can select it and then go to the Tools menu.
There you'll have an item called Actions for Contacts, then click Import VCARD/VCF. 
It takes a minute to do the work but the results I got were perfect, without any mangled or misplaced data.

Yeah, it worked for me too, for the most part.

If a field was present twice for someone, then only one of them got imported. I had some people with multiple Mobile or multiple Work numbers or multiple something else, and only one of each field was imported into Thunderbird.

---

