---
title: "Peculiar case of sudoers, it seems to be ignored by the system."
date: 2013-03-31
forum: Any Other OS
---

### Post by legolas_w on 2013-03-31
I have a redhat enterprise linux that I am trying to configure for sudo, it is a personal machine and I dont care that much about relaxing the security settings.

I have the following two users, one is member of sba and teel groups and the other one is member sba group:

```

pre: sba, teel
mtpre: sba

```

Now I want to give sudo permissions to these two users so that they could execute any command using sudo without the need to specify a password. To do so I edited the /etc/sudoers file (it was not present at the beginning, I created the file) and added the following lines to it:

```

bash-4.1$ sudo cat /etc/sudoers
Password:

%admin ALL=(ALL) NOPASSWD: ALL

%teel ALL=(ALL) NOPASSWD: ALL

%sudo ALL=(ALL) NOPASSWD: ALL

%sba ALL=(ALL) NOPASSWD: ALL

mtpre ALL=(ALL) NOPASSWD: ALL

pre ALL=(ALL) NOPASSWD: ALL


bash-4.1$

```


The mtpre user can use sudo but need to enter password when using sudo and the pre user cannot use sudo at all.

```

[pre@machine1 ~]$ sudo cat /etc/sudoers
Sorry, user pre is not allowed to execute '/bin/cat /etc/sudoers' as root on machine1.

```

If I do a ls -al using the mtpre for the sudoers file I get:

```

bash-4.1$  ls -al /etc/sudoers
-r--r----- 1 root root 519 Mar 30 23:05 /etc/sudoers

```

Do you see any problem in the sudoers file (I used visudo to edit it and I am sure that syntactically it is fine as visudo did not complain about it) or anywhere that can cause this peculiar issue? Do you know any solution or any means of diagnosing the problem?

Thank you.

---

### Post by schragge on 2013-03-31
TBH, this seems pretty overengineered to me. What exactly are you trying to achieve? Are there other members of the listed groups (admin, sudo, teel, sba) that should have full sudo permissions? Why would the following not be enough?
```

Defaults always_set_home
pre,mtpre ALL=(ALL:ALL) NOPASSWD: ALL

``` If this doesn't work, check the SELinux context of your users.
```

/usr/sbin/semanage login -l
id -Z pre
id -Z mtpre

```To be able to use sudo, both users should be *unconfined_u* and belong to the *unconfined_t* domain. If they are in the *staff_t* domain, you can still allow them to sudo by adjusting the settings in */etc/sudoers* accordingly.

---

### Post by legolas_w on 2013-03-31
Thanks for the reply.

I tried using the two lines you provided for the sudo and the result was some conflicts because the visudo didnt let me save the content. Then I changed it to the following and I managed to save it.

```

Defaults always_set_home
pre,mtpre ALL=(ALL) NOPASSWD: ALL

```

I foundout that SELinux was disabled so I enabled SELinux as explained here: [https://access.redhat.com/knowledge/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Security-Enhanced_Linux/sect-Security-Enhanced_Linux-Working_with_SELinux-Enabling_and_Disabling_SELinux.html](https://access.redhat.com/knowledge/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Security-Enhanced_Linux/sect-Security-Enhanced_Linux-Working_with_SELinux-Enabling_and_Disabling_SELinux.html)

and then tried executing your suggested commands:

```

bash-4.1$ /usr/sbin/semanage login -l
/usr/sbin/semanage: SELinux policy is not managed or store cannot be accessed.
bash-4.1$ id -Z
unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

```

The id -Z reruns the same output for both users.

The problem still exist and I cannot do something like the following:

```

[pre@machine1 ~]$ sudo cat /etc/sudoers
Sorry, user pre is not allowed to execute '/bin/cat /etc/sudoers' as root on machine1.

```


Any idea what else can I try to findout what is the problem?

Thanks.

---

### Post by oldos2er on 2013-03-31
Moved to Other OS/Distro Talk.

---

### Post by iamkuriouspurpleoranj on 2013-03-31
Would you not also have to "usermod -a -G wheel" pre and mtpre in addition to what you've put in the sudoers file?

---

### Post by schragge on 2013-03-31
@**iamkuriouspurpleoranj** I guess this would make more sense if */etc/sudoers* contained
```
%wheel        ALL=(ALL)       NOPASSWD: ALL
```
@**legolas_w** Hmm, strange. Try this
```

Defaults always_set_home
root ALL=(ALL) ALL
pre, mtpre ALL=(root) TYPE=unconfined_t ROLE=unconfined_r NOPASSWD: ALL

``` It explicitly states that users *pre* and *mtpre* should be able to run ALL command on ALL hosts as *root*, but they won't be able to assume other users' identities. I also added the root user, and specified SELinux type and role, just in case.

Also, look at the output of *sudo -l* for your users:
```
sudo -U pre -l
```

Are there any sudo-related messages in */var/log/messages*?

---

