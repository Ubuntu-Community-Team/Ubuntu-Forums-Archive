---
title: "Trying to update NVIDIA driver causes x-server failure???"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Kawasaki12 on 2007-08-02
as the title says, i tried to download a driver from NVIDIA (NVIDIA-Linux-x86_64-100.14.11-pkg2.run)....but it said something about root dictionary, so i tried something that a forum said (forget the link though..)...it said that i needed to uninstall the current driver, then install the new driver while having xserver off....so i've tried it, but as you can tell, it didnt help me out that much, lol...so i've actually got the chance to install the driver during the non-GUI terminal, then i wrote startx....then i actually got it to work!!!........but then whenever I turned off (restart) my computer and turn it back on, it does the same thing....i've tried tons of thing, going back to an earlier x-server configuration to creating a whole new x-server configuration.....maybe if i install the old NVIDIA driver in the Synaptic Package Manager???  Plz help guys.....

btw, sorry for making help threads.  Its just that Linux is a challenge for me ;)

---

### Post by asmoore82 on 2007-08-02
the nvidia drivers are available through apt/synaptic in the package 'nvidia-glx'

---

### Post by Kawasaki12 on 2007-08-02
> **asmoore82 said:**
> the nvidia drivers are available through apt/synaptic in the package 'nvidia-glx'

lol, i know..but i've tried to install the drivers through the nvidia website...but it was unsucessful...unless i installed it in the non-GUI terminal (when the x-server is crashed) then typed in startx...but thats only a temp. fix...ive tried converting back to nvidia-glx, then restarted my computer.  but it gave me the same x-server error message.....but now i've downloaded different nvidia drivers...but i dont want to restart my computer to find out that it will have the same message waiting for me, lol.....any other suggestions?

---

### Post by Kawasaki12 on 2007-08-02
any other suggestions??? common guys, lend out a friendly helping hand...

---

### Post by Kawasaki12 on 2007-08-02
well im going to try and restart my computer.  I'll report back if it or doesn't work...Hopefully you guys can help me out with this problem...thanks
btw, when i going to the quit button, it doesn't show the turn off or restart button....weird???  is it apart of the problem???

---

### Post by Kawasaki12 on 2007-08-02
well i'am back and when i restarted my computer, the Nvidia logo kept on flashing a couple of times, then it went back to the usual x-server error screen...I've tried installing the Nvidia drive that got it to work temp., but it didnt work this time, so i've  entered the code ```
sudo apt-get install nvidia-glx
``` which installed sucessfully, but when i typed in startx, it wouldnt start up...so i have to reconfigure the x-server settings...this time, i've changed the video driver thing to VSEA (i think thats how its spelted) because i've heard that that has worked for other people...so now im going to try and restart my computer AGAIN to see if this time it works.....hope me luck :)  feel free to give me advice...i really need it, lmao

---

### Post by Kawasaki12 on 2007-08-02
well i've believed that that has did the trick....i would love to say thanks, but only one person has actually attempted to help...so i guess i should be proud that i've solved my own problem ;)

---

### Post by Raineer on 2007-08-02
Very strange that you actually SAW the nvidia logo and then xorg crashed...

Typically when I've seen that it's because a mouse or keyboard definition failure.  Usually X will crash before the logo if it's a driver issue.

Sorry about people not helping fast enough, there are hundreds of xorg-type threads every day.  A quick search and you would have found the steps to setup an Nvidia driver probably 100 times over.  Glad you got it figured out though.

---

