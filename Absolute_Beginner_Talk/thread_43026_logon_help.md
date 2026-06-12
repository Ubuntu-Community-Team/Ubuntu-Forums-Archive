---
title: "logon help"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by wpyung on 2005-06-20
I just installed Ubuntu but ignored the option to add a username and password.

I have worked on other systems where there is always a root.

How can I logon ?

I want to setup the system for network logons - thats why I didn't add a user ...

---

### Post by intangible on 2005-06-20
You created a system without any user accounts whatsoever?  That is odd :D.

You should look into using the system the "Ubuntu Way" using normal user accounts and sudo, but if you want to use the root account instead, here's how to enable the root account:

1. Boot from a Linux CD, get to a prompt, make sure to change to the root account (on a Ubuntu Live CD, that would be **sudo sh** to get to a root account.
2. **mkdir /mydrive**
3. **mount /dev/hda1 /mydrive** (where hda1 is your root partition)
4. **chroot /mydrive**
5. **passwd root** Enter the new root password
6. Log Out of everything, reboot and the root account will now have a password.

Good Hunting!

---

### Post by wpyung on 2005-06-21
Thanks

I reinstalled again - as the quickest way around.

I'm now looking at a doc ActiveDirectoryWinnbindHowto

The steps in it don't seem to work 
apt-get hasn't heard of winbind or krb5-user

Any idea where I get the correct instructions ?
Or how to install Winbind ?

Thanks

---

### Post by intangible on 2005-06-21
You'll have to enable the universe repositories to get winbind: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

I have set up both a Debian box and a Ubuntu box with winbind authentication, wasn't too difficult.  Here's a howto: [https://wiki.ubuntu.com//ActiveDirectoryWinbindHowto](https://wiki.ubuntu.com//ActiveDirectoryWinbindHowto)

Have Fun.

---

