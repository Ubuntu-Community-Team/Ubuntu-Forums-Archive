---
title: "windows doesnt allow ubunto boot"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by aijazbaig1 on 2007-05-08
Hello.
I have an IBM T30 laptop which came with windows pre installed. Then I installed ubuntu and it co existed for quite some time. Then i removed windows completely.

Now when I have added windows OS in the un allocated space whch i left earlier intentionally, it directly boots without showin me the option to select which OS i would like boot from.

If there any boot related information that can help me fix this problem id be more than happy.

Lookin for some pointerrs about this.

C ya,

Aijaz.

---

### Post by Sef on 2007-05-08
Read [Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by Terl on 2007-05-08
Windows never plays nice.  When it is installed after Ubuntu windows wipes out the grub bootloader and does not give options to boot other o/s.  You need to reinstall Grub via your Ubuntu cd or you could use a super grub disc.

This page on the wiki will help:  [Reinstalling Grub after installing windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation")

---

### Post by aijazbaig1 on 2007-05-08
Hello There freinds,
I tried the suggestions first the [one]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") by Sef which didnt work for me. To be particular, **I tried the one which preserves the windows bootloader**. That didnt work. **It still booted win XP directly**.

Then I jumped over to the [method]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation") suggested by Terl and I realized that it was basically the same instead I wrote the GRUB to the MBR. Now it seemed that the GRUB gotg loaded during boot. However I still dont see the option for choosing the OS...now instead it loadd direcly to ubuntu. And then it gets stuck in the splash screen during which it is supposed to load all the boot files.

So now I dont see the windows partion neither does ubuntu get booted. So all that happens is that ubuntu tries to boot and gets stuck in the splash screen. Is there something that i can do now?..im a lil scared...:confused: 

Hope to hear from you, ill probably have to rely on the school computers meanwhile..

Best Regards,
Aijaz Baig.

---

### Post by wpshooter on 2007-05-08
This sort of thing is why I prefer to NOT have two different O/Ss on the same computer !!!

I know that does not help you, but good luck, I hope you find a solution.

---

### Post by meborc on 2007-05-08
try reinstalling ubuntu... just remember to install grub to MBR when asked... ubuntu install automatically sees your win partitions... then you should be able to see grub menu with ubuntu / windows lines on it...

---

### Post by Nythain on 2007-05-08
my advice at this point, use a liveCD, mount your physical drives somewhere... back up any and all important data, and start over... making sure to install windows first since its doesnt play nice with others, THEN ubuntu... much easier dual boot that way

---

### Post by aijazbaig1 on 2007-05-08
ah...damn...:( ..i can only think of one way now..i might try to re install ubuntu again. But i do not know if my previous actions have messed up with the windows bootloader or not. or even if they did, i just wanna make sure that the currently installed windows OS does show up on my grub list after I complete re installing ubuntu.

What exactly does the GRUB stand for. Can any one give some more insight in some simple and short words..

Eager to hear what you guys have to say about this.

Best Regards,
Aijaz Baig.

---

