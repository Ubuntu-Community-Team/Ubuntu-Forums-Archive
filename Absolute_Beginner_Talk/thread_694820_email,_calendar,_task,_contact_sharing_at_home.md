---
title: "email, calendar, task, contact sharing at home?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2008-02-12
Hi everyone!

I have made a 90% switch to Ubuntu but my wife is still using windows. One thing we have always wanted to do which we haven't even done in windows is set up a central server to store all our email and contacts and share our calendars. We both have a desktop, a laptop and a PDA and keeping them sync'ed up stinks. As I understand it, MS Exchange is one windows based solution but I would rather go with Ubuntu.

What sort of open source or closed source but free server system is avail for this? Also, how would it work with a simple personal internet access service like COX? Can these packages download and send email through the standard pop/smtp or IMAP ports?

I have heard the name HULA thrown around a bit. Would this be the system I am looking for?

Suggestions?

Thanks!
Eric

---

### Post by jhenager on 2008-02-12
You could use Evolution and just keep your messages on your POP server.  I haven't shared my calendar but I would expect it would be easy.

---

### Post by nowhere@cox.net on 2008-02-12
Do the ISP pop servers store calendar information on it too? I may make the switch to keeping email on the server for simplicity's sake unless there is a better option proposed here.

Thanks for the reply!

Eric

---

### Post by nowhere@cox.net on 2008-02-12
I just looked into leaving mail on the Cox server but this doesn't appear to be a good option. Everything left on the server stays unorganized in the inbox and anything filed in folders is done so on the local computer meaning I will have at least 2 different sets of email messages.  

What I need is IMAP access for this to work which Cox does not offer. 

In addition I was hoping to solve another problem by creating a single mail/calendar server. Right now, I cannot send mail using the Cox SMTP server if I am not inside the Cox network (ie if I am on my sprint broadband on the road). Right now I have to send ALL my mail using gmail account and set the reply to: field which confuses some of my recipients.  If I had a server on my network at home/office that would collect email for me and my wife and send mail for us that would be great.

What do you think?
Eric

---

### Post by maybeway36 on 2008-02-12
Gmail has IMAP support, so that's something you should look into.

---

### Post by emarkd on 2008-02-12
Some people don't like it, but Google's gmail + calendar would do what you want...

---

### Post by KCPokes on 2008-02-12
If you are looking to set up your own server, for mail (contacts, calendar, etc...), you could look into possibilities like Zimbra or OpenExchange.  Personally I prefer Zimbra and have been running it for a couple years now.

---

### Post by nowhere@cox.net on 2008-02-12
Thanks to all so far! 
KCPokes, I was just surfing Zimbra's website and was very impressed. What kind of environment are you running it in? Home? Office? I have a plain ole Cox ISP account and a wired/wireless router set up. I have a server that I develop on and have set up several port forwarding entries on my router to allow me access to various machine on my network at home.  I am a total networking novice so I am sure there is a better way than what I am doing but I am able to ssh to any of the 3 linux boxes I have inside my network as well as tunnel VNC through ssh to them as well.

Do you think ZImbra is a good choice for this type of environment? Will it "forward" mail from my cox email accounts to my email client apps  like evolution?  Or do you pretty much abandon client apps in lieu of their ajax app?

Thanks for the help!

Eric

---

### Post by KCPokes on 2008-02-12
Eric, if Cox will allow the needed ports through, then it shouldn't be an issue.  I run my server for both personal and business, handling email for three different domains.  Been running it for a couple years now without any issue.  Of course you can still choose to use an email client, such as Evolution or Thunderbird, but it is all a preference.  I choose to just use the webmail interface as 1) it basically has everything I'd need in a client, 2) allows me access to everything regardless of where I am.  Even allows me to publicly share my address book to friends and family that do not have email on my server via a regular URL which results in a CSV file.  

As far as networking, really comes down to what you are comfortable with.  I run a dedicated machine, running Smoothwall, for my firewall rather then an out-of-the-box router.  I prefer the options that Smoothwall offers me as well as the fact that I've had zero failures since I've switched over, which I cannot say for my previous Linksys router.  

Hopefully this gives you enough to get started, or at least give it a shot and see where you get.  You can shoot me a message if you have any questions or issues.

---

### Post by nowhere@cox.net on 2008-02-12
Thanks KC,

I will give it a shot. I have a LAMP server in the garage on the WLAN and I will see what I can learn on the web about mail server admin. Will be my first time.

i really did lke the looks of Zimbra and they have a new desktop client. I also gleened an article on CNET that claimed if it gets enough support it may replace evolution as the default Ubuntu package.

Thanks for the help. 

Eric

---

### Post by jrusso2 on 2008-02-12
A very easy thing to do is to share a google calendar.  Then you can both access it,  Also with thunderbird you can all the lightning and providor for google plugins to synch them on your desktops and pda's

---

### Post by Wizard of Aahz on 2008-02-13
Eric - Anothher option might be citadel. [http://citadel.org](http://citadel.org). Email, contacts, shared calendars and a very simple push button easy install.

-Aaz

---

### Post by nowhere@cox.net on 2008-02-26
Hey thanks Wiz!

I took a look at Zimbra and it looked very nice but I think I will give the true open source Citadel a try first. Seems to do everything I want and if your a correct about the installation then it should be perfect.

Now to decide where to set it up.  I will need to dedicate a machine to this...

THANKS!

---

### Post by Wizard of Aahz on 2008-02-27
Nowhere - No problem.. 

Good luck with citadel.

-Aahz

---

### Post by nowhere@cox.net on 2008-02-27
Wiz or anyone,

Got Citadel installed. It was a piece of cake. Webcit and everything runs fine. Now I need to see if it actually does what I need it to. I had anticipated that I would be able to set Citadel up to fetch my messages from my ISP pop server for me and my wife. I don't see any settings to do this. 

As for outgoing, I do see that I can specifiy a smart-host with an SMTP server and port and even provide authentication info. This looks like it will work with my ISP's SMTP server but I don't know for sure without trying it.

Anyone know how to set up a message fetch or do I have use my own domain name and work with my registrar to somehow have incoming main sent directly to my domain name? 

Thanks,
Eric

---

### Post by HermanAB on 2008-02-27
Use Citadel.  It only takes about 20 minutes to set it up.  See the bottom of this guide:
[http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html)

---

### Post by nowhere@cox.net on 2008-02-27
Thanks Herman,

But I have it installed. I need some configuration advice. My wife and I both have pop accounts with our ISP. Can I configure Citadel to grab our mail from the ISP servers and store it? That way we can point our clients to Citadel and even check via the webcit when needed? I already have apache up and ports forwarded to access it remotely.

If I can do this, where can I set the settings to tell Citadel what pop accounts to get mail for?

I suspect that this isn't really how it works so someone let me know please.

Thanks,
Eric

---

### Post by chris.a.barker on 2008-02-27
Here is a good way to get started on a secure Ubuntu Based mail server:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

As far as syncing all of the items you mentioned, I use Horde Groupware to do that. It is similar to Microsoft's Outlook Web Access only it is a lot more stable, secure, and offers a friendly interface.

Hope this helps you.

---

### Post by nowhere@cox.net on 2008-02-27
I found part of my answer for Citadel. I CAN fetch messages from another server. 

> In WebCit, simply navigate to the room into which you wish to fetch messages (usually your &#8220;Mail&#8221; room, i.e. your inbox) and select Advanced &#8211;> Edit or delete this room &#8211;> Remote retrieval, and then enter the hostname of your remote POP3 mail server, along with the username and password of your account there.

Only problem is I can't find any way, once it is set up, to tell Citadel to go ahead and fetch the messages. 

Almost there!

---

### Post by Ian Clark on 2008-02-28
My Evolution is so corrupt that it basically crashes on start.  It's stuck on "formatting", with the Gnome toes twiddling, then offers for me to wait or force quit.  It's even crashed my system.  I've checked into uninstalling it, but I found out that it can't be uninstalled.  Any suggestions?

---

### Post by nowhere@cox.net on 2008-02-28
Sorry Ian,

I don't know enough to help you with it but I would suggest starting a new thread asking the question. Someone watching this thread may be able to help but there are others that probably have looked at this thread, couldn't help and moved on that will never see your message.

I give this advice since I see that this was your first post. Also, I did a search on evolution corruption and there are several threads. I don't know your exact problem but browsing some of those may lead you to an answer.

Good Luck!
Eric

---

### Post by Wizard of Aahz on 2008-02-29
Nowhere - 

Make certain to check your networker settings. That's what makes the pop3 fetch happen.

-Aahz

---

### Post by nowhere@cox.net on 2008-03-05
Thanks Aahz, and everyone,

Right now I am trying out something that wasn't suggested. I am using Thunderbird with the Lightning plug-in and it syncs perfectly with scheduleworld.com.  Scheduleworld.com has calendar sharing so I suspect that I can have my wife's setup synced with my shared calendars. I haven't tried the sharing yet but the syncing works perfectly and was really really easy to set up. 

Evolution has a sync with scheduleworld too but after a couple of hours of screwing around an having my calendars all mixed together I gave up.

Thunderbird worked out of the box with almost zero setup. 

As for mail, I haven't really decided what to do. I don't think I can IMAP with my ISP's server so I am still stuck downloading mail only on one machine and leaving on the server for the others. Not ideal....

Eric

---

