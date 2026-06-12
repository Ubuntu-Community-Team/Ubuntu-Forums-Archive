---
title: "How to monitor software-RAID1?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by amigaone_xe on 2008-04-10
I've installed Ubuntu 8.04 Beta om my new fileserver.
The system is running on software raid1.

Everything works fine but I want to automatic monitor the raid-setup as I'm not going to logon to the fileserver that often.

I want an e-mail sent to me (not a local mail on the server) when the raid1 gets degraded.

I've tried following some how-to's on this foum but I don't get them to work the way i want. 
[http://ubuntuforums.org/showthread.php?t=666614&highlight=mdadm+monitor](http://ubuntuforums.org/showthread.php?t=666614&highlight=mdadm+monitor)
[http://ubuntuforums.org/showthread.php?t=739024&highlight=mdadm+monitor](http://ubuntuforums.org/showthread.php?t=739024&highlight=mdadm+monitor)
[http://ubuntuforums.org/showthread.php?t=739024&highlight=mdadm+monitor](http://ubuntuforums.org/showthread.php?t=739024&highlight=mdadm+monitor)

They try to send an e-mail but i get this local e-mail..
It seems that i can't send mails to remote domains. How do I enable that?

> This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  ********@hotmail.com
  **Mailing to remote domains not supported**

------ This is a copy of the message, including all the headers. ------

Return-path: <drbrain@fileserver>
Received: from drbrain by FileServer with local (Exim 4.69)
        (envelope-from <drbrain@fileserver>)
        id 1Jk0LB-0002C4-Ol
        for ********@hotmail.com; Thu, 10 Apr 2008 19:13:37 +0200
To: *********@hotmail.com
Subject: ./raid_status_2.sh: Software RAID device failure on FileServer
Message-Id: <E1Jk0LB-0002C4-Ol@FileServer>
From: drbrain <drbrain@fileserver>
Date: Thu, 10 Apr 2008 19:13:37 +0200

Failure of one or more software RAID devices on FileServer



Or is there another way to do this in an easy way?
Thanks in advance!

---

### Post by seepage87 on 2008-04-18
You can use esmtp to send the mail via gmail's smtp or something.  Just make sure you have this in your /etc/mdadm/mdadm.conf:
```

MAILADDR youremailaddress@whereitis.com

```

mdadm will use the sendmail command (which esmtp works fine with) to send you an email.  Just configure /etc/esmtprc with your smtp settings. e.g.:

hostname=smtp.gmail.com:587
username=youraddress@gmail.com
password=*******
starttls=required

---

### Post by amigaone_xe on 2008-04-19
Still the same error-message when running:  sudo mdadm --monitor --scan --oneshot --test

 "Mailing to remote domains not supported"

Could it be that its still trying to use exim as the mail delivery system?


Edit: Removed exim4 and installed postfix instead. Way easier to configure and worked like a charm almost directly...

---

