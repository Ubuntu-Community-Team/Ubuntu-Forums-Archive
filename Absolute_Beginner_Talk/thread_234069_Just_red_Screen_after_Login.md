---
title: "Just red Screen after Login"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Talisker on 2006-08-10
Hi

I was playing around with the powermanager in gnome and tried to write a executble file that would start laptopmode on startup.

Well, unfortunatly.... something went wrong.

When I boot and enter user/password the screen stays red and I just get the blinking arrow. When I try Ctrl/ALT/backspace I can open the Terminal and start programs.
When I try to start "failsafe Gnome" it tells me: "could not find the Gnome installation."

I need some help to fix that... I'm lost...*G*

Thanks

---

### Post by akniss on 2006-08-10
> **Talisker said:**
> Hi

I was playing around with the powermanager in gnome and tried to write a executble file that would start laptopmode on startup.

Well, unfortunatly.... something went wrong.

When I boot and enter user/password the screen stays red and I just get the blinking arrow. When I try Ctrl/ALT/backspace I can open the Terminal and start programs.
When I try to start "failsafe Gnome" it tells me: "could not find the Gnome installation."

I need some help to fix that... I'm lost...*G*

Thanks

if you can get to a terminal, can you remember where you put the script that borked your system? if so, ```
sudo nano /where/you/put/your/script
```and try to change things back to the way they were

---

### Post by Talisker on 2006-08-10
hmmm.... the file was /etc/init.d/laptopmode

the other was /etc/rc2.d/S99Laptopmode

After the reboot the screen problem appeared. I deleted the two files, nothing happened.

The funny thing is... I can start the applications including the package manager. It seems just Gnome is hurt.

I'm stranded......:sad:

---

