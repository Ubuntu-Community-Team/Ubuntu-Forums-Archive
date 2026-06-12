---
title: "Newbie on LINUX/UBUNTU (Howto adjust time and date?)"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by pius1225 on 2007-11-04
Hi all,

ive just wondering how can i adjust the time & date on my newly installed ubuntu using terminal console only? im just new to ubuntu and i think its different way changing on Redhat.

Any information would really much appreciated.

Thanks,
PIUS

---

### Post by linuxwizard on 2007-11-04
Using the command line, you can use tzconfig.

[https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=ChangeTimezoneHowto](https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=ChangeTimezoneHowto)

---

### Post by pius1225 on 2007-11-04
hi thanks for the reply.
i dont have gui base on my ubuntu right now, ive just installed the basic compponent. ive tried "tzconfig" it didnt changed the time. i got the same time and date "Sat Nov  4 20:41:31 SGT 2006"..... i need to change the year to "2007"

Pius

---

### Post by Partyboi2 on 2007-11-04
```
 date mmddHHMMYYyy
```so
date 110420152007
Nov 04 8:15 2007

---

### Post by pius1225 on 2007-11-04
hi,

ive tried the command "date" and type this "date 110415332007"  and i got this result "Sun Nov  4 15:33:00 HKT 2007" but when i type again the "date" it goes back to this "Sat Nov  4 23:30:16 HKT 2006"

Any idea whats happening?

Thanks,
Pius

---

### Post by JBAlaska on 2007-11-04
This says it all;
```
man date
```

When you set the date/time, don't forget to sudo;
```
sudo date mmddHHMMYYyy
```

If you want to do all this from the terminal and keep it sync'd with net time, try this;

**Install ntpdate client:**
```
$ sudo apt-get install ntpdate
```

[b]ntpdate will automatically run when your network interface gets activated by the system (i.e. while booting the Ubuntu Linux sever/desktop system).

Ubuntu Linux stores the script at /etc/network/if-up.d/ntpdate location.[/b]

If you wish to just run script again just type command:
```
$ sudo /etc/network/if-up.d/ntpdate
```

**Keep synced by running ntpdate every 1 or 2 hours using cronjob**

Install as cronjob:

Type:
```
crontab -e
```

# Adds hourly job:

**Paste this:**
```
#Setup NTPDATE
@hourly /etc/network/if-up.d/ntpdate
```

**Save and close the file.**

---

### Post by pius1225 on 2007-11-05
> **JBAlaska said:**
> This says it all;
```
man date
```

When you set the date/time, don't forget to sudo;
```
sudo date mmddHHMMYYyy
```

If you want to do all this from the terminal and keep it sync'd with net time, try this;

**Install ntpdate client:**
```
$ sudo apt-get install ntpdate
```

[b]ntpdate will automatically run when your network interface gets activated by the system (i.e. while booting the Ubuntu Linux sever/desktop system).

Ubuntu Linux stores the script at /etc/network/if-up.d/ntpdate location.[/b]

If you wish to just run script again just type command:
```
$ sudo /etc/network/if-up.d/ntpdate
```

**Keep synced by running ntpdate every 1 or 2 hours using cronjob**

Install as cronjob:

Type:
```
crontab -e
```

# Adds hourly job:

**Paste this:**
```
#Setup NTPDATE
@hourly /etc/network/if-up.d/ntpdate
```

**Save and close the file.**

hi ive done all of this but still it didnot work.. actually my main concern is the year, i cannot change the year... right now it 2006 instead of 2007..

Regards,
Pius

---

