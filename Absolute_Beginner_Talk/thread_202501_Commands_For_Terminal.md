---
title: "Commands For Terminal"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by deweese on 2006-06-23
List of Commands For Ubuntu Linux to Be Used In &#8220;Terminal&#8221;

1).sudo apt-get update is for updates
2).sudo apt-get upgrade is for upgrades
3).ps ux tells what applications are running in the entire system
4).kill -9 then four digit number of application that ps ux displays this kills an app
5).gksudo &#8220;update-manager -d&#8221;  one way to upgrade to a newer version of Ubuntu
6).sudo apt-get dist-upgrade  This is another way to upgrade from one distribution to the next.
7).sudo apt-get remove (then put the name of the program you want to remove).
8 ).sudo passwd root (then enter user password, then select a superuser password)

---

### Post by bruce89 on 2006-06-23
[QUOTE=deweese]
1).sudo apt-get update is for updates
2).sudo apt-get upgrade is for upgrades
...
5).gksudo “update-manager -d”  one way to upgrade to a newer version of Ubuntu
6).sudo apt-get dist-upgrade This is another way to upgrade from one distribution to the next.
7).sudo apt-get remove (then put the name of the program you want to remove).
8).sudo passwd root (then enter user password, then select a superuser password)
[/QUOTE]
1)Updates the package list
2)Upgrades the packages (if any available)
5)AFAIK, the -d switch is no longer needed, as dapper isn't the **d**evelopment version.
6)Requires the file /etc/apt/sources.list to be edited beforehand.
7)sudo aptitude remove is preferred
8)Not encouraged

---

### Post by deweese on 2006-06-23
ok thanks what's edgy then? -e ??

---

### Post by bruce89 on 2006-06-23
[QUOTE=deweese]ok thanks what's edgy then? -e ??[/QUOTE]
No, the -d means **d**evelopment.

Aptitude is preferred to apt-get now, see [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude).

---

### Post by egorgry on 2006-06-23
kill with no options is safer as it cleans up after itself
kill -3 if desparate. (quits out gracefully)
kill -9 if all else fails. (can leave a mess behind)
If you really need a root shell when you are doing a lot of configuring and such I would recommend using sudo -s you will get a root terminal for that session. No need to create a root account.

df -h get's FS size in human readable ie; gb, mb
top system moitor
pkill by process name (pkill evolution) will kill your mail client.
there is too many cmd line options ;)

---

