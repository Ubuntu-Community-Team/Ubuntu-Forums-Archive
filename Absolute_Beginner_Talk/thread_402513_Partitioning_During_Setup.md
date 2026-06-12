---
title: "Partitioning During Setup"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Stevo0687 on 2007-04-05
Hey all!
    I'm trying to install Ubuntu 6.06LTS.  When I get to the part where I whip out the HD or manually partition I choose manually partition.  I am already running XP and Vista and have a shared partition for "My Documents."  
    I have created an extended partition that is a little over 10GB.  From there I believe I need 8 or so for /  (called root).  That is what Ubuntu is actully installed on, correct?  And then 2 GB for swap?  Is this correct?  Do I need any other partitions?  
   I want to use the shared partition with "My Documents" with Ubuntu also.  Do I set that up now or do I configure that later?  If I set that up now which Mount Point would that be?  Also, if I set that up now, will it erase the data that is on the shared partition already?   Should I back up that info just in case?  
   Please help me out here.  If anything I've said is wrong please correct me and point me in the right direction.  Thank you very much in advance.  All advice is greatly appricated.

---

### Post by halitech on 2007-04-05
if you have an empty partition, you should be able to select using the largest empty space and let Ubuntu decide the amounts.

Manually, unless you have little ram (hard to see if you have XP running ;) ) then you probably only need a gig or less for swap. for /home I've give 2-3 gigs (should be lots) and the rest for / (otherwise known as root). 

for your windows stuff, don't worry about mounting that now, when you get into Ubuntu, you can use the disk tool to mount in in your home folder.

---

### Post by Stevo0687 on 2007-04-05
Thanks, Hailitech.  Yeah, I thought I had chosen to use the largest available partition when I installed this before.  Though now that I think about it, it is set as ext file, so maybe I need to make it unallocated.  

 An 10-4 on the disk tool once I have it installed.  Thanks for your help. I think I'll back up my documents, just in case and try again.  Thanks.

---

### Post by jbumgar on 2007-04-05
I set mine up with 500 meg of swap and then 40 gig to root and have no problems.

---

### Post by Stevo0687 on 2007-04-05
Alright, I've installed Ubuntu. It works fine and it even recognizes XP and allows me to choose either one when I boot the PC.  BUT it does not recognize Vista.  Does anyone have any suggestions as to what I do?  

IF all else fails, can I go into g-parted, delete Ubuntu, and will it go back to dual booting Vista and XP or will I have to reconfigure it, or will I have to reinstall Vista.

But I hope all else doesn't fail.  Does anyone know how I handle this so that it will allow me to triple boot.  Thanks in advance.

---

### Post by Stevo0687 on 2007-04-05
EDIT EDIT EDIT EDIT:   I was wrong. Once I selected XP it gives me the choice of XP or Vista.   I finally got it!!! I've been trying to Triple boot: XP, Vista, Ubuntu for months (well, not trying every day, but researching and stuff when I have time). And I finally got it.  I'll leave my post above of me thinking it didn't work in case others read this and have the same problem. 

So it IS possible to do this.  All I did was install XP, then Vista which gave me a dual boot for either one.  I have a 3rd partition for shared files between the operating systems and the 4th partition I left unallocated for Ubuntu.  I installed Ubuntu using the free space.  Once that was done I could restart.  When the computer boots it gives a few Ubuntu options or Windows XP.  You can choose the top Ubuntu for Ubuntu, obviously, of pick XP which will take you to a boot screen for XP or Vista.  Thats all I did.  Nothing special.  I just messed up a few times along the way.   Thank you very much to everyone on this forum who has helped me.  I couldn't have done it without you.   I'm sure I'll have plenty of questions as I get used to Ubuntu and experiment with it so I'll be back, but I've made my biggest hurdle which turned out to not be so big after all.  Thanks.

---

### Post by halitech on 2007-04-05
glad to see you have things all set up and ready to go :)

we are here to help and be helped so any questions, fire them at us and we'll do our best to help you out

---

