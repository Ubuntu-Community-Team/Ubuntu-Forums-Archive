---
title: "Wifi not working after 111 upgrades"
date: 2008-03-21
forum: Apple Intel Users
---

### Post by ThatGuyThere on 2008-03-21
I had installed the macbook pro wifi with these instructions ( [http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25) ). Then, I had realized that I had 111 updates waiting for me, and installed them all. Now, my wifi is borked :(. Anybody know a fix?

---

### Post by ThatGuyThere on 2008-03-21
Would undoing all of the stuff that I did to get my wifi to work, work? If so, can any of you provide the commands? (Just throwing out ideas that might help me :))

---

### Post by scottro on 2008-03-21
No, don't undo what you did. 
What happens here (and will happen anytime you see a howto that involves running make, using kernel-headers and the like) is that your kernel was upgraded and the program that made your driver work was built against a particular kernel.  One of the upgrades probably upgraded your kernel, so the driver no longer works--it might be looking for, say, /lib/modules/kernel-XYZ/files and now you have /lib/modules/kernel-XYZ.1.  (This is an oversimplification, but hopefully, you get the idea of what happened.)

So your best best is to (if you followed the instructions to extract into a directory in that howto) is to go into that directory if you still have it.  Then type

sudo make uninstall

(This might or might not be necessary, but it won't hurt and can help to avoid any conflicts.)
Whether you do that or not, afterwards, simply repeat the instructions that you followed before, making sure you have the problem linux-headers-$(uname -r).  The chances are that when the kernel was upgraded, they were too.  

Then, a reboot might or might not be necessary, but it should work again.

---

### Post by ThatGuyThere on 2008-03-21
It worked! THanks!

---

### Post by scottro on 2008-03-21
Glad it worked.   :)

---

### Post by cyberdork33 on 2008-03-21
This will likely occur everytime the kernel is updated unless you use only packages from the repository that would also be updated automatically.

---

