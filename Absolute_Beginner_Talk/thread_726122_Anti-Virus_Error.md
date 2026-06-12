---
title: "Anti-Virus Error"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by gunnerb on 2008-03-16
I'm very new at this and would really like to wean myself off of 
Microsoft so please bear with me.
I recently downloaded AVG anti-virus software to use with my Ubuntu Linux system.  While trying to update the software, I received an error message saying that the update process failed.  Reason: Sorry you do not have permission to execute avgupdate.  As the owner/administrator why don't I have permisson and how do I change it.
TIA
Gunnerb

---

### Post by SpenceMakesSense on 2008-03-16
try typing in a terminal 

sudo avgupdate

---

### Post by Myglaren on 2008-03-16
If only it were that simple with (ptooey) Vista.

---

### Post by Ub1476 on 2008-03-16
Anti-Virus isn't really necessary unless you want to scan mail you send to Windows-users (even though the mail application should be able to handle this itself). There are no viruses in the wild for Linux. You might want to use ClamAV (and clamtk if you want GUI) instead of AVG if you still want anti-virus software.

AVG is simply poorly integrated into Linux. Try to run it from the terminal with "sudo" infront of it.

```
sudo avg #if this is the launch name of the AVG anti-virus
```

---

### Post by SpenceMakesSense on 2008-03-16
> **Ub1476 said:**
> Anti-Virus isn't really necessary unless you want to scan mail you send to Windows-users (even though the mail application should be able to handle this itself). There are no viruses in the wild for Linux. 




This is very true. But if you insist on having an anti-virus anything that requires "permission" requires the Sudo command in front of it

---

### Post by gunnerb on 2008-03-16
Thanks very much for the info.   I used the sudo command and got a list of options.  used one of them and it did indeed download the files, but I have no clue as to where they dumped to.  I'm trying to figure out the path as we speak.
thanks again.  If I learn one thing every time I turn this box on, I'll be happy
Gunnerb

---

### Post by Myglaren on 2008-03-17
If you are using Gutsy there is a built-in virus scanner.  It popped up a few days ago and alerted me to the fact that there was a virus in an email attachment received from a Windows user.
It is in Applications->Accessories.

---

### Post by toasty_ghosty on 2008-03-17
> **Myglaren said:**
> If you are using Gutsy there is a built-in virus scanner.  It popped up a few days ago and alerted me to the fact that there was a virus in an email attachment received from a Windows user.
It is in Applications->Accessories.

Really? I don't have that installed. Was that always included with Gutsy?

---

### Post by Oldsoldier2003 on 2008-03-17
> **toasty_ghosty said:**
> Really? I don't have that installed. Was that always included with Gutsy?

Gutsy does not have a built in virus scanner....

---

### Post by Myglaren on 2008-03-17
Must have come from one of the repositories then.  I don't recall installing it.

[[IMG]http://img222.imageshack.us/img222/7161/clamtkay3.th.png[/IMG]](http://img222.imageshack.us/my.php?image=clamtkay3.png)

---

### Post by bodhi.zazen on 2008-03-17
That is a gui front end for clamav

Clamav is in the Universe repositories. ClamAV is not installed by default, and in fact the universe repo is not either.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=clamav&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=clamav&searchon=name&subword=1&version=all&release=all)

---

