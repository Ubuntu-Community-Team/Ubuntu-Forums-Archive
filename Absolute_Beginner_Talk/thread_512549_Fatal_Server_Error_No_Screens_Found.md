---
title: "Fatal Server Error: No Screens Found"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by alex maria on 2007-07-29
I just installed Ubuntu 7.04 on an Acer notebook with AMD 64X2. Everything went fine. Finally when I boot up I get a message "Fatal Server Error: No Screens Found" Then it goes to command line prompt. This is the first time I will try Linux or Ubuntu. I think a GUI is suppose to come up.

I hope somebody can tell me what the problem is. I've searched around for a solution but could not find any. There must be some documentation of error messages of Ubuntu or X windows.

Thanks to anyone who may shed light.

---

### Post by PaulFr on 2007-07-29
This is usually related to your X-Windows screen options and the driver for the graphics card in your system. See **[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)** for some information on Acer laptops. Hope this helps.
After looking around, I saw a comment on **[https://wiki.ubuntu.com/AcerLaptopUbuntu](https://wiki.ubuntu.com/AcerLaptopUbuntu)** in April 2007 saying that you need to boot into command line mode and update the Feisty software using ```
sudo apt-get update
```

---

### Post by alex maria on 2007-07-29
Tried your suggestion, "sudo apt-get update",  I got a line of messages which started with "Failed to fetch http:// ", then security. ubuntu, ph.archive. ubuntu.com/  and so on and on, etc.

then I'm back with the prompt $

I think i should be connected to the internet. But the thing is this is a new laptop and theres nothing in it when I got it. Just Linpus/linus OS. So I don't think its configured yet for the net.

Thanks for the help. Hope you may have other suggestions.

Could it be possible that my X windows did not come with a GUI?

---

### Post by splintercellguy on 2007-07-29
I doubt there's no window manager present. Can you show us the contents of /etc/X11/xorg.conf and the output of the lspci command?

---

### Post by PaulFr on 2007-07-30
Yes, the error with http implies the network is not set up. So IMHO that problem needs to be fixed first (I would suggest you make a separate post indicating your laptop model details and ask for networking help), before attempting to fix the X-Windows problem. I presume you are able to login (since you could run sudo apt-get update).

---

