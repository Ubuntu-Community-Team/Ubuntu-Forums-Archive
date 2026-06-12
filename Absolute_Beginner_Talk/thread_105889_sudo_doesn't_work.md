---
title: "sudo doesn't work"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-19
I have a fresh server install of ubuntu on an old laptop, but there's a problem: the sudo command doesn't work. I will type it in and the first time, it asks for my password. After I type it, it immediatly returns to the command prompt. If I try again, it returns to the command prompt without asking for my password. What's up here? I need root powers to do quite a few things on my system, and it's not letting me.

---

### Post by bscbrit on 2005-12-19
Are you typing

sudo command_that_you_want_to_run

or simply

sudo

on its own line?

---

### Post by aysiu on 2005-12-19
Can you post the entire output (including the command itself) of this command? ```
sudo apt-get update
``` Don't describe the output. Copy and paste it into the thread.

---

### Post by earobinson on 2005-12-19
dose the server install set up su instead of sudo?

are you using that current users password?

---

### Post by wr0x2 on 2005-12-19
I'm typing "sudo <command here>"

output from sudo apt-get update is NOTHING.

$ sudo apt-get update
$

That's what happens. Nothing. What's wrong here? I've logged out/in, and rebooted but that hasn't helped. Also, yes, I'm using the current logged on user's password. I have another ubuntu box and sudo works fine on it.

---

### Post by earobinson on 2005-12-19
did u set up a root account during the install

try
```
su
<password (try all the paswords you entered during install)>
<command>
exit
```

---

### Post by jrib on 2005-12-19
Can you:
[LIST]
[*]paste what the following command returns: ```
groups
```
[*]if you have a root account enabled can you access /etc/sudoers and paste its contents?
[/LIST]

If you don't have root access then you are going to have to boot with the livecd and edit some files.

---

### Post by wr0x2 on 2005-12-19
I added my regular user account to the sudoers file and it works. Thanks.

---

### Post by earobinson on 2005-12-19
did you have to boot with the live cd?

---

### Post by wr0x2 on 2005-12-20
No, I logged in as root and edited the file from there.

---

