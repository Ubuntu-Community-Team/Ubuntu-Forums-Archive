---
title: "And this error means...help.."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-07-01
I thought everything was going well. Until I logged on after shutting down and I got this error:

    Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. Users $HOME directory must be owned by user and not writable by others.

Any help would be very nice.

---

### Post by oldmanstan on 2007-07-01
here ya go...
[URL="http://ubuntuforums.org/showthread.php?t=91455"]
http://ubuntuforums.org/showthread.php?t=91455[/URL]

---

### Post by toasty_ghosty on 2007-07-01
solution:
1. leave your permission as they are(see below).

2. in /etc/gdm/gdm.conf in section security insert:
"RelaxPermissions=1"

3. restart gdm by killing and starting it again from a real console([CRTL-ALT-F1] ->login->#killall gdm->#gdm).

that should fix it


I tried that, but when I found gdm.conf I could not save it. Should I change the 0 to 1 and then just restart it? And when I restart it should I just restart the machine itself, or just ctrl alt bckspace it?

---

### Post by cogadh on 2007-07-01
You need to edit the gdm.conf file using this command:
```
sudo gedit /etc/gdm/gdm.conf
```
That will give you ther permissions to save the file.

---

### Post by toasty_ghosty on 2007-07-01
Thank very much.

---

