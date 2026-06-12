---
title: "I installed Windows inside Linux"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by xcvcx on 2008-04-20
I installed windows inside my Linux but i can't connect to the internet with it.. Wirelessly. Also their is no wireless option.. anyone have an idea?

---

### Post by SunnyRabbiera on 2008-04-20
what like a virtual machine?

---

### Post by aktiwers on 2008-04-20
Did you remember to share your internet card with the Virtual Machine?

---

### Post by lswest on 2008-04-20
also, chances are the wireless will be "wired" in the VM, since it connects through a virtual ethernet card to the actual internet connection on the Host OS

---

### Post by pastalavista on 2008-04-20
so, would you mind sharing how you did that?

---

### Post by xcvcx on 2008-04-20
I just used this


qemu -localtime -cdrom /dev/cdrom -m 356 -boot d win.img


This command creates a virtual computer which boots from your local cd rom and has 356 MB of memory allocated as it's RAM .

now to start it up i use that command

---

### Post by aktiwers on 2008-04-20
I would recommend you to use VirtualBox, it's both easier and faster IMO.

---

### Post by xcvcx on 2008-04-21
Can someone tell me how I would go by getting rid of the windows I already have installed then?

---

