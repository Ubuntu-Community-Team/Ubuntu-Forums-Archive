---
title: "Error. Failed to start X server"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by chapmc on 2006-08-25
Hello again.  I haven't used ubuntu for a couple of days and when I started it today I got "failed to start x server".  It went into the shell which is where it is now.  I tried it twice and same thing.  The last thing I did was install fluendo-mp3 so I could use online radio and that was working ok.  Any suggestions, please?  I am on a different computer right now because I don't know how to get on this forum without gui.
I am using ubuntu v6 with Duron 800 processor, 512 mb ram. I am linux iliterate.

Thanks for any help.

---

### Post by neilp85 on 2006-08-25
This should probably fix your problem:
[http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)

---

### Post by Niamor on 2006-08-25
Hello,

Look in the sticky on top of the forum Absolute Beginner Talk, this will help you.

Looks like neilp85 was faster than me :)

---

### Post by chapmc on 2006-08-25
Thanks for the quick replies.
I tried the fixes you suggested but the dist-upgrade ended with 0 updated, etc. 
need to get 0B of archives.

I did sudo aptitude show xserver-xorg-core | grep Version
and got 
Version: 1:1.0.2-0ubuntu10.3

What now?

---

### Post by hobbit1983 on 2006-08-25
The output from grep looks like you are using the broken x-server package.  This needs to be updated to 10.4 which is available in the main dapper repositories.

Did you try 
sudo apt-get update before trying to upgrade the version of the x-server?

Also (you are probably doing this) you need to enter these commands on your installed linux machine (Against running it on a LIVE CD version or anything)

If you have done all the above, I apologise but pls post back and we will see if we can help some more

---

### Post by chapmc on 2006-08-25
Yes I did use sudo apt-get update and it did download some things.
And I am doing this on the ubuntu machine that has the problem.
Is Version: 1:1.0.2-0ubuntu10.3 wrong?  I assume it should be 10.4.

---

### Post by mssever on 2006-08-25
10.3 is the broken version. Are you connected to the Internet when you issue ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hobbit1983 on 2006-08-25
Yes it should be 10.4

Could you possibly list the command you entered and the output from those commands.

Sorry if this is a pain but it could help to see what is going wrong.

---

### Post by chapmc on 2006-08-25
OK, I rebooted then:

sudo apt-get update

err: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security release.gpg
Temporary failure resolving 'security.ubuntu.com'
Failed to fetch,,   etc.etc.

I don't know if this was the case the first time I ran this.  I don't remember seeing errors.

My internet connection is via usb wifi and I imagine that the shell isn't recognizing the connection.

I may need to reinstall.  I haven't really done much to the system yet and it wouldn't be a terrible job.

I think I'm quitting this for the night.  Will check in the morning.

Thanks.

---

### Post by jdong on 2006-08-25
Try **sudo apt-get install xserver-xorg-core/dapper**, which hopefully you have without network access. That should restore your desktop where you can configure your Internet access.

---

### Post by greg m on 2006-08-25
at least i`m not the only one still having problems.

---

### Post by chapmc on 2006-08-25
jdong
[PHP]Try sudo apt-get install xserver-xorg-core/dapper, which hopefully you have without network access. That should restore your desktop where you can configure your Internet access.[/PHP]

I tried this and it said 1 item was downgraded but when I reboot it still get the same error.  Oh well.
I don't know how to quote what you had written.

---

### Post by jdong on 2006-08-25
If after the downgrade your X server still fails to start, then it's your X windows configuration that's at fault, not this update.

Try running **sudo dpkg-reconfigure -phigh xserver-xorg** to re-detect your video card and monitor.

---

### Post by chapmc on 2006-08-26
> If after the downgrade your X server still fails to start, then it's your X windows configuration that's at fault, not this update.

Try running sudo dpkg-reconfigure -phigh xserver-xorg to re-detect your video card and monitor.

Well this didn't work either.  I think I am going to reinstall.  Thanks for all the help.

---

### Post by jdong on 2006-08-26
Alright, best of luck. Sorry it had to come down to reinstalling :-/

---

