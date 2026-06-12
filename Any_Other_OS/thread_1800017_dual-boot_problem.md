---
title: "dual-boot problem"
date: 2011-07-08
forum: Any Other OS
---

### Post by TuxTorvalds on 2011-07-08
I deleted every single trace of Linux Mint I could find, even searched for it, but I found out that I wasn't doing it properly. I even tried Re-installing Linux Mint and then using the Uninstall program, but Linux Mint is still on my start-up. When I try to access it, it gives me some error. I want Linux Mint off my computer but now, I don't think that's possible. Please help. :( By the way, my main os is Windows 7, and I used Mint4Win to install Linux Mint.
 
EDIT: I need this fixed!

---

### Post by Rubi1200 on 2011-07-08
I don't know if this will work for Mint4Win, but since it is probably based on Wubi you can try the following method:

On Windows go to Control Panel > System > Advanced > Startup and Recovery and press "Edit".

If there is an entry for Mint4Win, remove it.

If this does not help, let us know and we will try and find another solution for you.

---

### Post by TuxTorvalds on 2011-07-08
All I found was a button that said " Settings " I  clicked on it, and it showed a list that could edit what your default operating system is. It said Windows and Linux Mint, but I want to get rid of Linux Mint. I automatically boot into Windows, and I can't afford to do anything risky.

---

### Post by Blasphemist on 2011-07-08
First, I don't and haven't used WUBI which is what mint4win is built from. It's a way of running linux "within windows" so to speak. It sounds like your uninstall didn't remove grub. So you may have completely uninstalled mint but grub hasn't changed so you still have an option showing to load mint. I won't presume to tell you how to resolve it but you may want to look at this link. [http://duncsweb.com/2009/09/27/mint4win-a-wubi-based-installer-of-linux-mint/](http://duncsweb.com/2009/09/27/mint4win-a-wubi-based-installer-of-linux-mint/)

Now I just found this link that seems to say that mint4win uninstall should edit the boot.ini to remove the mint entry. So I don't know if grub is installed or not. [http://www.wilderssecurity.com/showthread.php?t=229029](http://www.wilderssecurity.com/showthread.php?t=229029)

---

### Post by TuxTorvalds on 2011-07-08
I need a solution!

---

### Post by Blasphemist on 2011-07-08
Jeez, lighten up a bit. It sounds from Rudi1200's post that it is boot.ini or at least not a grub issue. I'm sure you're capable of researching this yourself then.

---

### Post by TuxTorvalds on 2011-07-08
Fix this now!

---

### Post by TuxTorvalds on 2011-07-08
Fix this!!!!!!!!!!!!!!!11

---

### Post by IWantFroyo on 2011-07-08
Please stop before a mod locks the thread. We do want to help you.

LM is NOT going to brick your computer. 

If Mint4Win is based off of Wubi, then you should be able to find the "ubuntu" or "linux mint" folder, enter it, and find the "Uninstall Linux Mint.exe" or "Uninstall Ubuntu.exe"

This will completely remove it.

PS- Sorry for all the LM/Ubuntu stuff. I've only used Ubuntu Wubi.

---

### Post by TuxTorvalds on 2011-07-08
I'm afraid I deleted the folder with the Uninstall so I can't do that.

---

### Post by Elfy on 2011-07-08
Closed for the moment for you to realise we are all volunteers.

---

### Post by Rubi1200 on 2011-07-09
TuxTorvalds,

we all understand that you want a solution. But, as forestpiskie pointed out, we are volunteers here.

From what I understand of your posts, Mint4Win has been removed from your computer. 

However, there is still an entry in the bootloader menu that you see when starting the computer.

There is a way to fix this that will not damage your computer, but you need to follow the instructions carefully.

First, download and install EasyBCD:
[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

Then, use the instructions on how to remove entries:
[http://neosmart.net/wiki/display/EBCD/Deleting+Menu+Entries](http://neosmart.net/wiki/display/EBCD/Deleting+Menu+Entries)

Make sure to only remove the entry for Mint4Win!

Good luck and we hope you continue using Linux in some form or another in the future.

---

### Post by Elfy on 2011-07-09
Thread moved to Other OS/Distro Talk.

---

