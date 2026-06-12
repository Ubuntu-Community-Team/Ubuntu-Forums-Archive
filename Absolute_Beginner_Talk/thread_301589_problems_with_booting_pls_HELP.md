---
title: "problems with booting pls HELP"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by muhaha! on 2006-11-17
muhaha! says hi! I have already started a thread concerning this problem but I thing I must give out more details to help you help me :) 

I have a pc with two HDDs. Master with Ubuntu 6.10 and slave with Windows XP . The problem is that while booting I get directed straight to the master HDD. 

=>What can I do for the pc to give me an option to choose in which HDD I want to get in?

=>While in grub can I switch to the other HDD and start Windows XP?

=>If I put Ubuntu in slave and Windows in master and create a grub floppy can this help me indirectly to choose HDDs? Insert floppy for Ubuntu and the oposite(no disket in floppy) to get Windows?

I am new to computers generally so sorry if my questions seem TOO stupid. Pls give detailed answers so that I understand what you mean

---

### Post by lloyd_b on 2006-11-17
You can define the XP drive in GRUB, and then pick whether you're booting Ubuntu or XP from the GRUB menu....

Take a look at this [howto]("http://www.ubuntuforums.org/showthread.php?t=275728")

Lloyd B.

---

### Post by bulldog on 2006-11-17
I don't understand your problem I guess,you stated Ubuntu is master so GRUB should be in the MBR,so you should see GRUB at startup and you can choose Ubuntu or windows in about 10 seconds time window.

Why should you want to boot from the other disk?

You can set in GRUB which OS should be the default boot [default is Ubuntu,but can be windows as well],you even can hide GRUB so what is the problem you have?

Most modern computers have the option to hit a button during bootime to get a menu to choose which boot device should be used.
If your computer can do so,you should know.

---

### Post by muhaha! on 2006-11-17
TRUE the F8 button while booting is great BUT still to luck
the only option AS I SAID that the computer provides is the master HDD. I have now changed permenatelly the settings in order to have Windows XP as the default setting PLUS Windows do not see Ubuntu and vise versa. ANYWAY I believe that that although I have not solved the problem YET I have learned much PLUS the way people share inormation in the forums is great. thanx a lot

---

