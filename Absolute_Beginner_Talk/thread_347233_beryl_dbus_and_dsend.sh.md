---
title: "beryl dbus and dsend.sh?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by no24 on 2007-01-26
Hi,

I was trying to find a way to execute beryl window attributes through the command line and the closest I got was this.

[http://wiki.beryl-project.org/wiki/Using_DBUS](http://wiki.beryl-project.org/wiki/Using_DBUS)

I'm a bit confused as to how to get it going though, I understand it's already installed in beryl-plugins but I don't know how to use the feature.

---

### Post by aidanr on 2007-01-27
create a new file somewhere in your path (eg. ~/bin or /usr/local/bin) copy the first bit of code there into it, save it as dsend.sh and make it executable

then go into beryl settings manager and make sure the dbus plugin in extras is active

then open a terminal and try out some of the example commands on that page

---

### Post by no24 on 2007-01-27
hey thanks,

i think one problem i encountered earlier is that there doesn't seem to be such an option available in the extras section.

I was able to make dsend.sh executable.. am I missing something else? executing dsend.sh gives an error so I assume I have to enable dbus first, but I can't find the option.

---

### Post by aidanr on 2007-01-27
well the dbus plugin was only integrated with beryl-plugins recently in the last version or two, so make sure you've got the latest version or if you're on dapper ```
sudo apt-get install beryl-dbus
```

---

### Post by no24 on 2007-01-27
hmm yea, im on edgy and it says that the dbus-plugin is already in the beryl-plugins. I've only installed beryl a few days ago. can anyone confirm the most updated version of beryl has the dbus setting in the beryl settings manager?

---

### Post by no24 on 2007-01-27
okay i had to reinstall beryl-plugins and now it's appeared. thanks!!

---

### Post by no24 on 2007-01-27
aidanr, 

thanks for your help but do you (or anyone) know why I get this error now when I try to use the dsend.sh commands?

```

7899: arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 797.
This is normally a bug in some application using the D-Bus library.
7899: arguments to dbus_message_set_auto_start() were incorrect, assertion "message != NULL" failed in file dbus-message.c line 2363.
This is normally a bug in some application using the D-Bus library.
Couldn't allocate D-Bus message

```

---

### Post by no24 on 2007-01-28
bump? :T

---

