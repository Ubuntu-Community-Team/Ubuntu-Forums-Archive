---
title: "Evolution Mail Setup"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-13
This program confuses me to no end.  Is there a way to set this up with 
a) A hotmail account
b) a webmail-server account
c) both?

If so, how on earth would i go about doing this? i don't know what types of servers these are, and after going through the wizard it seems like i need to know.
Any help is appreciated. 
Thanks.

---

### Post by chadridesabike on 2007-12-13
from what i have read, you cannot use a hotmail account with evolution mail.

---

### Post by jordank on 2007-12-13
that's a shame, seeing as it's so popular.  How about a webmail account, any idea about that?

---

### Post by jken146 on 2007-12-13
What sort of webmail?  There is a plugin for Thunderbird that gives access to hotmail.

---

### Post by jordank on 2007-12-13
I don't exactly know what thunderbird is, but when you say it gives access to hotmail, are you saying that evolution then recieves from hotmail?

Webmail, like a university email server.

example:
webmail.uvic.ca

What CAN I configure evolution with?

---

### Post by jken146 on 2007-12-13
Evolution is an email client (program) that can be configured to receive email from servers of types POP, IMAP and Microsoft Exchange, among others.  Webmail is a fake email client that you see in a web browser.  You'll have to ask your uni IT support what protocols their mail server uses and for the details needed to connect to it.

Thunderbird is another email client.  It's developed by Mozilla, the organisation behind Firefox.  It's in the Ubuntu repositories.

---

### Post by jordank on 2007-12-13
Would thunderbird work the same way as evolution?  I like the idea of having a client that's an actual program.  Would i be able to set up thunderbird, then use evolution with thunderbird?  Sort of like having a middle man?

---

### Post by jordank on 2007-12-13
Is there a tutorial on thunderbird?

---

### Post by rsambuca on 2007-12-13
You can use Evolution with hotmail.  [Details here]("http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html").

---

### Post by rsambuca on 2007-12-13
If you prefer Thunderbird, [details are here.]("http://opensourcearticles.com/articles/thunderbird_15/english/part_01")I have been a long-time Thunderbird user, since it allowed me to share folders between Windows and Linux.  Since Gutsy came out, I decided to give Evolution a chance, and so far I like it.

---

### Post by jken146 on 2007-12-13
I think you misunderstood me.  Evolution and Thunderbird are two completely separate programs for sending and recieving email.  If you go to Applications > Add/Remove and type 'email' in the search box you'll see there are other programs too.  If you're curious, try installing Thunderbird and see how you like it.

---

### Post by jken146 on 2007-12-13
> **rsambuca said:**
> You can use Evolution with hotmail.  [Details here]("http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html").

Interesting.  I didn't know that.  Thanks.  (not that I use hotmail anymore)

---

### Post by rsambuca on 2007-12-13
> **jken146 said:**
> Interesting.  I didn't know that.  Thanks.  (not that I use hotmail anymore)

I can not say whether or not it works, though!  I don't use hotmail either.

---

### Post by jordank on 2007-12-13
After taking a look at thunderbird, i think i would prefer to use this as opposed to evolution.
How would I get hotmail to load on to thunderbird, would I follow the same steps as those for evolution?
Also, I'm still trying to figure out how to get my webmail account working for thunderbird. Would this be the same idea as hotmail?
I realize not many people use webmail, so i'm not sure what type of server it is, and i can't find out very easily.  Any suggestions to getting both of these working with Thunderbird?

---

### Post by rsambuca on 2007-12-13
Are you talking about a university webmail server, or some other webmail server?  Almost all of them can be set up to be used with outside email clients.  Go to the help page at your server site and I am sure there are instructions there.

---

### Post by jordank on 2007-12-13
Yeah, i'm talking about a university webmail site
webmail.uvic.ca
how would i set up thunderbird with hotmail?

---

### Post by rsambuca on 2007-12-13
Here is the info you need for setting up either Thunderbird or Evolution.  Probably the easiest method is to use the POP client.  

In your settings, the uvic POP client is:

Incoming Mail:  pop.uvic.ca
Outgoing Mail:  smtp.uvic.ca

That is what you need to enter when setting up your accounts in any email program.  You will then have to enter your username (usually the part before the '@' sign, and then your password.

Here is the[ link to the page]("http://helpdesk.uvic.ca/software/applications/email/email.html") that I googled for you and retrieved the information from.

---

### Post by jordank on 2007-12-14
Since i already went through the wizard, i'm having a hard time finding where i enter that information you gave me.  Any tips?

---

### Post by jordank on 2007-12-14
Disregard. Figured all of that out, thank you very much for that, by the way.
Now to tackle hotmail. For this will i have to make an all new account in thunderbird, or can i make it on the same account?
Also, what is the information needed for this?

---

### Post by rsambuca on 2007-12-14
I dunno.  Try these links.

[http://kb.mozillazine.org/Using_webmail_with_your_email_client](http://kb.mozillazine.org/Using_webmail_with_your_email_client)
[http://lifehacker.com/software/email-apps/check-hotmail-using-thunderbird-034583.php](http://lifehacker.com/software/email-apps/check-hotmail-using-thunderbird-034583.php)

---

