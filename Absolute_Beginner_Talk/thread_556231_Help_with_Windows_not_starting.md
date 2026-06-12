---
title: "Help with Windows not starting"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Zerolance on 2007-09-21
When i start my comp and after choosing windows xp pro on the grub loader it loads the window logo screen then a quick blue screen and the comp just restarts wondering if any can help me with this. I'm not getting any error msg or anything after choosing xp on the loader.

---

### Post by PreviousN on 2007-09-21
When I did a dual boot setup I made sure to have xp installed first. I had 2 partitions when installing windows. 1=windows, 2= for ubuntu

After installing windows I popped in the ubuntu cd and restarted. Then I chose text mode install and installed. When it prompts to modify the mbr, choose yes..make sure it detects windows for the grub menu. Then start ubuntu. 

You should be able to then restart and choose windows. If your getting an error the windows install then you might not have followed steps word for word. 

Windows is very touchy and if you miss a step or do it in reverse mean nasty things happen, (like have linux installed THEN install windows) it'll overwrite your mbr! 

When I set up my dual boot about a year ago that was the case. Heres a guide on the subject:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=2)

You may try this: putting in the windows xp install cd anddoing a "repair" install. it'll overwrite your mbr. Then put in the ubuntu install cd, choose text mode install, then keep hitting cancel till you get a menu. Choose in the menu the last thing, which should be something like "complete installation" and that should reinstall grub to the mbr.

Please correct me if I'm wrong, anyone...


I think I  went in a roundabout way of answering your question:

== Answer ==
1. I don't know which blue screen you're talking about. If its bsod thats usually hardware error.
2. I don't know how to easily fix this problem except for a repair installation. (see below)
2. If a welcome screen, try the "repair" installation on windows install cd
3. After that, reinstall grub to mbr using ubuntu live/install cd.

---

### Post by Zerolance on 2007-09-21
Not sure what the blue screen is either as it was going to fast and sometimes doesnt show up when i try to run windows, but i can choose my windows on the loader it just goes to windows logo then restarts the comp. I did have windows installed first, then partitioned part of my hd for ubuntu. Is there any other way besides using a live cd?

---

### Post by PreviousN on 2007-09-21
Sorry, didn't see your response. You may see I'm waiting on a response for my own problem. 

Anyways, I don't think there's any other way than using a live cd. Because the error is windows related I can see that the people on this forum will/could be like "not ubuntu, not our domain".  So even if there is that I don't know about its unlikely they'll reply...I think.

You may not even have to use the ubuntu live cd btw: I've def (ok,one time like a year ago) used the windows bootloader to run ubuntu. But thankfully, from your description the problem IS NOT a BSOD. So that indicates that the problem is with your windows install, not your hardware.

You might try booting into ubuntu and activating ntfs-write support (add/remove programs, type in "ntfs"). Then it'll find your windows partition and you might be able to recover data that way by copying stuff over/off. Then you may want to restart and see if the problem continues. If it does, disable the ntfs write support and then do the repair windows install. I don't think its THAT time consuming...and its the only way I can think to help you.

---

### Post by hyper_ch on 2007-09-21
it is not related to grub. It would be a grub problem if you coudln't see the windows logo at all. So you have a corrupt windows installation there.

---

### Post by gupta_sumesh63 on 2007-09-21
Use Gparted Live CD to format your win partition.

2.    Reload XP with XP loader CD.

3. If The MBR is overwritten and you boot straight into Windows, then do the following:

4.   Boot with Ubuntu Live CD.

5.     Open the terminal.

6.     Run following commands :

> $ sudo grub

> grub> find  /boot/grub/stage1

(This will give something like root (hd?,?). Usually (hd0.0). May be different in your pc. Suppose its hd0 then run following command:

> grub> setup (hd0)

> grub> quit

7. Then reboot after removing the Live CD.

8. You should boot into Grub screen.

Hope this helps.:guitar:

---

### Post by hyper_ch on 2007-09-21
gupta:

He said he sees the windows logo so that's already way beyond grub... it means the windows partition was correctly found etc.

---

### Post by Zerolance on 2007-09-21
Well when i try the windows install cd both install and repair, it says setup did not find any hard disk drives installed in your computer, but i can see my windows hard drive when i'm in ubuntu
Edit: i forgot to mention that after i choose windows xp under grub it shows a screen where i can choose to start windows safe mode, safe mode with network, safe mode with control, normally, and setting that works, but i tried all these options and they dont do anything. I think it maybe a hard drive detection problem, but in ubuntu i can see my windows file, and my windows isn't detecting that harddrive. Is there any way for my windows to boot that drive that i can see in ubuntu

---

### Post by Zerolance on 2007-09-22
I think the problem is that ubuntu is reading my partition instead of my windows so therefore my windows has nothing to boot. Am i suppose to see my windows partition when i'm in ubuntu sry new to this so i don't know. Is there any way to stop ubuntu from reading my windows partition. I installed ubuntu like this: First i had xp pro tablet edition my this lab, which was working fine and all. Then i installed ubuntu partitioned part of my hd, now i can boot into ubuntu, but not windows. If i remove ubuntu would this problem be solved? and if it will how can i remove ubuntu from my comp?

---

### Post by gupta_sumesh63 on 2007-09-22
My aim was to tell him to reinstall windows after formatting the ntfs partition using Gparted Live CD,which could be corrupt as of now (absolute new install). Thats why I said to reload (what I meant was reinstall windows) and not Grub. In case windows over wrote the grub then my suggestion was to setup grub using Ubuntu live CD. 
I never intended to say that grub was a problem.

other option is to use Win 98 CD which has options to read the drives/partitions.

---

