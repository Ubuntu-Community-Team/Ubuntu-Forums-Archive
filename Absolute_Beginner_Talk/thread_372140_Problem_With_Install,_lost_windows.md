---
title: "Problem With Install, lost windows"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Cikrum on 2007-02-27
Hello, 
I have used Ubuntu for about the past year. I recently got a new hard drive and after I put it in my computer Ubuntu Stopped working. I am pretty sure this is because it was looking for the boot on the wrong hard drive. So I wiped Ubuntu for numerous reason, (not because its not great). A few months later I have tried to reinstall Ubuntu but this time it didn't go so well.  My hard drive is a 250 GB hard drive. I have 170 for windows and the rest I left unpartitioned. So that I could swap files from windows I made a 30 GB fat32 partition. This went fine. It was after this that I started to install Ubuntu. I put it in the extra space on this hard drive and I let the automatic installer do its work. It seemed to work fine and said to use the newly installed system I should reboot, so I did. This is where everything went terribly wrong. When I tried to boot it said "operating system error". This is when I panicked and used the Live CD to wipe Ubuntu's partition thus getting rid of it. This was probably a bad idea and I should have just started trouble shooting from there but, again I panicked. I hoped that is would pretend it never happened but of course it didn't. This might have to do with GRUB I'm not sure, but it will no longer boot into windows either. it says " Disk boot failure" 
I really would like to use ubuntu but I Also need some of the things on my windows. Most of my files are on my other hard drive but reinstalling windows again is just a pain in the butt, especially when i have done it 8 times in 4 months.
Any help would be greatly appreciated.
Thanks 
Cikrum

---

### Post by Cikrum on 2007-02-27
Update: I have tried reinstalling Ubuntu and now it doesn't if say Disk Boot faliure rather is just sits there and does nothing.

---

### Post by rccharles on 2007-02-27
> **Cikrum said:**
> Update: I have tried reinstalling Ubuntu and now it doesn't if say Disk Boot faliure rather is just sits there and does nothing.

What you need to do is re-install the Windows Master Book Record (MBR).  I look around and find a program that does that.

Robert

---

### Post by rccharles on 2007-02-27
> **rccharles said:**
> I look around and find a program that does that.

Robert

Here:
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

Robert

---

### Post by Cikrum on 2007-02-28
thanks for the reply
But sadly this doesn't fix it. I tried the FIXMBR but it doesn't help. I also tried fixboot and the doesn't help either. I now just says, like before disk boot failure, insert system disk and press enter.
Any ideas, cause i am fresh our.
Thanks
Cikrum

---

### Post by rccharles on 2007-02-28
> **Cikrum said:**
> thanks for the reply
But sadly this doesn't fix it. I tried the FIXMBR but it doesn't help. I also tried fixboot and the doesn't help either. I now just says, like before disk boot failure, insert system disk and press enter.
Any ideas, cause i am fresh our.
Thanks
Cikrum
SuperGrub will let you boot a partition without a valid MBR.  I am not sure it will help you, but here is superGrub:


Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

This wouldn't be a permanent solution, but it would get you started.


Robert

---

