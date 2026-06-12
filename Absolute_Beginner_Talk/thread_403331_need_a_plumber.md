---
title: "need a plumber"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by rgp-02 on 2007-04-06
OK, do we have any plumbers out there? here's my problem.

evolution email says:

Error while performing operation.

Could not send message: Broken pipe

---

### Post by nudnik on 2007-04-06
> **rgp-02 said:**
> OK, do we have any plumbers out there? here's my problem.

evolution email says:

Error while performing operation.

Could not send message: Broken pipe

Check the Synaptic Package Manager, and click on the "fix broken packages" option.
If that doesnt work, more intrusive command line work will have to be performed.

---

### Post by TheMono on 2007-04-06
Hilarious question. I'm sorry, but I'm going to need to buy a part to fix this, and while I do so you're going to have to stare at my crack poking out over my plumber's shorts.


On a slightly more relevant note, what smtp provider are you using? As in, are you sending through gmail SMTP, or a university SMTP, or your ISP? And are you sure it is configured correctly?

Further, has it worked in the past, or never worked?

---

### Post by rgp-02 on 2007-04-06
thank you(s) for your responses.

tried the “fix broken packages” thing; didn't work.

not sure if configured correctly....did it a few months back (probably screwed it)....can't remember what kind of crap i entered into it........it never worked so i kinda sidestepped it a while, but it would be nice to get it working.

---

### Post by nudnik on 2007-04-06
> **rgp-02 said:**
> thank you(s) for your responses.

tried the “fix broken packages” thing; didn't work.

not sure if configured correctly....did it a few months back (probably screwed it)....can't remember what kind of crap i entered into it........it never worked so i kinda sidestepped it a while, but it would be nice to get it working.


Presented with this new information, I can say it sounds like your email settings are incorrect. I thought perhaps Evolution had been scrambled by a modification.

Most ISPs and or mail service providers offer instructions for configuring your mail client. 99% of them will not offer instructions for Linux, but, fortunately, Microsoft's Outlook Express is so similar, you can usually fudge your way to success using the instructions for that client.

---

### Post by freebird54 on 2007-04-06
I had trouble at first with Evo - until I figured out that its defaults were not qite what I though they were...  The most likely point of error, IME, is in the choice of Authentication type:

Edit->Preferences (select your connection) Edit->Sending Email (tab) and near the bottom is Authentication.  Most common I've seen is Login - but you might try a few others to see.  I think the button next to it offers to try to discover it for you.  BTW - if it is Login - A prompt will appear for you to enter your password into when you next attempt a connect.

Hope this helps!

---

### Post by rgp-02 on 2007-04-07
Thank you guys again for your helpful responses, but it doesn't look too optimistic for a retarded specimen like myself.

went to edit/preferences/edit/sending email tab and probably screwed up here because i have no idea how to fill in these fields. 

Server Type: SMTP or Sendmail (no idea)

Server Configuration
Server:  (no idea)

Security (no idea)

etc. etc. etc.

also, edit/pref/edit/receiving email Server Type: has a dropdown w/several options of which i am not at all familiar.

How do i go about finding out what to put in these?

---

### Post by Maestro23 on 2007-04-07
> **rgp-02 said:**
> Thank you guys again for your helpful responses, but it doesn't look too optimistic for a retarded specimen like myself.

went to edit/preferences/edit/sending email tab and probably screwed up here because i have no idea how to fill in these fields. 

Server Type: SMTP or Sendmail (no idea)

Server Configuration
Server:  (no idea)

Security (no idea)

etc. etc. etc.

also, edit/pref/edit/receiving email Server Type: has a dropdown w/several options of which i am not at all familiar.

How do i go about finding out what to put in these?

I'm with Comcast.  Here is mine:

> Receiving: POP
                    mail.comcast.net

Sending: SMTP
                  smtp.comcast.net


Contact your ISP if you don't know yours.

---

### Post by freebird54 on 2007-04-07
One of the easiest ways to find it is in an existing Windows configuration - if you have one  The answers are the same (they are for your ISP) regardless of the OS you are accessing them from.  Here's my settings too:

```
Server Type:  **POP**
Server:  **pop.*nameofserver*.com**
Authentication:  **Password**
Remember password: **ticked**

```
Send is like this

```
Server Type:  **SMTP**
Server: **smtp.*nameofserver*.com**
Server requires authentication: **ticked**
Authentication:  **Login**
Username:  ***yourusername***
Remember password: **ticked**
```

YMMV  (your mileage may vary) - but that is a quite common setup - and all that it needs to know.  Hope you can track doen the information!

---

### Post by rgp-02 on 2007-04-07
PROBLEM SOLVED!

THANKS FOR YOUR HELP!

BOTH SEND & RECEIVE WORKING WELL!

I AM NOW TOTALLY OVERJOYED AND NEED TO BE SEDATED!

KETUSHHHHH (that was a beer)

ubuntu.................I LOVE YOU!

---

### Post by freebird54 on 2007-04-07
Hope the beer does the job!  If you get a chance, EDIT your first post, choose Advanced, and tick RESOLVED, and SAVE - always helps other searchers.... :D

---

### Post by Maestro23 on 2007-04-07
> **rgp-02 said:**
> PROBLEM SOLVED!

THANKS FOR YOUR HELP!

BOTH SEND & RECEIVE WORKING WELL!

I AM NOW TOTALLY OVERJOYED AND NEED TO BE SEDATED!

KETUSHHHHH (that was a beer)

ubuntu.................I LOVE YOU!

Good deal man.  Have a Killian's for me.:guitar:

---

### Post by freebird54 on 2007-04-07
Damn - can't find any around here.  Where would I look?  In the meantime I'll settle for a Lakeport Honey Lager..... :)

---

