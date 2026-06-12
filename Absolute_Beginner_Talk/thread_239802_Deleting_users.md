---
title: "Deleting users"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by NorseDude on 2006-08-19
I often open the same programs all the time (mainly AbiWord with my current novel and Xmms), so I created a user called "Quick start" that opened all of that every time I logged it. Then after a while I decided to delete the user since I didn't need it anymore, but no such luck. I went to the Adminstrator -> Users or whatever it's called and deleted Quickstart, but nothing really happened. I mean it didn't give me an error message or anything, so in theory the user is no more. But the login screen tells me Quickstart is still around, and the home folder is still around.

And by the way, how can I let two users share my music files? I have them currently stored in the home folder as I can't seem to place them anywhere else.

---

### Post by taurus on 2006-08-19
Make sure you don't have it start in the session in System -> Preferences -> Session -> Startup Program.

If you want to share stuff in your home directory with others, you need to set the permission to that as

```

chmod 755 ~

```
Now, everyone can read and execute stuff in your home directory.

---

### Post by steve.horsley on 2006-08-20
Deleting the user doesn't delete the user's home folder. Delete that with:
**sudo rm -rf /home/quickstart**

I believe that it is normal to allow others to see inside your home directory, so its permissions would be 755 or drwxr-xr-x. You can check this with:
**ls -ld ~**
This would allow anyone to read inside your home directory. If you prefer some directories to be more private, you can set those directories to 700 (drwx------) to keep prying eyes out.

The easiest way to understand the permissions is to right-click on the directory in question with nautilus and look at the permissions.

If you prefer to keep your whole directory private, you can change its permissions to 700 but then you will have to find somewhere else to keep your shared music files. Create a /shared directory perhaps, where anone can write anything. But /tmp is ideal for that - anyone can write there, but they can't delete each other's stuff.

---

### Post by NorseDude on 2006-08-20
Thanks.

---

