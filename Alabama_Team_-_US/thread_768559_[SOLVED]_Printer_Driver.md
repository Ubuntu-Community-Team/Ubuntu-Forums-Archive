---
title: "[SOLVED] Printer Driver"
date: 2008-04-26
forum: Alabama Team - US
---

### Post by retiree on 2008-04-26
I purchased a HP Photosmart D7260 and Ubuntu recognized it and recommended a driver that appeared to be a model 7100 series and it actually worked. I went to HP website and found their Linux driver on scourceforge.net and downloaded  a driver that supports my printer. I downloaded it to my desktop and copied and paste to terminal,but nothing happened.I manually put it in terminal and still the same thing,but with an error message folder not found.I followed the website instructions on how to install, and it said not to run in root terminal but I had to have root permission by putting in my password which I did.The file is 'hplip-2.8.4.run' I've not seen this type of file before, any suggestion on how to install this file would be appreciated. Thanks, Retiree

ps I took a screen shot but I don't know how to get in my post.
I did manage to get it in as an attachment.

---

### Post by retiree on 2008-04-26
Hi 
I found a forum with instructions on how to install a "run" file and it worked perfectly. It installed all required dependencies. My printer now works fine. Retiree

---

### Post by crane on 2008-04-26
Sorry I didn't see this earlier. Generally a .run file can be run the the sh command.
$sh /path/to/file.run
Glad you got the printer working. That is my next big project at work. I have a cannon I want to get working.

---

