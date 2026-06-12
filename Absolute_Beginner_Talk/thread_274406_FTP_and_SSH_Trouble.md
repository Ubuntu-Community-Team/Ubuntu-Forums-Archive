---
title: "FTP and SSH Trouble"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by splendid on 2006-10-09
I installed and have had FTP and SSH working for about 3 months with ddclient.  I am unable to access it by ip address or my dyndns domain.  I did not change anything recently.  Any ideas on where to check??

Thanks

---

### Post by wieman01 on 2006-10-09
Have you installed a firewall (e.g. Firestarter) recently? What about port forwarding on the router?

---

### Post by dmizer on 2006-10-09
after 3 months of service with dyndns, you have to "touch" your account or they assume it's inactive and turn it off.  go to dyndns.com and log in.  go to "account" and under "my services" click on the "my services" link.  under "host level services" select "dynamic dns" (which you'll likely find has been disabled).  if your ip address has changed, update it with the new one, if not, don't change it at all, and simply click "modify host".

all should be well then.

if you have a router, some routers can be configured to automatically update this for you.  if your server is directly connected to your modem, there is a utility that can perform this for you as well, though i don't have information on hand at this moment.

edit: i see ... ddclient (which  you indicate you're using).  you sure ddclient is working correctly?  is your server behind a router? (if so, ddclient will update dyndns with your local ip ... 192.168.1.x ... rather than your web ip).

---

### Post by wieman01 on 2006-10-09
"NOT touching" the account is only a problem if you don't have any sort of client running that takes care of you DynDNS account. Usually a client logs on and updates the IP address during startup which then tells DynDNS that your account is still active. 

So I don't think that's his problem. He cannot even "ping" his computer using the IP address. It's obvious something else is wrong.

N.B.: My router (WRT54G with latest firmware) actually supports DynDNS. So I disabled DDClient a while ago... Pretty good option as the network is kept in sync with DynDNS without me having to boot my server all the time.

---

### Post by wieman01 on 2006-10-09
Plus... Check with your service provide if they started to block the SSH/FTP ports. That's also a possibility next to the mentioned firewall.

---

### Post by dmizer on 2006-10-09
> **wieman01 said:**
> I don't think that's his problem. He cannot even "ping" his computer using the IP address. It's obvious something else is wrong.

agreed ... see my edited post.  i got carried away with answering questions and not reading carefully enough.  my bad.

---

### Post by dannyboy79 on 2006-10-10
are you sure that your IP didn't change from your ISP? I know it is very uncommon for ISP's to hand out Statis ip's for home based consumer's. my ip changes a few times a year. it's possible that it changed and his software to update his ftp ip didn't work? is your ftp/ssh services even running, did you check that? these are just thoughts in helping you trouble shoot this. i recently couldn't figure out why my ftp server wasn't allowing me to get access and it was because i had a power outage and when my machine turned back on and loged on the ftp service didn't start backup for some reason?

---

### Post by splendid on 2006-10-11
Thanks for all your replies.  I am going to take a look at it tonight and follow your suggestions.  I'll let you know how I make out.

---

### Post by splendid on 2006-10-11
Gang,

I went to my DynDns account and updated settings (I really did not change anything), and wala it worked.

Thanks for all your help.  Now I can focus on my Apache problem.

---

