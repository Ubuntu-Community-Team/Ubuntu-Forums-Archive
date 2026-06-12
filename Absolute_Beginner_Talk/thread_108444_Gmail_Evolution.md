---
title: "Gmail Evolution"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2005-12-26
HI,

Can anybody tell me how to set up evolution so I can recieve my gmail emails through it please?

I tried doing it myself but it didn't work, if possible I would like all my old emails there aswell.

Thank you very very much.

---

### Post by qiemem on 2005-12-26
No problem (hopefully this will work; its been a while so I'm kinda doin this from memory):

First, add a new account (obviously), that'll start up the wizard. First, you just need to enter your name and email address (including the @gmail.com). Don't worry about the optional information, unless you want to make this your default account, in which case you check that box...
Next, at the "Receiving Email" part, select POP for your Server Type. Enter pop.gmail.com for the server and your email address for the username (including the @gmail.com). Choose Always for secure connection and don't worry about the password stuff. At Receiving Options, you probably want it to automatically check for email, so check that and enter how often.
Ok, Sending Mail: 
Server Type: SMTP
Server: smtp.gmail.com
check Server requires authentication
Use Secure Connection: I did whenever possible... might want to do always, not really sure.
Username: email address (including @gmail.com)

Ok, that should be it.

---

### Post by bscbrit on 2005-12-26
I don't know either so I am trying to set it up.  I can see where you are having problems though.. where to specify SSL and TSL etc.

I'll let you know if I succeed.

---

### Post by anil_robo on 2005-12-26
The tutorial given above is an excellent tutorial to make evolution understand how to send/receive email from gmail accounts. But you have to configure your gmail account to make it understand that evolution will come and fetch mail.

To use this, enable POP access in Gmail (usually enabled by default). Login to your gmail account in firefox, choose settings, and go to POP settings. Enable pop there.

---

### Post by anil_robo on 2005-12-26
[quote=qiemem]Use Secure Connection: I did whenever possible... might want to do always, not really sure.[/quote]

Select ALWAYS. That's what I have selected and Evolution works well.

---

### Post by kaamos on 2005-12-26
This should work pretty well for evolution as well I gues.. 
[http://mail.google.com/support/bin/answer.py?answer=13285&topic=1556](http://mail.google.com/support/bin/answer.py?answer=13285&topic=1556)

---

### Post by qiemem on 2005-12-26
Oh, heh, good call anil_robo. Oh and thanks for the input on the smtp stuff, I'll go change mine as well :)

---

### Post by bscbrit on 2005-12-26
kaamos, thanks for the link but we have both read that.  Unfortunately, it asks that SSL and TLS are enable specifically and there is nowhere obvious in Evolution that allows that.  I have selected the various security settings in turn but haven't got it to play yet.

I have also used qiemem's advice but it still does not want to play.  I have proven that it is not my firewall - this machine has a direct link to the internet and does not go through it.

I'm just trying to run it through various software packages to see where it is getting stuck.

Still, it will give me something to play with while I am waiting for the responses from other ubunut threads.

---

### Post by bscbrit on 2005-12-26
Ok, sorted and everybody here contributed!

In the GMail help it states the servers are googlemail.com - wrong, gmail.com is correct. (at least for my account)

'Use Secure' _must_ be set to 'always' and not 'whenever possible'.  There is some form of link negotiation if you select 'whenever possible' which is not answered by the Gmail server.

Authentication type is 'password'

Dr VBB, let me know if you still have problems and I will go through each of my settings.

---

### Post by cstudent on 2005-12-26
Make sure you go to Gmail via the web and enable receiving POP in the settings.

In Evolution set the receiving mail settings to:
server type: POP
server: pop.gmail.com
username: [email]yourusername@gmail.com[/email]
use secure connection: always
authentication type: password
remember password: check (if you want)

For sending email use:

server type: SMTP
server: smtp.gmail.com
require authentication: check
secure connection: always
authentication type: plain
username: [email]yourusername@gmail.com[/email]
remember password: check (if you want)

---

### Post by Dr Von Bon Bon on 2005-12-26
Thanks guys,

I think that i have got it working as it appears to be getting all my emails.


Again, thanks loads.

---

### Post by odin on 2005-12-26
Does anyone know how to set it up when you are in a network behind a proxy?

---

### Post by Nameless on 2005-12-26
[QUOTE=Dr Von Bon Bon]Thanks guys,

I think that i have got it working as it appears to be getting all my emails.


Again, thanks loads.[/QUOTE]


Dr Von Bon Bon, were you able to import the tags/folders that gmail uses into Evolution?

---

### Post by bscbrit on 2005-12-26
odin, have you tried setting it up as described in this thread, or do you suspect it simply will not work behind your proxy?  I'm not saying that you are wrong, but I would hope that the proxy wouldn't prevent you from accessing valid email sites.  I would be interested to hear if it does cause problems - I know nothing about using proxies but I would like to know the drawbacks of using them in case I wish to suggest that someone else uses one.

---

### Post by viscount on 2005-12-26
Yes, this worked rather well, infact, too well.

Without really thinking of the consequences I chose to download
everything in my Gmail account. 

[341MB and almost 5000 emails later]("http://noodlejunkie.blogspot.com/2005/12/hampster-and-lots-of-ducktape.html") I can honestly say "yes, this works".

One more thing, when setting up Evolution under "
Sending Email->Authentification Type" I chose "Login" and 
it works fine also.

Now what the heck am I going to do with 5000 emails?

Oh I know, 
#1 Setup my inbox filters
#2 Setup my spam filters
#3 Try to import my contacts

..uh.. naw, I think i'll just delete all that crap because Gmail already
does it, and a bunch more as well.

Sorry but Ill stick with Gmail, [especially after I found this site.]("http://gmail.pro/")

But at least I can compose emails in Evolution now if I really want 
to get some fancy formating and stuff, or if I want to compose emails 
while in offline mode for some strange reason.

---

### Post by odin on 2005-12-27
[QUOTE=bscbrit]odin, have you tried setting it up as described in this thread, or do you suspect it simply will not work behind your proxy?  I'm not saying that you are wrong, but I would hope that the proxy wouldn't prevent you from accessing valid email sites.  I would be interested to hear if it does cause problems - I know nothing about using proxies but I would like to know the drawbacks of using them in case I wish to suggest that someone else uses one.[/QUOTE]

Well I guess there's something I have to do.I have read many places that whe you are in network with proxy you have to "tell" to every application that contects to any place outside the network the settings of the proxy.I have to do it with firefox wit apt/synaptic and wget for example.I dont know about evolution but I have followed this thread and it didnt work so I guess it could be that.I think the problem is that all traffic from the network to the internet is routed through the proxy in special port and every application should know where the proxy is and what port to use.I maybe wrong but I really have tried everything but the good solution.... :confused:

---

### Post by bscbrit on 2005-12-27
Although I'm wandering from the original thread - I wonder the value of a proxy.  I cannot see any gain that is worth losing some capability for.

But, having never used one perhaps I am missing the point, or perhaps your ISP simply insists (which would make me very suspicious but that's a conversation more worthy of /. and not this forum)

---

### Post by odin on 2005-12-27
no I'm at work that's why we have the proxy.I just have a machine with ubuntu installed because there are somethings we have in linux and I'm the one making experiments with this things cause I love it and people here does not know a lot about linux so I'm just the lucky one in charge of this!!!

I'm not sure that I have to set anything in evolution that has to do with the proxy but  since anything works for me and I've check the rules of the proxy and nothing tells me I cant use this kind of applications I wondered if this might be the problem.I can live without evolution but It would be nice to get it working.

---

### Post by Esca on 2005-12-27
thanks guys, had the same problem, did the above and it works :)

---

### Post by odin on 2005-12-27
I've tried everything but still not working yet...I dont know is that ssl tls thing important or is already set selecting all the options in the way you say?

By the way the error message I get is 

Resolution of host failed: pop.gmail.com: Temporal failure in host's resolution name

and the same with smtp.gmail.com

---

### Post by bscbrit on 2005-12-27
Just a guess - your proxy might be blocking the relevant ports?

---

### Post by odin on 2005-12-27
yep I did not see it before but I'm scanning the ports with nmap and they are close.I was almost sure that it would be that but I didnt see any rule in the proxy blocking it(any obious one) so I wanted to keep the hope...

but yes no evolution at work

Thank you all very much

---

### Post by paulgroovy on 2005-12-29
Will this work the same with a yahoo mail account?

---

### Post by cstudent on 2005-12-29
[QUOTE=paulgroovy]Will this work the same with a yahoo mail account?[/QUOTE]

It's been awhile, but the last time I checked Yahoo mail can only be downloaded via POP like this if you have a paid Yahoo account. If you have the free one you can't use an email client on your computer to get your Yahoo mail.

---

### Post by paulgroovy on 2005-12-30
I just checked and you can use POP with the free yahoo account, however they will spam you.  

I just set up my gmail account in evolution and found that when I open an email in evolution, it isn't marked as read when I log into gmail through firefox.  Is there any way to change it so that when I read it in evolution it will be marked as read in the gmail account itself?

---

### Post by anil_robo on 2005-12-30
[quote=paulgroovy]I just set up my gmail account in evolution and found that when I open an email in evolution, it isn't marked as read when I log into gmail through firefox.  Is there any way to change it so that when I read it in evolution it will be marked as read in the gmail account itself?[/quote]

Open your Gmail acccount, and go to settings. Go to "forwarding and pop". Tell Gmail to archive the email when it's popped by Evolution. That should mark it as read in Gmail when you read mails through Evolution.

---

