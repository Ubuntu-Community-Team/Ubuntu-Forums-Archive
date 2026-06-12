---
title: "I need to give up!!!"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by naturalhl2 on 2006-01-09
Ok I install ubuntu and got the grub loader working right and everything.. windows xp and ubuntu both work fine!! my first Successfull duel boot! Now this is my promblem I forgott the formatt I typed my password.... I may be getting my username or password wrong is there a way for me to change my password without reinstalling Ubuntu..??

---

### Post by Masteroc on 2006-01-09
This might help you out...

[HTML]https://wiki.ubuntu.com/LostPassword[/HTML]

---

### Post by aysiu on 2006-01-09
[QUOTE=Masteroc]This might help you out...

[HTML]https://wiki.ubuntu.com/LostPassword[/HTML][/QUOTE] Why is it so easy to reset the password? So anyone can take over your account?

---

### Post by Masteroc on 2006-01-09
would you rather have it so that you cant reset your password and lose all your data?

But i do agree partially, i think that it is easy to change the password and some measure of security should be added. Maybe a security question, but someone could always forget that too :confused:

---

### Post by t_huankiat on 2006-01-09
[QUOTE=Masteroc]would you rather have it so that you cant reset your password and lose all your data?[/QUOTE]
choice is pretty obvoius isn't it? LOL!

---

### Post by Masteroc on 2006-01-09
yeah it is!

---

### Post by naturalhl2 on 2006-01-09
Ah thank you guys for the help but I just reinstalled linux Im soo proud of my self with the duel boot dont call me stupid but Ive been trying it for years I suck at numbers..

---

### Post by Masteroc on 2006-01-09
not vary patient are you?

Good job on the reinstall and dual boot!

---

### Post by naturalhl2 on 2006-01-09
eh Im a little unpatient but if I wasent patient I would have given up on linux years ago.. Installing Java is out of this world! HARD!

---

### Post by aysiu on 2006-01-09
[QUOTE=Masteroc]would you rather have it so that you cant reset your password and lose all your data?

But i do agree partially, i think that it is easy to change the password and some measure of security should be added. Maybe a security question, but someone could always forget that too :confused:[/QUOTE] I thought the whole point of a password is that you don't forget it, and you're forced to type it in twice, too, just to make sure you didn't mistype it. If *anyone* can press Esc at Grub and reset your password, I don't see the point...

---

### Post by Mustard on 2006-01-09
[QUOTE=aysiu]Why is it so easy to reset the password? So anyone can take over your account?[/QUOTE]

Grub comes with the option to have a password on it, which many users would probably not use.  Ideally in a multi-user environment, the password for grub would be set.  

Ofcourse on the flip side of this,  the user above would have been totally stuffed if he had forgotten both his grub password and user password. :)

I recall reading a thread somewhere about how to lock down your machine completely, but I don't recall where atm.  I think in addition to a password on grub, you would need to limit access to the CD drive as well, as someone could use a LiveCD to access your system as well.  Any method that allows someone to get root access is a security problem.  The moral of the story I suppose is don't forget your passwords, and password lock everything you can.

---

### Post by naturalhl2 on 2006-01-09
Guys.... How come when I try to install my nvidia drivers it asks for my password and I cant type it in my terminal when it asks??

---

### Post by Mustard on 2006-01-09
[QUOTE=naturalhl2]Guys.... How come when I try to install my nvidia drivers it asks for my password and I cant type it in my terminal when it asks??[/QUOTE]

The key presses are hidden in terminal.  The key presses are registering, but not visible.  Just type your user password in and press enter.

---

### Post by GreyFox503 on 2006-01-10
This is one reason you might want to set the root password.  I haven't tried the second method in the wiki, but if you choose "recovery console" in GRUB, you will need to enter the root password if it has already been set.

---

### Post by az on 2006-01-10
[QUOTE=GreyFox503]This is one reason you might want to set the root password.  I haven't tried the second method in the wiki, but if you choose "recovery console" in GRUB, you will need to enter the root password if it has already been set.[/QUOTE]


...That's what the second method is for.  


No root password.  You don't need it.

As for security - the very basic reality is that anyone with physical access to your box can become root or access all your data.  Unless you have an encrypted drive, all your data is theirs - if not by a kernel on a live cd, by a screwdriver.

---

### Post by naturalhl2 on 2006-01-10
Wow thanks alot guys for the help but I have one more question.. ok when I restart my computer and when the Grub loader comes up I see 2 copies of the same Ubuntu setup? How can I delete one?? There is like two of everything and I only installed ubuntu once on this partition??

---

### Post by emperor on 2006-01-10
[quote=naturalhl2]Wow thanks alot guys for the help but I have one more question.. ok when I restart my computer and when the Grub loader comes up I see 2 copies of the same Ubuntu setup? How can I delete one?? There is like two of everything and I only installed ubuntu once on this partition??[/quote] 
With every kernel upgrade there will be another entry unless you uninstall the older kernels, which will remove the entries automaticly.

The file of interest is "/boot/grub/menu.lst"

---

### Post by Chipmunk on 2006-01-10
slight thread hijack: How does one uninstall the old kernels? I have been running an updated kernel for ~3 weeks now, no signs of instability, and would like to reclaim the disk space (it's only a 3G drive).

---

### Post by naturalhl2 on 2006-01-10
So how would i be able to delete the one I dont need?? Another question.. sorry Im finally understanding all this soo im asking alot of questions.. I got my nvidia drivers installed but the Settings file in home How can I make that more accesable without having to hunt threw the home folder??

---

### Post by emperor on 2006-01-10
[quote=Chipmunk]slight thread hijack: How does one uninstall the old kernels? I have been running an updated kernel for ~3 weeks now, no signs of instability, and would like to reclaim the disk space (it's only a 3G drive).[/quote] 
Very Carefully :p

use Synaptic but be carefull you ONLY REMOVE the OLD kernel image, resticted packages, and etc. Check the 2.6.12-xx numbers twice or even 3 times!

Be sure you know what kernel you are running!!!

---

### Post by naturalhl2 on 2006-01-10
whats the old numbers?? and new numbers??

---

### Post by DirtDawg on 2006-01-10
It seems to me like the earlier suggestion of a security question is not a terrible idea. 

I also didn't know it was *that* easy to break into an Ubuntu box. I suppose the password feature is more or less for multi-user systems, not super-security.

---

### Post by Mustard on 2006-01-10
[QUOTE=naturalhl2]whats the old numbers?? and new numbers??[/QUOTE]
He would be talking about the old version 'numbers' and the new version numbers.

Using my GRUB menu.lst entries as an example, this is my current kernel I boot into (ie the one i choose to boot into from the grub menu at startup)

```
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot


```

This is the new kernel I  have listed in my GRUB menu.
Note that it is version **2.6.12-10-386**

```
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

```

This is the old kernel I have listed in my GRUB menu.
Note that is is **2.6.12-9-386**


So the numbers are very similar, except for the '9' and '10'.  Which is why it was advised that you use caution when choosing which kernel to uninstall as you may uninstall the wrong kernel.  In my example, you would want to uninstall the '9' version, not the '10' version.  Also you should check which kernel you are currently running on, so that you are not trying to unistall the kernel that is actually running your system at the time.  You can do this with this command..

```
uname -r
```

-edit-

Doh..made a silly mistake and posted the same grub menu listing for both kernels..Its the right one now.

---

### Post by naturalhl2 on 2006-01-10
so that code you gave me tells me what kernal im running off of...?? if soo Im running off 9.. soo I need to reboot back into 10 correct?

---

### Post by Mustard on 2006-01-10
[QUOTE=naturalhl2]so that code you gave me tells me what kernal im running off of...?? if soo Im running off 9.. soo I need to reboot back into 10 correct?[/QUOTE]

That would be correct.  Look for the '10' kernel in your grub menu and boot into that one.  You can do the uname -r command again when you get in, to confirm in your own mind what is going one.

---

### Post by naturalhl2 on 2006-01-10
Ok soo I need to restart and boot into 10 right on.. after I get into 10 how would I go about deleting 9 threw the respatories?

---

