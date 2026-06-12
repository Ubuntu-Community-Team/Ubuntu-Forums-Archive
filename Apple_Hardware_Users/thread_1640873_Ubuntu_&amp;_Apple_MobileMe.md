---
title: "Ubuntu &amp; Apple MobileMe"
date: 2010-12-08
forum: Apple Hardware Users
---

### Post by Andrew_Read on 2010-12-08
Greetings!

I thought I would share my experiences of working with Apple MobileMe within Ubuntu. Below is an extract from a website that I am using as a personal scrapbook, I hope that this information will be useful for others wishing to use MobileMe with their Ubuntu computers.

If anybody has comments, suggestions or more information perhaps we could all share and create an Ubuntu with MobileMe how to guide.

**Introduction**

This page outlines my experiences of working with Apple's cloud platform MobileMe with Ubuntu 10.10, this guide is also relevant to most GNOME based desktop systems. So far I am able to work with:
[LIST]
[*]iDisk
[*]Mail
[*]Calendar
[/LIST]
As usual Apple are not interested in supporting the open source technologies which they no longer feel the need to exploit, Apple would also like to impose Microsoft products onto those of us who do not want to carry a £1000 netbook around. Before continuing I would like to recommend that all PC users avoid Apple products which restrict your freedom, for those of us who for some reasons are stuck with Apple below is how to get some of MobileMe working.
iDisk Access

[LIST]
[*]Once you are logged into Ubuntu select from the menus &#8220; Places &#8594; Connect to Server &#8221;.
[*]When the Connect to Server dialogue appears enter the following details:
[[LIST]
[*]Service Type: WebDAV (http) 
[*]Server: idisk.me.com 
[*]Folder: your MobileMe user name excluding @me.com 
[*]Check &#8220;Add Bookmark&#8221;, this makes connecting simpler in future, you can give the bookmark any name you like.
[/LIST]
[*]Click the &#8220; Connect &#8221; button, you should now be prompted for your username and password. Your username is the first part of your MobileMe e-mail address excluding @me.com, input your password and decide if you want to save your password for quickly connecting in future.
[/LIST]
If all went well you should now have full access to your iDisk when you are online, the option for keeping a local copy is not present when using the above method, I have not investigated other solutions at this time. If you created a bookmark for your iDisk you can connect quickly from the &#8220;Places&#8221; menu.

**Mail**

MobileMe mail should work with any standard e-mail application on most platforms and will also keep in sync with any other computers or me.com with no special requirements. Ubuntu supports a number of e-mail client applications which are easy to set up, Mozilla Thunderbird only needs your MobileMe e-mail address and password to automaticaly set up your computer to send and receive e-mail through MobileMe. Below are the settings you need to configure any e-mail application to work with your MobileMe e-mail accounti:

- Incoming Mail - 
server type:	 IMAP mail server:	 mail.me.com 
username:	 first part of your MobileMe e-mail address excluding @me.com 
server security:	SSL encryption 
authentication type:	password 

- Outgoing Mail - 
server type:	 SMTP 
server:	 smtp.me.com 
other:	 server requires authentication 
security:	 no encryption 
authentication type:	PLAIN 
username:	 first part of your MobileMe e-mail address excluding @me.com 

**Calendars**

Calendars stored on MobileMe can be viewed through some applications which Apple does not support, you can use Evolution Calendar supplied with Ubuntu 10.10, Evolution 2.30 . Versions of Evolution supplied with earlier releases of Ubuntu will not work with MobileMe Calendars, please note that there is an issue which I have identified. Calendar viewing and editing works mostly within Evolution with one exception, if you delete and event on me.com or any other device you are using MobileMe Calendars with, Evolution will not reflect the deletion. Where you have deleted an event outside of Evolution you will have to delete that event within Evolution also, this will display an error dialogue after which the event is deleted from Evolution.

In the following example I will demonstraite how to add a MobileMe calendar to Evolution, this will me my &#8220; Home &#8221; calendar.

From Evolution's Calendar click the &#8220; New Calendar... &#8221; underneath the caledar list on the left hand side of the window.
In the &#8220; New Calendar &#8221; dialogue which appears enter the following: 

Type:	 CalDAV 
Name:	 What ever you like, in this example I will call it &#8220; MobileMe - Home &#8221; . 
Copy calendar contents locally for offline operation	 If you want! 
Mark as default calendar	 It's your choice, you probably do want this. 
URL:	 caldav://cal.me.com/principals/ 
Use SSL	 Yes 
Username:	 Your MobileMe e-mail address excluding &#8220; @me.com &#8221; . 

With the &#8220; New Calendar &#8221; dialogue filled in click the &#8220; Browse server for a calendar &#8221; button, you will be prompted for your MobileMe password, you will then see a list of calendars you have available from your MobileMe account, select the one you want which in this example is &#8220; Home &#8221; then click &#8220; OK &#8221;.
In the &#8220; New Calendar &#8221; dialogue click OK, your calendar is now available in Evolution. Follow the same steps to add your other MobileMe calendars as you wish.

---

### Post by el_heffe on 2010-12-08
As a user of .mac, I applaud your write up!  I personally have never used galleries but have you tried to make them work?  I know my iPhone 1st Gen is supported by f-spot and rythmbox.  Let us know how any future endeavors go!

---

### Post by David Crockett on 2010-12-16
I have gotten MobileMe idisk to work well with Ubuntu, thanks to your instructions.   I am quite happy.  

However, I can't get the calandars to work with MobileM.   I do not see any button for "Browse server for a calendar" as indicated in your instructions.  it asked for my password that's it.   When I start Evolution Calendar it seems happy with MobileMe calendar, but I cannot get it to see the individual calendars on MobileMe.

Reards,
DC

---

### Post by Andrew_Read on 2010-12-20
Hi David Crockett,

Are you running Ubuntu LTS (10.04) by any chance? I don't think the calendars will work with the supplied version of Evolution as I had the same issue on an LTS virtual machine.

I also have not had much luck figuring out how to get anything else in MobileMe working, Apple seem to use proprietary and closed protocols to work with the majority of MobileMe.

I'll be updating my writeup with screen shots when I get a chance, probably this week which will hopefully make it easier to follow.

---

### Post by robbie75 on 2011-03-30
Thank you very much for your setup guide Andrew!

It worked out of the box for me and it's very very useful for my job.

But I want to let you know that you can apply to evolution task the same steps you provided for calendar sync and so you can also have the mobileme tasks in your evolution/gnome panel!

Now it would be nice if one could sync notes too...

best
Roberto

---

### Post by David Crockett on 2011-04-08
Andrew,
This information was indeed quite useful The ironic thing is that the iDisk seems to work faster with my Ubuntu machine than with the Apple.   So I am quite happy with it.   The calendar sync is also quite useful works pretty well.

The only issue that I have is when I copy files from the iDisk to my Ununtu machines I have to copy the individual files and not the file folders.   If you drag the folder all you get is an odd sort of empty file.   It does make backing up complex directories a bit irritating. 

Regards,
DC

---

