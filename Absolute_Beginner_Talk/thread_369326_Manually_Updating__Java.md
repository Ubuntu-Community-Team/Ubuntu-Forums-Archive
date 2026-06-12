---
title: "Manually Updating  Java"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by notrublw on 2007-02-24
Currently using 6.06 LTS and Sun Java 1.5.0_06-b05, and would like to update java to latest version.

The installation directory is /usr/lib/jvm.
The Firefox plugin directory is /usr/lib/firefox/plugins.  The symbolic link here points to a symbolic link in /etc/alternatives, which in turn points to the actual plugin in the Sun Java install directory in /usr/lib/jvm.

If I followed Sun's instructions and installed Java in /usr/lib/jvm,
and then changed these symbolic links in /etc/alternatives
   firefox-javaplugin.so
and
  mozilla-javaplugin.so
to point to the new plugin in the installation directory in /usr/lib/jvm,

and also changed these sympolic links in /etc/alternatives

java_jvm
javaws

to point to the right places in the new installatioin directory in /usr/lib/jvm

would I have the new version of java properly installed?

Would running Easy Ubuntu or Automatix be an easier way to update?
Of course, there's always the question "Is it really necessary to update?"  Even if it isn't I thought that doing it would be a good learning experience.

Thanks in advance.

---

### Post by overdrank on 2007-02-24
> **notrublw said:**
> Currently using 6.06 LTS and Sun Java 1.5.0_06-b05, and would like to update java to latest version.

The installation directory is /usr/lib/jvm.
The Firefox plugin directory is /usr/lib/firefox/plugins.  The symbolic link here points to a symbolic link in /etc/alternatives, which in turn points to the actual plugin in the Sun Java install directory in /usr/lib/jvm.

If I followed Sun's instructions and installed Java in /usr/lib/jvm,
and then changed these symbolic links in /etc/alternatives
   firefox-javaplugin.so
and
  mozilla-javaplugin.so
to point to the new plugin in the installation directory in /usr/lib/jvm,

and also changed these sympolic links in /etc/alternatives

java_jvm
javaws

to point to the right places in the new installatioin directory in /usr/lib/jvm

would I have the new version of java properly installed?

Would running Easy Ubuntu or Automatix be an easier way to update?
Of course, there's always the question "Is it really necessary to update?"  Even if it isn't I thought that doing it would be a good learning experience.

Thanks in advance.

I used automatix to install but the site is down now.

---

### Post by notrublw on 2007-03-10
Thanks for your reply.  As it turns out I was prompted to reload the lists of programs in the repositories, and when I did this Sun Java 6 (plugins, etc) was there, installed the relevant
files, and now I have the latest version of java up and running in firefix.

---

