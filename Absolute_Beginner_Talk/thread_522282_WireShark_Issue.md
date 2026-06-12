---
title: "WireShark Issue"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by uniquesolutions01 on 2007-08-10
I am trying to setup and configure WireShark on my Ubuntu Server. I used the 
       **sudo apt-get install wireshark**     command. After that is there anything else i have to do. Does WireShark come with a Web Gui. Thanks in advance.

Unique Solutions

---

### Post by p_quarles on 2007-08-10
It doesn't have a web GUI (?), it uses a normal GTK+ window. To run it:
```
gksudo wireshark
```
It's also in the applications menu under Internet.

---

### Post by uniquesolutions01 on 2007-08-10
thanks. but still have another problem. I installed gksudo with the following command.
                           **sudo apt-get install gksu**    . then rebooted server then tried 
                             **gksudo wireshark**   and got this error

**(gksudo:4303): Gtk-WARNING **: cannot open display:**
did i miss something?


Phillip

---

### Post by p_quarles on 2007-08-10
No, I'm the one that missed something. My eyes skipped over the part where you said you were using this on a server. My bad. 

The command-line version of wireshark is called tshark. There's no GUI for it, web-based or otherwise, as far as I know. But, it's still relatively easy to use from the console if you're already familiar with wireshark. 

Sorry about my mixup. Hope this is helpful.

---

