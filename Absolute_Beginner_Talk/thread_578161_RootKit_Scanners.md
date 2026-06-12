---
title: "RootKit Scanners"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-16
Would it be wise to download a RootKit Scanner and run it every now and again.
Can I download one from the Repositories, I really don't trust something like
that from anywhere else.

---

### Post by Sef on 2007-10-16
> Can I download one from the Repositories....

Yes, you can.  I'll post the name shortly or someone else will.

Update: One is rkhunter.

---

### Post by expatCM on 2007-10-17
Do rootkit scanners work on the basis of detecting already installed rootkits or do they basically inoculate a system and then identify subsequent changes which could be made by rootkits?

---

### Post by Martje_001 on 2007-10-17
> **expatCM said:**
> Do rootkit scanners work on the basis of detecting already installed rootkits or do they basically inoculate a system and then identify subsequent changes which could be made by rootkits?
It scans for known rootkits.

---

### Post by hyper_ch on 2007-10-17
And there's also
```

chkrootkit

```

Should also be in the repos I think.

---

### Post by gerrymoth on 2007-10-17
I regularily run the following two rootkit scanners:

Chkrootkit

```
sudo apt-get install chkrootkit
sudo chkrootkit
```

Rkhunter

```
sudo aptitude install rkhunter
sudo rkhunter --update && sudo rkhunter -c -sk
```

---

### Post by FredB on 2007-10-17
If you don't use programs from unknown source, a rootkit scanner will be useless.

Anyway having it is a great idea.

---

### Post by Sef on 2007-10-17
> If you don't use programs from unknown source, a rootkit scanner will be useless.

Not true.  You can be hacked, and have a root kit installed.

---

### Post by Orbital75 on 2007-10-17
Thank you guys.......... I'll go ahead and download these and run them once and awhile.
There are a few places that I have downloaded software other than the repositories but
I consider them trusted sites so to speak ( [www.getdeb.net](www.getdeb.net) ). But from my understanding,
even well know websites can get hacked and inject code ( Java ) to the user.

Thanks for the help everyone.....  :)

---

### Post by Orbital75 on 2007-10-18
Downloaded chkrootkit from the synaptic package manager.
Could someone help me run it. I know I don't have a RootKit
but it's always good to learn how to scan incase I feel there
is a need in the future.

Thanks

---

### Post by the.phantom on 2007-10-18
i use both and these are the commands from the terminal

 to run chroot

sudo chkrootkit



update and run rt hunter

sudo rkhunter --update && sudo rkhunter -c -sk

not a expert !

---

### Post by bodhi.zazen on 2007-10-18
This is a nice link : [http://www.kanenas.net/comments.php?y=06&m=05&entry=entry060502-073518](http://www.kanenas.net/comments.php?y=06&m=05&entry=entry060502-073518)

---

### Post by Orbital75 on 2007-10-18
Thanks guys..... good info  :)

---

