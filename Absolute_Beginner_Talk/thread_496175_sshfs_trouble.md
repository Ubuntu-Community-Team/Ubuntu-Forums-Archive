---
title: "sshfs trouble"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2007-07-08
Hi All:

I've successfully used crazymonkey's howto on using sshfs to mount remote directories ( [http://ubuntuforums.org/showthread.php?t=275856]("http://ubuntuforums.org/showthread.php?t=275856") ).

It is supposed to be quite simple like this:

sshfs username@ipaddress:/remote_directory_path_hame /local_mountpoint

However, when I rebooted one of my machines and used sshfs again, I got the message: "remote host has disconnected" and the remote filesystem would not mount /remote_directory_path_hame.

What should I do? What did I do wrong?

Many thanks again Ubuntu community!
Phil Smith
Duluth, GA

---

### Post by eternalsword on 2007-07-08
did you unmount locally before rebooting the remote machine?  If not did you try unmounting after rebooting the remote machine but before attempting to mount again?

---

### Post by Old Jimma on 2007-07-09
Thanks for your reply, Eternasword:

I did not umount local_mountpoint. However, when I did a /umount local_mountpoint this morning, the local machine gave the message: "/local_mountpoint not mounted according to mtab."

Then, I tried

sshfs username@ipaddress:/local_directory_path_name /local_mountpoint I still get the message, "remote host has disconnected."

Any further help you can offer will be greatly appreciated!

Thanks,
Phil Smith
Duluth, GA

---

### Post by monkeyking on 2007-07-12
can you ssh the normal way?

---

### Post by Old Jimma on 2007-07-13
Nope.

---

### Post by monkeyking on 2007-07-16
well sshfs depends on ssh,
so you set up a proper ssh server on your machine.

Or actually you should always set up a ssh server.

Install a ssh server,
I think it's called open ssh server and open ssh client.

Use apt-get or something.

Tjeck afterwards if you can login

---

