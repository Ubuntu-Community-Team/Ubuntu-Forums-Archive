---
title: "Setting up Evolution or Thunderbird."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2006-09-28
Since I have to keep track of several email addresses, I think it would be best to try a mail client, like Evolution or thunderbird.

The two adresses that I want to use are my Gmail address, and my University Email address.

I tried looking up some guides for running Gmail, but I couldn't find any good ones.

Can anyone help me out?

---

### Post by Bachstelze on 2006-09-28
You need to know for both accounts the incoming mail server (POP or IMAP) and your username/password. For Gmail, I think you have to activate POP delivery for your message, they most likely have a help page for it. For your Uni account, ask the administrator if there is no help page.

For the outgoig mail server (SMTP), use your ISP's, it shouldn't require authentication (authentication is done with your IP).

---

### Post by GreenHawkIA on 2006-09-28
A real quick note - I know my University email uses Microsoft Exchange Server for it's email.  (You can tell if your's does too - do you use Outlook Web Access to get at your email on the web?  If so, the answer is yes.)  If yours does, Evolution is the only solution for Linux that will connect to Exchange.   It's slow & buggy because it doesn't connect directly, but rather goes through the web access interface, and can be a pain to set up. So...you'll need additional info if the account is exchange - and I can help you set that up, just let me know through a post here.  Most school administrators have little/no knowledge to help with Linux clients.  (Thunderbird does have an advantage there - they may be able to support it because of its heavy Windows use.)
As to Gmail - log into your Gmail account.  Once you're in click on settings, then the "Forwarding and Pop" tab. Click one of the "Enable Pop" buttons (your choice) and save your changes.  Then click on and follow the "configuration instructions" link on the page - which is very good & easy to understand.  Once again, post here with questions.
Best!
PS - GMail will provide you with their own SMTP server you can use for your GMail accounts so you don't have to go through your ISP if you don't want to.  Your University most likely will not.

---

### Post by streetlightout on 2007-06-09
GreenHawkIA, hey i've been trying to set up either thunderbird or evolution with my microsoft exchange that i have through my college, but i can't get it to work, could you help me out??

---

### Post by quinnten83 on 2007-06-09
What I do at my university is to have all the mail delivered to my school's inbox forwarded to my gmail account.
from there  on I just only have to set up my evolution/ thunderbird to fetch mail.
Evolution can be somewhat of a pain to set up with gmail, since they use secure ports.
whenever you have to enter an pop adres or smtp address, you can finish it with ":port#".
That worked for me.

---

