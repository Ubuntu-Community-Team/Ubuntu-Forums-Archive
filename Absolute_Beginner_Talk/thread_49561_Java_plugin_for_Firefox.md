---
title: "Java plugin for Firefox"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by Zaare on 2005-07-16
I installed Java Runtime Environment using:
```
sudo apt-get install sun-j2re1.5
```
This is supposed to include the plugin for Firefox, but when I try to load a site with a java applet I get: "Additional plugins are required to display all the media on this page". And it tries to install Java Runtime Environment when I click the "Install missing plugins" button.
Any ideas on why this isn't working?

---

### Post by poofyhairguy on 2005-07-16
[QUOTE=Zaare]I installed Java Runtime Environment using:
```
sudo apt-get install sun-j2re1.5
```
This is supposed to include the plugin for Firefox, but when I try to load a site with a java applet I get: "Additional plugins are required to display all the media on this page". And it tries to install Java Runtime Environment when I click the "Install missing plugins" button.
Any ideas on why this isn't working?[/QUOTE]

Are you using 64 bit Ubuntu? 64 bit version lacks Java.

---

### Post by RastaMahata on 2005-07-16
first, check ifjavainstalled correctly:```
java -version
```If itdid install correctly, type the following command```
sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so
```Then open firefox (or restart it if it was already open) and in the addressbar, type:```
about:plugins
```If you see the java plugin listed, you're ready to go. Good luck ;)

---

### Post by Zaare on 2005-07-17
Thanks RastaMahata, the linking worked like a charm. (At least that's what I think "ln -sf" did) ;)

[QUOTE=poofyhairguy]Are you using 64 bit Ubuntu? 64 bit version lacks Java.[/QUOTE]
Nope, but good to know. :)

---

### Post by KB8GT on 2005-07-21
sudo apt-get install sun-j2re1.5  ---- results in the following warning.

WARNING: The following packages cannot be authenticated!
  sun-j2re1.5

An option is given to install anyhow, but it does not and  the command line is returned

What might I be doing wrong  ???

Thank You
Larry

---

### Post by MikeyXX on 2005-07-21
[QUOTE=RastaMahata]first, check ifjavainstalled correctly:```
java -version
```If itdid install correctly, type the following command```
sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so
```Then open firefox (or restart it if it was already open) and in the addressbar, type:```
about:plugins
```If you see the java plugin listed, you're ready to go. Good luck ;)[/QUOTE]
 Everything went without error, but it doesn't show in that about:plugin list. Suggestions?

---

### Post by André on 2005-07-24
Hi everybody,

i had the same error. J2SDK installed (also j2re but only because i was getting desperated ;-) AFAIK J2SDK includes J2RE) but no java plugin in firefox.

So i started to browse my system a bit and here is what i found.

1. ls -al /usr/lib/mozilla-firefox/plugins/:

lrwxrwxrwx   1 root root   39 2005-07-15 13:48 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

2. ls -al /etc/alternatives/ | grep firefox:

lrwxrwxrwx    1 root root   57 2005-07-24 12:31 firefox-javaplugin.so -> /usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

3. But there was no plugin directory in /usr/lib/j2sdk1.5-sun/

4. cd /etc/alternatives

5. rm firefox-javaplugin.so

6. ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so firefox-javaplugin.so (is you installed the JRE package)

I think this could also be ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so firefox-javaplugin.so (for the SDK package)


7. Restart firefox and you should have a nice java plugin

Greetings and hope that it helps you
André


P.S.: I noticed that there was a similar answer above. But the problem there was AFAIK that you installed "only" the JRE (which is enough for you to run the plugin) and then the plugin is in  /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so not in /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so.

---

