---
title: "Cant install Ubuntu on HP computer"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by enetic on 2007-08-24
I bought a new HP laptop today, and i want to install ubuntu on it. I tried to install the x86 version but it dident work. then i found out that i had to download the amd64 version, but that did not work either. i dont know what the problem is, but every thing i try, wont help. 


i tried to install the newest version of ubuntu.

Do someone here know whats wrong?


thanks in advance 

(urgent!!!)

---

### Post by brownknight on 2007-08-24
Can you be more specific with the problem? Did you mean you downloaded ubuntu and burned it on the CD and the CD woul not run? Did you download ubuntu and burn it as .iso?

---

### Post by logos34 on 2007-08-24
Depending on what problem it is you're having, you might want to take a look at these links:
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
[https://help.ubuntu.com/community/BootOptions?highlight=%28boot%29](https://help.ubuntu.com/community/BootOptions?highlight=%28boot%29)

EDIT: and 64-bit capable CPUs can run either x86 or AMD64/EM64T version.  So you don't 'have' to run 64-bit version of ubuntu

---

### Post by oilchangeguy on 2007-08-24
i think this is a better iso how to link:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by crjackson on 2007-08-24
> **enetic said:**
> I bought a new HP laptop today, and i want to install ubuntu on it. I tried to install the x86 version but it dident work. then i found out that i had to download the amd64 version, but that did not work either. i dont know what the problem is, but every thing i try, wont help. 


i tried to install the newest version of ubuntu.

Do someone here know whats wrong?


thanks in advance 

(urgent!!!)

okay, I take it you have an AMD64 system since you think you MUST have that version.  That is a false assumption however.  If you have an AMD64, either version should install.  x86 is the 32 bit version, the other is the 64 bit version (my preference).

Can you describe exactly what you mean by "it didn't work"?

---

### Post by ritterrav on 2007-08-24
Aswell as the EXACT specifications of your laptop?

---

### Post by A3sthetix on 2007-08-24
These links will help you (note my specs in my signature):

[http://ubuntuforums.org/showpost.php?p=3218583&postcount=7](http://ubuntuforums.org/showpost.php?p=3218583&postcount=7)
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

This might also help you on your quest:
[http://wubi-installer.org/](http://wubi-installer.org/)

Note:
Most HP / Compaq laptops require the same steps. I've noticed this with all dv6xxx dv9xxx and dv2xxx
The most important thing is the boot parameters. Once you get in, install all updates reboot again using the same params. Install you graphics and wireless. Once that is done, you won't need the special boot params (atleast in my case).

Good luck!

---

### Post by enetic on 2007-08-25
thanks, but i got it to work. my problem was that i booted my laptop with the Ubuntu amd64 cd. it would not start, but then someone told me to press f6 or something (other settings) when booting up, and write noacpi (i may be wrong, i have a problem with remembering the commands in linux...) or something...

---

