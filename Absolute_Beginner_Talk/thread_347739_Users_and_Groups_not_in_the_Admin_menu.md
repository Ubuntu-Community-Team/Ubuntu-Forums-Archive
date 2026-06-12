---
title: "Users and Groups not in the Admin menu"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Bill_Ymr on 2007-01-27
:confused: Bear with me, folks.  I work in a Windows shop, and am extremely new to Ubuntu; but it came highly recommended from a friend.

After installing 6.10 and logging on as OEM, I had 110 updates.  I went ahead and installed them.  After rebooting and logging on as OEM again, I went to System-->Administration with all intentions of clicking on Users and Groups, but it is not there.  The last item in the menu is Update Manager.

I have searched all of the documentation I could find, but can't find how to turn on that menu item.  I am not skilled enough to try adding users and/or groups from a terminal session on my own.

I would greatly appreciate any help or guidance anyone can provide.

---

### Post by taurus on 2007-01-27
You need to run this command to create a regular account that you will use from now on.  Not suppose to use oem more than one session.

```
sudo oem-config-prepare
```

---

### Post by Bill_Ymr on 2007-01-27
Thanks, Taurus, but it has appeared again.  The only thing I did differently was change the permissions on a document.

---

### Post by chalex on 2007-01-27
What do you mean by OEM?  Is that the account you created during the install?

Adding accounts from the command line is pretty easy: `sudo useradd -m username` then `sudo passwd username`, and enter the password at the prompt.

---

### Post by taurus on 2007-01-27
You changed permissions on what document?  Better be real careful when you change permissions to system files because you change the wrong ones, you will break your machine.

---

### Post by taurus on 2007-01-27
> **chalex said:**
> What do you mean by OEM?  Is that the account you created during the install?

The oem account comes from the alternate CD!

---

### Post by Bill_Ymr on 2007-01-28
Trust me, I am not changing any system files.  This was a documentation file that I wanted everyone to be able to read, but not edit.  After setting those file permissions on the document, Users and Groups were in the menu.

I now have another issue that perhaps I should start a new thread.  I no longer have Shut Down or Restart in my Quit menu.  On the top, I have Log Out, Lock Screen, and Switch User.  On the bottom, I have just Sleep and Hibernate.  :confused:

---

### Post by Bill_Ymr on 2007-01-28
I guess all I have to do is post something to this forum and Ubuntu fixes itself.  If I could just find a way to get my truck on this forum...

:lolflag:

Earlier, I had turned off "Show actions" on the Login Window.  What that has to do with the Quit menu I can't figure out.  After turning that back on, Shutdown and Restart are back!

I'm beginning to think that a re-install is in order.  Or an exorcism!!

---

