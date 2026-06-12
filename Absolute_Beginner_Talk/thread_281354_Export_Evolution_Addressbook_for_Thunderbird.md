---
title: "Export Evolution Addressbook for Thunderbird"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2006-10-20
Y'all:

I wanted to stop using Evolution for a variety of reasons, and to use Thunderbird, again. If you want to do this, also, there are some things you have to think about... such as exporting your addressbook from Evolution, and then import it into Thunderbird.

There are not to many discussions on this, and not much guidance on the web that is explicitly for Ubuntu... so here is what I know about it. Please feel free to chime in and correct or add to this thread.

Here is what you have to do:

1. In Evolution, go to Contacts. Then under under File, save your addressbook as a VCard. Put the addressbook.vfc file in a directory that is handy for you.

2. Use synaptic and install kaddressbook. You are going to need this!

3. Open kaddressbook, the import the addressbook.vfc file. 

4. Save your addressbook in kaddressbook. Then export it as a .csv file... such as addressbook.csv.

5. Open Thunderbird, mash on addressbook, Tools > Import. Follow the wizard.

6. This should have imported your Evoluion addressbook. Note that some of the items seem to be in the wrong field. You'll have to live with this and change it over time, I guess... or maybe somebody else has a better way.

Well... that is it. After pulling my hair out over it and finding little guidance on the web, and finally getting it to work half-way ok, I decided that I should post a thread on it.

If anybody knows how to move your inbox from Evolution to Thundebird, I sure would like to know!!!

Best regards,
Phil Smith
Duluth, GA

---

### Post by ReaderRat on 2006-10-20
Thank you Phil....I will pass this on....ReaderRat, Athens, GA

---

### Post by Old Jimma on 2006-10-21
Folks:

After testing the directions given by Phil Smith, I discovered that there is alot of missing information that does not get transfered. For example, you might be missing street addresses, etc.

If anybody knows a better way of transfering data from the Evolution addressbook to Thunderbird, this is the thread to provide it.

Many Thanks,
Phil Smith
Duluth, GA

---

### Post by hyper_ch on 2006-10-21
sorry, if this is offtopic: Why do you talk about yourself in the 3rd person?

---

### Post by Stefano Fonzarelli on 2006-11-14
> **Phil Smith said:**
> Folks:

After testing the directions given by Phil Smith, I discovered that there is alot of missing information that does not get transfered. For example, you might be missing street addresses, etc.

If anybody knows a better way of transfering data from the Evolution addressbook to Thunderbird, this is the thread to provide it.

Many Thanks,
Phil Smith
Duluth, GA

I worked around the same problem today! 

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

Can anyone help me with the mail-export from Evolution and import to Thunderbird. Importing about a 1000! mails one-by-one is just too much.
There must be another way. Moving around files in the .evolution/... directories is getting me nowhere.

---

### Post by clee991 on 2006-11-24
There is a very handy web based file conversion tool that worked perfectly for me to convert exported contacts from evolution (file/save address book as Vcard) to csv to import into Gmail , should work the same to TB 

[http://labs.brotherli.ch/vcfconvert/]("http://labs.brotherli.ch/vcfconvert/")

---

### Post by neoraptor on 2007-01-08
Thank you very much for your tutorial. :D 
It was very helpful for me.

---

### Post by argraff on 2007-11-09
The vcf converter was very useful! Thanks for posting it.

However, it won't keep any groups together...*sigh*...

BUT - still better than commandline coding for a relative n00b. Why can't Evolution just export?!?!?!?

---

### Post by wombat20 on 2007-12-22
Great advice thanks. One more tip however.

I tried it by exporting from kaddressbook in LDIF format, which Thunderbird seemed to import fine, along with all addresses and telephone numbers.

---

### Post by cmckdub on 2008-01-01
I have found that Evolution can export to CSV directly. (Perhaps this is new in the version I am using = 2.12.1)
However, when importing into Thunderbird, quite a bit of shuffling of fields was required to keep all the fields I had used.

---

### Post by tonywhelan on 2008-02-17
> **Phil Smith said:**
> Y'all:

I wanted to stop using Evolution for a variety of reasons, and to use Thunderbird, again. If you want to do this, also, there are some things you have to think about... such as exporting your addressbook from Evolution, and then import it into Thunderbird.

<snip>

Best regards,
Phil Smith
Duluth, GA

Folks, if anyone wants to play with scripts for this sort of task, you could reverse-engineer one I found on the web that maps Thunderbird tab-separated-text files to the correct Evolution fields in a VCF file that Evo can import.

See: [https://sourceforge.net/projects/tsv2vcf/]("https://sourceforge.net/projects/tsv2vcf/")

I am **not** volunteering for that task (as I have just gone back to Evolution so Tracker can index and search my email).

---

### Post by tonywhelan on 2008-06-10
An alternative method I just worked out below:

1. EXPORT
In Evolution, choose the address book you wish to export. Right-click and choose Properties, then click the "make default" checkbox.

Now in a terminal, run the command:  ```
evolution-addressbook-export --format=vcard > giveitaname.vcf
```
This will export the currently-default contact list to a single VCARD (vcf) file. (if you only have one address book, its automatically the default, but some of us have several address books, hence the details above).

2. INSTALL ADD-ON
See this site: [http://nic-nac-project.de/~kaosmos/morecols-en.html](http://nic-nac-project.de/~kaosmos/morecols-en.html) fo an interesting Thunderbird addon that enhances the address book functions. It's not in the Mozilla addons repository, you need to download from the above website directly, and install in Thunderbird. 

3. IMPORT
Create a TB address book, select it and then go to the Tools menu. There you'll have an item called Actions for Contacts, then click Import VCARD/VCF. 

It took a minute to do the work with a largish address book, but the results were perfect - no transposed or messed-up fields! Note that I only use email/phone/mobile/address fields, so can't vouch for any of the others.

---

### Post by Hilko on 2008-07-21
This Add-on for Thunderbird is fantastic !!!

If you wish to migrate from evolution to thunderbird or the other way around you will definitely want this add on. Mozilla should put it in their repositories. It worked perfectly and I guess it saved me a lot of time, as I read the other complicated instructions for migrating the adressbook.

One detail to the above instructions:
To install the add-on, save the .xpi zip archive in some place. Then in Thunderbird choose from the menu: Tools --> Add-ons,  then click install, then browse to the saved .xpi file and click ok.

Thank you Tony for the excellent instructions.

---

### Post by Hilko on 2008-07-21
You might also be interested in this page:
[https://help.ubuntu.com/community/MigrateEvolutionToThunderbird]("https://help.ubuntu.com/community/MigrateEvolutionToThunderbird").

It explains how to migrate your mail boxes from Evolution to Tb.

---

