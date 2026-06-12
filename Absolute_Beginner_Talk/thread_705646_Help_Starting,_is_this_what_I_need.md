---
title: "Help Starting, is this what I need?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by rgotten on 2008-02-23
I am completing new to Ubuntu.  I am a doctor with a small office that has a network thru a wireless linksys router.  I am trying to build a server and reading over the Internet came to the website of Ubuntu. What I am trying to do is to  create a patient information database were i can save pictures, documents, and data and be able to access it for my other computers. These is the set up that I have at the present moment: 
Three computers wired to the router, and my laptop which is connected wireless.  All of them run windows XP. 

What I would like to do is for for all the windows computers to save and/or access the information on the server, as well after my laptop through the Internet if I am away from my office, to have back up automatically of the data (from what I have read it is called RAID), so if one hard drive fails the other one will automatically start. 

Is this something easy to do with ubuntu server edition, or it is time-consuming.  I am not in a rush and I can start to do this slowly as long as it is not so complicated

Your help will be appreciated

rgotten

---

### Post by northern lights on 2008-02-23
Ubuntu will do the job you want your server to do.

Do you already have an idea what software to use for the database? Is there an existing database (MS Access, or the like)  that needs to be imported?

Further, when it comes to backing up, lemme explain RAID. This is not so much a software question, as it is a hardware related one. The only software aspect would be, whether Ubuntu can be installed on a RAID system and it can. Hardware wise, either your mainboard (i.e. your onboard IDE/ATA/SCSI controller) needs to support it, or you gotta have an extra RAID controller (PCI). There is two RAID basic modi, RAID 0 and RAID 1. RAID 0 stands for striped mode, where two harddisks are emulated as if they're one. It improves performance but does not make your system more reliable, in fact is more prone to get screwed, as one bad hdd renders the data on both worthless. What you are looking to have is RAID 1 - where the two harddisks are mirrored. Any RAID controller is capable of these two basic modi.

You should have two harddisk of the same size (I've only done it with same model HDDs, dunno how important same cache, etc is...).

---

### Post by rgotten on 2008-02-23
I do not know what database software to use. For now i am using microsoft word for my dictation of my patient charts, and I use zoombrowser for saving the pictures, this documents are save by first and last name and by a chart number. My idea is to be able to save this information plus other that will be scanned (like insurance information, etc) and be able to localize it on teh database by name, last name or chart number. Any recomendation in regards to this?? From what i see on you comments, the motherboard i get should have controllers for RAID.? 

In relation to my laptop? let say I have the server with my charts created on the database, and i am in teh hopstial and would like to check one of my patietns chart...It will be easy and quickly to connect to my server and open the chart?, Also i saw on newegg that a 500 gb hard drive runs for about $100, will 2 hardrive be enough or i have to by biggers one, or what happens if i would like to add later on another 500 gig hdd, do i have to get two more or only one if I have the RAID 1 configuration

Thanks for your help and hope to hear from you

---

### Post by northern lights on 2008-02-24
I dunno how large your practice is, but 500 gig seem plenty for a patient database. You certainly can add another HDD later. However, if you want to have the security of automated mirroring, you obviously would have to buy two again. Let's say your database is on two 500 gig HDD set up as a RAID system and the new HDD is not meant to extend the database, but for storage of less vital files, you may also choose to just by one harddrive and not install is as RAID.

As far as database software is concerned, I only have experience with OpenOffice's Database (the Linux equivalent to Microsoft Access). It's quite powerful and capable of what you want it to do (store pics along with client/patient information, etc.). You might want to check [this tutorial]("http://sheepdogguides.com/fdb/fdb1main.htm") and then decide whether it's the right thing for you.

[EDIT]
When walking home tonight from an off-campus friend, I thought about your problem a bit -

As far as the server and access from different Windows machines is concerned, that's fairly easy unless you're planning on it being possible to have multiple people edit same patients information at the same time. If that's not the case, simply share the parent folder of your database file(s) - since you want Windows machines to access 'em, you'd need [samba]("http://us1.samba.org/samba/"), but that's about it. Alternatively, a more professional setup would be to do it via [VPN]("http://en.wikipedia.org/wiki/Virtual_private_network")/ [SSH]("http://en.wikipedia.org/wiki/Ssh").

Aside my studies, I do a bit freelance computer-based work (website maintenance, statistics for a German public opinion research institute) - if you want to I'll make you database. What is it you have in mind? First, middle and last name, address, phone number, date of birth, chronic illnesses yes/no checkbox, if yes: description & treatment information / prescribed medicine drop down menu? Do you wanna log every visit? Something like a "Add visit/session" button, which pops up a box with an automated date and let's you add session notes? Or rather just log prescriptions - "Add prescription" button, medicine dropdown menu? Both?
You can have several files - one medicine database, one patient one, one chronic illnesses one, etc.
[/EDIT]

---

### Post by rgotten on 2008-04-06
Thanks for your offer, i will take it into account, let me first try to start and make the server up and running, i just posted some concern about the installation, hope you or sombedy can help, then in will come back and talk to you about the database..thanks for your help

Finally i am ready to install ubuntu server edition and even though the motherboard is raid enable evidently is a fakeraid and will not work under ubuntu. After researching is my impression the the sofware raid will work well and even sometimes it is better than the hardware and less expensive. This is  my question in the event i need to buld from a crash ( i will still make backups of the server), But in regards to the raid this are my questions:

Originally i was going to do a raid 5, but then reading all over the internet found that i should have to do boot in raid 1 and the rest for storage in raid 5, so if the boot section is damage i can still boot up. I have (3) 500 gb hd then:
        a) how big should the boot partition be for the raid 1? 
        b) Since i have the 3 hard drive, should i have the same boot partition areas on each of this 3 hd? and can this 3 partiton be on read 1 
        c) can i have raid 1 in this 3 equal size partitions, and then do the rest of the partition for each one of the hd for the raid 5 so evrything is on equal sizes?

Remember i am completely new to Ubuntu server, and instructions will be well apreciated

Thanks rgotten

---

### Post by rgotten on 2008-04-06
.

---

### Post by Martje_001 on 2008-04-06
You can create a 'soft' raid. It takes all three hard-drives and treats it as one. Just insert the install cd, it will point hisself out (is that good english?)

---

### Post by ugm6hr on 2008-04-06
Not sure if this is what you were thinking...

But once you've got the netwrok setup, there are plenty of pre-designed EMR software for Linux:
[http://www.informatics-review.com/wiki/index.php/Free_and_Open_Source_EMRs](http://www.informatics-review.com/wiki/index.php/Free_and_Open_Source_EMRs)

This one looks pretty easy: [http://www.patientos.org/index.html](http://www.patientos.org/index.html)

---

### Post by hyper_ch on 2008-04-06
I think the first thing is to decide what kind of software you want to use for storage/retrieval of the medical records of your patients...

Once that is clear, then one can think about how to get multi-user access to it, how to secure/limit access... how to backup....

When I read the first post I thought I would do that in php/mysql so that I can manage that by a browser.

As I will open a little firm on my own in a year or so I will be in the same need... it won't be medical records but law records and documents.

---

### Post by apostate on 2008-04-06
Hi Doctor,

This is how I would do it, if I may.

I would say Ubuntu is definitely a great choice for your server. I would set up a box with a RAID controller, as suggested above. Use RAID1, for mirroring. 

Software: You want an industrial strength database, so something like MS Access is not a good idea for a couple of reasons. Also, databases can be complicated, so if you want your staff to be able to access and manipulate your patient data easily from Windows machines with browsers, you need an intermediary program, an interface if you will.  I think what you are looking for is a CRM (Client Relationship Manager).  

This is ok, you're in good shape. You can install these packages on your Ubuntu server to get a web-server running:

apache2 (web server)
php5 (active server-side scripting language)
php5 support for apache
mySQL (Database manager)
mySQL support for php5

All of these packages are in the Ubuntu repositories, and lots of knowledgeable folks here can help you install them. This will get you a web-server, with support for a high-quality, multi-user SQL database called MySQL.

Now, you may want to look into a program called SugarCRM. It is a 3rd party, open source CRM package that can use MySQL. It will allow you to create attractive web-pages where you can do data-entry, create forms, look up patient info etc. It will allow you to structure your database around business requirements, and takes some of the black-magic out of using a database management system.  You use a web interface to define the sort of data elements you want to associate with each patient, rather than the more arcane command-line tools that developers use. The result is a nice-looking intranet application your staff can use in the office from any PC, via a web-browser. You can generate reports off this data, schedule appointments, whatever. It will tie into your email if you want!


You can learn more about this software here:  [http://www.sugarcrm.com/crm/](http://www.sugarcrm.com/crm/)

Hope this helps.

---

### Post by rgotten on 2008-06-22
i have build my server 8.04 and in working nice, i need the following:

3 windows computers conected to my ubuntu server.they comunicate thru samba. , i am a doctor ( even thougth what i need can be aply to offices, etc) and this is what i need:

1)thru a web interface be able to search for a name, last name or custumer number from my windows computers. if it does not exist, then to be able to create a new one. When the person is found or created, then it will have folders (ie: documents, copies of bills, copies of lab reports (in pdf format), chart documents (in word format), pictures (jpg.

I heard that this should be thru indexing so is ligther.

Can anybody help

rgotten

---

### Post by apostate on 2008-06-23
See my post above, you will need to install MySQL, Apache, and php. I would suggest you grab these using Synaptic and then report back. Then look into a content management system, or CRM. Take a look at Joomla, and SugarCRM.

---

