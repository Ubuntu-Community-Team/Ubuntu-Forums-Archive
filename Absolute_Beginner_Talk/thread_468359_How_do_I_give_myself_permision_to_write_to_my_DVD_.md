---
title: "How do I give myself permision to write to my DVD RW and USB disk drives?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Wynne G Oldman on 2007-06-08
As above, really. When I try to write to my DVD rewriter or my MP3 player, I am told that I don't have permission to write to them, because I am not logged in as root. I am sure that there is a really simple way around this, but at the moment, being a newbie, I can't see it. Please help.

---

### Post by RedRover1 on 2007-06-08
Not sure how to fix it but it sounds a bit like this bug.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/75753]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/75753")

---

### Post by diddler on 2007-06-10
Find it hard to believe it is a bug in something as basic as this.  I am having the same problem when I try to drag and drop a file onto a formatted DVD-RW.  I AM able to write using any of the CD/DVD writing apps.

---

### Post by ramjet_1953 on 2007-06-10
Dead easy!

Firstly, identify the drives that you have.
Remember that most external (USB or Firewre) drives are identifed as scsi.

In a terminal type the following command:

[COLOR="Red"]sudo chmod o+r+w /dev/xxxx[/COLOR] (where xxxx is your device)

and example would be [COLOR="Blue"]sudo chmod o+r+w /dev/sdb1[/COLOR] this is an external USB DVD, in my case.

Regards,
Roger :cool:

---

### Post by Wynne G Oldman on 2007-06-11
> **ramjet_1953 said:**
> Dead easy!

Firstly, identify the drives that you have.
Remember that most external (USB or Firewre) drives are identifed as scsi.

In a terminal type the following command:

[COLOR="Red"]sudo chmod o+r+w /dev/xxxx[/COLOR] (where xxxx is your device)

and example would be [COLOR="Blue"]sudo chmod o+r+w /dev/sdb1[/COLOR] this is an external USB DVD, in my case.

Regards,
Roger :cool:

Thanks for the help. I tried that, but it didn't change anything. I can't write to my internal IDE DVRRW drive either.

---

### Post by Wynne G Oldman on 2007-08-14
> **ramjet_1953 said:**
> Dead easy!

Firstly, identify the drives that you have.
Remember that most external (USB or Firewre) drives are identifed as scsi.

In a terminal type the following command:

[COLOR="Red"]sudo chmod o+r+w /dev/xxxx[/COLOR] (where xxxx is your device)

and example would be [COLOR="Blue"]sudo chmod o+r+w /dev/sdb1[/COLOR] this is an external USB DVD, in my case.

Regards,
Roger :cool:

I've just solved this problem. When I looked at the properties for my DVD writer in "hardware information" it said it was called /dev/scd0. I've just installed the trial version of Nero for Linux, and that described it as /dev/sg0. I ran the command that you told me to, inserting /dev/sg0 instead of /dev/scd0 and everything seems to be working OK now.

---

### Post by Wynne G Oldman on 2007-08-14
> **Wynne G Oldman said:**
> I've just solved this problem. When I looked at the properties for my DVD writer in "hardware information" it said it was called /dev/scd0. I've just installed the trial version of Nero for Linux, and that described it as /dev/sg1. I ran the command that you told me to, inserting /dev/sg1 instead of /dev/scd0 and everything seems to be working OK now.
I just re-booted my PC and I'm back to square one. Do I have to enter this command every time I login, or is there a way of making it permanent?

---

### Post by Blutack on 2007-08-14
Use the users and groups tool to check you are in the cdrom and plugdev group.

---

### Post by dasunst3r on 2007-08-14
Maybe it has to do with your user permissions to begin with.  Try this set of procedures:
[list=1]
[*]Go to System -> Administration -> Users and Groups.  You will need to enter your password.
[*]Select your name and click on Properties.
[*]Go to the User Privileges tab
[*]Ensure "Access external devices automatically" and "Use CD-ROM devices" are checked.
[*]Click OK, then close.
[*]Log out and back in.
[/list]

---

### Post by Wynne G Oldman on 2007-08-14
> **dasunst3r said:**
> Maybe it has to do with your user permissions to begin with.  Try this set of procedures:
[list=1]
[*]Go to System -> Administration -> Users and Groups.  You will need to enter your password.
[*]Select your name and click on Properties.
[*]Go to the User Privileges tab
[*]Ensure "Access external devices automatically" and "Use CD-ROM devices" are checked.
[*]Click OK, then close.
[*]Log out and back in.
[/list]

I've just done that. Both those options are already selected.

---

### Post by Wynne G Oldman on 2007-08-14
> **Blutack said:**
> Use the users and groups tool to check you are in the cdrom and plugdev group.
I can't see any of the groups you said. Can I just create them? Also, when I look in all the other groups, I can see "root" and my name in all of them. Next to each name is a box. There are no ticks in any of the boxes for Root and my name. Should I tick them all?

---

### Post by Blutack on 2007-08-14
Sorry, for some reason they do not appear in the GUI.
If you type
groups
in a terminal you should get a full list.
Try using the command
sudo adduser 'yourname' plugdev
and then
sudo adduser 'yourname' cdrom

---

### Post by Wynne G Oldman on 2007-08-14
> **Blutack said:**
> Sorry, for some reason they do not appear in the GUI.
If you type
groups
in a terminal you should get a full list.
Try using the command
sudo adduser 'yourname' plugdev
and then
sudo adduser 'yourname' cdrom
I tried that and it said that I was already a member of both groups.

---

### Post by Wynne G Oldman on 2007-08-15
Bump. Please help.

---

