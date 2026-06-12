---
title: "Same Old KVM Issue"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by flatline on 2006-06-02
Ok, so I have been looking for a solution to this problem for several months now.  It started with Breezy, and I was hoping doing a dist-upgrade to Dapper would fix it... but no dice.

I have scoured the forums for a solution, and there are many, many posts on this topic.  But none of them are concise or helpful.  Most are like "Well, my KVM works.  So bollocks to yours."

Can an experienced Ubuntite give me an answer to this?  I saw several posts that were [Locked] so I couldn't find out the latest status.  Is this something that is not going to work?  I have this KVM and I'm not exactly thrilled over the prospect of having to drop $50-60 for a new one.

I've checked these posts (and others) and tried and nothing has worked:
[http://www.ubuntuforums.org/showthread.php?t=6550&highlight=mouse+kvm]("http://www.ubuntuforums.org/showthread.php?t=6550&highlight=mouse+kvm")
[http://ubuntuforums.org/showthread.php?t=142092&highlight=KVM+mouse]("http://ubuntuforums.org/showthread.php?t=142092&highlight=KVM+mouse")
[http://ubuntuforums.org/showthread.php?t=156183&highlight=KVM+mouse]("http://ubuntuforums.org/showthread.php?t=156183&highlight=KVM+mouse")

This isn't a world-shattering problem, but the frustration it causes is ridiculous and seems so unnecessary.  At this point I would be willing to put a bounty up for a solution.




Here is my original post:

Ok, so I just installed Breezy **(Dapper now)**. First-time with Linux. I tried searching the forums, but everything seems to be referring to Hoary or Warty, and the fixes listed did not work for me. Here is my issue:

[LIST]
[*]I just got the new 2-port PS/2 KVM "Flip" from Belkin. If it matters, one end is my girlfriend's XP box, the other is my Ubuntu box.
[*]I'm using the USB mouse that came with the XP box with a USB-to-PS/2 converter.
[*]Whenever I switch to Ubuntu, the pointer goes bananas, randomly moving and clicking all the buttons whenever I move the mouse at all. If I unplug the mouse and plug it back into the KVM switch, after a second it recognizes it and all is well until the next time I try to switch.
[/LIST]

Searching the forums, I tried a fix from 4.10, by adding a file to /etc/modprobe.d that included the line: "options psmouse proto=imps".

Another thread in the forums from 5.04 suggested I modify /etc/modules to include the line "psmouse proto=exps".

Neither of these solutions fixed my problem. I understand this may be a kernel thing, or it may be an issue with using the USB-to-PS/2 mouse in a KVM switch. Whatever it is, it's driving me up a wall. Does anyone out there have any prognosis on this? Will getting a USB keyboard and a USB KVM switch save me?

Thanks in advance,

Matt

---

### Post by stevanbt on 2006-06-02
Hi Matt,
I'm no expert, but I think the most likely cause of your problem is the usb-to-ps/2 converter.  Your KVM is expecting to have ps/2, who know's what the usb-to-ps/2 converter is doing to the signal.  Do you have a spare ps/2 mouse?

I know this won't be of any comfort, but I have a KVM (ps/2 all round) and it works like a dream.

Cheers, Steve.

---

### Post by bobpur on 2006-06-02
I've read the forums, too, and have not been able to solve my KVM switch problems either. My impression is that the extra length of the cables causes signal degradation leading to poor sound quality (If yours supports sound), poor picture and video quality and poor keyboard and mouse response. 
Other people in the forums have working KVM Switches and are happy with them. USB seemed to work better than PS/2, but it wasn't great either.  I have two KVM switches and can't get either one to work.
My final solution, An "L" shaped desk, two complete computer setups and a swivel chair.
You are not alone with this problem. My switches now reside in a drawer.

---

### Post by Geekboy on 2006-06-03
It really seems like Ubuntu does not like PS/2 KVMs.  I have an 8 port and always had problems with Ubuntu.

I also had the problem with the USB to PS/2 converter.  It just would not work for me.

 So I broke down and bought an optical PS/2 mouse at Target for aound $10.  I also had to add "psmouse proto=exps" to my  /etc/modules for it to work.  Once I did that everything was fine.  If you have an old PS/2 mouse try that.

My last problem is that the mouse won't work if I boot up and have my Ubuntu PC selected on my KVM.  I have to leave my KVM switched on another PC and wait till I get to Ubuntu's logon screen.  Then I can switch over and everything works fine.  I suspect that this is a problem with Ubuntu and a PS/2 optical as I do not have this issue with a standard PS/2 mouse.

---

### Post by erniewinner on 2006-06-03
i use a belkin 4 port ps2 box. i play some dos games which usb can't do and would prefer ps2 to usb anyway. (longer better support.) if the mouse is your only problem you won't need to pay out for a new box just a mouse... at ebuyer a scroll mouse is 59p... also i think the belkins have an updateable bios on them? check that out. i have had no issues with a usb to ps2 adaptor... electrically all is the same once converted??? perhaps you should look into the make of the mouse and then look up any issues it has in ubuntu? :rolleyes:

---

### Post by Stew2 on 2006-06-03
Okay, I don't have a Belkin KVM so I am not sure exactly how they work but I do have a D-link DKVM-2K Kvm switch. I am also using a USB to PS2 adapter that came with the mouse (I think most mice come like this now anyway, I have about half a dozen diffrent ones and they all seem to use the same adapter). 
     The documentation that came with the switch doesnt mention any linux support whatsoever, I suspect this is why they can be tempermental with linux. Mine switches over fine say 7 out of 10 times. The other 3 or so times I switch I lose my mouse input altogether or everything goes nuts when I move the mouse (menus opening all over etc. :) ) Never have a problem though when switching over to my XP gaming machine. Im not sure if there is anything you can do in linux to fix this, but on my D-link there is a key combination "scroll lock + scroll lock + M", which resets the keyboard and mouse if they are giving you trouble. This has always solved the problem for me. I wouldnt doubt that your Belkin switch has something similiar. I found the command in the troubleshooting section of the manual for my switch. Hope this helps, I know how annoying hardware incompatibilities can be... I have an ATI video card ;) 

Regards,
Stew2

Edit: Summary of my rambling post,
1) Most KVM's (maybe all) don't support linux.
2) I don't think its a problem with usb to ps2 adapter, almost all mice come like this now anyway.
3) See if your switch has a key combination to reset keyboard and mouse (after switching to ubuntu box)... most switches do.

---

### Post by TuxCrafter on 2006-06-03
maybe this wil work

```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

or make a script of it

make a new file paste the text in it.
```

#!/bin/bash

sudo modprobe -r psmouse
sudo modprobe psmouse
```

change the file to be executable and run in terminal

---

