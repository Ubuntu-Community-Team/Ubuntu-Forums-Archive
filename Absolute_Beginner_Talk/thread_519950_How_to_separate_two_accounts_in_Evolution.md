---
title: "How to separate two accounts in Evolution?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2007-08-07
I just set up Evolution for my emails.

I have two accounts set up. But Evolution mixes the two accounts together. I'd like to see two accounts separately. I mean I like to see:

[email]myname1@gmail.com[/email]
   inbox
  sent
  draft
   trash
[email]myname2@aol.com[/email]
   inbox
  sent
  draft
   trash

instead of 
 
on this computer
   inbox
  sent
  draft
   trash

BUt I can not figure out what to do. Thanks.

And where is the "Message filter"? Thank you.

---

### Post by nichipet on 2007-08-07
I'm not sure if it can be done. What you want, it sounds like, is to not use a global inbox. Thunderbird has this separation. In Thunderbird you can use the global inbox and every account shares folders or you can not use the global inbox and they each get their own set of folders. One option you have is to switch to Thunderbird. If you weren't aware of it being called "global inbox" maybe that can help with searches. I'll see if I can find anything else on it.

---

### Post by walkerk on 2007-08-07
> **Hxsrmeng said:**
> I just set up Evolution for my emails.

I have two accounts set up. But Evolution mixes the two accounts together. I'd like to see two accounts separately. I mean I like to see:

[email]myname1@gmail.com[/email]
   inbox
  sent
  draft
   trash
[email]myname2@aol.com[/email]
   inbox
  sent
  draft
   trash

instead of 
 
on this computer
   inbox
  sent
  draft
   trash

BUt I can not figure out what to do. Thanks.

I'm curious myself. I've used tbird but I wanted to come back to Evolution. My currect fix is that I have seperate folders under Inbox (for each account) w/ rules to place email in the correct folder. Of course this fix only works for the Inbox.

---

### Post by nichipet on 2007-08-07
According to this screenshot, it can be done.

[http://www.gnome.org/projects/evolution/images/screenshots/2.4/read-mail.png](http://www.gnome.org/projects/evolution/images/screenshots/2.4/read-mail.png)

---

### Post by Hxsrmeng on 2007-08-07
> **nichipet said:**
> According to this screenshot, it can be done.

[http://www.gnome.org/projects/evolution/images/screenshots/2.4/read-mail.png](http://www.gnome.org/projects/evolution/images/screenshots/2.4/read-mail.png)

This is exactly what I want. But how?
Thanks.

---

### Post by Ajc on 2007-11-04
- both of the accounts shown in your picture appear to be network related.

- the I created "two accounts", was to create a folder for each account concerned, then created rules based on that address.
e.g. email for [email]fred.bloggs@wherever.com[/email]  => Fred's folder

re sent items, there is an option in the accounts setup to say where you want sent items from this account to go
- i would choose Fred's / Sent Items folder
(having created a folder of that name of course under the folder)

trust that helps !

Ajc:guitar:

---

### Post by AgentZ86 on 2007-11-08
> **walkerk said:**
> I'm curious myself. I've used tbird but I wanted to come back to Evolution. My currect fix is that I have seperate folders under Inbox (for each account) w/ rules to place email in the correct folder. Of course this fix only works for the Inbox.

I would like to the instead of option can anyone express how to do this.

I setup my first email account as a IMAP account and it is working well, however I prefer the global inbox type of feature as shown in the (instead) part of the thread as posted.

Please advise how to configure Evolution to combine all my inboxes etc. I don't want all these accounts listed. I prefer the more thunderbird-ish type global inbox ? 

Please advise.
Thanks

---

### Post by Turin Turambar on 2007-12-06
I don't know how to create global thunderbird-ish inbox, but here's how to use the filters.

If you want to receive mail in separate inbox do this:
First, create a folder, like "Peanut Inbox".
Then, go to Edit/Message filters. Use "show filters for mail: incoming".  Add a filter. In the first line use "Recipients containts <youremail>". THEN "Move to folder"  "Peanut Inbox".

By creating this filter, every mail that contains your email address will be filtered to Peanut Inbox. The same can be created for Outbox, just use the opposite filter rules.

Hope this helped.

---

