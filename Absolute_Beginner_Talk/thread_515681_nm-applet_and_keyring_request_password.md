---
title: "nm-applet and keyring request password"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by slamdunk on 2007-08-02
Hi,

I have a WPA connection to wireless. My system start with auto-login (however same password for login and connection), but after automatic-login, keyring asks me a password for nm-applet connection.

I followed suggestions here: [http://ubuntuforums.org/showthread.php?t=514360](http://ubuntuforums.org/showthread.php?t=514360)

but it doesnt' work.

$ sudo gedit /etc/pam.d/gdm

#%PAM-1.0
auth	optional	pam_keyring.so my_password
session	optional	pam_keyring.so
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password

I have tried to use : @include common-pamkeyring instead of:

auth	optional	pam_keyring.so my_password
session	optional	pam_keyring.so

without luck

obviously libpam-keyring package is installed.

Have you any idea?

Thanks,
Julio

---

### Post by happy-and-lost on 2007-08-02
Whilst not holpful now, this problem is due to be fixed in Gnome 2.20, which is released 19th September and should make it into the final Gutsy release come October :)

---

