---
title: "ACT for Linux"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-03-27
Hello all,

My friends and I are starting a little business.  One of my partner's boss uses a program called ACT to keep track of all sorts of client data.

Does anyone know of a similar program for us linux users.

I run ubuntu 6.06 exclusively with the kubuntu desktop installed also.

I have never used ACT but he said that it was really involved and highly configurable.

Thanks

---

### Post by octoberdan on 2007-03-27
You may want to try installing it with wine.

1. sudo apt-get update && sudo apt-get install wine
2. put the install disk in the drive
3. cd over to the disk using a console
4. "wine Install.exe" or setup.exe or whatever the installation file is named.
Any questions, let us know. Good luck and happy geeking!

---

### Post by octoberdan on 2007-03-27
Oh, incase you didn't know.

"Wine is an Open Source implementation of the Windows API on top of X and Unix.

Think of Wine as a compatibility layer for running Windows programs. Wine does not require Microsoft Windows, as it is a completely free alternative implementation of the Windows API consisting of 100% non-Microsoft code, however Wine can optionally use native Windows DLLs if they are available. Wine provides both a development toolkit for porting Windows source code to Unix as well as a program loader, allowing many unmodified Windows programs to run on x86-based Unixes, including Linux, FreeBSD, Mac OS X, and Solaris." - [http://www.winehq.com/](http://www.winehq.com/)

---

### Post by charles.g.moore on 2007-03-27
> **octoberdan said:**
> Oh, incase you didn't know.

"Wine is an Open Source implementation of the Windows API on top of X and Unix.

Think of Wine as a compatibility layer for running Windows programs. Wine does not require Microsoft Windows, as it is a completely free alternative implementation of the Windows API consisting of 100% non-Microsoft code, however Wine can optionally use native Windows DLLs if they are available. Wine provides both a development toolkit for porting Windows source code to Unix as well as a program loader, allowing many unmodified Windows programs to run on x86-based Unixes, including Linux, FreeBSD, Mac OS X, and Solaris." - [http://www.winehq.com/](http://www.winehq.com/)

I was thinking about something open source that could do the same thing as ACT.
Truthfully, I do not want anything windows on my lappy.  

I already have a virtual XP loaded using VmWare and that alone makes me sick...

Any suggestions?  
I guess i'm looking for some kind of all in one customizable calendar, contact info, and notepad application.

---

### Post by Scunizi on 2007-03-27
I've used Act since version 2.x and currently have v6.xx on my wife's machine.  I've been looking for a suitable replacement for some time.  Other than Evolution, which has the features you mentioned, you can also use a combination of things to get the job done.  Thunderbird for email, sunbird for calendar, Tomboy for notes or Google's Open Notepad which interfaces with Firefox.  Another way would be to use Google's Calendar function online combined with any email client (gmail?, Evolution, thunderbird etc).  What I'm looking at also is web based CRM software that is much better than Act and might even be a suggestion for your boss to unify all his empolyees data in one location that is accessable from anywhere.  I'm looking at vTiger, SugarCRM and a host of others.  They take a little getting use to and will typically need to have custom fields setup for the business you're in.  These programs are very customizable and offer many more features than what Act has.  They will not lock your data like Act does either since they use MySql database and PHP.  Act tends to allow you to export only a small subset of the data you enter for each contact.  If it's neccessary to get it all out you have to buy a third party program to do it.  Their tech support also leaves a lot to be desired since they use third party "experts" that charge by the hour.  The opensource CRM's I mentioned above have a thriving community of users that help each other out like this forum does.  SugarCRM also has a paid support program for enterprise use if needed.  Good Luck!

---

### Post by octoberdan on 2007-03-27
Evolution is supposed to be an outlook replacement. Perhaps that?
EDIT: Sorry, late response.

---

### Post by charles.g.moore on 2007-03-27
Scunizi,
Thanks for the info, i'm definitely going to do research into SugarCRM and vTiger.
It seems a bit involved (getting it up and running/configured) but we'll see if it looks like it may be worth the time investment.

---

### Post by Scunizi on 2007-03-27
On a side note, I'm also playing with Joomla which is a CMS (content management system... web site development)  This is also web based.  I tried to do it on a server install of 6.06 and have been struggling to get it functional.  However I did try on my XP partition and WAMP installed without issue as well as Joomla.  I had it up and running in under 20 minutes.  My learning curve is still steep on Linux and I've been banging away on this "new" system for months.

---

### Post by charles.g.moore on 2007-03-27
I have a server set up at home with the LAMP stack installed (it's not doing anything except for file sharing)  
I might have a go at that.
What made the XP box so much easier?  
How do you like the Joomla UI?

---

### Post by Scunizi on 2007-03-27
Probably becuase the WAMP stack has more GUI configuration tools and all the files are located pretty much in one directory off C:\.  On the LAMP stack it's mostly a command line affair.

---

### Post by charles.g.moore on 2007-03-27
I know what you mean, everytime I use that server I have to fight the urge to install the GUI

---

### Post by Scunizi on 2007-03-27
What's the name of the GUI?  Inquiring minds want to know.

---

### Post by charles.g.moore on 2007-03-27
As I understand it all you have to do is:

sudo aptitude install ubuntu-desktop 
or 
sudo aptitude install kubuntu-desktop

This will give you the GUI environment in which to work...

Uh oh I feel I may have let the cat out of the bag for you, you must resist and embrace the CLI!!!

---

### Post by Scunizi on 2007-03-27
The desktop I've got ok.. It's GUI setup tools for the MySql database and Apache server I'm looking for.:)

---

### Post by charles.g.moore on 2007-03-28
Ahh, that I dunno...

---

### Post by shane2peru on 2007-04-05
This thread is looooong over due!!!  I have used ACT for a loooong time as well.  I have yet to find a suitable Linux substitute.  I have settled with Evolution, but it is far lacking from what ACT does.  I did finally breakdown and get ACT installed via wine, but it wasn' t easy, and is not 100%.  That being said, are there any other suggestions as far as a substitute program?  I'm really pleased with ACT except there email end is really sorry too.  Not that I'm that impressed with Evolution.  I will have to look into the Sugar and Tiger mentioned earlier.  Great topic!

Shane

---

### Post by Scunizi on 2007-04-05
I just remembered... you should also look at Zimbra.  It looks more like what Act was designed to do.
  
Charles.. I'm sorry it's taken so long to get back to you on your question about Joomla... It was easy on the Windows side because I had a wild hair one night and installed the WAMP stack and Joomla in about 20 minutes.  It was that quick.  The WAMP stack I used came with a lot of gui tools for administrating apache, php etc.  I'm a real nOOb at all this and very use to the gui.  Although I'm getting better at the linux command line I often get lost just figuring out what command to use to do something.  Googling for hours gets tedious sometimes.  Eventually I hope to know this system (linux) as well or better than WinXX.  

I am going to try to put up Joomla on a commercial server tonight in a sub directory of the site that is running now... I don't know if it will work that way or not.  The worst that can happen is I delete the sub directory and move on from there.  I know I'll have access it using the standard address with /subdirectory.  I just don't know if Joomla will talk to the rest of the server from there.. It's just a test.  More learning.  There's even a way to integrate Zimbra and Joomla but I understand that it's not for the faint of heart. :)

---

### Post by adriantry on 2007-04-06
> **charles.g.moore said:**
> My friends and I are starting a little business.  One of my partner's boss uses a program called ACT to keep track of all sorts of client data.

Does anyone know of a similar program for us linux users.

I'm just starting to look at a web service called Highrise
[http://www.highrisehq.com/tour](http://www.highrisehq.com/tour)

It's a web based solution that seems to link contacts and tasks in a way similar to Act! (which I used to use back when DOS was state-of-the-art). Their motto is "Your address book doesn&#8217;t do enough. Traditional CRM software tries to do too much. Highrise is the just-right solution."

Here's a quote from their "Why it works" section. This description really reminds me of Act!

> Ring. It&#8217;s for you.

Ping. You&#8217;ve got mail.

It&#8217;s a new contact, a lead, a customer, a journalist. It&#8217;s someone saying something important you need to remember.

What do you do now? Where do you log notes from the conversation? Where do you put the contact information? Where do you set up your next action?

In Highrise.
The answer to the avalanche

So many people. So many phone calls, emails, notes, follow-ups, and tasks. Who&#8217;s this person again? When did we last speak? What did we talk about? Has anyone else in my company talked to this person? What&#8217;s supposed to happen next? Highrise is here to keep track of it all.
A personal assistant for everyone in your company

When you use Highrise, contacts and communication history can be shared across your entire company. No more &#8220;Jim has the client&#8217;s number and he&#8217;s out of the office today.&#8221; No more &#8220;I don&#8217;t know what Jane told the printer last week.&#8221; No more &#8220;Oops, I didn&#8217;t know you already called her back &#8212; I just did too.&#8221; With Highrise, everyone&#8217;s on the same page.
One history, many interactions

Highrise is your homebase for everyone that&#8217;s important to your business. It puts together all those little points of contact so you can see the bigger picture. It makes one history out of many interactions. Highrise helps you make sense of it all.
Not too little, not too much

Your address book doesn&#8217;t do enough. Traditional CRM (Customer Relationship Management) software tries to do too much. That&#8217;s why we built Highrise. It&#8217;s the just-right, more thoughtful way to keep track of the people, conversations, and tasks that are the lifelines of your business.

Highrise. Good business is about people. Keep in touch.

I'm having a look at it right now. It sounds promising.

Adrian

---

### Post by Scunizi on 2007-04-06
Looks interesting but doesn't show if you can add your own fields or not..  Also at the basic level it's $29 a month for a limit of 500 leads.  Not good enough and for a monthly fee, I think taking the time to customize something that is GPL'd is more to my liking.

Edit:  Let's all keep looking though.  This is an area of serious need for lots of self employed and small businesses.

---

### Post by adriantry on 2007-04-07
> **Scunizi said:**
> Looks interesting but doesn't show if you can add your own fields or not..  Also at the basic level it's $29 a month for a limit of 500 leads.  Not good enough and for a monthly fee, I think taking the time to customize something that is GPL'd is more to my liking.

Actually, at its most basic level it is free (as in beer), and has a limit of only 250 contacts.

The program is basic, but designed in a way that is very smart and very useable. But 250 contacts will be eventually too few for me, and the more expensive options don't seem like excellent value.

So far, this is one of the best options I've found - but there's not a lot of competition. Maybe we can start working on an OpenOffice.org database that we can share with others.

Adrian

---

### Post by Scunizi on 2007-04-07
That's an interesting thought.  Basically, all you have to do is put all the fields in a spread sheet on row one and populate it, then convert it to a database, build a data entry screen and you should be done.  My only concern is OO is not always the most reliable.  Maybe better to develop the fields in MySql (for which I know nothing about even though I'm playing with it.) then build the front end in OO to access it?  I understand it should interface without a problem.  My specific needs (as related to my business) are Real Estate and Loans.

---

### Post by ramjet_1953 on 2007-04-08
This site might be worth a look:

[http://www.deksoftware.com/dcrml/index.html](http://www.deksoftware.com/dcrml/index.html)

Regards,
Roger :cool:

---

### Post by r00tintheb0x on 2007-04-08
[http://www.sugarcrm.com/crm/](http://www.sugarcrm.com/crm/)

w00t!

---

### Post by adriantry on 2007-04-08
> **ramjet_1953 said:**
> This site might be worth a look:

[http://www.deksoftware.com/dcrml/index.html](http://www.deksoftware.com/dcrml/index.html)

Here is their pricelist:
	1 to 5 Users	$595.00 each User
	6 to 10 Users	$495.00 each User
	11 to 25 Users	$395.00 each User
	26 to 50 Users	$295.00 each User
	SITE LICENSE*	$14,995.00
	CORPORATE LICENSE*	$26,500.00

---

### Post by Scunizi on 2007-04-08
I've been keeping track of a few programs..

[Adempiere]("http://www.adempiere.com/index.php?option=com_content&task=view&id=24&Itemid=31") 
[Open Bravo]("http://www.openbravo.com/index.php?option=com_content&task=view&id=128&Itemid=242")
[Simple Groupware]("http://www.simple-groupware.de/cms/")[URL="http://obm.aliacom.fr/"]
O.B.M.[/URL]
[Compiere]("http://www.compiere.org/")

I think most if not all of these are GPL'd.

---

### Post by MrKlean on 2007-04-08
Thunderbird has an addon that makes it just like Outlook...It adds the calender,notes,and email ; )

---

### Post by jonlink on 2007-06-16
Hey folks, I'm new to Ubuntu and I am converting my dad to it at the same time (yikes) I've got him just about sold on it except for there being no ACT! replacement  I see this thread trailed off in April, does anyone have anything new to add?

It looks like he mainly uses it to sync files, contacts, and calendars to his Palm.  Any helpful suggestions would be greatly appreciated!

---

### Post by Scunizi on 2007-06-16
It really depends on if you're running gnome or kde... on gnome you have "Evolution".  the email client with calendar, todo's, contacts etc..  In Evolution you go to Edit/Syncronize options and it will walk you through setting up the palm.  On kde you have koffice.. not sure what they have there but I'm sure it's similar.  The palm interface is better for syncing than the MS version.... 

Koffice does have an attractive feature in that you can add you own fields to it if needed.. You can also run it in gnome.. just use Synaptic and install..

---

### Post by jonlink on 2007-06-16
I set up gnome for him.  I'll have a look at evolution first since that is preinstalled an all.  Thanks for the input.

---

### Post by shane2peru on 2007-06-16
> **jonlink said:**
> I set up gnome for him.  I'll have a look at evolution first since that is preinstalled an all.  Thanks for the input.

 I can tell you right now that using anything is going to be a far cry from ACT.  I too used ACT, and absolutely loved the interface.  I despised it's email capability, and did get it running under wine, but it took some work.  I have since lost all my setup and have to do it again, and haven't gotten back to getting it running yet in wine.  I don't care much for evolution myself either, plan on looking at Kontact for KDE again.  You can sync evolution with Palm, and it did an ok job, but I wouldn't give it a grade A.  :)

Shane

---

