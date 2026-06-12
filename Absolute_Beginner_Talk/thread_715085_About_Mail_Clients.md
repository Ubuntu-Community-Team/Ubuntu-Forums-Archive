---
title: "About Mail Clients"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Tomana on 2008-03-04
As you may know, Ubuntu 7.10 comes with FireFox and Evolution and Iwas
wondering why it didn't come with Thunderbird instead? Also, I'm used to
being able to add pictures to the email body using Outlook Xpress and at
the moment I'm using Claws Email but it doesn't let you add pictures (just
lets you attach pics). 

What program is the Ubuntu Linux equivalent to Outlook Xpress?

Also, is there a Dictionary I can install (even if I need to buy it)
that is a stand-alone that doesn't need to connect to the internet to get the definitions?

---

### Post by Cypher on 2008-03-04
You can install Thunderbird yourself with
```

sudo apt-get install mozilla-thunderbird

```

---

### Post by philinux on 2008-03-04
Thats the transition package now

sudo apt-get install thunderbird

or use synaptic

---

### Post by mcdan on 2008-03-04
thunderbird is in my opinion the best mail program, i think the only reason ubuntu comes with evolution is because it is bundled with open office, where as thunderbird can be installed separate from firefox

---

### Post by Tomana on 2008-03-04
that was the ticket, thanks

---

### Post by Najmudin on 2008-03-04
You can use stardict , i'm using it from long time , its very good , you can download the latest version form there site :
[http://stardict.sourceforge.net/]("http://stardict.sourceforge.net/")
or just search for it in synaptic or add/remove .

you can also download some dictionary files from the same site and add them to the application file in your home directory .

---

### Post by Kat of Zion on 2008-03-04
I have to say that Im very happy with Thunderbird.  Sadly I need to have a secondary email program to call up mail from some mail accounts that are work related and thus should be seperated from my 4 or so personal email accounts.

I used Sylpheed Claws but Im quite displeased with its lack of a good search feature for searching thru my old emails.  I wasnt pleased with Evolution either.

Any ideas?

---

### Post by stchman on 2008-03-04
> **Tomana said:**
> As you may know, Ubuntu 7.10 comes with FireFox and Evolution and Iwas
wondering why it didn't come with Thunderbird instead? Also, I'm used to
being able to add pictures to the email body using Outlook Xpress and at
the moment I'm using Claws Email but it doesn't let you add pictures (just
lets you attach pics). 

What program is the Ubuntu Linux equivalent to Outlook Xpress?

Also, is there a Dictionary I can install (even if I need to buy it)
that is a stand-alone that doesn't need to connect to the internet to get the definitions?

Thunderbird is just an email program where as Evolution has a calendar, task list included.  I have used both and I find Evolution to be a superior program over Thunderbird.  I have used Outlook for years and Evolution functions very similar.  Also Evolution works with Microsoft Exchange accounts.

It is all personal preference.

Also Evolution is a Gnome project so that may have something to do with it.

The Evolution in Feisty's repos is 1.5 and very out of date.  Gutsy has 2.0.0.12 in it's repos.

For you Feisty and older users I have a script to install Thunderbird.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

---

### Post by philinux on 2008-03-04
TB has lighting calendar and task list addon that is very useful. I believe that TB 3 has calendar out the box.

---

### Post by Tomana on 2008-03-05
ok, downloaded stardict but can't seem to find the free word definitions add-ons
at [http://stardict.sourceforge.net](http://stardict.sourceforge.net) ... the add-on page has install code but no files?
Anyone know where to get a good, free and legal dictionary or add-on files for
stardict ?

also need install help if you would. Thanks

---

### Post by Najmudin on 2008-03-05
> **Tomana said:**
> ok, downloaded stardict but can't seem to find the free word definitions add-ons
at [http://stardict.sourceforge.net](http://stardict.sourceforge.net) ... the add-on page has install code but no files?
Anyone know where to get a good, free and legal dictionary or add-on files for
stardict ?

also need install help if you would. Thanks

You will find it in dictionaries tab on the same link , but you have to chose one of the links with blue color , this is one of them :
[http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php]("http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php")
just download of the files , then uncompress it .
When completing the installation of  (Stardict) , start the application.
Go to home folder and enable showing the hidden files.
Look for a folder named .stardict
Open it and make a new folder named ( dic ) and paste the dictionaries inside it.
Restart the application.
then you can manage the dictionaries from the application , and forgot to tell that you can just double click on andy word on your screen and you'll get the meaning directly. fanatastic
Done.

I hope that helps :)

---

### Post by Tomana on 2008-03-07
wow, I looked but failed to find the link to that page - fantastic! Thanks a bunch ...

:guitar:
:-({|=\\:D/
Jam'n

---

### Post by dcstar on 2008-03-07
> **Tomana said:**
> As you may know, Ubuntu 7.10 comes with FireFox and Evolution and Iwas wondering why it didn't come with Thunderbird instead? Also, I'm used to
being able to add pictures to the email body using Outlook Xpress and at
the moment I'm using Claws Email but it doesn't let you add pictures (just
lets you attach pics). 

What program is the Ubuntu Linux equivalent to Outlook Xpress?
.........?

1: Evolution is far more functional and is integrated into the Gnome desktop, that is why Ubuntu uses it. As others have shown, you can install whatever you like afterwards.

2: Because having "inline" pics in e-mail is a non-standard Microsoft feature, that things like Outlook do but not e-mail clients that adhere to accepted standards. If you want pics in e-mails then you have to compose the message in HTML so all clients (that support HTML) can use them.

---

### Post by Tomana on 2008-03-08
Just one more step to install the dictionary:

- I need to unlock the File system, I go to properties and it tells me
I can't change anything because I'm not the Owner and when I
try to place the dictionary files in File System > USR > Share > StarDict > Dic
I get an eror message that says I do not have permission to write to that folder.

Am I root when I boot? Or do I have to use Terminal to become root?

---

### Post by Najmudin on 2008-03-08
> **Tomana said:**
> Just one more step to install the dictionary:

- I need to unlock the File system, I go to properties and it tells me
I can't change anything because I'm not the Owner and when I
try to place the dictionary files in File System > USR > Share > StarDict > Dic
I get an eror message that says I do not have permission to write to that folder.

Am I root when I boot? Or do I have to use Terminal to become root?

If you want to access the system files to add something there you have to do this:
- open the terminal and type: 
```
 gksudo nautilus 
```
it will ask you to enter your password , after that a window will appear so you can access to your file system and paste the dictionaries to the file you mentioned above.
But i think no need to do that if you can just add them to your home folder>stardict>dic , like the instruction in my previous post.

---

### Post by rbo83 on 2008-03-14
Please note that there are 2 significant features available in Thunderbird but missing in Evolution :

1-)  Evolution does not have the option to download only the message headers. So if you have a very large file attachment, it will be downloaded automatically in Evolution, consuming your bandwidth, and bad if you are roaming on a paid service.

2-) Evolution does not have the option to delete individual messages on the POP server when you delete them manually (or move them) from your inbox. This feature is important for people who share a mailbox between different e-mail clients (e.g office and home)

Other than that, both Evolution and Thunderbird are excellent products

---

### Post by scramasax on 2008-03-17
> **rbo83 said:**
> 2-) Evolution does not have the option to delete individual messages on the POP server when you delete them manually (or move them) from your inbox. This feature is important for people who share a mailbox between different e-mail clients (e.g office and home)

People who need to access an email account from more than one location would really be far better off using IMAP, since that's what it was designed for, whereas POP3 was never designed with that in mind.  There's quite fine-grained control over what IMAP headers Evolution will get for you under Mail Accounts > IMAP Headers.  Best to use the right means for the task.

Evolution is a fine and very full-featured program, although heavy on resources.  It's probably the best choice for most people and needful in the business sector because it's not just a mail client but a full-blown PIM -- and because it will talk to Exchange.  All-in-all it's hardly surprising that Canonical makes it the default.

But not everyone will like it.  People getting huge amounts of mail and real "power users" might well prefer to use a traditional command-line client like Alpine.

[http://en.wikipedia.org/wiki/Alpine_(e-mail_client)](http://en.wikipedia.org/wiki/Alpine_(e-mail_client))

 It depends on what you're doing -- and what your preferences are.

---

### Post by bruce89 on 2008-03-17
> **mcdan said:**
> thunderbird is in my opinion the best mail program, i think the only reason ubuntu comes with evolution is because it is bundled with open office, where as thunderbird can be installed separate from firefox

> **Tomana said:**
> that was the ticket, thanks

Evolution is part of GNOME, not OO.o.

---

### Post by kaivalagi on 2008-03-22
Generally speaking I prefer Thunderbord to Evolution because of the nicer RSS integration. Evolution can do RSS with a plugin, but it's much less useable...and doesn't support exporting to OPML etc

Quick question about thunderbird, maybe requiring a new thread?

I recently switch from Evolution to Thunderbird, because of the better RSS support, however one annoying thing in Thunderbird I don't seem to be able to change, is the handling of inline message history.

I like having inline email content rather than attachments which both clients handle, but TB does things back to front. On replying to an email, my new message text defaults to the bottom of the email and not the top...does anyone know how to change the default behaviour so I can reply with new text defaulting to the top of the message?

Would using the config editor in advanced settings help?

Any help much appreciated

---

### Post by thane1 on 2008-03-22
I too changed to Thunderbird (within the last week).  All in all I prefer it  so far to Evolution, kmail, claws/sylpheed/sylpheed-claws.  But there have been a few shortcomings, which I gather are directly related to the version 2 incarnations of Thunderbird.  No easy antivirus inclusion to protect my friends still on Winduh that I want to forward emails to.  No support for British English Dictionary v.1.19 which I understand worked great on the previous Thunderbird versions.  Also I had to do quite a bit of searching to find a cure for the non-inclusion of the BCC (block copy command) for Tbird 2's address book, when composing messages.  Only Add To and Add To CC appear by default, but not Add to BCC).  This last one I found a solution for on the MozillaZine website.  This being said, I'm sticking with Tbird for the next while in hopes, that the first two problems can be sorted out.  Cheers

---

### Post by Kimm on 2008-03-22
I prefer Thunderbird (with Lightning calendar extension). Only thing I dislike is that it doesn't adopt the GTK theme very well, I'm hoping Thunderbird 3 will fix this.

The old Mozilla mail was also nice (essentially the same, but with a different theme)

---

