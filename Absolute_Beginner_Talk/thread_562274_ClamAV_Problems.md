---
title: "ClamAV Problems"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-28
I installed clamav on a mail server and found that it was using 100% processer
for 15 minutes at a time then off for 5 minutes and on again for 15 minutes this is way to much drain on the old system are there any fixes.

I have seen something about clamd,but how would I start this using this with mailscanner, I have a command in the mailscanner.conf file that says Virus Scanners = Clamav which starts automatically ?

---

### Post by kc5goi on 2007-09-28
Larry, last week I replaced and old sendmail server with a postgrey, postfix, MailScanner (ClamAV and Spamassassin) setup.  Aptitude did not install clamd for me.  I have not seen the processor issue you referred to but I did have an issue with ClamAV not being able to update.  Clamd takes care of that process and I believe it is started as a daemon on boot.  Once I installed clamd, my issue with clamd.ctl stopped and updates were happening on my defined time frame.

---

### Post by HermanAB on 2007-09-28
You should use clamd and spamd for best efficiency.  However, you should ensure that clamd is only called on what little is left over after greylists, blacklists, dcc, razor and spamassassin.  Since virus scanning is very processor intensive, it should be the very last thing in the chain.  

An alternative to grey and blacklists is to severely throttle the incoming SMTP server.  Put a 5 to 10 second sleep between waking up and sending the SMTP banner, then do a 1 second sleep every step of the way through the SMTP state machine.  This is guaranteed to make 90% or more of spammers give up and go away in disgust, while real mail is only delayed by 10 seconds or so.  Note that if you do this, then you have to allow for more simultaneous threads.

Cheers,

Herman

---

### Post by larry Gaminde on 2007-09-28
If you have a gui interface right click on the upper or lower pannel and click on add to pannel go to utilities and drag system monitor to your pannel then right click on it and make sure processor is selected and watch it a while and see if your processor usage goes sky high for minutes at a time when nothing else is  happening.

---

### Post by larry Gaminde on 2007-09-28
also my system shows clamscan running so how did you get clamd to run

---

### Post by larry Gaminde on 2007-09-28
I have the setup you are suggesting but had to remove clamav because of the processor usage it was just running all the time even if I did not get mail which is very little on this setup

---

### Post by larry Gaminde on 2007-09-28
Herman how do you run clamd and spamd Im really not sure how they are being started or how to set up for this as clamav run clamscan for me


> **HermanAB said:**
> You should use clamd and spamd for best efficiency.  However, you should ensure that clamd is only called on what little is left over after greylists, blacklists, dcc, razor and spamassassin.  Since virus scanning is very processor intensive, it should be the very last thing in the chain.  

An alternative to grey and blacklists is to severely throttle the incoming SMTP server.  Put a 5 to 10 second sleep between waking up and sending the SMTP banner, then do a 1 second sleep every step of the way through the SMTP state machine.  This is guaranteed to make 90% or more of spammers give up and go away in disgust, while real mail is only delayed by 10 seconds or so.  Note that if you do this, then you have to allow for more simultaneous threads.

Cheers,

Herman

---

### Post by HermanAB on 2007-09-28
I used to run Postfix, Amavisd-new, SpamAssassin and ClamAV.  Amavisd-New will unpack attachments and archives before submitting them to the scanners.  This kind of setup is explained in howto guides on the Postfix web site ([http://www.postfix.org](http://www.postfix.org)).

Nowadays, I run Citadel ([http://www.citadel.org](http://www.citadel.org)), which uses a small script to hook ClamAV into SpamAssassin ([http://wiki.apache.org/spamassassin/ClamAVPlugin](http://wiki.apache.org/spamassassin/ClamAVPlugin)).

I find the Citadel solution to be vastly superior.  It installs in a few minutes when using Easy Install. Citadel is fast, efficient and zero maintenance.

Cheers,

Herman

---

### Post by Pacif13r on 2007-09-29
I have a similar problem and it ends with mail often being barred as a denial of service attack for taking so long to scan. From what I've been able to discover this is due to clam taking an absurd amount of time to start up from cold. This combined with Mailscanner starting it for every mail or batch results in a scan rate on my small server (Athlon 2.5Ghz w/ 512MB) of approx 25 bytes per second. Therefore a 3KB text mail can take around 5 minutes so may well be running when the next batch starts which as you can imagine leaves two clam threads trying to consume 100% CPU.

Apparently this is a relatively new development and is the result of a change in the clam code. The solution is to use clamd which is always running. However as you've noticed the old version of Mailscanner that comes with ubuntu is not able to easily support clamd. Versions since early June are able to, but for some reason this package is quite out of date in ubuntu, seemingly over a year.

I was hoping to wait for an official package update but even the latest version of ubuntu appears to be using a very old version of Mailscanner so I'm not going to hold my breath. May end up installing it myself at this rate, though I'm loathe to take on the hassle of security patching manually, I like to just set and forget.

Hope that helps, I may be wrong but that's where I think it's at.

---

### Post by HermanAB on 2007-09-29
Instead of mailscanner, you should try amavisd-new.  It works essentially the same way, only better.  Amavis listens on a port (usually 10024) for a message passed to it by the MTA (usually Postfix).  It then unpacks the attachments and scans them using spamd and clamd (or whatever scanners it can find - it is autoconfiguring - nice).  When done, it sends the message back to the MTA (usually port 10025) for delivery (or junking).

Cheers,

H.

---

