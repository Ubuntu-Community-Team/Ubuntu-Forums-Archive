---
title: "hibernate from command prompt"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by energiya on 2007-01-02
Hi,

I like working using the command prompt, and doing all the nasty stuff without the help of Gnome (using Ubuntu), but I don't know how to send my computer to hibernate from command line. Could someone help?

Thanks

---

### Post by Ecthelion on 2007-01-04
> I like working using the command prompt, and doing all the nasty stuff without the help of Gnome (using Ubuntu), but I don't know how to send my computer to hibernate from command line. Could someone help?

I googled it up for you:[ this article]("http://spidertools.com/ub_power.php") tells you more about the power management.

[QUOTE=article]apmd – controls power management tasks
apm – command line access to print current battery status or suspend power
xapm – battery meter for X Window[/QUOTE]

You can find more info how to use these commands with man.
For example:
```
man apmd
```
That's the one you want.

---

### Post by energiya on 2007-01-04
Thanks a lot!

---

### Post by leafw on 2007-03-07
Have a look at

/etc/acpi/sleep.sh
/etc/acpi/hibernate.sh

and other scripts at the same folder, which can be executed with sudo.

Beware that your laptop may be using APM instead of ACPI.

---

### Post by energiya on 2007-03-08
Tanks! Anyway, problem solved some time ago!:)

---

### Post by Galdor on 2007-09-24
he man,

this works fine.
but I have to be root or do it be using sudo.

I want to fill the command in powermanager xfce as a command to do as the  battery runs low.
At this point I would prefere to not have to type the root password.

Any ideas will be welcome.

cheers
G.

---

### Post by jordanmthomas on 2007-09-24
Galdor, try this:
```
sudo visudo
```
Go to the bottom of it (press i to go into edit mode) and add 
```
[COLOR="Red"]your_user_name[/COLOR] ALL= NOPASSWD: /usr/sbin/hibernate
```
Hit escape after adding this, and type :wq to save the file and quit.
After this, your user shouldn't be prompted for a password when running the hibernate comnmand.

(note, visudo is kind of the same as just using any editor to edit /etc/sudoers, but it checks to make sure you didn't screw something up when it quits.  So, if you absolutely can't figure out how to use vi, you can use nano or gedit.  JUST BE CAREFUL if you use something else because if you screw up your sudoer file it will be a pain to fix since you'll have to reboot into recovery mode)

---

### Post by energiya on 2007-09-24
Wow this thread  is old...

Just for the sake of security you could do something like
```

USERNAME IP = NOPASSWD: /usr/sbin/hibernate

```
Won't work with a local ip (like 127.0.0.1, 192.168.x.x, 10.10.x.x or localhost), so first try what jordanmthomas said, and only then, if you consider it worths is, try this

---

### Post by Galdor on 2007-09-24
you really want me to free ../sbin ???

just if I would, it is not that easy

I have problems removing battery.ko because of the rights

freeing it in the sudoers file does not help

:(

---

### Post by jordanmthomas on 2007-09-24
> **Galdor said:**
> you really want me to free ../sbin ???
:(

Well, just one file in sbin.  You're the one who doesn't want to type a password after all. :)

I'm not sure what to do about permissions if this doesn't work right other than chmod u+s ing the hibernate script (probably a BAD idea)

---

### Post by Galdor on 2007-09-25
hello,

ok permitting one file is not as bad as doing this for the whole sbin directory ;-)

doing chmod on that script seems helpfull
by just allowing to execute but not to modify

how ever I was searching for the command neccessary to run for hibernation and the important hint I found here plus fast and friendly support

Thank You.

---

### Post by stdPikachu on 2008-01-27
Howdy there, I'm looking to hibernate my machine from the cmdline via irexec and have also been researcing the issue.

I can understand why you'd need to add a sudoers entry for using the hibernate script, but how do the desktop environments handle it? They don't need you to type in your password to shutdown/whatever...do they re-implement hibernate/suspend/shutdown internally?

---

### Post by jordanmthomas on 2008-01-27
> **stdPikachu said:**
> Howdy there, I'm looking to hibernate my machine from the cmdline via irexec and have also been researcing the issue.

I can understand why you'd need to add a sudoers entry for using the hibernate script, but how do the desktop environments handle it? They don't need you to type in your password to shutdown/whatever...do they re-implement hibernate/suspend/shutdown internally?

I bellieve the desktop environments just run the command as root.  For example, gdm is run as root so when a user is running gnome and gdm, gdm calls reboot / hibernate.

I think this is the case because if you run gnome without gdm, you lose the option to reboot.

---

### Post by stdPikachu on 2008-01-27
Cheers, that explains alot, wasn't aware it was ?dm managing my shutdown options.

Edit: wooh, further thanks are in order, the commands gdm users are clearly visible in /etc/gdm/gdm.conf:
```
banquo@banquo:~$ grep -i hibern /etc/gdm/*
/etc/gdm/factory-gdm.conf:HibernateCommand=/usr/sbin/pmi action hibernate
/etc/gdm/gdm-cdd.conf:HibernateCommand=/usr/sbin/pmi action hibernate
/etc/gdm/gdm.conf:HibernateCommand=/usr/sbin/pmi action hibernate
```
As suspected, a `sudo pmi action hibernate` does the job, so all that needs doing is to add pmi to sudoers and all should be huny dory. Will let you know when I get irexec working :)

---

