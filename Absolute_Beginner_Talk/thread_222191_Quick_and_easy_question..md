---
title: "Quick and easy question."
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by N84 on 2006-07-24
Quick Question:

After you install ubuntu and you take out the CD after the restart does it unpack everything after booting into it for the first time? And does gnome start automatically after that? If not, what is the command to start the windows manager. (On slackware you first use xorgconfig/xorgsetup to configure it and startx to start it.) And if it is suppose to start right away, why didn’t my install unpack/start gnome. 

A brief recap of my ubuntu experience:

I’ve had a lot of problems installing ubuntu. I really liked the live CD but it is starting to seem like I was destined not to run it. I finally have grub working and a dysfunctional kernel that requires me to mash the keyboard while its booting if I want to have functioning I/O hardware. (No, this is sadly not a joke. ) From the instillation guides I was under the impression that ubuntu had to unpack all of the software after the basic system install and then started gnome at the beginning. If it is I am in for some more head to table contact.

---

### Post by Paerez on 2006-07-24
Prepare for ](*,)
because gnome should start automatically on your first boot. The best way to manually start it is to run:
```
sudo /etc/init.d/gdm start
```
to open up GDM to log in.

---

### Post by s_h_a_d_o_w_s on 2006-07-24
Did you install it or did you just run the livecd? I'm not too sure what your question is, but if you loaded the livecd (the on that loads up ubuntu without installing) then you should  click the "install ubuntu" icon on the desktop to install.

---

