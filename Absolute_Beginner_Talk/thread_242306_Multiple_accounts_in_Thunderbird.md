---
title: "Multiple accounts in Thunderbird?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Big Fish on 2006-08-23
I'm trying to setup multiple accounts in Thunderbird and it says that I can't have multiple with the same username & server. In Outlook Express, I could make multiple accounts so that when I send an email, I could choose what email address I wanted to send from. Any ideas?

---

### Post by Big Fish on 2006-08-23
anyone? :confused:

---

### Post by ThrashJazzAssassin on 2006-08-23
Try setting up an account with your desired email address, Just type random letters in the boxes where it asks for username and server, then tell Thunderbird to not check that account (server settings).

---

### Post by Big Fish on 2006-08-23
I actually just got it configured with evolution. Is one better than the other?

---

### Post by CarpKing on 2006-08-23
It should be under Edit-> Account Settings.  There will be a button that says "Add Account," which will give you a chance to specify the new email address you want to use, as well as what incoming server it comes from.  The outgoing server is the same for all messages, though I think you can decide which email address shows up on the other end by changing the "From" bar while writing a message.

---

### Post by tomjennings on 2008-06-04
> **CarpKing said:**
> It should be under Edit-> Account Settings.  ... The outgoing server is the same for all messages, .

Oh no, that can't be true? It makes no sense. I have a work address, and a personal address, adn each must use it's own outgoing server. business won't relay for personal, and vice versa.

I assumed Thunderbird could handle this elementary detail... I'll go RTFM.

---

### Post by tomjennings on 2008-06-04
> **CarpKing said:**
> It should be under Edit-> Account Settings.  The outgoing server is the same for all messages, 


This is not true. It's configured slightly oddly, but easy enough.

* Create each email account.
* In 'outgoing server smtp' add each outgoing server.

Then under account settings, click the account name in the left column (this is default when you open account settings). Select the desired outgoing server in the 'outgoing server' pulldown.

---

