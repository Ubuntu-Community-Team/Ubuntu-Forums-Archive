---
title: "Startup screen"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by BeeRad on 2006-10-31
Hello All,

   I was wondering if it was possible to have a startup screen similar to windows XP.  The family is familiar to thier profiles with XP and I want an easy transition to Ubuntu for them.  I thought I saw something about a splash screen.  Is this what I am looking for?  Also, is there a way to see the chosen icon for the specified user?

BeeRad :confused:

---

### Post by NeoLithium on 2006-10-31
If you take a look at [gnome-look]("http://www.gnome-look.org") under their selections, there's quite a few screens, as well as [gnome-art]("http://gnome-art.org"); there may be something nice and convenient that you like.

As well, check out System -> Administration -> Login Window; I don't remember, but there are several options I have that allow a list of users to be selected similar to the Windows XP logon screen.

---

### Post by highneko on 2006-10-31
Edit: Didn't read your post well enough. No, a splash screen isn't what you want, but you might want to try one.

---

### Post by BeeRad on 2006-10-31
I have tried as you have said but I still end up with only one user login available.  Is there a step missing in setting up ALL the users to be listed?

BeeRad

---

### Post by NeoLithium on 2006-10-31
Do you have a login screen selected such as DebBlueList or HappyGnome with Browser?  Those should be pulling all users available (except root) from the password list.

---

### Post by BeeRad on 2006-11-01
> **NeoLithium said:**
> Do you have a login screen selected such as DebBlueList or HappyGnome with Browser?  Those should be pulling all users available (except root) from the password list.

Yes, thank you I was able to select HappyGnome.  The list of users is in the left column but all icons look the same except for mine (when I try to switch user) it has Ubuntu logo and the word Ubuntu beside the logo.  All the others look like a faceless shape including shoulders.  Can the selected icon for the particular user be shown here?

BeeRad

---

### Post by NeoLithium on 2006-11-01
Run 'gdmsetup' from F2 ('Run Program...' from the main menu) or the console, choose 'Standard Greeter' for local login in the General tab and choose 'Show choosable user images (face browser)' from the 'Standard Greeter' tab.

That should do it :)

---

### Post by BeeRad on 2006-11-02
I tried to run 'gdmsetup' and I was not allowed to access because a window with 'You must be the root user to configure GDM.

BeeRad

---

