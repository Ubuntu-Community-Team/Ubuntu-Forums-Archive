---
title: "Eeeek! WTF happened to my files?!"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by 4.9 on 2007-01-12
I installed Kubuntu Desktop through apt-get and well...

[IMG]http://img291.imageshack.us/img291/3628/screenshotps2.png[/IMG]

What do I do?!

---

### Post by aysiu on 2007-01-12
I think we need more details in order to help.

What's the problem exactly?

---

### Post by rai4shu2 on 2007-01-12
Is that really the root folder?

---

### Post by Frak on 2007-01-12
when you restarted, you did choose KDE in the sessions menu right? Hey what happened to all of your files...

---

### Post by ButteBlues on 2007-01-13
Hit "Control+H".

---

### Post by rai4shu2 on 2007-01-13
That's either a bug in Nautilus or your system is totally poofed.

---

### Post by Shatrat on 2007-01-13
Does KDEs file manager maybe hide anything you dont own by default?
Seems odd, and I dont remember it doing that back when I was a kde person.
(edit)
obviously its the file manager or something.  There's no way the system would even boot without /bin and /dev/ and /etc and so forth.

---

### Post by aysiu on 2007-01-13
Your filesystem has to be there... otherwise it couldn't be functioning without the /etc and /lib and /bin directories... right?

If you go to the command line and type ```
cd /
ls -a
``` what do you get?

---

### Post by msak007 on 2007-01-13
You're probably referring to the annoying "feature" that was included in Kubuntu Edgy. There's a file called ".hidden" in the root directory. You have 2 choices:

1. Edit the file and uncomment any folders you want to show up.
2. Delete the file completely. It won't harm your system, and will restore all the directories you are missing.

Needless to say this annoyed many, and will not be included in Feisty.

---

### Post by maddog39 on 2007-01-14
Your system files are just hidden, thats all. If they were all gone your system wouldnt even boot. :)

---

### Post by MkfIbK7a on 2007-01-14
that happend to me too press the button that looks like a pad of paper and pencil
type /path/of/file
e.g. /usr/bin/
it will show you that its still there

---

### Post by zerhacke on 2007-01-14
> **4.9 said:**
> I installed Kubuntu Desktop through apt-get and well...

What do I do?!

Log out of Gnome, and on the GDM window select SESSIONS and choose KDE.  Then log back in.

---

### Post by aysiu on 2007-01-14
> **zerhacke said:**
> Log out of Gnome, and on the GDM window select SESSIONS and choose KDE.  Then log back in.
I think the question was about where the files went, not how to log into KDE. I could be wrong.

---

### Post by ButteBlues on 2007-01-14
> **aysiu said:**
> I think the question was about where the files went, not how to log into KDE. I could be wrong.
Enable "View Hidden Files" through Ctrl+H in Nautilus or through the View menu in Kubuntu.

---

### Post by pebo on 2007-01-14
Under the root filesystem there is a file, .hidden, which lists the missing folders. If you do a 
```
sudo nano /.hidden
```
you can remove the folders that you want to be able to see from the list.
hth
edit: sorry missed msak007's post

---

### Post by msak007 on 2007-01-14
Yea I think a lot of people are missing the point of this post. Believe me, the files are not hidden in the traditional sense where you can just enable hidden files and they'll be restored. It's that .hidden file, which in itself is hidden, that hides everything. Enabling hidden files will reveal that file, but you still have to edit / delete it to restore the missing directories. The rationale behind this was that most people don't need or want to see any directories aside from home and media, so they hid them. The problem is that this wasn't clearly documented anywhere and left many confused as to how to view the files if they need to in Nautilus / Konqueror / whatever, and you could only view them through the terminal if you want to.

---

### Post by zerhacke on 2007-01-14
> **aysiu said:**
> I think the question was about where the files went, not how to log into KDE. I could be wrong.

Ahh, judging from the topic you're probably right.  It would seem the part about installing KDE was extraneous.

---

### Post by kinematic on 2007-01-14
> **msak007 said:**
> Yea I think a lot of people are missing the point of this post. Believe me, the files are not hidden in the traditional sense where you can just enable hidden files and they'll be restored. It's that .hidden file, which in itself is hidden, that hides everything. Enabling hidden files will reveal that file, but you still have to edit / delete it to restore the missing directories. The rationale behind this was that most people don't need or want to see any directories aside from home and media, so they hid them. The problem is that this wasn't clearly documented anywhere and left many confused as to how to view the files if they need to in Nautilus / Konqueror / whatever, and you could only view them through the terminal if you want to.

hmmm...taking the mac route.
you don't want to see this....you don't need to see this....it's best if you don't see this....we decide what you need to see.

---

### Post by aysiu on 2007-01-23
Apparently, the hidden files/folders are defined in this file:
/etc/kubuntu-default-settings/hidden-root

If you just get rid of that file, all the folders come back as normal (not hidden): ```
cd /etc/kubuntu-default-settings
sudo mv hidden-root hidden-root.old
```

---

