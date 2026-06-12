---
title: "Lose usb drive"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by dante7921 on 2007-09-25
Hello all. I am very very new, an absolute beginner, to ubuntu/linux. I appreciate any help you can give me. Here is my problem:

Remember, I am very new to this. I installed an FTP. Works great! I have an external usb hard drive that i use for my main directory to the FTP. Everytime I have to reboot for updates or new installs I lose the usb hard drive. It's there. I know this because on my gnome desktop it's in the computer places. When I click on it, it gives me the error " cannot mount selected volume" "could not execute pmount". 

I have no idea what this means and I am not very good on the shell. 

Please, can somebody tell me how to mount this drive again and make it permanant?

Thanks in advance!

---

### Post by hotweiss on 2007-09-25
Did you install NTFS-3G?

---

### Post by dante7921 on 2007-09-25
No I did not install NTFS 3-G. What is it? How do I install it? 

FYI. The drive did work at one time. I know it's there.

Thanks in advance!

---

### Post by scrooge_74 on 2007-09-25
1st issue:  under what format is the drive? NTFS, FAT32?

2nd issue: Gnome is probably reading the system that is normal, but you need to declare it on your fstab file so it can be mounted by the system each time you boot.

This [link]("http://www.psychocats.net/ubuntu/mountlinux") should be helpfull

---

### Post by alienexplorers on 2007-09-25
/dev/drive_name /media/directory_name ext3 defaults 0 0

---

### Post by dante7921 on 2007-09-26
Thanks everyone for your advice. Unfortunatly nothing has solved this problem yet. The drive is still in my "places" on my gnome dt but when i click on it, same error. cannot mount selected volume. cannot execute pmount. 

I will try anything. I used the link supplied by scrooge (thanks) and I understand what you are getting at with that link but it did not solve my problem. Any more tricks up your sleeve for me???

Please any other suggestions?

Thanks in advance!

---

### Post by scrooge_74 on 2007-09-26
maybe format the disk on a windows machine (ouch) using fat32 as the file format.

Then try again to use it in Linux

---

