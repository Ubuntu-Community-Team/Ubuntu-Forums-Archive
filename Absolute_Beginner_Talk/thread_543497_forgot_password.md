---
title: "forgot password"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by blinkja on 2007-09-05
forgot password

---

### Post by blinkja on 2007-09-05
username i know :KS but i forgot the password :(

---

### Post by scxtt on 2007-09-05
reboot into recovery mode (should be an option in your grub menu during boot - hit escape if necessary), you'll be root and can do **passwd <that username>**

---

### Post by mikewhatever on 2007-09-05
You can not recover the forgotten password, but it is possible to reset it.
[https://help.ubuntu.com/community/LostPassword?highlight=%28password%29](https://help.ubuntu.com/community/LostPassword?highlight=%28password%29)

---

### Post by por100pre1 on 2007-09-05
Enter in Recovery Mode, you'll be root.

```
passwd <username>
```

(replace <username> with your user name)

type your new password, nothing will be seen

do it again, then

```
reboot
```

---

### Post by blinkja on 2007-09-05
thanks i got reset the pass and back to ubuntu

now can anyone explain what is this [http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu) and the password i just reset

---

### Post by blinkja on 2007-09-05
If it is the same or not? I did sudo passwd  and changed password to something ultra long and hard to guess 
back when i was in ubuntu when i update/synaptic i get the password prompt
but the password i put in there was not ultra long and hard to guess pass, the pass i putin there was when i first installed ubuntu from livecd .

where it asks username password :guitar:

---

### Post by mikewhatever on 2007-09-05
When you install Ubuntu, by default, two users are created. One is root, but the root account is not enabled and no password is set, the other is your personal account with the username and password you choose. That account is different from the root one, because it does not have admin privileges all the time, and yet, can temporarily acquire them. A regular home user does not need the root account enabled. A network admin may want it to save time typing the password numerous times.

---

### Post by jmeyer on 2007-09-05
i had my user account created jason and i know the password.  i was trying to join to our domain and it would only add it to the domain as a disabled account.  i did CTRL+ALT+BACKSPACE to restart to see if that would help joining the domain, and now i can't even log into Ubuntu.  it says username and password are not correct.  i have tried through the root to change the password and also through /etc/passwd.

---

### Post by KeeperOS on 2007-09-09
Then isn't this defeating the whole purpose of having a password?

I mean, if I and you can do it then ANYONE with physical access to the PC can do it, all he'd need is the username (unless there's a way to list the existing users thus, he'd need nothing...)

---

### Post by scxtt on 2007-09-09
welcome to the understanding that (virtually) no amount of OS security can protect you from someone w/ physical access and malicious intent.

;)

---

### Post by funrider on 2007-09-09
u can set bios password, physically lock you PC, lock the PC (server) room, etc

---

### Post by KeeperOS on 2007-09-09
Erm, what if this is a family/work PC that is used by many (each with its' own account)?

Everyone must have access to it but none should have access to any account other than his/her own...

---

### Post by scxtt on 2007-09-09
by default, they wont ... but, in general, you can't stop someone w/ physical access to the host from booting into recovery mode and changing passwords, sure you can remove it from menu.lst, but they could edit any bootable entry and get a root prompt if they know how recovery mode works ... you can p/w protect grub, but still - physical access is really the determining factor ...

and that's not linux's fault ;)

---

