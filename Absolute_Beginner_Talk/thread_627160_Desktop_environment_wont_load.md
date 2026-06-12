---
title: "Desktop environment wont load"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Blessed_Coffee on 2007-11-29
I just installed ubuntu, but I cant get the desktop to load up.  What am I doing wrong :confused:  Is there something I missed? :/

---

### Post by PmDematagoda on 2007-11-29
Do you mean that the X-server won't start up?

If so, could you post your specifications so that we could make our next move.

---

### Post by Blessed_Coffee on 2007-11-29
Ya, the x-server doesnt start.
I dont see an error message saying it failed to start though.

If you are speaking of my computer specs, then:
Nvidia geforce fx 5500
celeron D
Integrated sound card (Dont know)
384mb of ddr2 ram

I also got some error messages while installing, but I cant get the installer to run again.  I used unetbootin-ubuntu710rev14 to install ubuntu, because my cd burner wont burn the iso file.

Edit:  It just occured to me that unetbootin isnt working anymore because Im using ubuntus grub.

---

### Post by PmDematagoda on 2007-11-29
Why can't you get the installer to run again? If there was an installation error then it could be that your Ubuntu OS is not installed properly and the reason for that would be a corrupted CD.

---

### Post by Blessed_Coffee on 2007-11-29
It wont run again because it got formatted during the install, and to install unetbootin requires that grub be in the default location C:/boot/grub.   Im a little loss now :(

---

### Post by PmDematagoda on 2007-11-29
Why are you using unetbootin? Why don't you simply use a Live CD?

---

### Post by Blessed_Coffee on 2007-11-29
> **Blessed_Coffee said:**
> because my cd burner wont burn the iso file.:(

---

### Post by PmDematagoda on 2007-11-29
Oh, sorry, I did not see that. As I do not use unetbootin at all, I'm afraid that I cannot help you much, but why don't you order the Ubuntu Live CD from the Ubuntu web site using [ShipIt]("https://shipit.ubuntu.com/"), they can deliver it to you.

---

### Post by Blessed_Coffee on 2007-11-30
I finally got ubuntu installed.  I figured out that unetbootin was set up incorrectly in grub's menu.lst file, so I fixed it, and reinstalled.  The issue was the ubuntu desktop didn't install.  I've only used this linux for a few hours, but it is already my favorite.  This is much better than linspire, which is the OS I wanted to replace.  I might even throw linspire away. :rolleyes:

---

