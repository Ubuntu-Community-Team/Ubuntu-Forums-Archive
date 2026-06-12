---
title: "Ubuntu will not load after selecting it from GRUB! HELP ME!"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by GhostlyLeech on 2008-01-24
Hello. I'm brand new to Ubuntu and these forums so if I'm leaving out valuable information in the description of my problem, could you just post asking for the specific piece of information that you need? Thanks!

I installed Ubuntu 7.10 on my Compaq Presario v2630CA laptop. Once the installation was complete, I restarted the computer and the GRUB bootloader opened. I selected the option for Ubuntu operation system and it spat out a few lines saying something about the kernel (I think...I'm writing this from my office computer so I'm not quite sure). It looked pretty legit so I just ignored it. Anywho, after I saw these two lines, a blank and black screen appeared. I waited about a minute for something to happen but my machine just turned off (I think that could have been due to my extremely crappy fan system in my laptop). I tried rebooting a few times and the same thing kept happening.

Please help! Could this be a graphics driver problem? Did I install it incorrectly?

Random specs that may help...

Video Graphics: ATI RADEON® XPRESS 200M IGP
Microprocessor: 1.8 GHz AMD Turion™ 64 Mobile Processor ML-34 with PowerNow!™ Technology

I had an error during the partitioning (I think it was during the partitioning) and I'm not quite sure what it was. It gave me the option to delete or not delete. I had no clue what this error meant so I thought the best thing to do was to say not delete. I think the word 'aplet' was in there. I didn't try reinstalling Ubuntu and pressing delete to this error to see if it made any difference (I was a little bit scared of breaking something. Haha!).

Man, I'm such a noob.

I hope you guys can help! I would love to start running Ubuntu on my machine.

---

### Post by ByteJuggler on 2008-01-24
Do you have Windows on there as well still?  If so, does that boot?

---

### Post by barbedsaber on 2008-01-24
this is probobly the blind leading the blind, but can you boot into a command line, I did it once. I think that would rule out graphics card issues. maybe reinstallations would be best, but get input from someone who REALLY knwos what they are doing first.

---

### Post by Nano Geek on 2008-01-24
If I were you I'd just reinstall. I think it would take less of your time, and sometimes things just go fluky like that.

---

### Post by jken146 on 2008-01-24
Since it's a brand new install, the easiest thing would probably be to check the integrity of your install CD and install Ubuntu again.

---

### Post by barbedsaber on 2008-01-24
if you decide to reinstall (which I whole heartedly suggest you do) could you please mark this thread as solved, info in my sig.

---

### Post by GhostlyLeech on 2008-01-24
**ByteJuggler:** Yup. When I selected Windows, it booted perfectly.

**barbedsaber:** When you say 'get help from somebody who really know what they're doing', do you mean to get a friend who uses Ubuntu to help (cause I don't have any) or somebody from here. Haha! I would try using command line but it's extremely foreign to me and I wouldn't even know where to start. Do you know any links where it contains information on booting via command line?

**asjdfwejqrfjcvm msz34rq33 / jken146:** I'll give the reinstallation a try once I get home. Would this require repartitioning the drives? If it does, and if I get that error again, what should I do? I choose to not delete last time. That question probably doesn't help considering I haven't supplied you guys with the exact error...

---

### Post by barbedsaber on 2008-01-24
[http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php")

[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

[https://help.ubuntu.com/7.04/basic-commands/C/]("https://help.ubuntu.com/7.04/basic-commands/C/")

dont know what you mean by booting form the shell, but learning a bit of it is a good idea, (I am trying) if you are curious about a command, open a shell, and type 

man thecommandthatyouarecuriousabout

and press q when you are finished reading. another thing that I have done that seems to be working, is set a keyboard shortcut to open the terminal, that way, you are more likly to check stuff by putting man in front of it, and when you can use it a bit, you are more likly to try it.

---

### Post by ByteJuggler on 2008-01-24
OK.  For the record:

1.) If you don't have a backup of your Windows/Data yet, now would be a good time to make a backup, just as a disaster recovery precaution.  This is important!

2.) When you install, you must try your best to understand the messages that the system is telling you, and/or get someone to help you understand if required.  Particularly messages warning you about deleting data need to be taken very seriously, unless you don't care about accidentally deleting your Windows partition/data due to carelessness. 

3.) When you get error messages, please note down the exact text and post that, as well as exactly where you got it and what you did beforehand.  All of this will help us troubleshoot it more effectively.  

4.) There is a screen snapshot tool in Ubuntu (I think on the applicatoins menu/Accessories, may be wrong on that) so ideally if you can post a screenshot that would be really helpful.  Remember this should work even from the LiveCD.  You can upload images to any free hosting service, for example [ImageShack]("http://imageshack.us/"), who will provide you URL's you can use in postings here.

Can you boot up with your LiveCD, to the desktop.  Then, once it's finished booting, press Alt-F2, and copy and paste into the "Run" dialog shown, the following command (you can also type it, but be extremely careful to copy it exactly as shown) and press enter to execute it. :

```
sudo fdisk -lu >/tmp/fdisk.txt; gedit /tmp/fdisk.txt
```

A text editor window should pop up with the output of the command string, listing the contents of all the partitions on your system.  Please post that text back here, so we can better suggest what to do and how to reinstall.  You can copy and paste it as normal from the text editor window to a browser window.

---

### Post by diwas on 2008-01-24
Actually i had the same problem except that the Kernel Panic error came in. I searched for the forums, made one myself but no solution. I waited abt 3 weeks for the solution so that i wont have to re-install the OS...But i could do nothing except that. 
Sorry no solution except re-installing from my side.

---

### Post by GhostlyLeech on 2008-01-25
Is there anything I should do before reinstalling Ubuntu again? Am I going to run into any problems with partitioning?

Also, I should mention that I found a weird way of actually getting into Ubuntu by pressing alt F2. I don't know why that worked. Maybe that could clear up something. When I was actually into the OS, I tried downloading GNOME partition editor from the package manager and it kept asking me to refresh. I also couldn't enable my drivers in the restricted drivers application.

---

### Post by GhostlyLeech on 2008-01-25
ByteJuggler: I ran that command you gave me and I got this output....


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   129805199    64902568+   7  HPFS/NTFS
/dev/hda2       141259545   156296384     7518420    c  W95 FAT32 (LBA)
/dev/hda3       129805200   140649074     5421937+  83  Linux
/dev/hda4       140649075   141259544      305235    5  Extended
/dev/hda5       140649138   141259544      305203+  82  Linux swap / Solaris

Partition table entries are not in disk order

Will this help you at all?

---

### Post by GhostlyLeech on 2008-01-29
I'm still having this problem...

Think anyone can help out? I don't really understand what this command output means...

Ok. If no one has the answer to the question above, could someone guide me in the reinstall?

---

### Post by ByteJuggler on 2008-01-30
OK, this means you currently have Linux installed on the following partitions

/dev/hda3 
/dev/hda4 
/dev/hda5 

You need to delete those, then re-install, using the option "use largest available free space" (or whatever it's called)

I'll post more detailed instructions tonight (can't right now.)

---

### Post by GhostlyLeech on 2008-02-01
> **ByteJuggler said:**
> OK, this means you currently have Linux installed on the following partitions

/dev/hda3 
/dev/hda4 
/dev/hda5 

You need to delete those, then re-install, using the option "use largest available free space" (or whatever it's called)

I'll post more detailed instructions tonight (can't right now.)

I tried doing this, I deleted the partitions and I wanted further instructions but need my wireless so I had to reboot into Windows. When I rebooted, it didn't load Windows but it gave me an option to do a system restore. Also, I should mention that in the partition list, hda3 and hda5 were the only ones listed from the list you gave me. What do I do?!

---

### Post by GhostlyLeech on 2008-02-04
Ok...since the Windows system restore, the GRUB bootloader has vanished. I'm assuming Windows has removed Ubunutu from my machine via system restore?

---

