---
title: "Printer support"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Voloo on 2005-11-21
1) I own a PSC 1350 made by HP [Link]("http://www.shopping.hp.com/webapp/shopping/supplies_model.do?tab=product_support&model_name=PSC+1350#defaultAnchor")
but it isn't in the list of supported printers, so I don't know how to get it to work.

2) How can I temporary grant myself root privileges, I want to drag a folder to the /usr/lib directory without dealing with command line.


Any help will be appreciated.
Thanks to the Ubuntu crew for a great product.

---

### Post by The Headhunter on 2005-11-21
1) sorry, someone else will have to help you out with this
2) 
   a) go into the terminal window (Applications->Accessories->Terminal)
   b) let's suppose there's a folder called "test" inside your home directory, which is the directory where you
   start off when you open the terminal window
   c) type this in:
   sudo mv test /usr/lib
   d) type in your user password

---

### Post by 311005901 on 2006-07-01
I also own a PSC 1350. I have some things fixed, but I still can't get the card reader port to work.

I can help you with the file moving. I use an easier method for moving, renaming, and deleting files. This way does it graphically instead of completely through the terminal.

1. Open a terminal. (**Applications** -> **Accessories** -> **Terminal**)
2. Type: ```
sudo nautilus
```
3. Type in your password and press press enter.
4. You can do anything in the file browser now because you have root privileges.

---

