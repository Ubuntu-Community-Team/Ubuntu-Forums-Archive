---
title: "wireless problem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-05
Hi, i've isntalled recently Ubuntu Feisty on my HP Compaq nx6325

Now I can't make it connect to the internet, not even recognise the wireless card (which is a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PC I Card (rev 01)... or well that is what appears at the last line of typing ```
lspci
```)

Some people had told me to use Ndiswrapper but I can not understand the guides!!!!

Can anyboyd help me please?

---

### Post by Bachstelze on 2007-05-05
What is it that you do not understand in the guides ?

---

### Post by Jorge32 on 2007-05-05
for example one said something about cabextract windows driver or something like that and the other ones are kind of summarized so I don't understadn other steps....
I would be very grateful if someone can tell me something a litlle bit mor specific or someone help me more step by step.... :oops:

---

### Post by Bachstelze on 2007-05-05
Basically, just install the ndiswrapper packages, get the Windows driver, install them, you're done :)

Sometimes, Windows drivers are distributed in EXE files and cabextract is a tool that will let you extract the files from it.

---

### Post by Jorge32 on 2007-05-05
how do I make cabextract and how do I use the file with ndiswrapper¿

---

### Post by Bachstelze on 2007-05-05
First things first. First, you need to install ndiswrapper and get the correct Windows drivers for you card. Any problem there ?

---

### Post by Jorge32 on 2007-05-05
yes i already installed ndiswrapper and I have the cd of drivers for my pc.

---

### Post by Bachstelze on 2007-05-05
It's pretty straightforward then. What format are your drivers in (ZIP, EXE... ) ?

---

### Post by Jorge32 on 2007-05-05
i can get the .exe from the webpage but i have some that are .cva.


I am downloading the .exe from the page...



no wait I found there are some in the wlan part of the cd named setup.exe and a bunch of files which are dll, .inf, .sys.........

---

### Post by Jorge32 on 2007-05-05
ok sorry for the confusion, now i have the .exe file, what's next?

---

