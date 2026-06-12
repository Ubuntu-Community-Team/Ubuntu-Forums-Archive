---
title: "VSFTPD help--Please be kind."
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by ravosava on 2007-09-29
Hi, I've been using VSFTPD for a little while between myself and a friend, but I would like to start using it at school, so I need to create a login/password, but since I am a complete noob, I don't know how to do it. I am using Ubuntu 7.04 if that helps anyone...I saw that some one had already asked this question, and some one said "I have no clue"...
I know theres some genius out there who can do this though, so, if it's not too much trouble, please help me. :(

---

### Post by cursebg on 2007-09-29
I think this should help you: [http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-ftp-vsftpd-conf.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-ftp-vsftpd-conf.html)

---

### Post by ravosava on 2007-09-29
Okay..I'm completely confused

"#

userlist_deny — When used in conjunction with the userlist_enable directive and set to NO, all local users are denied access unless the username is listed in the file specified by the userlist_file directive. Because access is denied before the client is asked for a password, setting this directive to NO prevents local users from submitting unencrypted passwords over the network.

The default value is YES.
#

userlist_enable — When enabled, the users listed in the file specified by the userlist_file directive are denied access. Because access is denied before the client is asked for a password, users are prevented from submitting unencrypted passwords over the network.

The default value is NO, however under Red Hat Enterprise Linux the value is set to YES.
#

userlist_file — Specifies the file referenced by vsftpd when the userlist_enable directive is enabled.

The default value is /etc/vsftpd.user_list. "


Can some one please explain this to me...Because I think I am reading it totally wrong.
To me it says, If this [userlist_enable] is enabled, then users in the list are denied access. If you use with this [userlist_deny] and its 'defaultly no' then you can log in....
It really doesnt make sense....


and how do i create the userlist file? as in, what format should i put the users/passwords in?

---

### Post by ruibernardo on 2007-10-01
Hi ravosava,

I think you have to enable local users also with "local_enable=YES" in /etc/vsftpd.conf.

If you use "userlist_enable=YES" then you have to say "userlist_deny=NO", because userlist_deny is yes by default if you use the userlist_enable option.

```
userlist_enable=YES
userlist_deny=NO

```By default it will use /etc/vsftpd.user_list. With "userlist_enable=YES" and "userlist_deny=NO", add the users that [COLOR=Red]**can**[/COLOR] login in vsftpd to the file /etc/vsftpd.user_list.

To use another file, then use the "userlist_file=" option.

Restart vsftpd to apply the configuration:

```
sudo /etc/init.d/vsftpd restart
```It worked here.

---

