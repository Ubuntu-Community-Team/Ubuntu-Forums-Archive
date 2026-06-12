---
title: "Owning files/being root question about FF"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by AmberBanana on 2007-11-15
I am dual booting Vista and Gutsy.  For the life of me I cannot remember how to get root on Ubuntu. What I want to do is copy my FF bookmarks.html file and replace the one in Ubuntu with it.  This should be easy.  If I recall, it has something to do with chown.  I tried several likely things to do, but got on the failboat.  I am sleep deprived as I installed Ubuntu early this morning.  Any tips?  Thanks.

---

### Post by Dr Small on 2007-11-15
If you login to Nautilus as Root (gksudo nautilus), you'll have full permissions to do it that way, or you could just:
```
sudo chown *user* file
```

---

### Post by taurus on 2007-11-15
Your personal bookmarks.html should go to ~/.mozilla/firefox/<numbers_letters>.default.  And since you are the owner of your own $HOME, you do not need to use sudo for that.

---

### Post by Dr Small on 2007-11-15
Yeah, taurus is right... I was wrong. You shouldn't need sudo for any of that.

---

### Post by AmberBanana on 2007-11-15
> **taurus said:**
> Your personal bookmarks.html should go to ~/.mozilla/firefox/<numbers_letters>.default.  And since you are the owner of your own $HOME, you do not need to use sudo for that.
OK, you lost me.  I can add new bookmarks in Ubuntu as the need arises.  Still, I have the problem of not knowing how to get root access to files that I definitely want to change (the options are greyed out).

---

### Post by taurus on 2007-11-15
What files do you want to access and what are the locations of those files?  Again, your $HOME should be owned by you so you can write to it anytime you want.  If you need to use sudo to write to your own $HOME, then there is something wrong with the permissions.

---

