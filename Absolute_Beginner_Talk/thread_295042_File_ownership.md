---
title: "File ownership"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by PsiKloPx on 2006-11-07
I downloaded a file (tar.gz) that I couldn't find with the Synaptics Package Manager.  I extracted it to the desktop.  My main account was the only one logged in (my son has an account).  Now I have a folder on my desktop that is "owned" by my son, and I can't delete it, or move it.  I've tried changing ownership with CHOWN (CD to Desktop, then 'chown root /foldername' but I get the message "No such file or directory"
On a side note I can try to install the program using ./build.pl but it errors out at "line 220".

I should mention - This is my first foray into Linux (using Kubuntu on an HP Pavilion 4400 laptop - dual booting with WinXP Home) This forum has been great; I have been able to solve all of my issues - including getting my wireless PCI card working - just by searching here.  But I didn't find anything that addresses my current issue.

Thanks!

---

### Post by CatKiller on 2006-11-07
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

You don't want that / in front of foldername: that tells it to look for a sub-directory of the root directory. You're also unlikely to want to chown it to root, unless your normal user account is called root, which would be a bad idea.

You also might like to check out these pages:
[RootSudo wiki page]("https://help.ubuntu.com/community/RootSudo")
[File Permissions in Ubuntu]("http://www.psychocats.net/ubuntu/permissions")

---

### Post by PsiKloPx on 2006-11-07
Thanx! My desktop is back to it's normal pristine emptiness!

---

