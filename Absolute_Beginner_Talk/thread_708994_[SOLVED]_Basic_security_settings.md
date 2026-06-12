---
title: "[SOLVED] Basic security settings"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2008-02-27
[FONT="Comic Sans MS"]Hi guys, just saw this site - [COLOR="Red"]http://www.itsecurity.com/features/ubuntu-secure-install-resource/[/COLOR]
and was wondering about the quality of the advice there.
Specifically re this;> [/FONT]
[I][FONT="Century Gothic"]Getting Started 
Surprisingly, many new Ubuntu users fail to take the most basic steps toward* securing their install, even when they know better. Thankfully, the list of critical changes isn't long. Making modifications may not excite you as much as, say, adding a whole new security program, but these simple changes will go a long way to closing up Ubuntu's security weaknesses.
Modifying Default Settings
The first set of basic critical changes requires you to modify three insecure default system settings:
Reconfiguring shared memory
Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:
tmpfs /dev/shm tmpfs defaults,ro 0 0 
Disabling SSH root login
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:
PermitRootLogin yes
to
PermitRootLogin no
Limiting access to the "su" program
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:
sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su[/FONT][/I]

[FONT="Comic Sans MS"]I assume the default settings are done that way for a good reason. If I was to make these changes what other effects might happen?[/FONT]

---

### Post by yabbadabbadont on 2008-02-27
If I remember correctly, (it's been a while since I used ubuntu), changing the /dev/shm permissions rendered the system unusable.  Since sshd is not running by default, disabling root logins through it are not really necessary, but still a good idea.  (just in case)  Also, only the first created user on the system is a member of the admin group, so even if others can run those commands, they can't do anything with them.

---

### Post by PeterJS on 2008-02-27
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi guys, just saw this site - [COLOR="Red"]http://www.itsecurity.com/features/ubuntu-secure-install-resource/[/COLOR]
and was wondering about the quality of the advice there.
Specifically re this;

[FONT="Comic Sans MS"]I assume the default settings are done that way for a good reason. If I was to make these changes what other effects might happen?[/FONT]

The defaults are good, Ubuntu takes a more moderate approach to security, it takes work to make linux insecure, but there are still trade off between ease and paranoia.

> 
Modifying Default Settings
The first set of basic critical changes requires you to modify three insecure default system settings:
Reconfiguring shared memory
Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:
tmpfs /dev/shm tmpfs defaults,ro 0 0

Not sure what version this was written for but the default in gutsy is to use RAM for shared memory, so this one's already done.
> 
Disabling SSH root login
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:
PermitRootLogin yes
to
PermitRootLogin no

I can see this being applicable in a server environment, but on your average desktop sshd won't be installed so there's no sense in changing the configuration on something that isn't installed.
> 
Limiting access to the "su" program
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:
sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su

This is reasonable, non-admin users can have legitimate uses for su, but the more access untrusted users have the more vectors for attack you're open to. So it comes down to paranoia vs need and convince, if you have a need for non admin user that needs access to multiple accounts leave it as is, if not, it can't jurt to err on the side of caution.

---

### Post by carloslosgrande on 2008-02-27
[FONT="Comic Sans MS"]Yabba and Pete, thanks very much, that was just what I wanted to know. I don't have ssh installed and I'm the only one using this machine.[/FONT]

---

