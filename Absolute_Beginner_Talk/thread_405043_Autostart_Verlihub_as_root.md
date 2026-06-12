---
title: "Autostart Verlihub as root"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by k0rv3n on 2007-04-09
Hi

I have a server with Ubuntu 6.10 on. 
I've compiled verlihub and it works great except that I can't get it to autostart.
I've setup the server to autologin my user so I can use VNC and some graphical clients and remote them when I need too. The problem to get verlihub to autostart is that I need to be root when starting it to be able to use port 411.
I've just added vh_runhub to startup programs in Sessions but that does not make it start as root. Now I use the sudo command and then I have to enter my pass.
Is there an other way to do this?

---

### Post by k0rv3n on 2007-04-11
bump..

---

### Post by Meserias on 2007-11-22
[SIZE="3"]How can I configure my Ubuntu 7.10 to autostart VerliHub as a background process. This is useful because in case of Power Failure the hub must restart without admin intervention. [/SIZE]
](*,):???:

Please contact me here or better on YM: tender_vlad

---

### Post by BrendanM on 2007-11-26
Has anyone come up with a solution to this issue?

How would you run any program as root on startup before login? And have it continue running after login?

Somebody must know how to do this.

---

### Post by kingcharles1666 on 2007-12-16
I am looking for a similar function and came across this:

> Make sure the line in your /etc/sudoers file looks like that :
Code:

%admin ALL= NOPASSWD: /usr/sbin/firestarter

So /usr/sbin/firestarter not /usr/bin/firestarter.

Does not work for me (I need to run "/etc/init.d/networking restart" as sudo on startup every time to get my wireless going) But it may work for you as it is a program

Just replace firestarter with your app.

---

### Post by kingcharles1666 on 2007-12-16
wow, after re-thinking my own statement i decided it may just work for me also
and it did!!

Some more details on the how-to

```

sudo visudo
```

```
yourusername ALL= NOPASSWD: /path/to/executable/you/want/to/run/as/sudo/in/sessions
```

and press ctrl+x to exit. Press Y to accept

---

### Post by mike_tyrell on 2008-02-01
Thank you very much on this fix. I have been to several other forums had no reply to same situation or replies that us new people dont understand yet
thank you for the great work

---

