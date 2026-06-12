---
title: "GNOME &amp; Active Directory"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by 919Guy on 2007-08-02
I've searched high and low, and can't seem to find an answer to this.  I've performed the steps located [here]("http://ubuntuforums.org/showthread.php?t=91510"), and while I can log in via SSH using AD credentials, I cannot log into GNOME.  Is this expected behavior?  If not, what have I done wrong?  If so, let me know.  Thanks in advance.

---

### Post by Raineer on 2007-08-02
I'm going to play the kn00b here because I don't have any experience with Active Directory... However when you state you can't "log into GNOME" do you mean the GUI screen?

Typically this requires some sort of VNC program to login remotely.  SSH is basically text-only.

If I'm way off just ignore this, I'm just kinda guessing at your post.

---

### Post by 919Guy on 2007-08-02
Yes, I mean that I can't log into the GUI screen *locally*.  I'm sitting at the box.

However, I just found something, and I'm not sure what to think....

I edited /etc/pam.d/gdm, and included the line:
              > auth       sufficient       pam_winbind.so

Now, I can log in with AD credentials and get to the desktop.  This is as far as my testing has gone......

---

