---
title: "Evolution How to set email account password"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by bteck on 2007-02-04
I could not use Evolution to connect to my email account.  In setting up Evolution, there is a place to enter username but no place to enter password for my email account.  My ISP need me to enter username and password in order to access my email account.  What should I do? 

I could set up Windows Outlook Express and access my email account without problem.  Pls help.

---

### Post by kingmonkey on 2007-02-04
When you try and connect a window will pop up asking you for your password. There will be a little tick box for it to remember it.

---

### Post by bteck on 2007-02-05
> **kingmonkey said:**
> When you try and connect a window will pop up asking you for your password. There will be a little tick box for it to remember it.


After I started Evolution and clicked [Send/Receive], a [Send & Receive Mail] window appeared, showing almost immediately smtp (send part) complete but pop (receiving part) just stayed at 0%.  After about 3 minutes, an [Evolution Error] window appeared, stating: "Could not connect to pop.streamyx.com: Connection timed out".   There was no window to ask me about my username and password.  What could be wrong? Thanks for your response.

---

### Post by unisol on 2007-02-05
do you have a hotmail account?

---

### Post by kingmonkey on 2007-02-05
When it connects it will ask you for password.

Are you sure there are no problems with pop.streamyx.com? If there isn't then try increasing the timeout interval.

---

### Post by bteck on 2007-02-05
Thanks to all for your replies.  I have finally resolved the issue with Evolution after solving my connection problem for package updates!  The problem was I did not set any "search domain" in my DNS settings.  Once I did that, and ran Evolution, it was able to connect to my ISP and the window asking for my passwor did finally appear!  I am now able to send and receive email using Evolution.

Below is a repeat of my post at another thread.  It may be helpful for other newbees.

"I have finally resolved the issue of connection to ubuntu sites for updating of packages.

I ran System->Administration->Networking. In the [Network Settings] window, under the [DNS] tab->[Search Domains] edit box, I clicked the [Add] button and added the domain name: [www.google.com](www.google.com). I then clicked the [Close] button.

When I started a Terminal session and typed: sudo aptitude update, the system was able to connect to various ubuntu update sites and downloaded the required files.

What I have learned for this and from observing the many similar problems faced by newbees is that there is a serious lack of examples in the various Ubuntu help documentation (perhaps the same can also be said about other Linux doc?). Below is an example I picked from the Networking help to make my point:

"3.6.&#8195;To add a new search domain
In the Search Domains section, press the Add button and fill in the new list row with the new search domain."

From this help, the user is not certain whether a "new search domain" is absolutely necessary, or does the system already has some well known domains as defaults which were not shown? If it is absolutely necessary, the help documentation MUST state so, and give a few examples of well known domain names (such as [www.google.com](www.google.com) which I used) to help the newbee.

I understand that it takes lots of efforts to produce a good documentation. It is just a thought that could we make it a point to add at least ONE example for each item requiring a help? Otherwise, the efforts put into help is wasted anyway.

Anyway, thanks for all who has responded. Your certainly have helped me."

---

