---
title: "accessing unix server with linux"
date: 2005-05-09
forum: Absolute Beginner Talk
---

### Post by linux_fish on 2005-05-09
Here's what I'm trying to do: my company runs  workstations off a unix server. Currently the server can be accessed remotely (within the company's network) via Telnet in Windows. However, do to my dislike of Windows, I wanted to use a linux distro (ie Ubuntu) to acomplish the same thing. Is this possible and if so how?

---

### Post by kassetra on 2005-05-09
[QUOTE=linux_fish]Here's what I'm trying to do: my company runs workstations off a unix server. Currently the server can be accessed remotely (within the company's network) via Telnet in Windows. However, do to my dislike of Windows, I wanted to use a linux distro (ie Ubuntu) to acomplish the same thing. Is this possible and if so how?[/QUOTE]

Well, Telnet is available in Linux as well, including Ubuntu.  You have to open a terminal window by going 
Applications->System Tools->Terminal
That opens a terminal window; from there you type telnet and an address.

Do you know the address that they're using on the Windows side?  That would greatly help you out when trying to connect to the servers.

---

### Post by linux_fish on 2005-05-09
I do know the address (I'm assuming IP). Can this be tested from a live CD?

---

### Post by the_clown on 2005-05-09
[QUOTE=linux_fish]I do know the address (I'm assuming IP). Can this be tested from a live CD?[/QUOTE]
 Yes,telnet can be tested with the live cd.

---

### Post by kassetra on 2005-05-09
[QUOTE=linux_fish]I do know the address (I'm assuming IP). Can this be tested from a live CD?[/QUOTE]

Yes, IP address.

Yes, you can totally test this out with a live cd.

Pop in the cd, reboot, when it boots up - you'll want to make sure you have a network connection (if you don't know how to check, I can help) then - 

Applications->System Tools->Terminal
type this in the window:
```
telnet IP_ADDRESS
``` Press enter.  You should get something back asking for user/pass if your company requires authentication.  Log in, and you're good to go.  :)

---

### Post by linux_fish on 2005-05-09
Thanks for the help. I'll post after I test it out!  :smile:

---

### Post by linux_fish on 2005-05-22
[QUOTE=linux_fish]Thanks for the help. I'll post after I test it out!  :smile:[/QUOTE]


Had no luck with the Live CD, will try with a laptop with Ubuntu installed. More to come.

---

### Post by socratesgdl on 2008-01-30
Hello friends. I just installed ubuntu to access unix server (mfg-pro database), using telnet 192.168.4.200 (with console), but when I request a report, the printing appears in the console and NOT TO THE PRINTER...

In windows, when I access the unix server, I use REFLECTION emulation and it works well.

How can I solve this problem?


thanks

---

