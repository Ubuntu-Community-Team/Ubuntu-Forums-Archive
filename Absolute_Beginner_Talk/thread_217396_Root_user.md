---
title: "Root user"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by tx1138 on 2006-07-17
Hi all. I was just wondering how to access as a root user. In setup it only asked me for a username and password :S. I don't know if there actually IS a root user (most distro's have one I believe) but if there is, is there a specific password or something I need? thanks.

Also, another problem I have. When I try and use the internet, I have to always go in to network-admin in terminal, deactivate the ethernet, then activate it again for it to work. EVERY time I log in. I'm on adsl connection, so why would it be doing this? After I activate it, it says null error failed or something, however the internet works for one session. Any help would be appreciated, it's driving me nuts....

Thanks in advance,
tx

---

### Post by scxtt on 2006-07-17
for the root issue, preface any command you want to use as root w/ sudo, for example:
[indent]sudo vi /etc/fstab[/indent]enter your user password, you'll have the same privileges as root ... and if you want a constant root prompt, use **sudo su -** ... there isn't a root user, a la fedora, w/ ubuntu - just 1 more layer of security ...

---

### Post by ecto on 2006-07-17
For security and stability purposes Ubuntu has diabled what many refer to as "true root" Instead Ubuntu provides a utility called "sudo" which allows "root-like-access". Sudo [when typed into the terminal is not capitalized] works in a number of ways. The most common is sudo [command-name] where [command-name] is replaced with a command such as ifconfig or mount. Heres a clear example:
> sudo apt-get update
In this example sudo precedes apt-get update which is a command that only users with root privelges can execute. Once you press eneter you are prompted for password (which is your normal user password). Another way to use sudo is similar to the su root command. If you type
> sudo -i
you are immediately prompted for a password and then immediately placed as the root user.

---

### Post by Ragazzo on 2006-07-17
> **scxtt said:**
> for the root issue, preface any command you want to use as root w/ sudo, for example:
[indent]sudo vi /etc/fstab[/indent]enter your user password, you'll have the same privileges as root ... and if you want a constant root prompt, use **sudo su -** ... there isn't a root user, a la fedora, w/ ubuntu - just 1 more layer of security ...

You can login as the root from the text terminals (eg ctrl+alt+1) if you have set a password for it (sudo passwd) but not from the graphical one. You shouldn't use it though, use sudo instead.

---

### Post by scxtt on 2006-07-17
> **Ragazzo said:**
> You can login as the root from the text terminals (eg ctrl+alt+1) if you have set a password for it (sudo passwd) but not from the graphical one. You shouldn't use it though, use sudo instead.any particular reason you chose my comment to quote when making that post?

---

### Post by Ragazzo on 2006-07-17
> **scxtt said:**
> any particular reason you chose my comment to quote when making that post?

You said there was no root user and I went into more depth (not that I think you didn't know it).

---

### Post by tx1138 on 2006-07-18
Thankyou everyone for all your help. I was up in arms about whether was a specific user for this distro. Thanks for your time.

---

