---
title: "Evolutions and GMail"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Rob_J on 2007-07-02
Hi all, hope this is the right place to ask my question. :)

I've just installed Ubuntu for the first time (a recent Windows escapee) and am trying to get Evolutions mail set up with my GMail account.  I've half succeeded.  By following the instructions [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/UsingGmailWithEvolution") to the letter I've set up my account with the following results:

> If I send an email to myself from another account - or from the GMail web interface - and click "Send/Receive" in Evolutions it detects the message perfectly.

> If I send an email to myself from Evolutions I receive it through the other account - or the GMail web interface if sending it to my GMail account - without a hitch.

> If I send an email from Evolutions to my GMail account I _[COLOR="Red"]**cannot**[/COLOR]_ receive it through Evolutions.  If I then check the GMail web interface the message has arrived, it just doesn't show up in Evolutions.

I've had a look around the internet but cannot seem to find an answer to this problem.  The fact that I can receive messages from other accounts - and even the same account when sending a message via the web - but not when sending from Evolutions is a little puzzling.  My account is set up as follows (with "myemail" substituted in place of my actual username) :

Email Address: [email]myemail@gmail.com[/email]

**Receiving mail:**
Server Type: POP
Server: pop.gmail.com
Username: [email]myemail@gmail.com[/email]
Secure Connection: SSL
Authentication: Password

**Sending Mail**
Server Type: SMTP
Server: smtp.gmail.com
"Requires Authentication" is ticked
Secure Connection: TLS
Authentication Type: Login
Username: [email]myemail@gmail.com[/email]

Can anyone give me a hand?  Many Thanks
Rob

---

### Post by Saveferris23 on 2007-07-02
Just a noob at all of this, but this is how I did it, and never had a problem... Hope this helps...
Select server type as “smtp,” type in “smtp.gmail.com” as the host, and check that the “Host requires authentication” box is checked. Next, select, for “Use Secure Connection,” always. Finally, make sure that Authentication type is “Plain” and your user name should be the same as you email address. Click Forward.

---

### Post by Rob_J on 2007-07-02
Hey, thanks for the input.  I've tried doing as you say (in fact that's how my settings were specified beforehand, but thanks!) and still no dice.  Suggestions still welcome.

---

### Post by Seisen on 2007-07-02
Perhaps adding the port numbers to  pop.gmail.com and smtp.google.com might fix the problem.

---

### Post by arijit on 2007-07-02
> **Rob_J said:**
> Hi all, hope this is the right place to ask my question. :)

--- snip ---

**Sending Mail**
Server Type: SMTP
Server: smtp.gmail.com
"Requires Authentication" is ticked
Secure Connection: TLS
Authentication Type: Login
Username: [email]myemail@gmail.com[/email]

Can anyone give me a hand?  Many Thanks
Rob

change the value of 
Secure Connection: TLS to "SSL"
and 
Authentication Type: Login to "PLAIN"

save the settings and try now.

---

### Post by Rob_J on 2007-07-02
Thanks for the input guys.  I've tried both of your suggestions and even with the port numbers and different authentication it still doesn't work.  I'm having intermittent problems with it which makes it hard to narrow the problem down, and if it stays unreliable I may have to find another email client.  Any suggestions?

---

### Post by arijit on 2007-07-04
You can try KMail. I've both ubuntu and kubuntu instralled. Both of their default mail client are setup with my gmail/yahoo accounts. and none of them are working fine. So, you can try kmail.

---

### Post by andrew.46 on 2007-07-09
Hi,

 Read your post with interest:

> **Rob_J said:**
> Thanks for the input guys.  I've tried both of your suggestions and even with the port numbers and different authentication it still doesn't work.  I'm having intermittent problems with it which makes it hard to narrow the problem down, and if it stays unreliable I may have to find another email client.  Any suggestions?

 You may be interested in trying a setup guide I have been working on which uses mutt to use Gmail as a relay:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 Mutt is a little different to many of the GUI email clients but it is worth becoming used to.

                         Andrew

---

