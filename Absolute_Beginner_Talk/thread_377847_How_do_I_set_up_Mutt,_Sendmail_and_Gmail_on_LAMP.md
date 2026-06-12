---
title: "How do I set up Mutt, Sendmail and Gmail on LAMP"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-03-06
[LEFT]I have successful setup LAMP with Drupal

However, Drupal needs to submit emails via SMTP.

Would using Mutt, Sendmail and Gmail be a fisable way to approach this problem.

Also how do I implement!!!!

HELP!!!!

Kind Regards

Mr Noob
[/LEFT]

---

### Post by compiledkernel on 2007-03-06
I rather perfer postfix as MTA myself. 

As such 
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

This howto does alot. 

as far as mutt goes, 

sudo apt-get install mutt

---

### Post by robinlennox on 2007-03-06
Another Noob Question...

Can I use postfix to direct mail from the server to go via my gmail account?#

Sorry to be a bother... I know how my Windows Noob users feel now.... :lolflag:

---

### Post by robinlennox on 2007-03-06
OK, OK....

I give the guide a go... and not sure what I was doing... :confused:

Is it possible to run an SMTP server from LAMP?

Can someone clear this up, with a less technical explanation then this guide!

---

### Post by EndPerform on 2007-05-07
> **robinlennox said:**
> OK, OK....

I give the guide a go... and not sure what I was doing... :confused:

Is it possible to run an SMTP server from LAMP?

Can someone clear this up, with a less technical explanation then this guide!

Drupal wants to send out emails using an SMTP server, not run the server itself. The SMTP serverh can be installed alongside of Apache, mySQL, etc.  However, you do not need mutt, since it is a mail client.  There are various howtos out there, one of which was linked in this thread. 

So, technically yes, but you'd be accessing the server running on the box via Drupal, not having Drupal run the server for you.

---

