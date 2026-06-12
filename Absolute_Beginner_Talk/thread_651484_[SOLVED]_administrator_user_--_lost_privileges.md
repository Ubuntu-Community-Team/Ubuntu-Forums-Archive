---
title: "[SOLVED] administrator user -- lost privileges"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by hardmath on 2007-12-27
This seems very weird to ask, but when I installed Feisty Fawn (for a friend, on a a very minimal machine), I created the user "administrator" with administrative privileges (I think).

Now the user and password for "administrator" are intact but there are no more administrative privileges assigned (as best I can tell).

I did create (for the friend) a desktop user account, so it would seem indisputable that at one time the administrative privileges did exist.

But now the bulk of the applets (including user management and synaptics) that ought to appear under System -> Administration, do not.  Moreover those applications which require the administrative password prompt are failing with a message about sudo not allowing the program to operate.

So... is it possible that there is a catch in the Ubuntu security model that says, if you create an initial user account called "administrator" with administrative privileges, it will lose those privileges as soon as another user account is created regardless of the level of privilege of that account?

Yes, I do realize this sounds paranoid.  In the alternative, does anyone have a suggestion about reclaiming adminstrative rights on the machine, short of doing a reinstall?

regards, hardmath

---

### Post by LaRoza on 2007-12-27
I doubt you enabled the root account, so I imagine you are not familiar with sudo.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by hardmath on 2007-12-27
Thanks, but I have used sudo and gksudo before in Terminal.  Furthermore the applets that launch from the System -> Administration menu will invoke the administrative password prompt in Ubuntu, without any special action on the part of the user.

For example, I just ran Update Manager from the menu (one of six items that still remains there), and after the first run, a click on the Check button forced the invocation of the password prompt.  Instead of working behind the scenes with sudo, I get this error message:

[B]Failed to run /usr/sbin/synaptic '--hide-main-window' '--noninteractive' '--parent-window-id' '37748739' '--update-at-startup' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator.[/B]

There is the further clue that the Users and Groups applet has disappeared from my System -> Adminstration menu.  I know it was there before because I used it to create a desktop account for the friend who will use the machine.

regards, hardmath

---

### Post by The Cog on 2007-12-27
Sounds very odd. If you boot into recovery mode this logs you in as root, so you should be able to do what you need to. The command:
**adduser administrator admin**
will add admonistrator back into the admin group, which should give the sudo rights back.

---

### Post by LaRoza on 2007-12-27
> **The Cog said:**
> 
**adduser administrator admin**
will add admonistrator back into the admin group, which should give the sudo rights back.

+1 

Did you do something like run a GUI app with sudo instead of gksudo? I here that may cause such weird things

---

### Post by spiderbatdad on 2007-12-27
Not sure I understand what is going. Are you trying to access the user/groups menu from the account that lacks administrative privileges?

There is some good information in ```
man adduser
``` regarding what happens when passwd is used to set a password for the user.

---

### Post by hardmath on 2007-12-28
Before running the adduser command suggested by The Cog, I saw these properties:

```
id administrator
uid=1000(administrator) gid=1000(administrator) groups=1000(administrator)

```

After running the adduser command, I see:

```
id administrator
uid=1000(administrator) gid=1000(administrator) groups=1000(administrator),
 117(admin)

```

Here for comparison is how the properties look for an "admin" user set up during the install process on a different machine:

```
id chip
uid=1000(chip) gid=1000(chip) groups=1000(chip), 4(adm), 20(dialout), 24(cdrom),
 25(floppy), 29(audio), 30(dip), 44(video), 46(plugdev), 104(scanner), 112(netdev),
 113(lpadmin), 115(powerdev), 117(admin)

```

Note: I inserted some whitespace by hand into the terminal output above to make it wrap better.  

I'm pretty sure that I never ran any of the GUI apps from the command line before I noticed that user administrator had lost its root privileges.  The two applications I can recall running before that are the Update Manager, once I got the machine online after the initial install, and the Users and Groups application (to create the desktop user).

I've not tried to change the password for adminstrator since the initial installation, and the original password is still working.  As for the desktop user, I let her type one into the GUI app, and other than logging in to verify that it works, she's not used the machine.  I don't know that password and haven't tried to change it (or login/su to that account).

The installation was done last Friday, and the updates & user creation were done last Saturday (Dec. 22, 2007).  So the appearance of the problem is pretty recent.

regards, hardmath

---

### Post by hardmath on 2008-01-02
It was clear to me that the original Feisty Fawn installation had gotten clobbered somehow from the symptoms described above.  This was quite a minimal machine for Feisty, roughly 10 years old with it memory maxed out at the 256Kb minimum for Feisty.  I suspected that the arrangement of hard drives had played some role in the debacle, so I moved them around and tried reinstalling Feisty, but the installation (first with the alternate CD, then with the live CD) repeatedly failed.

So I dropped back and installed Dapper Drake.  It's been running quite solidly for the last five days.  Now the dilemma is that I need to install a dial-up modem for my friend, and the selection of modems available at retail outlets is pretty limited these days.  I settled on a Zoom USB external modem, which relies on Linuxant drivers.  And there's the rub -- they require a 2.6.20 kernel or better.  As best I can tell, Dapper only got to 2.6.15.

Thus I plan to push on to EdgyEft  with the gksu "update-manager -c" command. I'm setting this thread to solved and will submit a bug report if the incremental updates to my installation fail.

Thanks to all who replied; it was a good learning experience for me.

regards, hm

---

