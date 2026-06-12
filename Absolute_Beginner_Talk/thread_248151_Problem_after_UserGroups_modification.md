---
title: "Problem after User/Groups modification"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by TheHudson on 2006-08-31
Hello, I'm fairly new so please bear with me.

I am using Kubuntu, I wanted to set myself as root under K>System Settings>Users & Groups, so after selecting my name and entering administrator mode, I changed my primary group to "root". Afterwards it told me to reboot/re-login and now whenever I try to enter administrator mode again, I get an "Error - KDE su : Su returned with an error." message.

Is this recoverable? Thank you.

[Edit]: It seems this problem extends to a lot more than initially thought, even attempting to open "Add/Remove Programs" gives me this error.

---

### Post by kidders on 2006-09-01
Hmm... Habitually using the root account, or being a member of the root group is **VERY** strongly discouraged in Linuxy systems. Without harping on about it, it's the one sure way to defeat Linux's lovely security model that keeps it so safe from viruses, and cause yourself all kinds of other headaches.

I imagine what you'd like to do is put everything back the way it was, eh? Try this:

[LIST=1]
[*]Start with your usual graphical login screen, where you normally enter your username/password.
[*]Hit CTRL+ALT+F1 to switch to a text-based console.
[*]Log in using the root account.
[*]Type "usermod" and take a look at the help text, so you can get a feel for the kind of thing it does.
[/LIST]

By default, Ubuntu uses a "private group" scheme, where each user is the sole member of his own personal group, simplifying permissions management for beginners. Restore this arrangement with usermod, remembering to examine the permissions of files you may have created since you made the change.

[LIST=5]
[*]Type "usermod -g username username".
[*]Now, just to eliminate the possibility of permissions-related issues messing up your KDE/Gnome sessions, examine your home directory. Type "ls -al ~|less" and look for files that don't have your username in both the user and group columns of the output.
[*]If you find some, tweak them with "chown username:username filename"
[*]Now check your /tmp directory for files that have similar-looking permissions errors, such as "ksocket-username" or "kde-username". I'm not 100% confident it's completely safe to delete these, so put the ownership back the way it should be.
[/LIST]

Now everything should be back to normal.

[LIST=9]
[*]Hit CTRL+D to log out.
[*]Now hit CTRL+ALT+F7 to switch back to the graphical display and, to be safe, hit CTRL+ALT+BACKSPACE to force the X server to restart.
[*]Log in as normal.
[/LIST]

If you *reallllly* must give yourself a "root" membership, make it one of your supplemental groups, not the primary one. If you want my advice though, don't do either.

It's quite possible you did this in the first place, because you got tired of constantly typing your password every time you wanted to make the slightest tweak. Don't worry though ... as time passes, the need to do this diminishes. Something worth investigating is a file called /etc/sudoers though. It controls who gets elevated access to what. It is possible to use it to grant yourself root privileges on demand (ie you must type sudo), but side-step the password check.

I hope this helps!

---

