---
title: "[SOLVED] To Use mouse in text-mode"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by tobeme2 on 2007-12-02
Under Fedora or lfs etc. , I could use mouse to select and paste, and I find this quite useful.
How can I do so under ubuntu? Thanks a lot.

---

### Post by dgray_from_dc on 2007-12-02
I've had no problem doing this from a terminal window in the gui.  I don't know what settings to change to enable that functionality outside of x.

---

### Post by overdrank on 2007-12-02
> **tobeme2 said:**
> Under Fedora or lfs etc. , I could use mouse to select and paste, and I find this quite useful.
How can I do so under ubuntu? Thanks a lot.

Hi if I understand you correctly, using the single click on the mouse- click and hold drag to highlight, then right click on the highlighted text and select copy. To paste just right click in the field and select paste.

---

### Post by tobeme2 on 2007-12-02
> **overdrank said:**
> Hi if I understand you correctly, using the single click on the mouse- click and hold drag to highlight, then right click on the highlighted text and select copy. To paste just right click in the field and select paste.
that's right.
But how could I do so?

---

### Post by tobeme2 on 2007-12-02
I have got the answer in google:

sudo apt-get install gpm
sudo /etc/init.d/gpm start

and then, mouse worked in text-mode.

---

