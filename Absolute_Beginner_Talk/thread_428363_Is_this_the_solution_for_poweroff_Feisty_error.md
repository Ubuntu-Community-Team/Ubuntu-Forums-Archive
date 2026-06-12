---
title: "Is this the solution for poweroff Feisty error ?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Kuoi on 2007-04-30
Hello ,

Can somebody who's computer is not shutting down (poweroff) completely , test the following out  and tell here if it worked ?
 ... it did for me .
Please test it with Edgy and Dapper too , 

I had an issue with the "poweroff " button from the panel.
Everytime I used it , it hangs after a few seconds on a black screen , and I had to push the power button from my computer to turn my computer off .

--------------------------------------

Applications > System tools > Terminal as root

Then type > sudo gedit /etc/acpi/powerbtn.sh

At the very end of the text page you'll see this sentence > # If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"

Just insert a P after the -h , so it reads like this ... > # If all else failed, just initiate a plain shutdown.
/sbin/shutdown -hP now "Power button pressed"

Since I've changed this , my computers shuts down completely ( poweroff ) .
 
Hope this helps , Kuoi

---

### Post by klytu on 2007-05-07
> **Kuoi said:**
> Hello ,

Can somebody who's computer is not shutting down (poweroff) completely , test the following out  and tell here if it worked ?
 ... it did for me .
Please test it with Edgy and Dapper too , 

I had an issue with the "poweroff " button from the panel.
Everytime I used it , it hangs after a few seconds on a black screen , and I had to push the power button from my computer to turn my computer off .

--------------------------------------

Applications > System tools > Terminal as root

Then type 

At the very end of the text page you'll see this sentence 

Just insert a P after the -h , so it reads like this ... 

Since I've changed this , my computers shuts down completely ( poweroff ) .
 
Hope this helps , Kuoi

I didn't even know I had this issue with Fiesty until I read your post; it has been a long time since I last needed to turn off my computer! Your solution did not work for me, however.  I still have to push the power button. I don't have this issue in Dapper and I didn't have it in previous Ubuntu releases Hoary and Breezy.  

I DO have the same issue in WindowsXP and from what I understand there, it has to do with the way XP interacts with my BIOS ACPI. In XP I can correct this issue by using a different HAL, but when I do that  I get other, different problems that I am not comfortable with. I chose the lesser of two evils there - in the current XP HAL setup  the only issue I am aware of is with shutdown.  I could live with pressing the power button to turn off the computer so I left it at that.  Maybe the issue in Fiesty is related?

---

