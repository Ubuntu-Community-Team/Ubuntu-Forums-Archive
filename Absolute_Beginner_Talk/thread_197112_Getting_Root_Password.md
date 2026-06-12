---
title: "Getting Root Password"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by ascherjim on 2006-06-15
I have installed Ubuntu successfully (I think) from the direct install disk (not desktop), but nowhere in the install process does it ask me to establish a root password.  Hence, when I go su in the command line, I cannot enter a password which is recognized.  Help.

---

### Post by taurus on 2006-06-15
You use sudo to run those commands.
```

sudo <command>

```

---

### Post by Jagot on 2006-06-15
You can read more about it here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ascherjim on 2006-06-15
Many thanks guys/gals.  I'll give it a try.  When starting out, you learn something new every minute.

---

### Post by u.b.u.n.t.u on 2006-06-15
[QUOTE=ascherjim]I have installed Ubuntu successfully (I think) from the direct install disk (not desktop), but nowhere in the install process does it ask me to establish a root password.  Hence, when I go su in the command line, I cannot enter a password which is recognized.  Help.[/QUOTE]

It sounds like you installed the OEM setup.

If you use the alternate CD, select "text" setup, which is really a gui for some weird reason. The other one is an OEM and it doesn't ask for a username or password.

When I did that I just reinstalled ubuntu.  You can enable a username and password from an OEM but I don't know how.

---

### Post by Jagot on 2006-06-15
[QUOTE=u.b.u.n.t.u]It sounds like you installed the OEM setup.

If you use the alternate CD, select "text" setup, which is really a gui for some weird reason. The other one is an OEM and it doesn't ask for a username or password.

When I did that I just reinstalled ubuntu.  You can enable a username and password from an OEM but I don't know how.[/QUOTE]


He's talking about a root password, not the normal user password.

---

### Post by The Mekon on 2006-06-15
While it is not really neccessary you can use a root account with it own password.

Select System/Administration/Users and Groups, enter you normal password to bring up the Userand Groups conrol panel and tick "Show all users and groups" box.

At the top you should see a root user.Select it and click on Properties.

Now you can enter a root password.

In a normal terminal you can become root by typing su followed by the root password.  Remember to exit because it is not reccomended to use root for normal operations.

If you want to login from startup as root I think you will have to go System/Adminstration/Login window/security and tick the "Allow local system adminstrator login" box.

---

### Post by xeero on 2006-06-15
[QUOTE=Jagot]You can read more about it here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

I've tried "enabling the root account" by doing the "sudo passwd root" method with Breezy and Dapper.  Both times, all it seems to do is mess up my root password so that nothing I try is accepted no matter who i'm logged in as.  i then try to backpedal and enable the root account, but it doesn't help.  so then i need to boot into a safe runlevel to reset the root password back to normal.  

now what i do is create the first user as my "root" account and then follow the steps to "Let sudo ask for the root password" for my "normal" user accounts.  then i'll just use sudo and gksudo to do admin stuff.  this works for me and now i'm using ubuntu.  :KS

---

