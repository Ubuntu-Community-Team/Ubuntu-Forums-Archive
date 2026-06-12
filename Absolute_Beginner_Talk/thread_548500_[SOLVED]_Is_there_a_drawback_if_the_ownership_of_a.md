---
title: "[SOLVED] Is there a drawback if the ownership of a mount-point changes?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by kimabrandt on 2007-09-11
Is there any drawback if mount-points such as /media/*, /mnt/*, ... are getting the ownership of a normal user? That is when a device is mounted in its mount-point and then changing the ownership of the mount-point to something other then root.

Could it be that if the ownership is other then root a device could more easily getting corrupted?

Just a feeling.

---

### Post by southernman on 2007-09-11
Don't take my word as gospel, but it's just my feeling on the matter which you've posed here...

I wouldn't do it myself.

I am more curious though, why would you need to do this?

---

### Post by reckless2k2 on 2007-09-11
are you talking about something you are setting up to mount in those areas? if it's to a network share than you have to do some tweaking especially using smbfs or cifs in order for normal users to have r/w permissions.

---

### Post by kimabrandt on 2007-09-11
It's nothing I want to do rather get some information if there are issues by changing owner/group/permissions of a moint-point of a mounted device.

To clearify:

There are many posts[1] which deal with changing file owner, group and permissions of a usb-device to allow a normal user to read/write on the root of that device (e.g. /media/disk). All threads talk about using `chown' on the mount-point of a mounted device to allow users rw acces.

I just have the question: Is there a reason not to do so?

[1] [http://ubuntuforums.org/search.php?do=process&query=usb+disk+chown+ext3&s=&do=process&forumchoice%5B%5D=&childforums=1&exactname=1&op=](http://ubuntuforums.org/search.php?do=process&query=usb+disk+chown+ext3&s=&do=process&forumchoice%5B%5D=&childforums=1&exactname=1&op=)

---

### Post by vanadium on 2007-09-11
Technically, it is not at all a problem to change ownership of a mount point. There is no drawback. You are free to do it.

However, in my opinion, it is not tidy organisation. In my opinion, mount points (for non-removable devices) are a matter of the system administrator, and a user should not have to deal with mount points. My preference is to leave the mount point to the root, and then create directories on the mounted drive and give ownership of the directories to the user. To make that directory available straight from within their home directory, you can create (as root) a symbolic link there. This way, the user has all his data under his home directory.

An exception is removable devices. That is handled automatically by Ubunu by mount points in /media that are indeed owned by the current user.

---

### Post by kimabrandt on 2007-09-11
That answered my question, thank you vanadium.

---

