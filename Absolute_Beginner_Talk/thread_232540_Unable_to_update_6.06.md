---
title: "Unable to update 6.06"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Sarastro on 2006-08-08
I have spent the last week trying to solve this problem but I am now completely out of ideas.  After a new install of 6.06, I am unable to successfully perform any type of system update (using:  Update Manager, Synaptic, or any apt-get command) .  My Internet connection otherwise is fully operational.  I have checked my router for any configuration problems which may block my ability to receives updates finding nothing obvious.  


With each attempt I receive the following (this is only the first few lines, there's a lot more errors):

  guest@Oldfield:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release



Here is a copy of my current (I have tried many) sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

I am determined to get this to work so any input is greatly appreciated.

---

### Post by catlett on 2006-08-08
What happens when you hit on the links in your post? I go right to the repository servers. Do you? If you can reach the servers with your web browser, try running sudo apt-get update again to see what happens.

---

### Post by Sarastro on 2006-08-08
The links work fine, they take me to the repositories.  However the results with update are lines of error messages.  Here are the first few lines:

guest@Oldfield:~$ sudo apt-get update
Password:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release

---

### Post by msak007 on 2006-08-08
Can you post the contents of your apt.conf (/etc/apt/apt.conf)?

---

### Post by catlett on 2006-08-08
There are a couple of threads that say eliminating the line 
> Acquire::http::Proxy "false";

in the file /etc/apt/apt.conf cures the problem. It might be worth a shot.
To access the file enter  ```
sudo gedit /etc/apt/apt.conf
```
and put a # in front of the line. That is a comment marker. It tells the computer to ignore the following text because it isn't code nut a comment for people to read. If it doesn't have an effect, you just delete the # to put it back like before.

For example here is my file before the change
> APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";
And after the comment is put in
> APT::Authentication::TrustCDROM "true";
#Acquire::http::Proxy "false";
Save the document and run ```
sudo apt-get update
```If it works then update with ```
sudo apt-get update
```

---

### Post by msak007 on 2006-08-08
I'm not sure that's entirely the problem but it's worth a shot. For what it's worth that's the only line in my file, and mine works just fine. Sometimes there's a typo in there or an extra : that can cause the problem. Either way before commenting anything out, I think the contents should be posted first.

---

### Post by catlett on 2006-08-08
[http://www.ubuntuforums.org/showpost.php?t=193178&p=1139641](http://www.ubuntuforums.org/showpost.php?t=193178&p=1139641)
[http://www.ubuntuforums.org/showthread.php?t=190679](http://www.ubuntuforums.org/showthread.php?t=190679)
[http://www.ubuntuforums.org/showthread.php?t=202197](http://www.ubuntuforums.org/showthread.php?t=202197)
Three Ubuntu threads with members saying the false value was the issue is enough for me to offer it as an option.
Plus commenting something out does not cause any damage. The file is still there in it's original state. It only takes removing the comment to get it back. 
How else do you trouble shoot if not by changing a value and running the procedure again?

---

### Post by msak007 on 2006-08-08
I apologize if you interpreted my comments the wrong way but I never said it wasn't an option - I was simply suggesting that the file contents be posted first before making any changes to see if it's possibly something else. I was also stating that my file only has that one line and I've had no problems - everyone's machine is different and that may very well be the problem and I was in no way disagreeing with you.

---

### Post by Sarastro on 2006-08-09
I changed /etc/apt/apt.conf to the following:

#Acquire::http::Proxy "false";

Ran the apt-get update with the following result:

guest@Oldfield:~$ sudo apt-get update
E: Syntax error /etc/apt/apt.conf:1: Unsupported directive 'Acquire::http::Proxy'

---

### Post by Sarastro on 2006-08-09
Wow! Success.

I referred to the links provided by Catlett and noticed that those having success with removing the proxy false line actually erased it.  For some reason using # (normally a great idea) to mask the line does not clear the download problem.

Thanks for your help.

---

### Post by msak007 on 2006-08-09
That's odd that commenting the line didn't resolve it, but completely removing it did. So now your apt.conf file is completely empty? Oh well if it works then that's all that matters.

---

### Post by mrhealthpatriot on 2006-11-01
Updating from 6.06 to 6.10 was nearly impossible with the alt-install disks. So I used a server install cd of 6.10, and did a
"sudo apt-get install ubuntu-desktop" (Thanks Catlett)
and
"sudo /etc/init.d/gdm start" to get the GUI up.

Now everthing works great! You might want to give that a try.
(make sure you go get some coffee, do some chores, etc., while ubuntu-desktop is installing)

---

### Post by dan666 on 2007-06-15
THANKS A MILLION!

im quite new to linux and removing the 

Acquire::http::Proxy "false"; 

worked amazingly

thanks again:D

---

