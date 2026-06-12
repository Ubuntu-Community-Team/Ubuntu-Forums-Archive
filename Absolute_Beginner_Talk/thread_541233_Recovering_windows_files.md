---
title: "Recovering windows files"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by CaptainArD on 2007-09-02
I am in need of reformatting my windows drive, but before i do so, i need to recover files off of it. I have so far booted from a suse live dvd, mounted the /dev/sda1 drive to a folder in /home/linux. I am now able to navigate my windows drive and whatnot, but every time i try to copy a file from the windows folder to a USB stick, it tells me that "the file does not exist." So, i'm stuck. If i can see the file, how can it tell me it doesn't exist? I googled for a solution to no avail, and i'm pushing 4 hours of work to get this fixed, i need my computer back to running shape by tommorrow. Can anyone help? Thanks in advance.

edit: Btw, i'm on a dell d820 with 2575MB RAM. SUSE 10 live DVD, original OS Vista ultimate. dunno if that helps.

---

### Post by InGunsWeTrust on 2007-09-02
I would say that the file is probably not usable. The index for the file may be intact but the actual file itself may be corrupted. Another mistake you may be making is not actually mounting your USB stick. I don't know if SUSE automatically does that when you put it in so you could first try using the ubuntu live CD (because I know it does automatically mount USB sticks) then you can try a linux distro called helix. it is used in computer forensics to recover information off hard drives. 

This is a download link
[http://www.snipergaming.co.uk/Helix_V1.9-07-13a-2007.iso](http://www.snipergaming.co.uk/Helix_V1.9-07-13a-2007.iso)

This is a link to more info
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

---

### Post by CaptainArD on 2007-09-02
it cannot be corrupt, I can access it in windows.  My problem is that i have a problem with windows explorer and i cannot actually achieve anything in windows, because the explorer keeps crashing.  Any other programs work fine.  
I am under the impression that the USB stick is mounted, i can copy other files to it.

---

### Post by benerivo on 2007-09-02
I would have also guessed that the files are corrupted as the linux method should work if you are able to mount and see the files. Have you tried an alternative file manager in windows to see if that will stay open and allow transfer to the usb stick?

---

### Post by benerivo on 2007-09-02
Also, have you tried to open any of the files straight from the windows mount, such as a text file, to see if it can open in the linux text editor?

---

### Post by InGunsWeTrust on 2007-09-02
In windows open a command prompt and do this

```
xcopy C:\pathofthefile\nameofthefile E:\
```
Assuming E: is the driveletter of your usb stick.

If that doesn't work then the file or the USB stick is corrupt for sure.

---

### Post by CaptainArD on 2007-09-02
ok, i restarted my computer and logged into the live DVD as root. I dunno what that changed, really, but i am now able to access and copy all the files i couldn't before. so, linux has once again saved my ***, if only with a little frustration.
i got an alternative file manager just in case.
thank you all for your help.

---

### Post by InGunsWeTrust on 2007-09-02
I assume you were having mount issues in that case because the mount utility requires root priveliges.

---

