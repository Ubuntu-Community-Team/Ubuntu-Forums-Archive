---
title: "Terminal Emulator"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by eisle89 on 2006-09-09
Which Terminal Emulator is the best for the n00b ?? I'm having a little prob with permissions and was wondering if one or the other automatically sends you back to /root or not.

---

### Post by Albi on 2006-09-09
sudo before the command will give root permission

---

### Post by taurus on 2006-09-09
If you want to run something with root permission, use sudo from a terminal, any terminal...

```
sudo <command>
```

---

### Post by ButteBlues on 2006-09-09
If you are not being allowed permissions to do a task in the terminal, simply preface your command(s) with "sudo".

This will prompt you for a password (the same password as YOUR user), which'll give you temporary root powers in the terminal.

---

### Post by jimmygoon on 2006-09-09
or you can always "sudo bash" or "sudo -s"

---

### Post by bodhi.zazen on 2006-09-09
> **eisle89 said:**
> Which Terminal Emulator is the best for the n00b ?? I'm having a little prob with permissions and was wondering if one or the other automatically sends you back to /root or not.

Any terminal will do. I like 

[indent]Terminal 0.2.4 (Xfce 4.2.3.2)[/indent]

The other posts will help with sudo for root access.

---

### Post by eisle89 on 2006-09-09
Thanks alot you guys, this n00b owes you

---

