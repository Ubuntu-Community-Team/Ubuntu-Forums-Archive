---
title: "problem loading ubuntu -- hardware problem?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by badperson on 2007-12-02
Hi,

I described this issue in an [earlier post]("http://ubuntuforums.org/search.php?searchid=32360728"), but I'm still having the same problem. 

1. I had a machine with win xp installed on it that I had in storage over the summer while I was in the process of moving. When I got in the new place, I tried to start it up, but it gave me an saying it couldn't find c:\system\config\ or something like that, and that I should repair it with the system disk. 

2. I didn't have the same disk that had been used to install xp (xp pro was installed, and I had an xp home upgrade disk) I tried to do a reinstall of win xp, but I got a bluescreen. 

3. Then, I tried installing ubuntu desktop. I verified the cd was in good shape, and successfully installed ubuntu on another machine with that cd, so I know it's ok. I also checked the iso file that is described in the ubuntu documentation. 

4. when I installed, the bios went through ok, I got the main install screen, hit enter, I got the "installing linux kernel" message, then it just hung on a blinking cursor. 

5. Just recently, i opened up the machine, disconnected the HD's, and installed a new HD, I tried to install ubuntu again, with only the new drive connected. The new drive was detected in the setup menu, but I had a repeat of the same problem; I got the intitial ubuntu install screen, hit enter, I got the "installing linux kernel" message, then it just hung on the cursor again. 


could it be a problem getting power to the hd? I tried hooking the drive to the motherboard (using the red cable) with a new cable, i pulled out the PS connection and re-inserted it. 

anyone have any ideas? 
thanks, 
bp

---

### Post by st33med on 2007-12-02
Try checking your power supply. It could be that it is not correctly powering the Hard Drive. Is your motherboard bad? Is the hard drive making funny noises? Can you try a memory check in the LiveCD?

One last thing: in the LiveCD, go to the terminal and put the results of this command:
```
lspci
```

---

### Post by badperson on 2007-12-02
Hi...dumb question....is the LiveCD the ubuntu install disc?
bp

---

### Post by st33med on 2007-12-02
Yes, the Live CD is the normal Ubuntu install disk, providing you did not hit the checkbox at the download options for the Alternate CD. Also, there is no such thing as a dumb question. There are, however, dumb answers. :)

---

