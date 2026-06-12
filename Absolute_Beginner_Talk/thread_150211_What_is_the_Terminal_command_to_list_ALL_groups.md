---
title: "What is the Terminal command to list ALL groups?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-25
Hello All !!!

I would like to know the Terminal Command that will show me ALL the "groups" that exist in my Ubuntu.

If I launch a Terminal window & type:

root@ubuntu:/# groups
root
root@ubuntu:/#

I only see ONE group, the group I currently belong at...

I can NOT see the rest of the "groups" I have created...

What is the command to see that?

P.S.> I tried using "ls groups", hopefully for a full list of ALL groups, but it does not work...

Thanks.

---

### Post by wsanders on 2006-03-25
Well, they're listed in /etc/group . I'm not sure if there is a command to show them, though.

---

### Post by zourcast on 2006-03-25
In the command line type

cat /etc/group | more

That should do it.
The groups will be listed in the command line, with the people that belong to them in front of them. Just keep pressing enter until the list finishes.

---

### Post by dvarsam on 2006-03-25
[QUOTE=zourcast]In the command line type:

cat /etc/group

That should do it.
[/QUOTE]

I tried that, but I do NOT want the full list...

I only want the users I have added, like:

root,
my_name (e.g. dimitris),
mysql (I created this),
etc.

I do NOT want this whole thing:

root : x : 0 :
daemon : x : 1 :
bin : x : 2 :
sys : x : 3 :
adm : x : 4 : dimitris
tty : x : 5 :
disk : x : 6 :
lp : x : 7 : cupsys
mail : x : 8 :
news : x : 9 :
uucp : x : 10 :
man : x : 12 :
proxy : x : 13 :
kmem : x : 15 :
dialout : x : 20 : dimitris , cupsys
fax : x : 21 :
voice : x : 22 :
cdrom : x : 24 : dimitris , hal
floppy : x : 25 : dimitris , hal
tape : x : 26 :
sudo : x : 27 :
audio : x : 29 : dimitris
dip : x : 30 : dimitris
www-data : x : 33 :
backup : x : 34 :
operator : x : 37 :
list : x : 38 :
irc : x : 39 :
src : x : 40 :
gnats : x : 41 :
shadow : x : 42 :
utmp : x : 43 :
video : x : 44 : dimitris
sasl : x : 45 :
plugdev : x : 46 : dimitris , hal
staff : x : 50 :
games : x : 60 :
users : x : 100 :
nogroup : x : 65534 :
dhcp : x : 101 :
syslog : x : 102 :
klog : x : 103 :
dimitris : x : 1000 :
lpadmin : x : 104 : dimitris
scanner : x : 105 : dimitris
admin : x : 106 : dimitris
crontab : x : 107 :
ssh : x : 108 :
slocate : x : 109 :
messagebus : x : 110 :
hal : x : 111 :
saned : x : 112 :
gdm : x : 113 :
mysql : x : 1001 :
postfix : x : 114 :
postdrop : x : 115 :

I have even looked into this address:

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

And found Nothing...

Thanks.

---

### Post by zourcast on 2006-03-25
Have you already tryed to use the graphic interface?

Go System -> Admin -> Users and Groups (I dont know if that is the exact name of the menus because my ubuntu is not in english, but you should get it.)

Select the tab Groups.

There you have a shorter list. But it is not only the groups you created.

Not sure if there is a way to do exactetly what you want. But if there is one, I'm pretty sure somebody will tell you.

---

### Post by taurus on 2006-03-25
```

id <user name>

```

---

### Post by dvarsam on 2006-03-25
[QUOTE=taurus]```

id <user name>

```[/QUOTE]

Using "id username" seems much better!

Thanks.

---

### Post by dante on 2006-03-25
you can also type:
groups [username]
...it's about the same, minus the user and group ids

---

