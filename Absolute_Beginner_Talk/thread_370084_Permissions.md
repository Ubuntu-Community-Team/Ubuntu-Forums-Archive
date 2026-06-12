---
title: "Permissions"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-02-25
Most of the time, I don't worry that much about file permissions, and just leave them at the defaults. Occasionally, I make the file executable so I can run it. Other than that, if the permissions are wrong, I chmod it to 777 (which as far as I know gives everyone the ability to read/write to it). I have a strong feeling that I shouldn't be doing this. How should I chmod my files? What about files on my apache server? Would those need to be different to let my perl scripts write to them? Thanks a lot.

---

### Post by bodhi.zazen on 2007-02-25
It depends on the file in question.

permissions of 777 are obviously less secure.

For system files, you should access them and edit them via sudo.

sudo <editor> <file_name>

For example : sudo vim /etc/fstab

IMO you should restrict access as much as possible. I like 770 more then 777 for example.

---

### Post by nhandler on 2007-02-25
For system files, I rarely change the permissions, and use sudo (or gksudo) like you said.

One thing I forgot to mention was that I'm the only person using this computer. Does that mean I don't need to worry about the group/other people permissions? Could I just leave them as not being able to read/write?

---

### Post by mcduck on 2007-02-25
It's not safe to change permissions of system files, some of them need certain permissions for your system to work properly. Wrong permissions could break your system.

---

### Post by highneko on 2007-02-25
I usually chmod using 644 because that's what most file permissions are by default.
[HTML]--- = 0    r-- = 4
--x = 1    r-x = 5
-w- = 2    rw- = 6
-wx = 3    rwx = 7
users groups others all
usage: chmod 644 /example/filename[/HTML]

---

### Post by bodhi.zazen on 2007-02-25
It depends on your level of paranoia and the file in question.

certainly for (data) files in /home/user_name permissions of 700 are most "secure" or "paranoid".

Some files in /home/user_name, however, like .drmc require broader permissions (755).

I would advise against changing permissions of system files unless you know what and why you are making the changes.

---

### Post by nhandler on 2007-02-25
> **highneko said:**
> I usually chmod using 644 because that's what most file permissions are by default.
[HTML]--- = 0    r-- = 4
--x = 1    r-x = 5
-w- = 2    rw- = 6
-wx = 3    rwx = 7
users groups others all
usage: chmod 644 /example/filename[/HTML]

But since I'm the only one using the computer, could I chmod 600 or 700 (if it needs to be executable).


Also, I don't change the system files' permissions. I only change my documents and my web server stuff.

---

