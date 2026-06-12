---
title: "Changed permissions and now can't log in!"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by ciroandrade on 2008-02-22
Hello.  I am the admin user in ubuntu, and was creating a new account, called "guest", so others in my family could use linux too but without messing up anything.  

So in /home/ directory, I could see "ciroandrade" (me) and "guest".  

I wanted to keep the files in my own folder, "ciroandrade", private, so I changed the attributes or properties in that folder *and all subfolders* so that no other users could access them: no read nor write.

But I think I made a big blunder since I can't log into gnome interface anymore; I just get a terminal window.  

when I switch to another window with Alt + F8, I can read: "Starting GNOME Display Manager... FAIL"

Is there any way to get back to GNOME?  Please help!!

(And sorry for being such a noob klutz...)  :(

---

### Post by taurus on 2008-02-22
Switch to another console and log in with your username and password.  Then, try

```
cd /home
chmod -R 700 /home/ciroandrade
chmod 644 /home/ciroandrade/.dmrc
sudo /etc/init.d/gdm start
```

---

### Post by kool_kat_os on 2008-02-22
i just realized that taurus has over 21 thousand beans.....thats ALOT

---

### Post by ciroandrade on 2008-02-23
Thank you for the prompt reply.  Unfortunately it wasn't successful.  After typing the last command, I get again: 

* Starting GNOME Display Manager...  [fail]

Let me add some other symptoms.  

In the boot screen, where many components load "ok", the part that says "starting kernel log" fails.  

Any ideas?  Thanks for the replies.

---

### Post by ciroandrade on 2008-02-23
Additionally, when I try to log as "guest", I get a message that says: "Unable to cd to /home/guest".

Hope that helps...

---

### Post by taurus on 2008-02-23
Boot into recovery mode and post the output of this command.

```
ls -la /home
```
Then, try removing the old gdm and reinstall it again.

```
apt-get remove gdm
apt-get update
apt-get install gdm
shutdown -r now
```
Does GUI login screen start now?

---

### Post by ciroandrade on 2008-02-24
Ok.  Let's see...  After the "ls" command, it reads:

  total 24
  drwxr-xr-x   4      root                 root               4096   Feb 22 19:58   .
  drwxr-x---   21    ciroandrade     ciroandrade   4096   Jan 22 17:10   ..
  drwx------   70    ciroandrade     ciroandrade   12228 Feb 22  19:55  ciroandrade
  drwxr-xr-x  15    guest               guest             4096   FEb 22 19:52   guest

Now I'm gonna run those commands.

---

### Post by ciroandrade on 2008-02-24
Mmm...  Can't get those commands to run.  Apparently the computer doesn't recognize the internet connection.

Any "hard" solutions?

Thank you for your help.

---

### Post by asmoore82 on 2008-02-24
> **taurus said:**
> 
```
chmod -R 700 /home/ciroandrade
```

This command is a very bad idea, as it will set the executable permission on every file under the home directory.

---

### Post by asmoore82 on 2008-02-24
> **ciroandrade said:**
> Ok.  Let's see...  After the "ls" command, it reads:

  total 24
  drwxr-xr-x   4      root                 root               4096   Feb 22 19:58   .
  **[COLOR="Red"]drwxr-x---   21    ciroandrade     ciroandrade   4096   Jan 22 17:10   ..[/COLOR]**
  drwx------   70    ciroandrade     ciroandrade   12228 Feb 22  19:55  ciroandrade
  drwxr-xr-x  15    guest               guest             4096   FEb 22 19:52   guest

Now I'm gonna run those commands.(emphasis added)

the red line is the problem, according to that, the entire root filesystem is owned by your user account;
it should be owned by root with 755(drwxr-xr-x) permissions:
```
sudo chown 0:0 /
sudo chmod 755 /
```

---

### Post by ciroandrade on 2008-02-25
Thank you, thank you very much!

I did what you told me and now ubuntu is running again.  Internet connection and everything.  

Thank you asmoore82 and taurus, you have been extremely helpful.  You guys are awesome!

---

### Post by asmoore82 on 2008-02-26
> **taurus said:**
> 
```
chmod -R 700 /home/ciroandrade
```

> **asmoore82 said:**
> This command is a very bad idea, as it will set the executable permission on every file under the home directory.

This condition is fairly easy to fix; I just had to read `man find` ;):
```
find /home -type f -exec chmod -x '{}' \;
```

---

