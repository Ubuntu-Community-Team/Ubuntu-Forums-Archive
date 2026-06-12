---
title: "How do i install plugins for opera?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by noob12345 on 2007-05-05
I just got the Opera web browser, but it didn't have the flash or java plugins I installed for firefox

I googled, and couldn't find a tutorial specific to Opera

what is the quickest way to install the flash and JRE plugins?
do i have to remove them and go through the install procedure, or just go throught the install procedures again? I'm using dapper by the way.

---

### Post by darkrose on 2007-05-05
Have you read the Opera plugins for Linux page?
[http://www.opera.com/linux/docs/plugins/install/](http://www.opera.com/linux/docs/plugins/install/)

---

### Post by noob12345 on 2007-05-05
no, i didn't read that
thank you

---

### Post by noob12345 on 2007-05-05
okay, I read that, followed instruction for the flash, then for rpm file, but the installer wouldn't open when i typed in the command
i don't even remember how i got it on firefox

---

### Post by darkrose on 2007-05-05
what is the rpm for?

if you have flash and java installed already you shouldn't need to install anything, just point Opera in the right direction.

For Java:
open tools -- preferences --> advanced tab --> content
tick enable java, then use the java options button to point Opera to /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386 (it could be a little differant if you have an earlier version of java installed)

For Flash:
open tools -- preferences --> advanced tab --> content
tick enable plugins, then click on plugin otions
click change patth then add /usr/lib/flashplugin-nonfree
click ok
click find new - shockwave flash plugin should show up
click ok
click ok
restart opera and you're all done

---

### Post by noob12345 on 2007-05-06
Yes, thank you, that's what i wanted to know

---

### Post by Sef on 2007-05-06
> /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386

I just copy and paste that in the box under java options.

---

### Post by kerry_s on 2007-05-06
for media you can use mozplugger and mplayer with the w32codecs.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by navneeth on 2007-06-02
> **darkrose said:**
> For Flash:
open tools -- preferences --> advanced tab --> content
tick enable plugins, then click on plugin otions
click change patth then add /usr/lib/flashplugin-nonfree
click ok
click find new - shockwave flash plugin should show up
click ok
click ok
restart opera and you're all done

I've been searching for exactly these set of instructions. I didn't how to "point" opera to the plugin folder for firefox. Thanks a lot.

---

