---
title: "Asking For password"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by hardipdhillon on 2007-03-12
Hello Every Body,
                I am facing a problem that my ubuntu server has joined the windows domain .I can see its name in network neigborhood,the problem is that when i try to open this share it always ask for password which i don't want , so please help me in that matter.

---

### Post by TheRingmaster on 2007-03-12
> **hardipdhillon said:**
> Hello Every Body,
                I am facing a problem that my ubuntu server has joined the windows domain .I can see its name in network neigborhood,the problem is that when i try to open this share it always ask for password which i don't want , so please help me in that matter.
It would help if you were a little more specific with your problem details.

---

### Post by hardipdhillon on 2007-03-12
As i have written, i need that samba don't ask for password when i try to samba server from windows, firstly i used security= domain at that time i accept no password then i change it to security = user then it accept the user that i have created in samba then i change it to sucurity= share but it is still asking for password, i need that samba don't ask for any password when i open it in widows network neigborhood.

---

### Post by Najand on 2007-03-12
Did you  make a samba password using "smbpasswd"?

---

### Post by hardipdhillon on 2007-03-12
yes, i have created

---

### Post by Najand on 2007-03-12
Can you copy your smb.conf here. (delete personal information before posting)

---

