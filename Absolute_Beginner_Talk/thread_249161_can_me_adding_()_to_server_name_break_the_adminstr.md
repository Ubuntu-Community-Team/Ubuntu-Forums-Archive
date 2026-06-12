---
title: "can me adding () to server name break the adminstraive application???"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Budgi on 2006-09-02
Hi Guys,

I feel so stupid posting this. I think I have broken my server because I put brackets around the second word on the server name. So if you look at it from a pc you will see server (ubuntu) and now i have done it things arent working right and I went back in to fix it but the administration application wont load. PLEASE HELP!

Thanks guys.

- Budgi

---

### Post by rowanparker on 2006-09-02
If by servername you mean hostname look [here]("http://ubuntuguide.org/wiki/Dapper#How_to_change_computer_name").

---

### Post by Budgi on 2006-09-02
Yep sorry your right but i cant get into that bit 

    * Read #General Notes
    * System -> Administration -> Networking
    * Network settings 

General Tab -> Host Settings -> Hostname: Specify the computer name 

    * Save and close all opened applications, Reboot computer 

because i cant get into networking it doesn nothing it looks like it will load and then doesnt

---

### Post by rowanparker on 2006-09-02
How did you change it in the firstplace?
Did you edit /etc/hostname?

---

### Post by Budgi on 2006-09-02
no i did it as you said in the first place but now it wont let me back in.

---

### Post by rowanparker on 2006-09-02
Have you restarted?

If it doesn't work after you restart then make sure the first and second lines in /etc/hosts have your new hostname. If sudo doesn't work, boot into recovery mode.

---

### Post by steve.horsley on 2006-09-02
The trouble is that the hostname needs to match in two places - /etc/hostname and /etc/hosts. If you don't change both, you break sudo, and lose all admin rights. 

You need to boot into recovery mode, which should give you a root command-line. Use these two commands to make sure that the hostname is identical in both files:
[B]nano /etc/hosts
nano /etc/hostname[/B]

In /etc/hosts, the hostname should appear to the right of 127.0.0.1. 
In /etc/hostname, the hostname should be the only contents of the only line in the file (no spaces).

---

### Post by Budgi on 2006-09-03
Damn it I am so close to fixing it. You are right on the second nano thing I can see the name and I want to change it but I cant log into recovery with the maintenance password because i have no idea what it is. Is there a default password that normally comes with ubuntu?

---

