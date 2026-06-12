---
title: "Tell me about triple-boot GRUB difficulties."
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by cksubs on 2008-05-06
2nd Gen Macbook Pro
Triple Boot Leopard/XP/Ubuntu8.04

I've  tried to install Ubuntu several times on this computer, but run into the same problem every time. After a few reboots, or a few days, of having Ubuntu, the GRUB boot loader somehow "breaks," and, upon selecting either Ubuntu or XP from rEFIt, it boots into grub and gives me this:

> [ Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]

I'm then unable to boot from either OS. The way I have solved this in the past is to simply reformat the Ubuntu partition, as that makes Windows bootable again. But because of this, I've never gotten the chance to try out Ubuntu past a few days.

I researched this more before I installed 8.04, and found that I should install grub to the same partition as Ubuntu (using the "advanced" button on the page before the OS install). But this STILL broke after only two reboots and refused to boot either Ubuntu or Windows.

I'm fairly sure I can get the Windows partition working, using the "fixmbr" command when booting off the windows recovery disk. But I want some kind of confirmation that the Ubuntu partition will not stop working. I've since reinstalled Ubuntu (had to use it for a class), and am currently running it. I don't want to reboot for fear of it breaking again, as I've got the wireless running which was an annoying task in itself. What can I do to stop these GRUB errors?

---

### Post by cyberdork33 on 2008-05-06
> **cksubs said:**
> 2nd Gen Macbook Pro
Please make some indication that you are on Intel hardware in the Title of your threads. This will help you get the best responses.

> **cksubs said:**
> I'm fairly sure I can get the Windows partition working, using the "fixmbr" command when booting off the windows recovery disk. But I want some kind of confirmation that the Ubuntu partition will not stop working. I've since reinstalled Ubuntu (had to use it for a class), and am currently running it. I don't want to reboot for fear of it breaking again, as I've got the wireless running which was an annoying task in itself. What can I do to stop these GRUB errors?I would repair the MBR first as you stated. If grub is installed to the Ubuntu partition, but you still had reminents of grub in the mbr, you might be getting a conflict somehow. Even if you do get the problem you had before, you should not have to do a complete reinstall to get Ubuntu to boot.

---

### Post by cksubs on 2008-05-06
Welp, it broke again. After only one reboot. Great. I'm currently trying to find my Windows recovery disk to save that partition, but what can I do about Ubuntu? This time I'm not even getting the "Minimal Bash-Like" stuff, just "Grub_" where I don't think I can even enter commands. Any ideas?

***UPDATE***

So I was able to get back into Windows using fixmbr. Doing so removed the second Ubuntu Tux from rEFIt (I'm guessing that was a result of writing GRUB to the Linux partition, as I had never seen it before), and now running the Linux partition goes back to the Minimum Bash-Like command line.

---

### Post by cyberdork33 on 2008-05-07
> **cksubs said:**
> Welp, it broke again. After only one reboot. Great. I'm currently trying to find my Windows recovery disk to save that partition, but what can I do about Ubuntu? This time I'm not even getting the "Minimal Bash-Like" stuff, just "Grub_" where I don't think I can even enter commands. Any ideas?

***UPDATE***

So I was able to get back into Windows using fixmbr. Doing so removed the second Ubuntu Tux from rEFIt (I'm guessing that was a result of writing GRUB to the Linux partition, as I had never seen it before), and now running the Linux partition goes back to the Minimum Bash-Like command line.
you had two tux icons because grub was installed in two locations... MBR and the Ubuntu partition. fixmbr overwrites the MBR. you should have no problems booting into windows now. 

your grub issue is very weird, and it may have become screwed up somehow because of the way things were installed. go through the process of install grub to the ubuntu partition again. The link in my sig shows how to use the find command to run the correct commands.

---

