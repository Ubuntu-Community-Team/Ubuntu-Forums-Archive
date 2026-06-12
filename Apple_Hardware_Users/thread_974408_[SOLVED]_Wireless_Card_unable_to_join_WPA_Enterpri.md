---
title: "[SOLVED] Wireless Card unable to join WPA Enterprise network"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by anando on 2008-11-07
Hi

**Background**:
I have a (1,1) MBP running Intrepid. Since the proprietary driver gave me some problems with suspend, I started using the Ath5k drivers by installing intrepid-backports package.

I have been able to join WPA2 wireless network at home. However at work, I can't seem to connect to the WPA Enterprise network at all despite trying out all the various combinations of PEAP versions, Inner Authentication methods and setting the CA authority to [FONT="Courier New"]/etc/ssl/certs/ca-certificates.crt[/FONT] as advised in this website [**[COLOR="DarkSlateGray"]http://imss.caltech.edu/cms.php?op=wiki&wiki_op=view&id=563[/COLOR]**]("http://imss.caltech.edu/cms.php?op=wiki&wiki_op=view&id=563"). I used to connect quite often to this network when I had 8.04 installed on the same laptop before.

I wonder what has changed in 8.10 and if anyone in the forum has words of advice on this. I'd really appreciate it.

Regs,
Anand.

---

### Post by anando on 2008-11-10
Following the suggestion at the very end of [this post]("http://ubuntuforums.org/showthread.php?t=970236&page=3") in the Networking forum, I can confirm that if I choose the [FONT="Courier New"]/etc/ssl/certs/Thawte_Premium_Server_CA.pem[/FONT] file where it asks for the certificate file, I *am* able to join the **WPA2 Enterprise** networks using network-manager in 8.10.

Previously in 8.04 it used to be the case that one could use any old .crt file in /etc/ssl/certs - e.g /etc/ssl/certs/ca-certificates.crt would work well. After a lot of trouble, I figured out that since 8.10, *.crt files don't work with network-manager anymore, but .pem files do.

I hope this is useful to other people.

Cheers,
Anand.



> **anando said:**
> Hi

**Background**:
I have a (1,1) MBP running Intrepid. Since the proprietary driver gave me some problems with suspend, I started using the Ath5k drivers by installing intrepid-backports package.

I have been able to join WPA2 wireless network at home. However at work, I can't seem to connect to the WPA Enterprise network at all despite trying out all the various combinations of PEAP versions, Inner Authentication methods and setting the CA authority to [FONT="Courier New"]/etc/ssl/certs/ca-certificates.crt[/FONT] as advised in this website [**[COLOR="DarkSlateGray"]http://imss.caltech.edu/cms.php?op=wiki&wiki_op=view&id=563[/COLOR]**]("http://imss.caltech.edu/cms.php?op=wiki&wiki_op=view&id=563"). I used to connect quite often to this network when I had 8.04 installed on the same laptop before.

I wonder what has changed in 8.10 and if anyone in the forum has words of advice on this. I'd really appreciate it.

Regs,
Anand.

---

### Post by cyberdork33 on 2008-11-10
Thanks for the information. If this solution works for you, can you please mark this thread as solved?

---

