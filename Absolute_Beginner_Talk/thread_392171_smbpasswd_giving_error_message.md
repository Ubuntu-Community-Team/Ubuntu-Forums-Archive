---
title: "smbpasswd giving error message"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2007-03-24
Using ubuntu 6.06.

trying to configure samba. as soon as i am giving the following command to add a computer account to the samba password file, i am getting an error
```

patrick@patrick-desktop:~$ sudo smbpasswd -a -m patrick
Password:
Failed to initialise SAM_ACCOUNT for user patrick$. Does this user exist in the UNIX password database ?
Failed to modify password entry for user patrick$

```

The user patrick is the only user in this machine. What is the mistake I am doing? Please help.

---

### Post by Detonate on 2007-03-24
Why are you using the "-m" option?  If you are just trying to set up a user, then ```
sudo smbpasswd -a patrick
```

---

### Post by Linux Lover on 2007-03-24
Yah......it worked. Thank you. Actually I am learning the subject.

Now, I am again stuck. I use to share internet connection using firestarter. But as soon as I have installed firestarter, it blocked my SAMBA. How to configure firestarter so that my SAMBA starts working.

---

### Post by Detonate on 2007-03-24
Open Firestarter, open the Policy tab, make sure it is set to "Inbound Traffic Policy" right click in the bottom window, and click "Add Rule".  Select Samba (SMB)  from the Service pull down menu. Check "anyone" and click "Add".  Click "Apply Policy".  close Firestarter.

---

