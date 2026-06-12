---
title: "Thin client recommendations? (Edubuntu)"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-02-04
I have read through many of the help pages about setting up Edubuntu for thin client operation.

It didn't work the first time.  I am going to start over from scratch.

Do you have to have two NICs on the server?
Is it possible to connect the server to a switch through through which a number of other computers get the internet also?  Some of these computers will be thin clients, others will have Windows.
Should I plug both NICs cards of the server into the same switch, giving them different IPs, and domains, etc. so the clients have something easier to look for?

I appreciate any help.

---

### Post by iAtari on 2008-02-08
We're running an Edubuntu server with a few thin clients at our school.

Yes, two NIC cards are needed. One for input and one for output. You could use a wireless connection for input and ethernet for output, i'm not sure how well that works.

You can plug one NIC card into the incoming internet, on a switch or not, as long as no thin clients are plugged into this switch.

You'll need to assign the other NIC card to a switch where your thin clients will be booting off of. All thin clients must be plugged into this. Enable booting from a network on your clients. 

iAtari

---

