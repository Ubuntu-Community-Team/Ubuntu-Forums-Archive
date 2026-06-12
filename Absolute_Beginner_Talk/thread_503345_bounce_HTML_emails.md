---
title: "bounce HTML emails"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by kwacka on 2007-07-17
I would like to be able to bounce html emails, with an explanation to the sender as to why it has been returned.

Firstly, is this wise (live email address for spam) and, secondly, how? Will I need to setup/configure a mail server or are there any clients that can do this for me?

I'm not overly concerned about choice of email clients - currently using Thunderbird (although Evolution was superb until Novell took it over).

---

### Post by p_quarles on 2007-07-17
You wouldn't actually be able to bounce the emails without installing a server (which, in turn, means setting up an entirely new e-mail account under your own domain). You would also need to set up a spam filter, and given the percentage of e-mail that is spam, doing all of this is very likely to deliver a serious hit to your system's performance. If you have an older machine that you're willing to dedicate as an e-mail server, though, I guess it might work.

A couple things you could try: 1) See if your current e-mail provider(s) offer the option of rejecting html e-mails. 2) See if you can setup a filter in Tbird that identifies html e-mails (I don't know if this is possible), and then replies with a template + deletes it (easy).

---

### Post by kyphi on 2007-08-21
A bit late to respond, I suppose but there is a programme that lets you bounce email messages.  The problem is that spammers often use false email addresses and these cannot be bounced.  Bouncing may also contribute to the flood of junk mail if false addresses are used.

The best option is to delete the messages at the server so that they are not downloaded to your machine.  Using this method I have not seen hide nor hair of any malicious email for many years.

The programme that will accomplish this is MailWasher Pro.  It has been available for Windows for several years and the Windows version runs fine in Ubuntu via CrossOver.

There is a version (finally sufficiently refined) available for Ubuntu and Kubuntu at:

[http://www.firetrust.com/](http://www.firetrust.com/)

Check it out, you will never regret this.

Cheers.

---

### Post by kwacka on 2007-10-21
I was sure that I'd replied to say 'thanks' for the tips but it doesn't appear to be here, so I obviously didn't.

Powers of concentration/memory screwed by obstructive sleep apnoea.

Apologies for my oversight.

---

