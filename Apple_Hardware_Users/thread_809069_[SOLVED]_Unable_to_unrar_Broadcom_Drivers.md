---
title: "[SOLVED] Unable to unrar Broadcom Drivers"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by theghostbelow on 2008-05-27
I have installed Ubuntu on to my Macbook Pro Penryn and am trying to get the bcmw15.inf file off of the bootcamp cd but when ever I try and run unRar such as suggested in the wiki I get this error message.  

drew@drew-laptop:~$ unrar e BroadcomXPInstaller.exe

UNRAR 3.71 beta 1 freeware      Copyright (c) 1993-2007 Alexander Roshal

Cannot open BroadcomXPInstaller.exe
No such file or directory
No files to extract
drew@drew-laptop:~$ 

The file is saved in my home folder.  Thanks in advance

---

### Post by stueng on 2008-05-27
try unzip blah.exe or you could try my instructions if that still doesnt work @ [http://www.lostpeg.co.uk/content/view/34/76/]("http://www.lostpeg.co.uk/content/view/34/76/")

---

### Post by cyberdork33 on 2008-05-27
> **stueng said:**
> you could try my instructions if that still doesnt work
the dell drivers do not work on the later machines.

---

### Post by theghostbelow on 2008-05-27
I just tried unzipping the .exe file and i get a cannot find or open blah blah blah.  Do I need to navigate the terminal to a specific location before I enter the command or is something else wrong? Thanks I havn't tried the other work around with the dell driver but i will later if I have time.

---

### Post by cyberdork33 on 2008-05-27
> **theghostbelow said:**
> I just tried unzipping the .exe file and i get a cannot find or open blah blah blah.  Do I need to navigate the terminal to a specific location before I enter the command or is something else wrong? Thanks I havn't tried the other work around with the dell driver but i will later if I have time.you have to navigate to the directory that contains the file you are trying to unzip.

---

### Post by theghostbelow on 2008-05-28
Ok I got the drivers installed and in ndiswrapper thanks for helping but now I can see my wireless network but when I try to connect it will try to connect and then ask for my wpa password.  After entering the password it will try to connect for awhile again and then ask for my password and repeat until i give up trying to put in the password.  I am running 32 bit (8.04)  and the encryption is wpa/wpa2 personal using aes-ccmp encryption.  Sorry if I need to start a new thread on this that can be done if I do and thanks for all the help.

---

### Post by cyberdork33 on 2008-05-28
> **theghostbelow said:**
> Ok I got the drivers installed and in ndiswrapper thanks for helping but now I can see my wireless network but when I try to connect it will try to connect and then ask for my wpa password.  After entering the password it will try to connect for awhile again and then ask for my password and repeat until i give up trying to put in the password.  I am running 32 bit (8.04)  and the encryption is wpa/wpa2 personal using aes-ccmp encryption.  Sorry if I need to start a new thread on this that can be done if I do and thanks for all the help.try TKIP, and if that doesn't work, make sure that everything works without encryption to make sure it the drivers are working OK.

---

### Post by theghostbelow on 2008-05-28
After switching the security to none on my wireless router I still get the same problem the network is detected but when I try to connect it spends 20 to 30 seconds and then the window asking for a wpa password pops up again even though I know that it doesn't need one.  I tried rebooting to see if that would help and it didn't.  I am going to start over with a clean install and see if that helps and if not I will return, anyways thanks for the help so far cyberdork the community is one reason I really want to get into linux.

---

### Post by cyberdork33 on 2008-05-28
You are apparently not alone. Several people have been reporting the same issue on the MacBookPro4,1

---

### Post by theghostbelow on 2008-05-29
Yes it would seem so. After doing a complete reinstall and following the instructions to a T. I get the exact same error as before. Thanks for your help cyberdork and what should I do now, I guess wait until the issue is worked out?

---

### Post by theghostbelow on 2008-05-29
Ok apparently the real apple driver started working for some reason other than the dell driver, NOTE the dell driver does not work.

---

### Post by cyberdork33 on 2008-05-29
> **theghostbelow said:**
> Apparently the Dell drivers do work at least for me where as the apple driver on boot camp did not. 
Thank you for all your help
Are you sure that you have a Penryn Macbook Pro? Can you post the output of 'lspsci'?

---

### Post by theghostbelow on 2008-05-29
I will soon I just reinstalled again because being a complete newbie I messed up some other files trying to change settings, as soon as I get the driver working again I will post what you asked. Edit: dell driver didn't work

---

