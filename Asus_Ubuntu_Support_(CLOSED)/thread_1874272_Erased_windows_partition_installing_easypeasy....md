---
title: "Erased windows partition installing easypeasy..."
date: 2011-11-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Layla6942 on 2011-11-02
I apologize. I've looked at some of the install problems already posted and they all seem to be about losing ubuntu when installing windows in a parallel partition. 


Recently installed EasyPeasy on my EeePC (on the suggestion of my boyfriend) because I hate windows. I was being impatient and rather than figure out how to install it while preserving a partition for windows i just went ahead and let it claim the entire hard drive. 

:-\"

I of course have no CD-Rom drive... when booting into Windows from a USB thumb drive it does not see the hard drive. I wouldn't care except that...

#-o

I cannot get .Net Framework v4 to work with Wine. So I need windows to run Armonia, the DSP I use on the sound system at the club I work at. 
:guitar:

So... I would be happy if I could do one of the following things -[INDENT]1. Get .Net Framework v4 (specifically, earlier versions won't work) and wine properly configured so I can use it to run Armonia. Open to other methods and programs as well. \\:D/

2. Figure out how to get to the hard drive so I can find the Windows Recovery Partition so I can boot into that at work.  :rolleyes:


[/INDENT]Normally I would scour the webs and the forums for the answer but of course I have to work tomorrow night. The weekend starts on Thursdays here... in fact I don't think last weekend has ended....  :redface: my usual ninja search and pretend to understand command language is not working. 


[-o<
Help please? 

Thanks!
(insert image of happily purring bass kitten)
-Layla
):P

---

### Post by Layla6942 on 2011-11-02
PS - I am picking up where my boyfriend left off... I was there when Easy Peasy was installed but I do not know all the methods he's tried to fix the problem. Also, I'm open to a different version of linux. EasyPeasy seems clunky, slow and looks like it was designed for a five year old...

---

### Post by oldfred on 2011-11-02
You will not get .Net to work in Linux. Too much Windows based.

To get Windows to reinstall, you have to use gparted to remove the Linux partition so there is unallocated space and a primary partition available, or create a NTFS primary partition (sda1 thru sda4) with the boot flag (active partition in Windows). Then Windows should see the drive and let you install.

Several months ago a poster was running his entire DJ system from Linux. He posted several times before and after actually using it. It took a bit to get it going as I remember. But I do not have a link back to that thread.

Found thread:
[http://ubuntuforums.org/showthread.php?t=1634193](http://ubuntuforums.org/showthread.php?t=1634193)

---

