---
title: "User is admin but can't access administrative apps"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by timelord726 on 2007-02-08
Hi everyone,

I feel ashamed to have to bring my problem here as I'm not very new at this and should be able to figure it out on my own, but I'm sure I'm just missing something obvious.

I created a second user on my system which should have the same administrative rights as the first user automatically created by the Ubuntu installer.  I added this second user to the admin group, and now the user *can* run commands via sudo, but *cannot* run applications under System > Administration.

What am I doing wrong?  How can I allow the user to use those apps?

Thanks very much!

---

### Post by kebes on 2007-02-08
What happens when you try to run one of those apps? Does it just fail? Or does it provide a password prompt, but then denies you even with the right password..?

What happens if you run one of the apps using:
gksudo *appname*

Does that let the app run?

---

### Post by timelord726 on 2007-02-08
Thanks very much for the response.  I apologize for not being clearer.

When I run one of those applications, I receive the following message:

[B]The configuration could not be loaded
[/B]You are not allowed to access the system configuration.

EDIT: When running the app with gksudo appname, the password box prompt comes up and it allows me into the program when I enter the correct password.

---

### Post by kebes on 2007-02-08
Okay, so at least you can run those things if you really have to...


Is this new user part of the groups "adm" AND "admin" ? If not you can add by going:
sudo adduser newuser adm


You can run the command "groups" as both your normal user (that can access the apps) and this new user, and see what the differences are. I believe you need to be part of group "admin" and "adm", but perhaps it needs to also be in group "plugdev" or something (if the app you are opening accesses those functions...).

---

### Post by timelord726 on 2007-02-08
Thanks for the reply.  The new user was already in adm, admin, and plugdev, but using the groups command, I found that my regular user was also in video and (what I suspect to be the culprit) lpadmin.

Strange... I've reconciled the differences between the two users (both users are now members of the same groups) and my newer user still gets the same message when trying to run those apps.

---

### Post by kebes on 2007-02-08
Hm... that's strange. Did you try logging out and then back in?

Also, are the menu entries identical in the two login sessions? Maybe because on first login you weren't part of the proper groups, the menu entries for that user are set wrong?

(Just random guesses here... I thought it would work if you were part of the right groups...)

---

### Post by timelord726 on 2007-02-08
No worries -- I thought it would work too!

I did log out and back in several times, as I needed to anyway to switch between the two users.  From what I can tell, the menu entries are identical, so I'm not sure what the problem could be.

Thanks for your help on this -- nice to know it's not just me.  ;)

---

### Post by timelord726 on 2007-02-08
I don't know what was wrong and I don't know how I fixed it, but I fixed it.  I ran an APT upgrade and then restarted the computer, and after restarting, my new user now gets the normal password prompt like he should.

Thanks very much, kebes!

---

### Post by kebes on 2007-02-08
Weird! Well at least it works now...!

---

### Post by tommyg on 2007-02-13
Forgive me for hijacking the thread, but I'm having the same issue... only not with a second user account.  For me, it's happening with the initial account created upon installation!

For instance, when I try to run "gksudo services-admin", I get the following in console:

```

user@server:~$ gksudo services-admin

(services-admin:4930): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(services-admin:4930): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
4930: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
4930: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:4930): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
4930: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
user@server:~$ 

```

... and that is accompanied by a pop up box that states, "The configuration could not be loaded.  You are not allowed to access the system configuation."

Any thoughts?!?  The remedy expressed by timelord (i.e. doing a "sudo apt-get upgrade" and a reboot has not gotten me anywhere.

I can, of course, run commands with sudo without issue... password prompt and all.

Help?!!!??!!

---

### Post by tommyg on 2007-02-13
Ah... nerver mind.  After looking around the forums and noticing the dbus error, i found that starting:

/etc/init.d/dbus start

did the trick.  not sure why it isn't starting when the machine is booted...

---

### Post by yoda715 on 2007-02-28
I am having this issue now as well. Fresh install of edgy, then updated. Still having issue. I log into my account, and I cannot access the user and groups applet. I get prompted for password but then it fails to load. I tried starting dbus but it did not work. 

Any suggestions?

---

### Post by kemp_samurai on 2007-10-29
I'm having the same issue. 

here's the symptoms: I'm running Dapper Drake, on GNOME, and everything except the administrative apps are running just fine. (This might've happened when I removed the hostname) I cannot run sudo commands in the terminal, because of this. I cannot put back the hostname.

Help!!

:confused:

[EDIT]
FIXED!! I just broke down and reinstalled ubuntu. that cleared it up too.

---

