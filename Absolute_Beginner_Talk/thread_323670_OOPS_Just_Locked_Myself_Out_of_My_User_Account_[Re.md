---
title: "OOPS: Just Locked Myself Out of My User Account [Resolved]"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by E.T.Smith on 2006-12-22
I am new to to Ubuntu and enjoying it so far, but while trying to install some fonts (a matter I'll deal with in another thread) I have locked myself out of root permissions. The problem seems to be that I tried to set things up as I was used to from Fedora, giving all the administator permissions to the root account then denying them to my common account, with the expectation that if I needed to make any serious system modifications I'd login as root. Only after the deed was done did I discover that Ub' doesn't work that way and won't allow me to login as root. So I've just read up on this whole "sudo" approach, I understand how things are supposed to be done now, but the fact remains that as of now I can't make any administrative changes from my common login, including changing the settings to let me log in as root in order to fix the problem. Little help, please.

---

### Post by taurus on 2006-12-22
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
groups
```

---

### Post by E.T.Smith on 2006-12-22
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
groups
```

cut and pasted directly:

```
etsmith adm dialout fax cdrom floppy audio dip video plugdev lpadmin scanner
etsmith@etsmith-desktop:~$ 
```

When I attempt to go "System -> Administration -> Users and Groups", (where I made the modifications in the first place) I'm told I do not have that permission.

---

### Post by Tomosaur on 2006-12-22
Since you appear to have experience with linux anyway, you can just boot into recovery mode, where you get logged in as root automatically. You should be able to fix everything from there :)

---

### Post by E.T.Smith on 2006-12-22
> **Tomosaur said:**
> Since you appear to have experience with linux anyway, you can just boot into recovery mode, where you get logged in as root automatically. You should be able to fix everything from there :)

I'm not nearly as experienced as I should be by now. For instance, I almost strickly operate via GUI; the terminal is a strange and hostile country to me. How do I log into this recovery mode, and will there be any consequences (recent files or modifications lost)?

---

### Post by steve.horsley on 2006-12-22
Recovery mode is one of the options the bootloader gives you. It drops you in a command prompt as root. Perhaps easiest is the command
**adduser etsmith admin**
which will add you back into the admin group, which should allow you to use sudo in future. Reboot again to test if it worked.

If it didn't work, go back to recovery mode and use this command:
**passwd**
to set the root password, and then you can at least use **su** from your normal login.

---

### Post by Tomosaur on 2006-12-22
You can log into recovery mode by rebooting your machine. When grub loads, you should notice two entires for each kernel you have installed. One of them will say 'recovery mode' at the end. You just select that to boot, and you will log in as root automatically. If you don't know what you're supposed to do there, you may want to go looking around on the web first to see what you're going to have to do to get stuff working. Essentially what you'll need to do is re-set your normal account, fix any broken permissions etc etc. Remember - the 'man' command is your friend if you don't know what a command does :P

---

### Post by E.T.Smith on 2006-12-22
What is a "grub"? I gather you're referring to some sort of command line option. However, when I boot my system, it goes straight to the login screen, no textual interim of any kind. If there any way to sort this out in the Gnome environment? I'll try becoming su in the terminal, entering the suggested command, then rebooting...

---

### Post by E.T.Smith on 2006-12-22
...and that seems to have worked. Also, I am mistaken about there being no command line interim before the login screen, it just flickers by too quickly for me to have ever noticed it before. Thank you all for your help.

---

### Post by sailingboarder on 2006-12-22
for future reference,
grub is a bootloader
if you are duel booting, or even if you only have one os, grup decides which os to load
u usually won't notice it cause it will automatically load ubuntu (or wutever os u have set to default)

---

### Post by taurus on 2006-12-22
> **sailingboarder said:**
> for future reference,
grub is a bootloader
if you are duel booting, or even if you only have one os, grup decides which os to load
u usually won't notice it cause it will automatically load ubuntu (or wutever os u have set to default)

The default time out is 3 seconds...

---

