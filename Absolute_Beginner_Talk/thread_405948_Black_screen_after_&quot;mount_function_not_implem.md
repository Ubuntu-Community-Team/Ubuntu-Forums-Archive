---
title: "Black screen after &quot;mount: function not implemented&quot;"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by widomenhardt on 2007-04-10
I have a system running XP.

I put the Ubuntu CD in there (6.10), and I get the first graphical screen, and select "install".

I then get these messages (approximately):


  Activating Swap
  mount: Function not implemented
  Checking filesystems
  fsck 139


Then the screen goes black, and all activity (CD or HD) ceases.

What to do?

I have seen some posts about handling different file systems (XP probably has the wrong one?), but on a black screen I can't issue any commands, in XP or in Linux !!!

Thanks for any help. 

Wido

---

### Post by garlik42 on 2007-04-10
When I have gotten the black screen it has usually (in my experience) been because of a graphics issue. I pick the safe mode option on the boot menu and this has always fixed the problem for me.

---

### Post by widomenhardt on 2007-04-10
> **garlik42 said:**
> When I have gotten the black screen it has usually (in my experience) been because of a graphics issue. I pick the safe mode option on the boot menu and this has always fixed the problem for me.
I will try that, but just to be clear, the initial graphics (the progress bar, the Ubuntu install options etc.) show up beautifully, so at least the Ubuntu installer knows how to work the graphics.

---

### Post by widomenhardt on 2007-04-11
It was related to graphics, as you suspected!

This computer has on-board graphics, but at some point I had added a better graphics card. When I took that out and connected the monitor to the on-board graphics, it worked.

Thanks for your help!

---

