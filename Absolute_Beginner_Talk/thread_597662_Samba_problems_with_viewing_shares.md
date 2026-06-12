---
title: "Samba problems with viewing shares"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by eapache on 2007-10-30
I just installed gutsy, and I've been having trouble with seeing my windows shares. My setup has two XP pcs and one running Gutsy (all behind a router), so I know that it isn't a problem on the windows end. At first, I could see the computers and it would list the shared folders on them, but when I went to browse one of the shares, it would say 'cannot display contents of folder'. Also, in the properties window, it would say 'unreadable' for everything but the name.

I did some research and installed the samba server on the off-chance that it was somehow required to view them as well, but that didn't work. After more googling, I tried installing smbfs, which actually made the problem worse. Now I could not see the computers at all. The only thing in Places>Network was the Windows Network folder which was empty. Uninstalling smbfs did not fix this.

I have just discovered however, that going to smb:///ipaddres does display the XP computer's shared folders. When opening them now, I get a password prompt. After submitting a blank password, it gives me the same error message as it did originally. So I have two basic problems:

1. Why are the XP computers no longer showing up in the Network location in Nautilus even though samba can see them when pointed to the ip address?
2. Why does samba ask for a password and reject a blank one, when neither XP computer has a password set up (I can access the shares from one XP to another without entering any password)?

---

### Post by eapache on 2007-10-30
Update:

Problem one is now fixed, it just needed a reboot for some reason.

Problem two still stands on one of the computers, but not the other... this leads me to believe that I did in fact set up some sort of password on the computer that I'm having trouble with, perhaps as a side-effect of something else. Does anyone know where in XP that sort of option is so I can turn it off?

---

