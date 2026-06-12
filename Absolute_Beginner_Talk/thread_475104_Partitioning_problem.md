---
title: "Partitioning problem"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by pandoratomorrow on 2007-06-15
Hello.

I have a new disk on my laptop, and I'm installing Ubuntu. This will say that I have no partitions on the disk. When I get to the "Prepare partitions"-part of the installation, the list is empety, and if I click "Forward", there is a pop-up saying "No root file system is defined. Please correct this from the partitioning menu."

What do I do to continue the installation?

Thanks.

---

### Post by Happy_Man on 2007-06-15
You have to choose to either have the system automatically partition for you, or manually do it yourself. If you have manually done it yourself, then when you click next from the partition editor, it will apply changes and drop to a screen with your newly created partitions on it. All you have to do is right-click the partition names you want changed, and change them. More info here:[http://psychocats.net/ubuntu/installing#partitioning](http://psychocats.net/ubuntu/installing#partitioning)

---

### Post by pandoratomorrow on 2007-06-15
Well, I actually knew that, but the only option I can see is "Manual". I know there should be at least one more alternative. Anyone know the solution to this? 

Thanks for the quick reply anyway.

---

### Post by Happy_Man on 2007-06-15
Well, perhaps since it's new..... Ubuntu wants you to do it manually. No sweat. Just follow the directions I gave you.

---

### Post by pandoratomorrow on 2007-06-15
But when I click on manually, it says: "No root file system is defined. Please correct this from the partitioning menu."

---

### Post by NeoLithium on 2007-06-15
I actually recommend a manual partition anyway, since you can easily create your own /home partition, which comes in quite handy should you have to reinstall for any reason.

---

### Post by pandoratomorrow on 2007-06-15
I don't think you understand me. The only option I have is to do it manually. But when I click on "Next", to make the partitions, I get this message: "No root file system is defined. Please correct this from the partitioning menu." I can't get past it. That's my problem.

---

### Post by Happy_Man on 2007-06-15
....oh. That puts a new spin on things. Did Ubuntu recognize that there's an HDD in the computer at all? Please post the output of ```
cat /etc/fstab
``` from the terminal (system -- accessories -- terminal).

---

### Post by pandoratomorrow on 2007-06-15
"unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0"

---

### Post by H.E. Pennypacker on 2007-06-15
> **pandoratomorrow said:**
> I don't think you understand me. The only option I have is to do it manually. But when I click on "Next", to make the partitions, I get this message: "No root file system is defined. Please correct this from the partitioning menu." I can't get past it. That's my problem.

You should select manual partitioning.  It's better that way.  If this won't work, try re-installing Ubuntu. 


I am sorry, but I couldn't resist.  I have done a forum and Google search on this error, and it looks like it is a bug that has not been dealt with yet.  Your best bet will be to use a GParted LiveCD, and do the partitioning from there.  I always keep a GP LiveCD on me...it's always useful.

Once you've done the partitioning with GP, restart, and go through the process with the Ubuntu LiveCD.

---

### Post by Happy_Man on 2007-06-15
> **H.E. Pennypacker said:**
> You should select manual partitioning.  It's better that way.  If this won't work, try re-installing Ubuntu. 


I am sorry, but I couldn't resist.  I have done a forum and Google search on this error, and it looks like it is a bug that has not been dealt with yet.  Your best bet will be to use a GParted LiveCD, and do the partitioning from there.  I always keep a GP LiveCD on me...it's always useful.

Once you've done the partitioning with GP, restart, and go through the process with the Ubuntu LiveCD.

Really? It's a bug? Well then, I'll have to remember that. Thanks for the tip.... even people like me who have no problems can use stuff every now and then.

---

### Post by H.E. Pennypacker on 2007-06-15
> **Happy_Man said:**
> Really? It's a bug? Well then, I'll have to remember that. Thanks for the tip.... even people like me who have no problems can use stuff every now and then.

It has been reported on Launchpad.net.  Here:

[https://answers.launchpad.net/ubuntu/+question/8062](https://answers.launchpad.net/ubuntu/+question/8062)

[https://launchpad.net/ubuntu/+source/ubiquity/+bug/90949](https://launchpad.net/ubuntu/+source/ubiquity/+bug/90949)

---

### Post by pandoratomorrow on 2007-06-16
> **H.E. Pennypacker said:**
> You should select manual partitioning.  It's better that way.  If this won't work, try re-installing Ubuntu. 


I am sorry, but I couldn't resist.  I have done a forum and Google search on this error, and it looks like it is a bug that has not been dealt with yet.  Your best bet will be to use a GParted LiveCD, and do the partitioning from there.  I always keep a  on me...it's always useful.

Once you've done the partitioning with GP, restart, and go through the process with the Ubuntu LiveCD.

And how do I make a GP LiveCD?

---

### Post by bigken on 2007-06-16
download it its in my signature and use any iso burning software to create the cd

---

### Post by pandoratomorrow on 2007-06-16
Ok, thanks. Can you tell me what I should do now? I don't understand this completely. Should I use this in addition to my image-burning software, or is this another burning program?

Thanks for all the replies guys!

---

### Post by pandoratomorrow on 2007-06-16
By the way: You understood that my hard drive is new, and therefore I have no partitions on it, right? Don't all people trying to install the program on a new disk get this same problem?

---

### Post by stalkingwolf on 2007-06-16
from the live CD you can try  system>admin> Gparted.  you should be able to partition your drive there.

---

### Post by bigken on 2007-06-16
> **pandoratomorrow said:**
> Ok, thanks. Can you tell me what I should do now? I don't understand this completely. Should I use this in addition to my image-burning software, or is this another burning program?

Thanks for all the replies guys!


you need to burn the iso to a disc and boot from it gparted is a partition editor

---

### Post by pandoratomorrow on 2007-06-16
I tried starting Gparted from system-admin, but there was nothing on the list, and the only option the program gives me is to quit.

---

### Post by bomb-24 on 2007-06-16
I recently installed ubuntu on a flash drive. I didnt want to disturb my xp installation at all. I used a 4 gig flash drive, went through the installation process and when it rebooted and went to the grub menu it stated: grub loading stage 1.5
grub loading, please wait...
ERROR 5
What can I do?? I am out of options. I cant boot my xp now, all I have is the live cd to run. Can someone please help me?

---

### Post by bigken on 2007-06-16
> **pandoratomorrow said:**
> I tried starting Gparted from system-admin, but there was nothing on the list, and the only option the program gives me is to quit.

in a terminal 

sudo aptitude install gparted

---

### Post by bigken on 2007-06-16
> **bomb-24 said:**
> I recently installed ubuntu on a flash drive. I didnt want to disturb my xp installation at all. I used a 4 gig flash drive, went through the installation process and when it rebooted and went to the grub menu it stated: grub loading stage 1.5
grub loading, please wait...
ERROR 5
What can I do?? I am out of options. I cant boot my xp now, all I have is the live cd to run. Can someone please help me?


to get your windows back 

boot from a win xp cd 

press R when promted this will take you to repair console 

when at the windows promt type** fixmbr** enter **fixboot** enter **exit** enter 

now you should boot into windows ;)

---

### Post by gn2 on 2007-06-16
Hi Big Ken, you might want to edit your SuperGrub link in your sig... :(

---

### Post by bigken on 2007-06-16
> **gn2 said:**
> Hi Big Ken, you might want to edit your SuperGrub link in your sig... :(

cheers ;)

---

