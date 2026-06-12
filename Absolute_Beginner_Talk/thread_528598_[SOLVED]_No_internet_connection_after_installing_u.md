---
title: "[SOLVED] No internet connection after installing ubuntu (includes live cd as well)"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by teddyhugz99 on 2007-08-18
Okay I have no internet connection as of right now when i get into ubuntu.  How do i get one to work?  Here are my "stuff":

Connection type: Cable modem (no wireless routers)
Connected: ethernet via Realtek onboard ethernet
Computer config: dual boot with windows vista and ubuntu

Now i am able to get on the internet with vista but not ubuntu. after trying the "pppoeconf" and basic procedure, it still dont work but please tell me how to do the procedures properly cuz i may have missed something.  I really need help and i want to switch to ubuntu:KS but i still want internet connectivity:(.  I will reinstall ubuntu today to start off fresh and just give me help from here.  I feel soo nooby with ubuntu....and i dont like that....

---

### Post by teddyhugz99 on 2007-08-18
o yea i tried rebooting the modem and it didnt work either

---

### Post by Ek0nomik on 2007-08-18
Here is a thread which seems very related to your problem:

[http://ubuntuforums.org/showthread.php?t=523061](http://ubuntuforums.org/showthread.php?t=523061)

Please respond in this thread to let us know if it worked.  If so, please mark the thread as solved by clicking the 'Thread Tools' button to the far upper right of the screen.

---

### Post by teddyhugz99 on 2007-08-18
Is there any other way???  Is there a way to stop windows from putting my NIC asleep...cuz this can get annoying jus unplugging and replugging....i just dont know if it works yet so ill try it first.

---

### Post by damansandhu on 2007-08-18
ok , tell me what type of internet connection you are using , dsl or others?

---

### Post by damansandhu on 2007-08-18
ah, click on knetwork manager , then on manual configuration , then type on ip , dns gateway , you have to manually configure it .

---

### Post by teddyhugz99 on 2007-08-18
Actually u know wut I found a way to wake up my NIC...I used the bios.  If you want to know here is how to do it:

Go to the BIOS by pressing the appropriate key aka "Setup".  Then look for an option in one the menus that say "onboard LAN Boot ROM".  Then Enable it and save and exit the BIOS.  This should work in _almost_ any case where the NIC card is sleeping after windows shutdown or anything else.  This should be the first option before going into ubuntu to do some fancy coding since most of the time the NIC is sleeping when going into ubuntu.

I appreciate all your help guys and I hope this tip will help most users get online.  O yea if there happens to be a message sayin "configure device LAN" or something like that, you dont really need to do it unless u want to disable the message by going into the configuration and press disable where it says show message.

---

