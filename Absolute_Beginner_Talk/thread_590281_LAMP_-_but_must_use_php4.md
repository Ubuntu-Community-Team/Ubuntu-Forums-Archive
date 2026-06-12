---
title: "LAMP - but must use php4"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by vlazdir on 2007-10-24
Hi everyone,

I am a newbie, but I have searched the forum and cannot find an answer to my issue.

I am going to use eZ Publisher (CMS), but the problem is that it is not supported on php5. I won't run at all. So I have to use php4 and preferably Apache 1.3. I have installed LAMP and don't know how to configure this to work. 

Is it possible to uninstall Apache2 and php5 and then install Apache1.3 and php4? How do I do that and does anyone know if there exists a bundled package containing this for Ubuntu?

I appreciate any help!

/erik

---

### Post by rbprogrammer on 2007-10-24
i dont see any reason why you cannot do it... but i'm not sure exactly what commands you will need to execute.. but ehre is a general game plan:

[INDENT]
uninstall apache2
[INDENT]$sudo apt-get purge apache2[/INDENT]
uninstall php5
[INDENT]$sudo apt-get purge php5[/INDENT]

install apache1.3 and php4
[INDENT]$sudo apt-get install apache php4[/INDENT]
[/INDENT]

****NOTE:**
this is probably not too accurate, but hopefully it will give you an idea on how to uninstall the certain components and then install the ones you want.

****NOTE:**
if you installed a GUI, (ie gnome or kde) this would probably be easier if you used the package manager.
GNOME is System->Administration->Synaptic Package Manager
KDE is KMenu->System(or something)->Adept

---

### Post by vlazdir on 2007-10-25
I'll try this when I get home from work!

I installed a GUI last night, but I didn't have time to try it.

I really appreciate fast replies! Thank you!

---

