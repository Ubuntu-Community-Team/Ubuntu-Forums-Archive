---
title: "Ubuntu in developing countries"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by smurrbeast on 2006-12-01
Hi all,

I am very new to Linux and Ubuntu.  In a month I will be taking a computer to a women's small business cooperative in West Africa.  Due to budget constraints, the computer needs to run Linux.  I will need to train the women because they have never used computers in their lives, so I myself need to learn the ins and outs in the month before I go.  I have many questions:

1. I will install Ubuntu and word processing/small business software for them before i give it to them.  I don't want them to have to worry about any program editing or administrative stuff, or accidentally screw something up, but it would be a good idea to let someone know how to access the admin account to fix things if necessary, right?  is there a way to set everything up then close it off to editing/screwing up unless by someone who knows what they're doing?

2. I've heard that openoffice files convert readily to MSoffice files, but have also read a lot of posts in which people complain that you can't share anything with people when you run Linux.  What's the deal- how do I set up my ubuntu office programs to save things as shareable files by default? 

3. One thing I worry about is support- their computer will not be connected to the internet, though there is a cyber cafe in town.  What types of things could go wrong with their system that I would need to teach them how to fix?

i know these are all huge questions, but any info would be greatly appreciated.  thanks much!

PS, the computer i'm giving them is a mini itx with 40GB hard drive and DVD ROM.... and all programs will need to be in French!

---

### Post by KoRnholio on 2006-12-01
OpenOffice can easily save in Windows formats - I do that often when writing papers that I might need to work on at computers at school.  No 'conversion' is needed, you can simply save as .doc (or whatever format is required). Getting MS Office to read OpenOffice files is probably harder, never tried it.

---

### Post by az on 2006-12-01
> **smurrbeast said:**
> 
1. I will install Ubuntu and word processing/small business software for them before i give it to them.  I don't want them to have to worry about any program editing or administrative stuff, or accidentally screw something up, but it would be a good idea to let someone know how to access the admin account to fix things if necessary, right?  is there a way to set everything up then close it off to editing/screwing up unless by someone who knows what they're doing?

Well that's what sudo is for.  It is a priviledge escallation that is managed by a password.  You do things as a normal user and as such, you cannot write to anywhere else but your home drive.  System administration, which requires writing to system files, is granted by entering the password.

This is set up by default.  You install the machine for them and then you create the different user accounts for them.  By default, your's is the only one who can sudo and perform admin tasks.  You can, of couse, grant any user the same rights.



> **smurrbeast said:**
> 

2. I've heard that openoffice files convert readily to MSoffice files, but have also read a lot of posts in which people complain that you can't share anything with people when you run Linux.  What's the deal- how do I set up my ubuntu office programs to save things as shareable files by default? 

Just same them as MS word (or spreadsheet, presentation, whatever) format.  

> **smurrbeast said:**
> 
3. One thing I worry about is support- their computer will not be connected to the internet, though there is a cyber cafe in town.  What types of things could go wrong with their system that I would need to teach them how to fix?

That's quite a broad question.  However, Gnome being a very straghtforward desktop envirnoment, you should not have much go wrong once they learn how to use it.

You may want to send them security updates and bug fixes.  You can put them on a cd and send them the cd - they would have to inert the cd and install the updates from it.
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

or just

[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

> **smurrbeast said:**
> 
PS, the computer i'm giving them is a mini itx with 40GB hard drive and DVD ROM.... and all programs will need to be in French!

Again, the language packs are updated just about every month.  They would probably benefit from getting the more recent language packs.

How much RAM do these boxes have?

Also, use Dapper, the LTS (Long term Support) release.  It is best suited for your needs than Edgy....

---

### Post by smurrbeast on 2006-12-01
thanks- those are good ideas.  

256 MB RAM.  but i expect the most we'll be doing on the computer is word processing, spreadsheets, maybe budget stuff, and looking at pictures.

---

### Post by bapoumba on 2006-12-01
> **smurrbeast said:**
> .... and all programs will need to be in French!
That will be possible, no problem, you can choose your language and all the common packages (and many more) are translated in french ;)

---

