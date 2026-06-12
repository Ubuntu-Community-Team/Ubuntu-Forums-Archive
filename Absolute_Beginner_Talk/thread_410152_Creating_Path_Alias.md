---
title: "Creating Path Alias?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by holmb101 on 2007-04-15
I would like to transfer files to my windows partition, but I don't want to type out the full path each time.  Is there a way to create an alias for a path to a folder? 

I want to do something like this:

windesk = /media/sda2/Documents\ and \Settings/User/Desktop

---

### Post by lapsey on 2007-04-15
yes.

ln -s "/media/sda2/Documents and Settings/User/Desktop" ~/windesk

that will put a shortcut / link / alias to the folder in your home directory.

---

### Post by holmb101 on 2007-04-15
Thanks.  That's exactly what I wanted.

---

