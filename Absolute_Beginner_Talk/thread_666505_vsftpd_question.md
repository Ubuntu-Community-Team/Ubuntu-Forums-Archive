---
title: "vsftpd question"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by rbdragonfire on 2008-01-13
Hello All,

I recently started using Ubuntu (Server Edition - console only). I installed vsftpd on the machine using aptitude. Everything seemed well, and then  I came across 2 problems:

1) When I try to do this - sudo vsftpd [start/stop/restart], I end up with the error message
500 OPS: vsftpd: cannot open config file: [start/stop/restart]
Though the server is already running!! I also tried this sudo /etc/init.d/vsftpd [start/stop/restart], and it ended up to the same effect!

So now, when i make a change to the config file, I reboot the machine for the effect to take place :(

2) This is the main problem now - okay, I can log in to the ftp server with my username and password; it logs into my home directory. Now, I try to upload a file and I get error 550: Permission denied (this is my home directory though!)

I hope someone can help me out with these (at least #2). Thank you very much in advance!!!

---

### Post by bwhite82 on 2008-01-13
I'm not sure about your first problem but as for your second: Are you using root priveleges to log on? If so, don't.

Edit: Now that I think about it, both problems seem to be permissions related. Did you have to install with root priveleges?

---

### Post by rbdragonfire on 2008-01-13
Hi,

Yes, I had to install by 'becoming root' (I installed using aptitude). I tried uninstalling and reinstalling using apt-get as a normal user - I couldn't, so now, I have reinstalled it. This time I used,

sudo apt-get install vsftpd

---

### Post by bwhite82 on 2008-01-13
Is everything working fine then?

---

### Post by rbdragonfire on 2008-01-13
Hi Soldierboy,

Thanks for replying. I think I have got it working now - not sure if this is how it should be done (I hope I am not introducing new security threats for #2!). If this can be confirmed, it would be very much appreciated:smile:

Addressing problem #1 for some reason "sudo /etc/init.d/vsftpd restart" works now

Regarding problem #2, I did the following changes to /etc/vsftpd.conf: WRITE_ENABLE=YES. Now, I can upload files to the directory

---

