---
title: "Login screen asks for password twice"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-07-18
i have asked this many times, i believe there is a solution for this :

i have edited some configuration for keyring to stop asking for the keyring password in every login where it went fine, but after that the login screen started to ask me to enter the password twice to be able to login, any idea how to make it ask for the password just one time ???

---

### Post by Koybe on 2007-07-18
It seems to be a pam problem.

What did you do to any pam files? (/etc/pam.d)

---

### Post by akkad on 2007-07-18
as forum suggested i have added the following to this file /etc/pam.d/gdm :
auth	optional	pam_keyring.so try_first_pass
session	optional	pam_keyring.so

---

### Post by Koybe on 2007-07-18
I guess you installed libpam-keyring package.

So instead of 
```
 auth	optional	pam_keyring.so try_first_pass
session	optional	pam_keyring.so
```

in /etc/pam.d/gdm

just put :
```
@include common-pamkeyring
```

---

### Post by akkad on 2007-07-20
ok here is what i did :
- sudo gedit /etc/pam.d/gdm
- then i did the replacement u told me about

but it is still the same i should enter the password two times :(

---

### Post by Koybe on 2007-07-20
Could you explain more?

When exactly are you asked for the password the second time? Both in login screen? One before, one after?

Eventually, post your /etc/pam.d/common-auth, /etc/pam.d/common-account and /etc/pam.d/gdm

---

### Post by dca on 2007-07-20
It's possible network manager is asking the p/w after login when detecting networks???

---

### Post by akkad on 2007-07-20
here is the case exactly : 
on the login screen itself i asked to enter the username first then password, as i enter the password and then press enter the password text field is cleared and i should enter the password again after that it will login and load desktop.

guys am not talking about the network password or the keyring password, it is all in the login screen before loading the desktop, but i mentioned the keyring in my post because this behavior appeared after i did the configuration for keyring.

---

### Post by Koybe on 2007-07-21
Ok. Could you then post the files I asked you?

```
cat /etc/pam.d/common-account
cat /etc/pam.d/common-auth
cat /etc/pam.d/gdm
```

---

### Post by akkad on 2007-07-21
the result for cat /etc/pam.d/common-account :
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account required        pam_unix.so


the result for  cat /etc/pam.d/common-auth:
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    required        pam_unix.so nullok_secure


the result for  cat /etc/pam.d/gdm :
#%PAM-1.0
auth    optional        pam_keyring.so try_first_pass
session optional        pam_keyring.so
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password


i hope i got u the needed output.

---

### Post by Koybe on 2007-07-21
ok, I think I have found the problem. Try modifiying your /etc/pam.d/gdm according to this (remove the 2 first line and add the last... in this order):
```
 #%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
@include common-pamkeyring

```

---

### Post by akkad on 2007-07-21
Koybe am totally thankful it really works fine now, one time password and also keyring is fine, u know what,  u told me to do the same before by removing the two lines and add @include common-pamkeyring instead , but i added it to the begining of the file, so it seems a matter of sequence, thnx again and i appreciate ur follow up, i support upgrading ur level from quad shot of ubuntu to super charged shot of ubuntu :)

---

### Post by Koybe on 2007-07-21
Thank you. Nice this could help you. ;)

---

### Post by MikeSz on 2007-07-24
I seem to be having a similar problem though not sure if its related - I have setup my wireless broadband connection from my Fujitsu Siemens AP1510 (uses Atheros) to my Orange livebox and had to enter a 28 digit WEP key (though Ubuntu referred to this as the 'passkey')  Every time I boot up, it asks me for this passkey, which will then let me connect to my wireless broadband.  However, I have to do this EVERY time I boot up!!!  Can  I use the above fixes to remedy this as I really dont understand any of the above!  

I did install keyring and I have ensured that my passwords are all the same so what else am I missing?

---

### Post by MikeSz on 2007-07-24
Anyone have any ideas on this?

---

### Post by akkad on 2007-07-24
i had the same problem and it is solved, the keyring as i understand (thnx to ubuntu community) it is an application that let u save many passwords under one password that may be u can consider it as a super password, so once u set a keyring password, then any new network u will connect to the keyring will save the specified connection password automatically so later on u will not asked to enter it.

that was the keyring, but it seems there is some problem with keyring to do its job, which the problem i had that every boot it asks for the key ring password, so i read many posts to solve it where the simple working solution for me was :

- set a keyring password to be the same like ur login password (why ?? actually i dont know :) )

- go to System >>> Administration >>> Synaptic Package Manager and there do a search for the keyword 'libpam-keyring', from the results install the package with the same name 'libpam-keyring'

- after install, open a terminal and type gedit /etc/pam.d/gdm  and do what Koybe said in the above post  that to edit the file to be look like the following (note :i think by default the file will look the same except the last line that u should add, where make sure to have the same like the following lines with the same sequence) :  

 #%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
@include common-pamkeyring

- then save the file and close and thats it, i hope it works with u too.

---

