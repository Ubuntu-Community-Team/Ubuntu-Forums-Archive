---
title: "URGENT!!! Screwed root around!"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by sebz2005 on 2006-11-02
I was trying to install LAMP and some HOWTO said for me to edit /etc/host and to add this in:
```
127.0.0.1       localhost.localdomain localhost
192.168.1.195   server1.example.com     server1
```After doing that I restarted my system as it said and now I can't log back in as root (terminal or any other app that requires root privaleges) to undo the changes.

Help please!

Thanks

---

### Post by Klaidas on 2006-11-02
What kind of error message do you get?

---

### Post by sebz2005 on 2006-11-02
Direct terminal copy.
```
sebz@sebz-desktop:~$ sudo
sudo: unable to lookup sebz-desktop via gethostbyname()
sebz@sebz-desktop:~$

```

Please don't tell me that I have to reinstall. I've spent forever updating and installing and copying!

---

### Post by Klaidas on 2006-11-02
Hmmm :-k
Well, to undo those changes you could try booting in recovery mode.

---

### Post by sebz2005 on 2006-11-02
Can you give me step by step instructions for me to print out?
Thanks again.

---

### Post by Klaidas on 2006-11-02
If you want to undo those changes, you could try booting in recovery mode (I'm not sure if you will be able to do that though)
Here's what you should try:
[LIST]
[*]Reboot you computer
[*]Choose Ubuntu blah blah **recovery mode**
[*]Press ENTER to boot
[*]When you have booted and you are root, edit that file:
[*](I'll use vi in this example) vi /etc/host
[*]Press ESC, then :, then i
[*]Edit that file (undo your changes)
[*]press ESC, then :, then wq, then ENTER
[*]shutdown -r now
[/LIST]

If that works, you should now have a file like you had before. If the file was the problem you coudn't become root, the problem should be solved.

---

### Post by sebz2005 on 2006-11-02
Oh, you are a master!!!!!
Thank you soooooooo much!

---

### Post by Klaidas on 2006-11-02
Glad to help :)

---

