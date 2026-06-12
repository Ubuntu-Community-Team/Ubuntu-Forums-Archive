---
title: "VMware Server - doesn't want to use my hard drives"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by OtrMan on 2006-06-30
I have installed a few programs in my "virtual Windows" in VMware server beta,  and they seem to run properly.  I can even use my Maxtor one touch USB drive with VMware.  Can anyone tell me how to get VMware to recognize my normal hard drives?  I have tried adding them to the settings but the virtual machine won't recognize them.  It says I don't have the proper permissions.  I have tried starting with sudo but the results were the same.
A virtual machine isn't of much use if it's stuck in it's own little "virtual world".  I need to have it access partitions that a normal Windows installation can.
Thanks.

---

### Post by scxtt on 2006-06-30
AFAIK (meaning i haven't tried myself) you can't "load" your physical disks into a VM ... but you can add them as network drives via samba [ which i have done and use ] ...

---

### Post by OtrMan on 2006-07-01
Thanks for the samba suggestion.  I've downloaded the file and docs.  From what I've read so far it might be the ideal solution.  I'll let you know how it turns out.[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)
:D

---

### Post by OtrMan on 2006-07-01
Thanks scxtt for suggesting samba.  That looks like the best way to access my hard drives.  I have spent most of the day trying to get samba to run.  I haven't had any success.  Swat won't even run.  I have been going through the docs and some online stuff but nothing works for me.  I'll have to wait until someone in these forums figures it out.

These forums have provided a lot of help for me.  I don't post very often but I do appreciate the helpful proceedures others post.

(networking should NOT be so hard to set up)
famous last words?

---

### Post by scxtt on 2006-07-01
what are you doing exactly to load an ubuntu samba share in XP?  and what packages have you installed?

---

### Post by Mr Potter on 2008-01-25
The best toutorial for setting up samba I know of can be found here:


[http://www.youtube.com/watch?v=Ad17kma8rNM&feature=related](http://www.youtube.com/watch?v=Ad17kma8rNM&feature=related)

the instructions can be used with Fisty or Gutsy...not sure about older.

---

