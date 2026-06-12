---
title: "Help with a restricted driver, please"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by RWise on 2008-02-05
Ok yesterday, along with the usual *updates are ready* I got a notice that there was a *new restricted driver* for my system. So,,, I clicked on it and there were 4 or 5 in the list, the first one was for 3D graphics. Ok I like graphics,,,, so,,, I checked it to enable it,,, ouch! Now all I can get is 640 by 480, and it is not in the list of restricted drivers in system/administrator/restricted drivers manager, there is only for the modem (it is not enabled) that I do not need to use (high speed internet). I am new to Linux and ubuntu and am quit lost. 
How can I remove said driver, or go back to the way it was before? 
If I reinstall using a fresh download will it repair or over right everything?

I love this OS and think it should have Billy boy shaking in his boots! ;)

---

### Post by ichbinesderelch on 2008-02-05
what graphic card do you use?

---

### Post by RWise on 2008-02-05
It is built in intel 82845, (gateway box) (I know I should have built it myself) the last reboot it accepted it as the card in use and looks better. In another thread on the quiet splash I did
uname -r

followed by
sudo update-initramfs -u -k 2.6.22-14-386

then when I rebooted is when it took the card (intel 845) and looks better

now if I can get rid of the quiet splash but thats another thread!

---

### Post by RWise on 2008-02-05
Thanx for the help, I think I have it now, and got rid of the quiet splash also, and the multi entries for boot options.
And Thanx to all who moderate, develop or otherwise maintain this site and Ubuntu!

Bill Gates MOVE OVER!:guitar:

And someone please mark this as solved!:)

---

