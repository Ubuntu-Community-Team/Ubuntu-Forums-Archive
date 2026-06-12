---
title: "Default USERNAME"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by LAF4U on 2007-04-18
Hi Folks,

Ubuntu is now asking me to enter a USERNAME and PASSWORD.

What is the DEFAULT USERNAME and PASSWORD that I can use, and UBUNTU will recongnize?

Cheers

---

### Post by Cypher on 2007-04-18
I don't believe there is a default username/password. During installation of your Ubuntu system you were prompted to create a user that was also the administrator. Any subsequent users added were just regular users.

If you didn't install Ubuntu, you might want to contact the person who did..

Regards

---

### Post by LAF4U on 2007-04-18
> **Cypher said:**
> I don't believe there is a default username/password. During installation of your Ubuntu system you were prompted to create a user that was also the administrator. Any subsequent users added were just regular users.

If you didn't install Ubuntu, you might want to contact the person who did..

Regards

Well, I've put UBUNTU on my USB key. So it's booting off of my key.

I didn't create any users during instalation.

Thanks.

---

### Post by Cypher on 2007-04-18
Which version of Ubuntu was this and did you perform an installation on the USB key or put it on there by some other means?

---

### Post by szymon_g on 2007-04-18
or you can run ubuntu in recovery mode:
to do this you have to (on the beginning of starting computer) select ubuntu-something-recovery options (or just push 'esc' key if options aren't showed).
now you should be logged as root.
the easiest way is to make this commend :

ls /home/

it will show you a names of users (by default users have got theires main folder on /home partitnion: the main folder has the same name as user)

to change an users password, just type :

passwd user_name users_new_password

---

### Post by Outrunner on 2007-04-18
Maybe you installed the OEM version. if that's that's the case then I think the username is oem with no password(not sure though)

---

### Post by Seisen on 2007-04-18
It should ask you when you first boot it up what you want for username and password if its oem.

---

### Post by mcduck on 2007-04-18
> **Outrunner said:**
> Maybe you installed the OEM version. if that's that's the case then I think the username is oem with no password(not sure though)

even in the OEM install the installer asks to create a password..

(and if the OEM install is not completed by running 'sudo oem-config-prepare' it will never create the real user for the machine and 'oem' user is not removed)

---

### Post by LAF4U on 2007-04-18
> **Cypher said:**
> Which version of Ubuntu was this and did you perform an installation on the USB key or put it on there by some other means?

I followed these instructions:

[http://www.debuntu.org/book/export/html/160](http://www.debuntu.org/book/export/html/160)

Is this the right way to do it?

---

### Post by Cypher on 2007-04-18
OK..those instructions essentially replicate a Live CD that automatically boots up to the full Desktop. That being said, did you use at least Ubuntu 6.10 Edgy Eft as your source? 5.10 Breezy wasn't a live CD.

Regards

---

### Post by LAF4U on 2007-04-18
> **Cypher said:**
> OK..those instructions essentially replicate a Live CD that automatically boots up to the full Desktop. That being said, did you use at least Ubuntu 6.10 Edgy Eft as your source? 5.10 Breezy wasn't a live CD.

Regards

I used Edgy 6.10 as my source. That said, here's the error that gets written to the session-errors file:

gnome-session: 6706: WARNING: Unable to lock ICE authority file: /home/ubuntu/.ICEauthority

Does that ring a bell?

---

