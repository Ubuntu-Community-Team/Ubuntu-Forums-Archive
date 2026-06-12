---
title: "Editing Grub preferences"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by rogerdean on 2006-02-03
Hello folks
I'd like to change the default boot order and times in grub (breezy), but can't seem to find whatever graphical tool i used in hoary to make the changes. Can anyone point me in the right direction please?
Many thanks :D 
Roger

---

### Post by aysiu on 2006-02-03
I may be wrong, but I don't think there are graphical tools for this.

Applications > System Tools > Terminal ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` Change the *timeout 10* to however many seconds you want. Change *default 0* to whatever # entry you want (minus one).

---

### Post by rogerdean on 2006-02-03
Spot on, many thanks Aysiu. I'm sure there was a tool in the default drop-down menu in Hoary though, as I'd never have figured it out on my own! Anyone else remember this?
Cheers
Roger

---

### Post by charlwillia6 on 2006-02-04
I have a question as to what is showing in Grub when I boot.  I installed Ubuntu breezy, and then did all the updates.  Now, after I updated everything, it shows two kernels in my Grub menu:  2.6.12-10-386 and 2.6.12-9-386.  I can boot from both, but of course I only want to boot from the most recent kernel.  So why are both kernels showing up after the update, and how do I get rid of the other one in Grub?  Also, does this mean that both kernels are installed on my system?  Don't I ony need the updated one?

Thanks in advance,
Charles

---

### Post by aysiu on 2006-02-04
You can remove the old kernel. Open up Synaptic (or Adept if you're using Kubuntu) and search for the word *image*.

---

### Post by charlwillia6 on 2006-02-10
Thanks, I uninstalled the other kernell, and I think everything is still working ok.  Now if only I could get my menus edited.....:???:

---

