---
title: "Running shell script as user problems"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by nexus024 on 2006-10-02
I am having problems trying to run a shell script in user mode that requires sudo priviledges.  Let me explain what I am trying to do and hopefully someone can help me.  I have created two shell scripts that are run by a cron job during certain time periods throughout the day.  All the shell scripts do is execute an iptables command to add a chain or remove a chain.

Allow connections from monster.idsoftware.com
```
 
iptables -D INPUT -s monster.idsoftware.com -j DROP  

```

Block connections from monster.idsoftware.com
```

iptables -I INPUT -s monster.idsoftware.com -j 

```

The problem I am having is that these shell scripts can't be executed without being run by sudo.  Any help would be much appreciated!

---

### Post by nexus024 on 2006-10-02
Anyone?  :confused:

---

### Post by aysiu on 2006-10-02
What happens when you just plop the word *sudo* in front?

---

### Post by nexus024 on 2006-10-02
Asks for the sudo password when i type sh accept.sh

---

### Post by aysiu on 2006-10-02
Let's assume that your Ubuntu computer's username is nexus and that the accept.sh script is in /usr/bin/accept.sh right now.

Paste this command in the terminal: ```
sudo visudo
``` Then add in this line: ```
nexus ALL = NOPASSWD: /usr/bin/accept.sh
``` Save the file, and it should no longer prompt you for a password when you *sudo* that script.

---

### Post by nexus024 on 2006-10-02
Thank you... I will give this a try!

---

### Post by nexus024 on 2006-10-02
I added in the correct commands into visudo and it still says permission denied must be root.

---

### Post by aysiu on 2006-10-02
You still have to be root (```
sudo accept.sh
```) but you don't have to enter your password.

---

