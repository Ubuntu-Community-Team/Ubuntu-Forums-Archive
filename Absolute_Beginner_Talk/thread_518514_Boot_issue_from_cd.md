---
title: "Boot issue from cd"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by flatlandinpunk17 on 2007-08-06
ok i am rather new to ubuntu and i am trying to install ubunut feisty on one of my desktops. i already have it running on my laptop using the same disk that i am having the issue i am posting about and i installed it on my laptop after having this issue so i know it is not the disk. 

anyway on with the issue. 

when i boot from the cd if i either go with boot normally or boot in safe graphics mode it locks the whole machine up keyboard and mouse are completely unresponsive. this happens after the boot splash screen comes up and shows what is loading it loads restricted drives the splash screen goes away and everything is still responsive at this point and then it just locks up. desktop background is shown but nothing. the only way to get out of this is to hold down the power button or to hit the reset button. 

thanks in advance for any help

---

### Post by shadowen2 on 2007-08-06
I had a similar problem with my installation.  I have a Biostar motherborad and I found that I had to add an argument to the initial boot up in order to make it work.

I did this by pressing F6 on the initial boot up screen (after it loads from the CD) then added "linux noapic" to the end of the line that came up...pressed enter...and away it went.

Good luck!

---

### Post by overdrank on 2007-08-06
> **flatlandinpunk17 said:**
> ok i am rather new to ubuntu and i am trying to install ubunut feisty on one of my desktops. i already have it running on my laptop using the same disk that i am having the issue i am posting about and i installed it on my laptop after having this issue so i know it is not the disk. 

anyway on with the issue. 

when i boot from the cd if i either go with boot normally or boot in safe graphics mode it locks the whole machine up keyboard and mouse are completely unresponsive. this happens after the boot splash screen comes up and shows what is loading it loads restricted drives the splash screen goes away and everything is still responsive at this point and then it just locks up. desktop background is shown but nothing. the only way to get out of this is to hold down the power button or to hit the reset button. 

thanks in advance for any help

HI and if I understand you, you had a similar issue when installing feisty on your laptop? If you could give us some specs on your system you are installing on?

---

### Post by flatlandinpunk17 on 2007-08-06
ok i tried that and it hangs at the same place. doing the same thing.

---

### Post by flatlandinpunk17 on 2007-08-06
> **overdrank said:**
> HI and if I understand you, you had a similar issue when installing feisty on your laptop? If you could give us some specs on your system you are installing on?

no it installed fine on the laptop sorry for my bad wording. 

system specs

512ram 
128 nvidia graphics card (it has been a long time since i installed it so i do not remember the model number)

got the other board and processor from a friend the motherboard model number is k5s7a yes i do remember that lol.  its an amd processor running at 1.3ghz

---

### Post by asmoore82 on 2007-08-06
how much RAM is in the laptop and how much is in the desktop?

---

### Post by flatlandinpunk17 on 2007-08-06
> **asmoore82 said:**
> how much RAM is in the laptop and how much is in the desktop?
both have 512.

---

### Post by asmoore82 on 2007-08-06
just for your own sanity, I would check the CD just to be sure ...

place it in the Ubuntu laptop, open a terminal and ...

```
~ $ dd if=/dev/cdrom | md5sum
```
and post the ouput (it will take 5~6 minutes before there is any)

---

### Post by flatlandinpunk17 on 2007-08-06
ok so i got it fixed.

in replying with the computer specs i remembered i had overclocked this computer a while ago because i used it as a gaming machine. well i went in and un-overclocked it and now it works perfectly. 

thank you for all your help.

---

### Post by overdrank on 2007-08-06
> **flatlandinpunk17 said:**
> ok so i got it fixed.

in replying with the computer specs i remembered i had overclocked this computer a while ago because i used it as a gaming machine. well i went in and un-overclocked it and now it works perfectly. 

thank you for all your help.

Great glad you got it up and running! :popcorn:

---

