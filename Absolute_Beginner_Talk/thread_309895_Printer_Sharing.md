---
title: "Printer Sharing"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by tc10b on 2006-11-30
Hi,

I have two linux machines, one running Ubuntu 5.10 and one running 6.06. I also have a shared internet connection between the two with my router.

I wanted to know how to enable printer sharing, I've sort of read about doing it and would like to get it done, so that I can print from the other room.

Problem is I don't really know how to do it, and would appreciate some guidance.

Cheers

Tom

---

### Post by gborzi on 2006-11-30
I don't remember how to share printers in 5.10, but in 6.06 and 6.10 you have to give the following commands: > sudo /usr/share/cups/enable_browsing 1
sudo /usr/share/cups/enable_sharing 1 on your print server. Then configure the client through the GUI.

---

### Post by wpshooter on 2006-11-30
> **tc10b said:**
> Hi,

I have two linux machines, one running Ubuntu 5.10 and one running 6.06. I also have a shared internet connection between the two with my router.

I wanted to know how to enable printer sharing, I've sort of read about doing it and would like to get it done, so that I can print from the other room.

Problem is I don't really know how to do it, and would appreciate some guidance.

Cheers

Tom

Dear Tom:

I would not attempt to hold my breath while I was attempting to get this done.  I believe I would be very purple before it got done.  I have given up on trying to get printer sharing to work on a Ubuntu home network.  I believe I will wait until they have completed the programming, so this can be done without having to re-inventing the wheel.  I am sure you realize this could be accomplished in M/S windows in probably less than five minutes.

But good luck, if you decide to persue this.

---

### Post by tc10b on 2006-12-02
Hmm, I was hoping it might actually be possible and hopefully not too difficult.

Thanks for the advice everyone.

---

### Post by tc10b on 2006-12-02
tc10b@tc10b-175-175:~$ sudo /usr/share/cups/enable_browsing 1
Password:
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
tc10b@tc10b-175-175:~$ sudo usr/share/cups/enable_sharing 1
sudo: usr/share/cups/enable_sharing: command not found

---

### Post by gborzi on 2006-12-02
> **tc10b said:**
> tc10b@tc10b-175-175:~$ sudo /usr/share/cups/enable_browsing 1
Password:
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
tc10b@tc10b-175-175:~$ sudo usr/share/cups/enable_sharing 1
sudo: usr/share/cups/enable_sharing: command not found

You missed the leading / in the second command, it should read > sudo **[COLOR="Red"]/[/COLOR]**usr/share/cups/enable_sharing 1

---

### Post by zytsef on 2006-12-02
In cupsd.conf (usually in /etc/cups/ unless ubuntu puts it someplace strange)on the computer with the printer in the location directive make it look like the following:
```
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.* (or whatever your local IP subnet is)
</Location>
```
Then add the name of your now properly (hopefully) configured print server to /etc/hosts with its IP on the client, modify /etc/clients.conf with 'ServerName <name of the printer server here>' (without quotes, of course). You should more or less be ready to go from there.

Consult the man pages and [documentation]("http://www.cups.org/documentation.php") if you still have trouble.

---

### Post by bruceathome on 2006-12-17
Thanks guys, worked flawlessly.

---

### Post by tc10b on 2006-12-20
Hi, thanks for all the help guys.

Can I just ask a stupid question? What is the address 127.0.0.1

And if the client machine is running Windows, will I have to do anything else on the server end?

Cheers.

Tom

---

