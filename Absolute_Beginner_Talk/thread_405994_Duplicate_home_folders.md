---
title: "Duplicate home folders"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by e6626550w on 2007-04-10
I noticed that in "places" in the menu items, that my 'home folder' now appears twice. This just seemed to happen for no reason that I can figure out. Also the file in both of the folders... menu.lst has the lock icon on it. 

2 questions at least.... 1.... how do I get rid of one of the folders and ....2...how do I get the lock symbol off of the file? 

thank you,
eileen...

---

### Post by bodhi.zazen on 2007-04-10
I am not sure why you have a duplicate home folder.

The lock is a permissions issue.

See here for information on permissions : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Perhaps if you log out and back in your second home folder will correct itself, I do not know.

---

### Post by e6626550w on 2007-04-10
Thanks for the link. I was able to log in as 'root' and get the permissions changed but the folder is still there. It is more of a cosmetic issue than anything else I believe, but I'd like to figure out how to remove it. I'm obviously quite new with Linux and the experience after years of only clicking a mouse is both enjoyable and at times frustrating. This is a good example of the frustrating part. 

eileen...

---

### Post by Patrick K on 2007-04-10
Do you actually have two /home directories or is the extra only in the places menu?

If it is only in the places menu, it could be you somehow added it to your bookmarks. Open Nautilus and open the bookmarks menu. If it is there you can edit the bookmarks and remove it. That will remove it from the places menu. 

If you actually have two /home dir, I'm not sure what you can do. I suggest opening /etc/fstab and seeing if there are two /home entries there.

---

### Post by e6626550w on 2007-04-10
Thanks Pat.... that did it. It was apparently as you said a 'bookmark'. 

Eileen....

---

