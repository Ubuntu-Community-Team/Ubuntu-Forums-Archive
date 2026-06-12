---
title: "novice user -- virtualbox upgrade"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by matt5ash on 2007-10-17
Hi 

Somehow, the Virutalbox update fails to work using 7.10 ubuntu ... it seems that some driver won't uninstall ?? during the update process (using the update manager)

this is the update:
virtualbox-ose-modules-2.6.22-14-server

after trying to update:
e:/var/cache/apt/archives/virtualbox-ose-modules-2.6.22-14-server_6_i386.deb:subprocess new pre-removal script returned error exit status 1

I kinda expect that this info is not complete enough to answer the question (how should I complete this update?) ... however, I'm not sure what info would be important ...

in any event, I have the following questions

1) is this the correct place to ask a question?

2) is the server version the correct version to use ?

3) how should I proceed ?

3.1) it is possible to keep the XP "computer" I've installed, or should I just start from the beginning again?

Thanks very much for your thoughts and directions

-mattl

---

### Post by Beggar on 2007-10-18
1) When in doubt, this is the place to ask a question, although with third party software like this you can also try the virtualbox forums.
2) Do you need it? For most situations plain virtualbox is just fine. For a home user, if your just going to be running virtualbox on your own computer, I dont really think its needed.
3 both) Really the vdi, virtual disk, that it creates, is whats important, not the "Computer" you create. You can safely delete the computer, then create another computer that points to that vdi, and everything will work fine. My recommendation is that you uninstall virtualbox, take note of any customized settings you had, then reinstall it. 

```
sudo apt-get install virtualbox
```

Then just create a new computer that points to your original vdi.

---

