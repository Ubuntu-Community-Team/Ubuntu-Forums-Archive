---
title: "GNOME Orange icon in system tray- what is it?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by BadDolphin on 2006-12-13
In the system tray I have an icon that is orange, and has an asterisk-like character on it.  When I point the mouse at it, it says "There are 29 updates available."  It is right next to the icon for my ethernet cards, to the left of the date.

What is the name of the program that it launches, and how can I launch it at the command line as root?  The icon no longer works, apparently due to the "gethostbyname" bug, so to do any admin stuff I have to su to root (I enabled the root acct) and run the program manually- but I don't know the name of it nor much of anything else :(   Where can I find how to launch things manually, since there's no way to fix the real problem (see [http://ubuntuforums.org/showthread.php?p=1881133#post1881133](http://ubuntuforums.org/showthread.php?p=1881133#post1881133) for the background info)

---

### Post by Sqwishy on 2006-12-13
I think you're talking about the synaptic updatey thing. In the command line type
```
sudo apt-get upgrade
```
that pretty much does the same thing, i think.

---

### Post by moshuptrail on 2006-12-13
Try:
System > Adminstrator > Update Manager

Also, try setting your hosts file in two lines, and look up the real IP address used by your PC
example:

/etc/hosts
127.0.0.1   localhost
192.168.1.12   closetbox

---

### Post by BadDolphin on 2006-12-13
Both of those methods fail, but it gave me the answer I needed, so THANKS!

(I'm one of those unlucky few who cannot use sudo anymore at all, details in the other thread I mentioned above... I had to enable the root account and issue the command as root on the command line... and apparently it's not repairable, so I'll have to learn how to launch all admin stuff from the command line... this is highly painful for a newb like me...)

---

### Post by BadDolphin on 2006-12-13
Trying the two-line hosts file now, THANK you very much, brb... but wait... I don't think I always get the same IP... I get a private IP from a switch that has a DHCP server, and multiple users share the ports on the switch... can I do something like this:

127.0.0.1 localhost
192.168.1.1/24 closetbox

or something like that?

---

### Post by bulldog on 2006-12-13
Maybe you should consider a reinstall?
Didn't read the old thread,though.:D

---

### Post by BadDolphin on 2006-12-13
I guess I'm hesitating to reinstall because backing up data would be a big hassle, and I still just can't believe that one can trash a major OS by doing nothing more than editing the /etc/hosts file.

---

### Post by Delkster on 2006-12-13
I only have these lines in my hosts file and I have no problems:
```

127.0.0.1 localhost.localdomain localhost teacup

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet ip6-localnet
ff00::0 ip6-mcastprefix ip6-mcastprefix
ff02::1 ip6-allnodes ip6-allnodes
ff02::2 ip6-allrouters ip6-allrouters
ff02::3 ip6-allhosts ip6-allhosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback

```
(teacup is the hostname of this machine -- replace with yours if you try it)

Ok, I do have other stuff in the hosts file, too, but it's not relevant to this matter.

Disclaimer: I have no idea how those IPv6 addresses *should* be.

---

### Post by lyceum on 2006-12-13
> **BadDolphin said:**
> I guess I'm hesitating to reinstall because backing up data would be a big hassle, and I still just can't believe that one can trash a major OS by doing nothing more than editing the /etc/hosts file.

The good the bad and the ugly about FOSS. You get the freedom to do what you want... even mess up you stuff. ](*,)  :)

---

### Post by PriceChild on 2006-12-13
> **BadDolphin said:**
> I guess I'm hesitating to reinstall because backing up data would be a big hassle, and I still just can't believe that one can trash a major OS by doing nothing more than editing the /etc/hosts file.I'm guessing you mean that you can't use sudo because you didn't edit /etc/hosts and the other file at the same time "properly".

Just stick in a live cd and sort out whichever isn't correct.

bingo :)

---

### Post by BadDolphin on 2006-12-15
I've fixed them in recovery mode, and can find nothing wrong with either file, but I still can't run hardly anything.  If I even try to start Kaffeine, it just never starts.  I've read pretty nearly every log file I can find in the /var/log/ directory, and find nothing there.  

What else can even possibly account for this?  It's frustrating that almost all programs fail to launch, and I don't even get so much as an error message or log entry- it just fails to run.

---

### Post by Delkster on 2006-12-17
> **BadDolphin said:**
> If I even try to start Kaffeine, it just never starts.

Things fail even if you're not even trying to use sudo?

What do you get if you enter "kaffeine" in the terminal? It probably spews some error messages and stuff there.

---

