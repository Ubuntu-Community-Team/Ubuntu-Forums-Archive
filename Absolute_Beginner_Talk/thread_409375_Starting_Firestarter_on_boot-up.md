---
title: "Starting Firestarter on boot-up"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-04-14
Hey all! I'm trying to get Firestarter to run on boot-up (ie, I want the system tray icon to appear), but I can't seem to get it working. I added "firestarter" to my startup list in the Sessions options, but when I rebooted it said I couldn't run Firestarter because I wasn't root. So I went back into Sessions and changed it to "sudo firestarter." I then rebooted, but nothing happened, no message, no tray icon, nothing.

The guide on the Firestarter website is a little unclear, or I wouldn't be asking. :-(

Thanks!

---

### Post by heimo on 2007-04-14
Hi!

First of all, firestarter is just frontend for the actual firewall - so the firewall is running even when firestarter isn't. If you still want to run it automatically, you'll need to edit sudoers file. Use visudo to do that. Read these threads/instructions:
[http://ubuntuforums.org/showthread.php?t=341972&page=2](http://ubuntuforums.org/showthread.php?t=341972&page=2)
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by sad_iq on 2007-04-14
Why do you want to run Firestarter on boot? The firewall is still working even without Firestarter running!!! Anyway ...try changing "sudo firestarter" with "gksudo firestarter" !!!

---

### Post by hackle577 on 2007-04-14
> **sad_iq said:**
> Why do you want to run Firestarter on boot? The firewall is still working even without Firestarter running!!!

I often use an app that tunnels my Xbox's connection through my computer's connection, so it's nice to have the GUI there for rules creation, modification, etc.

---

### Post by hackle577 on 2007-04-14
Alright, I edited my sudoers file, here it is:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
adam ALL= NOPASSWD: /usr/sbin/firestarter
```

I also added "sudo firestarter --start-hidden" to my startup list, but the GUI is still not starting on boot. I'm gonna change that to gksudo and see if that works.

UPDATE: gksudo has no effect. I'm stuck here.

---

### Post by heimo on 2007-04-14
Try it like this:
```
xhost +local:root && gksudo firestarter
```

---

### Post by Maestro23 on 2007-04-14
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by hackle577 on 2007-04-14
> **Maestro23 said:**
> [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Tried it, see above.

---

### Post by hackle577 on 2007-04-14
"xhost +local:root && gksudo firestarter" in the startup list didn't work.

Any other suggestions?

---

### Post by heimo on 2007-04-14
> **hackle577 said:**
> "xhost +local:root && gksudo firestarter" in the startup list didn't work.

Any other suggestions?

Does it work from terminal?

---

### Post by hackle577 on 2007-04-14
"xhost +local:root && gksudo firestarter" runs Firestarter from terminal but it still doesn't run the GUI upon bootup. Once again, the contents of my etc/sudoers:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
adam ALL= NOPASSWD: /usr/sbin/firestarter
```

And Firestarter's entry in my Startup list is this:

```
sudo firestarter --start-hidden
```

This should work according to the FAQ on Firestarter's website, but the GUI still doesn't show in the tray after bootup.

---

### Post by hackle577 on 2007-04-14
Alright, I am now trying to simply uninstall Firestarter, but that isn't even working now. I can't even access the GUI either.

"gksudo firestarter" returns this error:
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:9457): Gtk-WARNING **: cannot open display:
```

Trying to completely remove it via Synaptic results in this error:
```

E: firestarter: subprocess post-removal script returned error exit status 1
```

Please help!

---

### Post by hackle577 on 2007-04-15
Bumpity bump bump. Help please? :-(

---

### Post by studentx on 2007-04-16
I created a hack around this because for some reason no one can get this to work 
the expected way.

Create a python script

Do the following in a terminal:
gedit firestarter.py

copy and paste the following into gedit:
import os
os.system('xhost +local:root') 
os.system('gksudo "firestarter --start-hidden" &')

Then go to System->Preferences->Sessions
Add a new program and in the command text box type:
python firestarter.py

Thats it.

---

### Post by hackle577 on 2007-04-16
SUCCESS! Thanks man, you rock!

---

### Post by zhinker on 2007-05-15
> **heimo said:**
> Hi!

First of all, firestarter is just frontend for the actual firewall - so the firewall is running even when firestarter isn't. If you still want to run it automatically, you'll need to edit sudoers file. Use visudo to do that. Read these threads/instructions:
[http://ubuntuforums.org/showthread.php?t=341972&page=2](http://ubuntuforums.org/showthread.php?t=341972&page=2)
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)
So you're saying Ubuntu always has a firewall running even if you don't see it?

---

### Post by Steve H on 2007-05-15
> **studentx said:**
> I created a hack around this because for some reason no one can get this to work 
the expected way.

Create a python script

Do the following in a terminal:
gedit firestarter.py

copy and paste the following into gedit:
import os
os.system('xhost +local:root') 
os.system('gksudo "firestarter --start-hidden" &')

Then go to System->Preferences->Sessions
Add a new program and in the command text box type:
python firestarter.py

Thats it.

Cheers studentx, that worked a treat. I have VMware player running XP, which has a bridged network with my Ubuntu box. I had found that Shields Up! was finding some of my ports open and not all ports were stealthed. Firestarter closes them when it is running in the tray, so I just wanted the piece of mind of it running. I´m sure there is a way to edit iptables with more finesse than I have managed but it will do for the time being.

Thanks again.


:)

---

### Post by Primefalcon on 2008-05-14
I have to say thank you myself

I run apache and php on this system for a local test environment, without firestarter active, everyone can access the pages by typing in my address in the url.

As you can imagine this is a major security concern, I dont want to have to resort to using htacess to limit access.

firestarter fixed the problem perfectly, when its running (icon in tray) I get notified when someone tries to access the page, and can either allow or deny the ip address.

no so unless firestarter is running in the system tray, you are NOT getting full protection.

---

