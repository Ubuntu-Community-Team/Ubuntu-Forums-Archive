---
title: "Unable to Read Mail on Evolution"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by woof603 on 2008-04-09
Evolution sends okay and seems to be receiving but I cannot read incoming mail anywhere.  Any thoughts, anyone?  Thanks

---

### Post by jameswillmer on 2008-04-09
the most likely cause is that you have not setup the account (server) details correctly

why don't you post some screenshots

---

### Post by woof603 on 2008-04-09
/home/roger/Desktop/Screenshot-Mail - Evolution.png

Tgis is the page I get when I open Evolution

---

### Post by lackofcreativity on 2008-04-09
Hmmmm........ It looks like Evolution isn't initializing correctly. The top-left was a different color and I don't see any parts other than the inbox. I would try to update/reinstall Evolution, but that would be a last resort...

---

### Post by plucky on 2008-04-10
> Any thoughts, anyone?


In Evolution goto **Views > Layout** and tick the three boxes. A column will come up on the left of the screen. Click on the pointer for **On this Computer** and this should display your mail folders.

Select **Inbox** to see if your emails are there.


Good Luck

---

### Post by woof603 on 2008-04-10
Thanks, Plucky.  I did as you suggested and got the side bar etc, then clicked on "on this computer"...still no mail.
Annoyingly, when I hit mail it shows I have 43 messages unread.
Any more ideas?

---

### Post by plucky on 2008-04-10
> then clicked on "on this computer"


Can you see your folders?

You should have a list

[INDENT]
Inbox
Deleted Items
Junk
Outbox
Sent[/INDENT]


If not click on the arrow head that points to **On This Computer** and the folders should appear.

Where does it say you have 43 new messages?

Are you using POP or IMAP server?

Can you access your mail as webmail?

Who is your email provider?

Do you use Outlook or Outlook Express?

:confused:

---

### Post by woof603 on 2008-04-10
Here's my current page:



I'm using POP
No Outlook or Outlook Express
Ican access my mail on the web thru Yahoo mail
When I click on receive mail on Evolution it removes all the current mail from my yahoo account and puts it in my inbox in Evolution  
But I still can't open the box.
Thanks again for your help.

---

### Post by plucky on 2008-04-10
for my Yahoo account in th UK ,I have to specify a different port for both incoming and outgoing emails.Is that the same for you?

My pop server has to be **pop.mail.yahoo.co.uk:995** an my SMTP server is **smtp.mail.yahoo.co.uk:465**

Notice the numbers at the end of the server lines.The accounts also need **SSL** encryption.

Hope this helps

---

### Post by rustutzman on 2008-04-10
How about a screen shot with your Inbox highlighted in the left column.

Russ

---

### Post by Zimmer on 2008-04-10
> **woof603 said:**
> Here's my current page:



I'm using POP
No Outlook or Outlook Express
Ican access my mail on the web thru Yahoo mail
When I click on receive mail on Evolution it removes all the current mail from my yahoo account and puts it in my inbox in Evolution  
But I still can't open the box.
Thanks again for your help.
According to that screen shot you had the Drafts folder selected (just a thought that this is a simple error?)  Click on the Inbox folder...... (if I am way off on this , sorry, but I am just going by what I see on the screenshot)

---

### Post by woof603 on 2008-04-10
Thanks to you all for the help.  Sorry, I've no idea how to add the port numbers and I didn't see them as required in the set up instructions.  I did enable SSL, however.
Attached is ss with inbox highlighted.

---

### Post by nickpaton on 2008-04-10
I have no solution, but digging around Google found this bug report which seems to relate to your problem:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/197290]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/197290")

The OP reported a 2Gb limit on the inbox and the only solution seemed to be to install Evolution on Windows and replace the .evolution folder with the one in Windows where the inbox details could be read.

Good luck!

---

### Post by scramasax on 2008-04-10
> **woof603 said:**
> Thanks to you all for the help.  Sorry, I've no idea how to add the port numbers and I didn't see them as required in the set up instructions.  I did enable SSL, however.
Attached is ss with inbox highlighted.

Add the ports in the way the earlier poster showed -- i.e., on the end of the server name put a colon and then follow that by a port number.

For example Google's Gmail smtp server would be:

smtp.gmail.com:587

---

### Post by wpshooter on 2008-04-10
> **woof603 said:**
> Thanks to you all for the help.  Sorry, I've no idea how to add the port numbers and I didn't see them as required in the set up instructions.  I did enable SSL, however.
Attached is ss with inbox highlighted.

Did you try dropping down to/clicking on the "incoming" folder under the inbox ?

I don't really know why that is there but my GUESS is that that is where your incoming mail is winding up.

What version of Ubuntu is this and what version of Evolution is this ?

Thanks.

---

### Post by nickpaton on 2008-04-10
Sorry just realised that you're wanting to read your Yahoo webmail.

I've got a hotmail free account which is notoriously difficult to read on a standalone email browser, however a program[ FreePOPs]("http://www.freepops.org/en/") comes to the rescue and converts Web based email to POP3 protocol.

To install FreePOPs on 32bit distro ( [http://cybertech.altervista.org/en/freepops.php]("http://cybertech.altervista.org/en/freepops.php")   refers) :

Close Evolution and all other email browser programs you may have open

Check all dependencies are installed:

```
sudo apt-get install debconf libc6 libcurl3-gnutls libexpat1 libgcrypt11 lsb-base
```

Download latest FreePOPs for Ubuntu:

```
wget http://cybertech.altervista.org/en/freepops.php 
```

Download the graphical updater:

```
wget http://cybertech.altervista.org/download/freepops-updater-fltk_0.2.6-1-bkm_i386.deb
```

Install FreePOPs first by going into your home folder and clicking on the .deb program

Do the same for the Graphical updater.

You will now find FreePOPs Updater under Applications > Internet.  Click on program and run the wizard to install the updates for the various web based email clients.

Done!

To specify a port for POP within Evolution, start Evo.  Edit > Preferences > Select your email account and click Edit on RHS.

Receiving Email tab:

Server Type: POP 

Server - localhost:2000

(FreePOPs recommends using ports 2000 and above)

Username: your yahoo username

Security

User Secure Connection: No encryption

FreePOPs recommends using ports 2000 and above

The rest of the settings are as you would expect.  Note that when sending you are using your ISP's SMTP protocol

So click on Sending Email tab:

Server Type: SMTP

Server Configuration

Server: (example using my ISP's SMTP settings) mail.fireflyuk.net

Server requires authentication I have ticked as per default settings, but if you cannot send properly try removing the tick.

Security: No encryption

Authentication: PLAIN
username: your ISP username (not yahoo one)

HTH

---

### Post by woof603 on 2008-04-10
Thanks for all the suggestions.

I added the port numbers...995 incoming and 465 outgoing.

I created the "incoming folder" to see if I could get mail in it.

Gnome 2.20.1

Evolution 2.12.1

The bug report didn't seem of much help.

I'm still unable to read the mail.

I'd appreciate some more ideas.  Thanks.

---

### Post by nickpaton on 2008-04-10
'nuther idea.

Move the contents of Evolution into Thunderbird and see if you can read the inbox from within T'bird.

HOWTO[ here]("http://www.linux.com/articles/113798")

IMHO T'bird is a better package than Evo, and I only use Evo for the Calendars and Task functions

---

### Post by scramasax on 2008-04-10
> **woof603 said:**
> 
I'd appreciate some more ideas.  Thanks.

I think there has to be a possibility that the email program is damaged or corrupted in some way.

The odd thing is the way it's not drawing on screen properly -- and that there's messages shown in the Inbox, but you can't read them.

I would back up the mailstores now, because if it's grabbed the mail off the server, you don;t want to get into teh position of having lost your mail.

Close Evolution.  Go to Places > Home

and then in the menubra select View > Hidden Files

You'll see Evolution's folder -- it's called .evolution.  Make a copy of that, because your mail is in there.  Put the copy somewhere safe.  You might remove the leading dot from the filename of the copy, so that it won't vanish from sight when you turn off viewing of hidden files again.

---

### Post by woof603 on 2008-04-10
Thanks, Scramasax, I saved as you suggested.
Attached are screen shots of my Evolution set up.  Anyone see anything wrong?

---

### Post by woof603 on 2008-04-10
And here are the last screenshots:

---

### Post by woof603 on 2008-04-11
problem solved.  I couldn't read any mail because the empty reading panel was jammed tight up against the top task bar, covering up all the incoming mail!
Nothing like something simple to waste your days.:)

---

### Post by nickpaton on 2008-04-11
LOL If only all solutions were so simple!!

Great news Woof :)

---

