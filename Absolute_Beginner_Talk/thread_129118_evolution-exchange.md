---
title: "evolution-exchange"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by yl200001 on 2006-02-13
1. I am trying to connect exchange with evolution. When I first started evolution, I can pass the authentication by click "Authenticate" button after inputting username and OWA url. But when I tried to access my mail box, the evolution prompted me to input password for another diffrent server name that I haven't inputted at all.
Ie. I inputted a.com as OWA url, but evolution asked me to inputted pwassword from server b.com. Then for sure the inputted pwd failed to be autenticated. How did this happen?

2. I can access my mailbox from browser by inpputing OWA url.

Pls help!!

---

### Post by nursegirl on 2006-02-14
I think that the protocol to use a desktop client with an exchange server should be at a dfferent url than for Outlook Web Access.  I've never used OWA, but at a previous workplace we were given a different set of instructions depending on whether we were going to use OWA vs Outlook/Evolution/whatever.

Check with your service provider about how you could use MS Outlook to access your iemail, and then it's pretty straightforward to follow the same instructions using Evolution.

---

### Post by jadajada on 2006-02-15
This is a real headache!  I too have this problem. I am sure I'm doing it correctly. It works in Debian Stable and Testing. My experience with this is that the evoution-exchange in Breezy is horribly broken!

I hope this gets fixed in Dapper. I have been unable to use my Evolution against our Exchange server for a long time now... I'm stuck with using Outlook through Citrix. Outlook is a terrible email-client, so this totally sucks. 

Please fix Evolution-exchange...:cry:

---

### Post by myha on 2006-02-15
Well, I have no problems with connecting to exchange server....
But the thing I did is that when I set up the connection I didnt use exchange but IMAP server, and everything works great (exept calendar and contacts).
So try to establish connection to your server through IMAP.

br,
Miha

---

### Post by fer5437 on 2006-02-15
For me there is no problem to setup the evolution mail with the exchange server. I can receive and also send mail. The problem I facing with evolution mail is i cant get my global address book to run. It show error that "Error Loading Addressbook". It show that i either enter a wrong URL or it cant connect to the server. So if I can received and send mail that mean connection with server is fine and the URL address also correct. But still why I cant load the global address book?? Any one ADVISE please.

---

### Post by fer5437 on 2006-02-15
I found out the solution to import PAB from outlook to evolution. Evolution is using LDIF format. So first import the PAB file then export it to LDIF.  Then with Evolution import the LDIF file and now my Evolution working fine with the address book. :D

---

### Post by yl200001 on 2006-02-15
Hi all,

To make it clearer:

1. I input OWA url as: [http://a.company.com/exchange](http://a.company.com/exchange)

2. But Evolution always tried to connect [http://b.company.com/exchange](http://b.company.com/exchange)

3. When I used [http://a.company.com/exchange](http://a.company.com/exchange) in browser, no problem at all

4. Now I just let name resolution pointing b.company.com to IP of a.company.com.
It is ok even evolutionstill trying to connect b.company.com

5. Name b.company.com is still my compnay node, but don't know what it is.
When I use b.company.com as URL in Browser, it prompt me to input user/pwd. after that it prompted me input user/pwd again but this time the connection was routed to a.company.com. Then I can access my mailbox from Browser.

6. Have removed all stuff related with b.company.com in /home/../.evolution/...., the folder with b.company.com will come again after I start evolution. Really don't know how the b.company.com comes?

7. I am able to access mailbox from Evolution IMAP. But I still want to user evoltion connector. I used to succussfully use evolution-connector in Suse 9.1 and 9.3

---

