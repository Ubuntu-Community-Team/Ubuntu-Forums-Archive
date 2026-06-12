---
title: "installing WUSB54Gv2"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by frtorreira on 2006-07-21
Hello,

I am a total newbie to both linux and ubuntu. I have been trying several distros and managed to install my linksys wusb54Gv2 via ndiswrapper. I am following the same steps in Ubuntu. Unfortuantely there is something wrong. Here are the steps:

1. installed ndiswrapper 1.21 (current version downloaded from the web)
2. went to folder holding windows drivers
3. typed sudo ndiswrapper -i wusb54gv2.inf

Here I could spot an error in the command line:
"[...] cannot copy line 144"

Then, when I do:
4. sudo ndiswrapper -l
I get:
" drivers installed:
wusb54gv2 invalid driver! "

I tried to remove it with ndiswrapper -e wusb54gv2.inf Surprisingly, i got a message saying that driver was not installed!!
So here I am, not being to remove an invalid driver and not knowing how to install a correct one. Any help?? Ubuntu looks fine and all, but access to the internet is essential to me.

Thanks in advance

---

### Post by Saphira on 2006-07-21
[http://doc.gwos.org/index.php/LinksysWireless](http://doc.gwos.org/index.php/LinksysWireless)

[http://doc.gwos.org/index.php/Prism54Driver](http://doc.gwos.org/index.php/Prism54Driver)

I think this is what you need, could be wrong.

---

