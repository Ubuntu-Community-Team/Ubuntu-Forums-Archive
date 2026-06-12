---
title: "Shared folders in 6.10 edgy-what's the password?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-29
I've been trying to get the shared folder option working over ethernet. So I downloaded
the samba package and installed it.
Now I see the shared folder in my windows network neghborhood but I get asked for
a password. I'm not sure what the password is. It isn't my user password because it
won't take that. I don't recall setting any other passwords.

Does any one know what password it is asking for and where to set it?
This is probably obvious but I can't find it.
Thanks

---

### Post by freebeer on 2007-03-29
Are you accessing the share from Windows?  My Windows box prompts me for both a user name and password.  I use the user name of an account on the Linux box and its password.  It also might be worth mentioning that Linux is case sensitive.

---

### Post by linuxjerk on 2007-03-29
No it just shows me a path to the folder that is shared and the only box I can fill
in is password.
Yes I know it's case sensitive. I enter it just the same as when I log onto linux.
There are no other passwords I have set that I know of.

---

### Post by linuxjerk on 2007-03-29
No one knows what this password could be?

---

### Post by dannyboy79 on 2007-03-29
you have to add a samba user.

sudo smbpasswd -a username

then enter the password for sudo, then enter the password you want to use from windows. this should do it.

---

### Post by linuxjerk on 2007-03-29
Thanks dannyboy79
That did it. Thank God someone around here know what their doing.

---

### Post by cowlip on 2007-03-29
smbpassword is a nasty thing to do to new users, and I think Ubuntu should include a graphic Samba tool to add users and configure Samba, like Red Hat does.  Comment on this bug if this thing stopped you from liking Ubuntu:   [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067)

---

### Post by dannyboy79 on 2007-03-30
I don't feel this is a bug at all. the default security for samba is "user". Therefor you want to setup your samba server or connect to it you need to add a user plain and simple. Now if you want some1 to create a gui to make this easier to do than maybe you should try out swat, it's already been designed. What they should do is just make swat easier to enable in Ubuntu since now it's not that easy at all. I tired to use swat but just ended up back in a terminal and gedit/mousepad. What about webmin? does webmin help setup samba and sharing? Doing new things require you to learn something, you chose to come to linux, you chose to share files with windows by installing samba, you need to read about samba and how to get it to work. Those are my feelings. Should ubuntu make it a little easier to configre shares, YES, I agree but I don't think the current "way" is a bug.

---

