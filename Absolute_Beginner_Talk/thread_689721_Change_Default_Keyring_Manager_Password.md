---
title: "Change Default Keyring Manager Password"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by mexpolk on 2008-02-06
I changed my user password in Ubuntu, everything was OK until the next time I booted my Linux box. Keyring Manager was asking me for a password (as my wireless connection needed stored WPA pass phrase), immediately figured out that this was caused by the password change.

The problem is that Gnome Keyring manager doesn't have an option to change the default keyring password. So, if your user password is changed, every time you log in Keyring Manager will ask for the password you supplied during Ubuntu's installation (awkward).

Due the lack of password change in Keyring Manager we need another application: Seahorse. To install type the following:

```
$ sudo apt-get install seahorse
```

Once installed open it, go to Edit -> Preferences menu. Select GNOME Keyring tab and change the password to match your actual Linux user password.

[IMG]http://bp1.blogger.com/_uMh73S0gl1I/R6o5aLmFmfI/AAAAAAAAAB0/DUqbJOstb9A/s1600-h/Screenshot-Encryption+Preferences.png[/IMG]

Hope this helps...

[http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html]("http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html")

---

### Post by cartisdm on 2008-02-07
That's awesome, I've been annoyed by this for over a month.  Nice How-To:)

---

