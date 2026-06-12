---
title: "hotmail and mail blocking"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by paulyche on 2006-06-13
I hope this is an OK place to make this query which isn't strictly ubuntu related. 

I'm have gmail account and am using it in Thunderbird over POP3. It's working well except I've just discovered that hotmail is blocking all emails sent from this account.

I also use another (university) email account in Thunderbird and if I send an email to hotmail with this one it's fine, but if I send the email from the gmail account it appears to send, doesn't get bounced - just doesn't ever appear to the recipient.

I've tried sending with both accounts using three different SMTP servers with the same effect gmail doesn't get through.

sending from the web interface for gmail seems to work.


Anyone else noticed anything like this/know anything about it.

---

### Post by richbarna on 2006-06-13
Just a suggestion, why don't you use Thunderbird to download and read your emails, but use sendmail to send emails directly from your pc?

---

### Post by paulyche on 2006-06-13
sendmail. Hadn't though of that.

I've had a quick look and I can't find a simple howto to set up sendmail for this type of setup. Do you have a link to how to do this before I delve deeper into very long posts and howtos?

---

### Post by Mahmoud on 2006-06-13
[QUOTE=paulyche]I hope this is an OK place to make this query which isn't strictly ubuntu related. 

I'm have gmail account and am using it in Thunderbird over POP3. It's working well except I've just discovered that hotmail is blocking all emails sent from this account.

I also use another (university) email account in Thunderbird and if I send an email to hotmail with this one it's fine, but if I send the email from the gmail account it appears to send, doesn't get bounced - just doesn't ever appear to the recipient.

I've tried sending with both accounts using three different SMTP servers with the same effect gmail doesn't get through.

sending from the web interface for gmail seems to work.


Anyone else noticed anything like this/know anything about it.[/QUOTE]

Did you check your Hotmail Junk folder?
Are you sure you are using Google SMTP?

---

### Post by Mahmoud on 2006-06-13
[QUOTE=richbarna]Just a suggestion, why don't you use Thunderbird to download and read your emails, but use sendmail to send emails directly from your pc?[/QUOTE]

This would probably increase the probability of the email being marked as SPAM. because the SMTP (Sendmail) will be a dynamic IP.

---

