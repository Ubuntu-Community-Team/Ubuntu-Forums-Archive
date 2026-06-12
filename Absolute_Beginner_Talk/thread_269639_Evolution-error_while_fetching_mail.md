---
title: "Evolution-error while fetching mail"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Taffy2 on 2006-10-02
I have Ubuntu up and running on a separate hard drive. I have a serial modem and a dial-up ISP. When I activate the modem it dials up and seems to make a good connection.

However when I try to download e-mails using Evolution I get the following message "error while fetching mail. host look-up failed"

When I try to use Firefox itsays "server not found"

I am new to Linux and very impressed with Ubuntu any help will be appreciated.

Taffy2

---

### Post by bluefrog on 2006-10-02
Looks like a dns problem to me.

to test you could open a terminal (apps/accessories/terminal) and try the following:

ping 82.211.81.166

if you have a reply your internet connection is ok

ping [www.ubuntu.com](www.ubuntu.com)

no response means a dns problem

in that case you will have to enter a proper dns server ip address in system/administration/networking (or sudo vi /etc/resolv.conf)

James

---

### Post by Taffy2 on 2006-10-02
James,
Thank you for your help. I entered my server IP address as suggested and got a reply to both pings. Firefox is working OK and I can download pages from the Internet but Evolution still will not fetch the mail giving me the same error message.

It is something that I will have to sort out with my ISP. I am much further ahead now after your help.

Thanks again

Ted.

---

### Post by Imsati on 2006-10-02
What type of mail do you use? Pop3/SMTP? Did you check to make sure both outgoing and incoming are typed in correctly?

For example, my outgoing is mail.comcast.net and incoming is smtp.comcast.net

---

### Post by Taffy2 on 2006-10-04
Thank you. Stupid question, where do I type the info in?
Ted.

---

### Post by macogw on 2006-10-04
edit > preferences should take you to the same screen as when you set up evolution

---

### Post by Taffy2 on 2006-10-04
Thanks for your help. Typed in the correct details this time and everything works. Will be able to dispense with XP shortly. Thanks again.

---

### Post by kenny1948 on 2007-11-04
I am having a similar problem. I use RoadRunner and have checked with my ISP and they insist my e'mail is working fine.  I have a Pop3 server and it (Evolution) is set up correctly. I get a return on a ping. 
Now here is my very strange problem.  I am getting all my messages on Evolution two days late!

This morning I got all my messages for November 2nd.  Anyone have any ideas as to what is causing this.  I also have a problem with Evolution timing out during a download.  Then Evolution shuts down entirely.  When I start it back up, it reloads all the old messages, including the ones I deleted.  I am mystified.:confused:

---

