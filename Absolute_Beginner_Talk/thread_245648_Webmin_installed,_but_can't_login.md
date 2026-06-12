---
title: "Webmin installed, but can't login"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-08-28
```
root@silverstone:/home/john# dpkg -i webmin_1.290.deb
Selecting previously deselected package webmin.
(Reading database ... 115480 files and directories currently installed.)
Unpacking webmin (from webmin_1.290.deb) ...
Setting up webmin (1.290) ...
Webmin install complete. You can now login to http://silverstone:10000/
as root with your root password.
```

When I goto the webpage it asks for username and password. I have tried root and (sudo password) my username and my password and I can't get in.


Whats wrong?


If all else how do I uninstall a deb package? 8-[

---

### Post by MrHorus on 2006-08-28
> **Scorpuk said:**
> ```

When I goto the webpage it asks for username and password. I have tried root and (sudo password) my username and my password and I can't get in.


Whats wrong?

It's entirely possible that it's looking for a real root user to authenticate against and since the root user is disabled by default in Ubuntu, this won't work.

If you want to enable the root user then this is how to do it but be sure to pick a STRONG password and be aware of the ramifications of what you are doing.

[code]sudo su
```

---

### Post by MrHorus on 2006-08-28
Sorry my mistake, might actually be

```
sudo passwd
```

---

### Post by Soarer on 2006-08-28
That's odd. I use my username (on the remote machine which is being managed) and password and it works fine. You aren't using your local username by chance?

---

### Post by Scorpuk on 2006-08-28
I don't think I'm using my username at home.


Away from home and I have been using putty to install stuff, but that logs me out as soon as I exit. Doesn't it?


Also I reboot the box the other day, but i did start a bf2 server while logged in as me on putty but with sudo su. Under root I see the screen, but under my username I don't. Could this be why?


```
john@silverstone:/home$ screen -ls
No Sockets found in /var/run/screen/S-john.

john@silverstone:/home$
```

```
root@silverstone:/home# screen -ls
There are screens on:
        6020.pts-0.silverstone  (Detached)
        6011.bf2-server (Attached)
2 Sockets in /var/run/screen/S-root.

root@silverstone:/home#
```

Not exactly sure what 6020.pts-0.silverstone  (Detached) is, but it appeared same time I ran the bf2-server.

Hmmm there is a user logged into the system. When I check my sysinfo it says 1 user logged in and then when I log in with putty it says 2... [Sysinfo]("http://scorpuk.plus.com/phpsysinfo/")

---

### Post by SlowYaRoll on 2006-09-01
I had that problem before.  I just finished testing out an install process for webmin on Ubuntu Dapper.  It should apply to all versions of Ubuntu.

To see the detailed instructions, go to [http://ubuntuforums.org/showthread.php?t=195093&page=4](http://ubuntuforums.org/showthread.php?t=195093&page=4)

Here's your problem. . .

You'll be prompted for a username and password.  By default, Webmin copies your system's root password as the Webmin root password.  Since the Ubuntu installation never prompts you to set a root password, you are unable to enter the root password.

To fix this problem, run the following command:
•	sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere

You should now be able to log into Webmin with the username root and whatever you've set as the password.

---

### Post by Scorpuk on 2006-09-01
cool, tnx for the advice. 

I'll try it when I can as my work's internet won't let me use putty, might be a block or somehting on the ports.

---

### Post by waffen on 2007-01-30
> **SlowYaRoll said:**
> I had that problem before.  I just finished testing out an install process for webmin on Ubuntu Dapper.  It should apply to all versions of Ubuntu.

To see the detailed instructions, go to [http://ubuntuforums.org/showthread.php?t=195093&page=4](http://ubuntuforums.org/showthread.php?t=195093&page=4)

Here's your problem. . .

You'll be prompted for a username and password.  By default, Webmin copies your system's root password as the Webmin root password.  Since the Ubuntu installation never prompts you to set a root password, you are unable to enter the root password.

To fix this problem, run the following command:
•	sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere

You should now be able to log into Webmin with the username root and whatever you've set as the password.


All is correct, but for Ubuntu Efgy this is the correct command:

```
sudo /usr/share/webmin/changepass.pl /etc/webmin root enterpasswordhere
```

---

