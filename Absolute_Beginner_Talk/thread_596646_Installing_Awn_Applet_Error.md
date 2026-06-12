---
title: "Installing Awn Applet Error"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by It_Was_Luck on 2007-10-29
So I tried to install the Pidgin Applet for AWN  from this site:

[http://code.google.com/p/awn-plugins/](http://code.google.com/p/awn-plugins/)

Then I downloaded the Pidgin one, then I went into Awn's settings and selected install, I selected it and it said "Unable to Install Applet"

Any help

---

### Post by Inxsible on 2007-10-29
Try this. ```
bzr checkout http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk awn-extras
```Then:     ```
cd trunk/
cd awn-plugins/
ls
cd pidgin
make && sudo checkinstall -D --pkgname='pidgin-plugin-awn'
```And, tada! You're done. You can now enable "AWN Plugin" in Pidgin's plugins menu.

---

### Post by It_Was_Luck on 2007-10-29
I tried the first line and it says I don't have bzr, I don't know what that is, I believe I know how to download it, but what does it do?

Also thanks for the code

---

### Post by Inxsible on 2007-10-29
> **It_Was_Luck said:**
> I tried the first line and it says I don't have bzr, I don't know what that is, I believe I know how to download it, but what does it do?

Also thanks for the codebzr is a code repository/archive like cvs or svn

---

### Post by It_Was_Luck on 2007-10-29
Okay I installed bzr, So I went to type in the first code again and this is what I get:

```
root@ben-desktop:~# bzr checkout http://bazaar.launchpad.net/awn-extras/trunk/
bzr: ERROR: Not a branch: http://bazaar.launchpad.net/awn-extras/trunk/

```

---

### Post by Inxsible on 2007-10-29
Try this wiki link

[http://wiki.awn-project.org/index.php?title=Awn_Extras](http://wiki.awn-project.org/index.php?title=Awn_Extras)

---

### Post by It_Was_Luck on 2007-10-29
I followed there install method and downloaded like 20MB of stuff for it to just come up with an error code... 

Still no luck, see I found the /usr/lib/ folder then I tried to "drag-and-drop" the pidgin applet I had right into the applet folder where all the other ones were, oh I though I had it, then it said "You don;t have permission to write to this folder.

(Sigh) There must be an easier way

---

