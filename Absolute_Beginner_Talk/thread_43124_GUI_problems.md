---
title: "GUI problems"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by frostyservant on 2005-06-20
Ubuntu has been unable to start up the GUI, citing problems with X Windows.  I believe that I have tracked down the problem to my BIOS, but the solution depends on downloading and running a certain file.  

Herein lies the problem.  While my Ubuntu system is connected to the internet, I can only use it via command line, making the use of traditional browsers impossible (I'm accessing this forum on a seperate XP machine).  Is there a text-only browser included in Ubuntu, or some other way for me to get the file to my Ubuntu machine?

(Additional bonus issue:  Can linux run .exe's?  I have yet to find a copy of the BIOS updater outside of that format.)

---

### Post by scourge on 2005-06-20
> Is there a text-only browser included in Ubuntu, or some other way for me to get the file to my Ubuntu machine?

If you need a browser, there's always lynx (install by typing "sudo apt-get install lynx"). But I don't think you need that much, you should be able to get the file downloaded via wget (type "wget URL", and the file will be downloaded to your home directory).

> Can linux run .exe's?

You can run some exe files with wine, but when it comes to updating your BIOS, I advise not to try it. Probably wouldn't even work.

This exe file is a DOS executable, right? If it is, then I suggest you to download a MS-DOS bootdisk image (the Net is full of them, just try Googling), create the bootdisk, copy the BIOS update file to the bootdisk, boot your PC from the disk, and finally, run the exe. Even for Windows users this is often the only way to update the BIOS.

---

### Post by frostyservant on 2005-06-21
It worked!  Thanks.

---

