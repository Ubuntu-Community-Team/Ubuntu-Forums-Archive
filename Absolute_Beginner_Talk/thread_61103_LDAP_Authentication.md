---
title: "LDAP Authentication"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by tsumi on 2005-08-30
Hey there. Before I go into my question(s) here I would like to point out how much I have used these forums and what a huge help they have been. So, if you are reading this, be you noob or *nix dinosaur - give yerself a pat on the back!

Ok - so on to my question:

I am wondering if there is a way to have X11 sessions authenticate vs an LDAP server. For example, something like SLiM (a session manager) would query and LDAP server instead of /etc/passwd.

Additionally, it would be stellar if that session manager, login script, whatever could pass out a %username% variable to the session that would result in a network mount (i.e. \\servername\directory\%username%)...

If anyone has any suggestions or can point me in the direction of a FAQ I would be extremely greatful.

Let me know if I am not explaining this well enough and I will go into more detail.

Thanks!

-Tsumi

---

### Post by KingBahamut on 2005-08-30
I believe that you have to tell PAM explicitly to use the ldap library to check LDAP for particular
authentication actions.  Look in /etc/pam.d/su (if exists) or /etc/pam.d/pam.conf At least thats how youd do it in Solaris. I dont know if its the same in Linux, I could be wrong. 

But Theoretically its possible I guess. 

Im not sure if you can pass out a %username% variable to the session though. It would be easier to setup NFS mounts and auth against those, rather than just depending on LDAP to do it. 

But then.....I could also be very wrong.

---

