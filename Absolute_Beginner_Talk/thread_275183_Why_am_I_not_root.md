---
title: "Why am I not root?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-10-11
Why do I get a message telling me permission denied when I try to do some things in a terminal? I am the only one with an account on this computer.
Is this something I have to so with sudo? Here is what I was trying to do:
echo <your-username> >>/etc/cron.allow
It came back and told me:
bash: /etc/cron.allow: Permission denied
What do I need to do to get permission?

---

### Post by Anonii on 2006-10-11
In short: **sudo echo <your-username> >>/etc/cron.allow**

With details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by HareBall on 2006-10-11
> **Anonii said:**
> In short: **sudo echo <your-username> >>/etc/cron.allow**

With details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Tried this and still got denied.

---

### Post by HareBall on 2006-10-11
> **Anonii said:**
> In short: **sudo echo <your-username> >>/etc/cron.allow**

With details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I went and read the page you posted. This is what I got when I tried again:
larry@larry-desktop:~$ sudo -l
Password:
User larry may run the following commands on this host:
    (ALL) ALL
larry@larry-desktop:~$ echo larry >>/etc/cron.allow
bash: /etc/cron.allow: Permission denied
larry@larry-desktop:~$
If I am allowed to run (ALL) ALL commands, how can I be denied permission?
This sounds like something Winderz would do :)

---

### Post by Sambie on 2006-10-11
Try typing sudo su.

---

### Post by HareBall on 2006-10-11
> **Sambie said:**
> Try typing sudo su.

Thanx, that was what I needed.

---

### Post by Sambie on 2006-10-11
Glad to hear that it worked for you :)

---

### Post by Charles Hand on 2006-10-11
> **HareBall said:**
> Tried this and still got denied.

> **Anonii said:**
> In short: **sudo echo <your-username> >>/etc/cron.allow**

With details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Actually, as the link points out, unless I'm mistaken, it would have to be:
```

sudo bash -c 'echo <your-username> >> /etc/cron.allow'

```

Otherwise, the redirection would be attempted as the user, not as root.

---

