---
title: "Getting files from Ubuntu box  using Windows?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by albs on 2007-03-14
Hi everyone, n00b here!

I've been trying to set up a mixed network, and can access files on Windows boxes using my Ubuntu box, all good.

I can also see my Ubuntu box from Windows, on "show all computers on your workgroup".

But I'd click on my Ubuntu box, and would be asked for a username and password.  Fair enough.  I enter my username/password as if I was logging into my Ubuntu box, but Windows will hand me back the authentication window, as if it was an authentication error.

What do I have to do on either the Windows or Ubuntu side?

---

### Post by irwa82 on 2007-03-14
Hi,

I am a command line guy so sorry if you prefer gui.

The problem is probably that you don't have a samba user created. In a shell run 'smbpasswd -a username' then give it a password. Samba updates its config every minute but to be paranoid you can restart it with /etc/init.d/smb restart (if its not smb it will be samba i am not if front of ubuntu right now).

Kind Regards,
Anthony Irwin

---

