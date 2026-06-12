---
title: "Is Webmail Localhost really that easy?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by kobinasucks on 2007-06-06
Am I the only one who is not finding the Thunderbird + Webmail option for viewing Hotmail and Yahoo accounts as easy as everyone says it is?

I have installed Thunderbird 2.0 and downloaded and installed the latest versions of the Webmail plug-ins. My Gmail works just fine but I cannot send or receive anything from my Hotmail and Yahoo accounts in Webmail.

I keep getting the message:

"Could not connect to server localhost. The connection was refused."

 I've tried to adjust my Webmail preferences: all three green lights are on (POP is port 1024, SMTP is 1025 and IMAP is 1429 and all are set to enable at start up)... the IMAP domains for Yahoo have big red crosses next to 'em... Webmail Hotmail tells me there are no Hotmail accounts (which is weird, as I have two. One Yahoo).

The server settings for one hotmail account are as follows (I've put [myname] where my actual name appears):
Account Name: [myname]
Your name: [my name]
Email Address: [myname]@hotmail.com
(Reply-to-Address and Organisation and Attach signature/vCARD are all blank)
Outgoing Server: Webmail - localhost (Default)

And my Outgoing Server settings for Webmail are:

Description: Webmail
Server Name: localhost
Port 1025
User Name: [myname]@hotmail.com
Secure Connection: None

Is there some obvious step I'm missing or should I just Gmail myself up right now? Somebody please help me...

---

### Post by p_quarles on 2007-06-06
I'm not exactly sure what you're trying to do . . . I searched the Thunderbird plugin pages, and found no reference to a webmail plugin. How does work and what does it do?

---

### Post by p_quarles on 2007-06-06
Okay, I found the Webmail extension on the Mozdev site; looks kinda cool. You might browse their forums ([http://groups.google.com/group/thunderbird-webmail-extension](http://groups.google.com/group/thunderbird-webmail-extension)). It looks like a number of people are having trouble with Yahoo and Hotmail, so it might just be a buggy extension right now. A couple of suggestions I saw there was to make sure the Webmail ext.'s SMTP address wasn't conflicting with any other outgoing servers; and to open up the Javascript console and look for errors there.

---

### Post by jazzman84116 on 2007-06-06
I use free pops to get my Yahoo mail on Thunderbird

Localhost  Port 2000   dont work to good with hotmail from what I can tell

---

### Post by kobinasucks on 2007-06-07
Thanks Guys.

P_Q: visited those pages and you're right. Maybe there is a wider problem. Will try and hang it out for now. Cheers.

Jazz:  how do you get free pops?!!!

---

