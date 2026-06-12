---
title: "No desktop on Edgy first load."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Fataltragedy2 on 2007-03-15
I'm getting a text-based DOS like command prompt window when I load ubuntu.. Where's the destkop :(?

---

### Post by qpwoeiruty on 2007-03-15
after logging in , does "startx" give you a graphical environment?

---

### Post by Fataltragedy2 on 2007-03-15
No, I just restarted. It doesn't recognise the command.

---

### Post by in_flu_ence on 2007-03-15
did you install the server version or the desktop version of Ubuntu? If it is a new install, do check the integrity of the media. It might just be broken when you burn it.

Other than that, as said above, startx should give you some graphical environment.

---

### Post by Fataltragedy2 on 2007-03-15
I installed the desktop version. It's a new install. I didn't even use the CD. I used the 'Install via ISO' method :(

Startx isn't doing anything for me :( the only thing I can remember that related to it was it asked me if I wanted to install the ubuntu desktop, I think I selected yes, but it isn't here now :(

---

### Post by Fataltragedy2 on 2007-03-15
(The md5checksum of the ISO's and everything is correct.)

---

### Post by in_flu_ence on 2007-03-15
try sudo apt-get install ubuntu-desktop and see if you have installed the desktop properly.

It seems to me that you are missing some files. That's why you don't have startx.

---

### Post by qpwoeiruty on 2007-03-15
Since startx is not recognized, is ubuntu-desktop installed?
The command is:
sudo apt-get install ubuntu-desktop

---

### Post by Fataltragedy2 on 2007-03-15
> **in_flu_ence said:**
> try sudo apt-get install ubuntu-desktop and see if you have installed the desktop properly.

It seems to me that you are missing some files. That's why you don't have startx.

Can I just uninstall ubuntu and reinstall from scratch? Would it work if I deleted the root partition and swap partition using partition magic? Thanks.

---

### Post by Fataltragedy2 on 2007-03-15
I just tried the sudo apt-get command and it gives me the error

ubuntu-desktop: Invalid operation or something or the sort :(

---

### Post by qpwoeiruty on 2007-03-15
Are you sure that you didn't neglect a word and typed in sudo apt-get *install* ubuntu-desktop?
If you did and you're still getting errors, it this point I'd personally give up and reinstall (since it's a fresh install). You can just install right over the old installation. No need to delete stuff.

BTW: If you used the Windows based installer, it's full of bugs and you might want to try another method...

---

### Post by Fataltragedy2 on 2007-03-15
I hadn't installed the desktop during installation. I did now and I can't believe HOW GOOD UBUNTU IS! I'm NEVER GOING BACK TO WINDOWS :)

Only problem I have is I can't access my windows files :(

---

### Post by qpwoeiruty on 2007-03-15
Congrats on the new working install! 
Accessing your Windows files isn't a problem either. Instructions on how to mount your Windows partition in Linux is available [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows).

---

### Post by Fataltragedy2 on 2007-03-15
Thank you! Before I did that I tried some other method which involved editing Fstab, Can I revert this?

Also, I want my 2nd drive to be available, Can I do this?

---

### Post by qpwoeiruty on 2007-03-15
If you have or made an fstab_backup,  you can 
```
cp /etc/fstab_backup /etc/fstab
```

You do have to edit the fstab though if you want it to mount at boot time (that's in the same section on that page).

And, what do you mean by wanting the 2nd drive available?

---

