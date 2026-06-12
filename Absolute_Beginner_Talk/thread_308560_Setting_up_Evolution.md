---
title: "Setting up Evolution"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Cod on 2006-11-28
Hi,
I'm setting up Evolution for the first time and want to use it at work.  My office uses Microsoft Exchange Server which apparently Evolution can work with if I know the OWA URL.  However, I don't know what this is.

Poking around in Outlook (my office is MSWindows only) I can find the name of the Microsoft Exchange Server but it is underlined.  I suspect this means that the OWA URL is hidden behind it somehow.

The tech guys are Linuxphobes and will not respond to any query about the system here that is not "normal".  Asking them for the OWA URL is futile.  

Does anyone know how to find out the OWA URL of a mail server?

Thanks

---

### Post by pdub on 2006-11-28
You really should seek permission first.

Some common names for OWA servers are:

Lets say your company domain is xyz.com

owa.xyz.com
webaccess.xyz.com
exchange.xyz.com
webmail.xyz.com

Try these first by substituting your domain name.

---

### Post by migla on 2006-11-28
They still might have to change some settings on the server...
Here's what I should tell my schools Microsoft-adminpeople:
[http://support.novell.com/cgi-bin/search/searchtid.cgi?/ximian/ximian328.html](http://support.novell.com/cgi-bin/search/searchtid.cgi?/ximian/ximian328.html)

---

### Post by mats_rickard on 2007-02-23
I'm also having problems with the "OWA-URL". OK, I'm a total newbie but anyway - here are my questions:

When using windoze, we have two ways of connecting to our Exchange server

1) The server name of** the exchange server** + username in the windows domain

<servername>.<companyname>.com
<username>


2) **The Outlook web access server name** + username in the windows domain including domain name

webmail.<companyname>.com
<windoze domain>\<username>

Which of these should be specified in the "OWA-URL"?

I have tried both and they don't work

1) generates the error "Could not configure the Exchange account because of unknown error"
2) generates the error "Could not find server"

What is wrong?
Is there a tutorial for newbies like me?

---

### Post by Mykal73 on 2008-02-21
I am having the exact same problem  as mats (and I'm the network admin!) does anyone know what might be causing the issue?

---

### Post by hiten_gajjar on 2008-07-11
Guys,

If you are using your company's mail box on http then you already have OWA.
Trying following on Windows machine that has your Outlook configured:
1. On Windows:
[INDENT]Start -> Control Panel -> Mail -> Mail Accounts -> View -> Change -> NOTE down the value in "Microsoft Exchange Server" field... lets say it is something.company.com[/INDENT]

2. Try http access using:
[INDENT][http://something.company.com/exchange/youraccountname](http://something.company.com/exchange/youraccountname)[/INDENT]

If this shows you web based outlook then simply copy the URL and paste it in your OWA.

If #2 step above does not work for you then contact your company IT department and ask them how to access Outlook over web and they should give you the details.

Thanks!
Hiten.

---

