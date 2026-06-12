---
title: "su/sudo passwords different."
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Ghozt on 2006-10-13
Ok, I've been running Ubuntu Dapper for about a month now without windows and I love it. But, one of the things I don't understand is why my sudo password is different from my su password. I just tried to install wine 0.9.23 using ./tools/wineinstall, and it asked me for my su password to install. I tried entering my password, failed. Entered it agian, aborting installation. Is there a way I can reset it, or is there a pre-set password? Thanks.

---

### Post by aysiu on 2006-10-13
sudo is your user password (assuming you're in the *admin* group)

su is the root password, which is, for all practical purposes, non-existent in Ubuntu unless you set it yourself.

---

### Post by Ptero-4 on 2006-10-13
you should open wineinstall (if it is a script) and change su (or su -) for sudo everywhere in the file.

---

### Post by Ghozt on 2006-10-13
@ aysiu, Is there an easy way to set it?
@ Ptero-4, Thanks, I got it installed.

---

### Post by aysiu on 2006-10-13
There is an easy way to set it, but there's no need to.

If you want to be root from the terminal, just type ```
sudo -i
``` If you want to be root graphically, press Alt-F2 and type ```
gksudo nautilus
``` If you absolutely must set an *su* password for the hell of it: ```
sudo passwd root
```

---

### Post by skymt on 2006-10-13
> **Ghozt said:**
> @ aysiu, Is there an easy way to set it?

Just run "sudo passwd" in a terminal.

---

### Post by aysiu on 2006-10-13
Skymt, maybe this is something I'm getting wrong, but wouldn't it be ```
sudo passwd root
```? I think ```
sudo passwd
``` just sets your own password...?

---

### Post by skymt on 2006-10-13
No, I'm right. ;) 

Without any arguments, passwd changes the password for the user associated with the effective UID. When used with sudo, the effective UID is 0, so it changes the root password.

That's what I think happens anyway. I know from experience that it changes the root password, so what happens behind the scenes doesn't really matter.

EDIT: I don't have a root password set, so when I ran it just now, here's what I got:```
$ sudo passwd
Password: # sudo, asking me for my password
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully # set the root password
$ sudo -K # Clear timestamp
$ sudo -s # -s runs the value of $SHELL as root, I'm using this to make sure I didn't just set my own password
Password: # the password I set
Sorry, try again.
Password: # my previously existing user account password
Ignore insecure directories and continue [ny]? y # normal for sudo -s, see the manpage
#
```

I then disabled the root account again, with "sudo passwd -l root". I doubt -l will work on the EUID, but I haven't tested it.

---

### Post by aysiu on 2006-10-13
Well, I learned something new, then. Thanks!

---

### Post by MasonM on 2006-10-13
Setting a root password is always the first thing I do.

$sudo passwd root
enter your password
enter new root password twice

---

