---
title: "Can't install windows xp"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by durus on 2007-01-11
Hi
I want to install windows xp on my first partition, but windows does not replace grub so I can't continue installing windows. 

I do boot from the windows cd, and after some configurations windows inserts some files on c and reboots, to continue with the installation some windows files must boot up, but grub starts instead and booting up ubuntu.

Do you know how i should config grub so that i can continue with the installation ?

---

### Post by JermainWijnhard on 2007-01-11
I don't know a lot, but i went for a dual boot install aswell and the advice i've gotten was to have ubuntu installed AFTER windows. I'm guessing its because of the problems you are experienceing now :/

---

### Post by jvc26 on 2007-01-11
I thought windows would automatically overwrite your MBR with the windows bootloader - that is why the advice is to install Ubuntu second, so that GRUB remains on your MBR and you can boot from the chainloader.
Can you post up the contents of the file:
/boot/grub/menu.lst
That will tell us if GRUB recognizes the windows installation. If not you would need to add the windows install to GRUB, however, I'm not sure whether thats particularly easy, as because windows hasnt completely installed yet - does this mean that the windows bootloader also hasnt installed... hence you wouldnt be able to launch it via GRUB.
Il

---

### Post by justin_c18 on 2007-01-14
Here's a good URl;
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo")

---

### Post by durus on 2007-01-16
thx, sorry i did forget this thread as i fixed the problem, i uncomment the windows lines in the grub setting files, and it worked

---

### Post by Jack Shankle on 2007-01-16
I tried installing UBUNTU after windowsXP and it didn't work.
Am thinking of giving up on UBUNTU.

---

### Post by ljpm on 2007-01-16
> **Jack Shankle said:**
> I tried installing UBUNTU after windowsXP and it didn't work.
Am thinking of giving up on UBUNTU.

Rather than telling us that it didn't work, ask for help.

If you do not know what to ask then even stating that will result in numerous post pointing you to howto guides and step by step instructions. 

Eventually you will learn enough to ask the right questions and soon you will start solving other peoples linux problems. 

I started playing with Linux in July, finally got it working properly in Aug. Screwed it up 3 or 4 times, reinstalled 6 or 7 times and have already helped others with problems related to xorg.conf, partitions, grub, screen resolution.

And still having fun screwing things up. Next challange is MythTV (third try). Hopefully I can limit my reinstallations to 1 or 2.  :D

---

### Post by bootslap on 2007-01-16
Yeah ... I second that... I have also installed, uninstalled and reinstalled ubuntu and XP atleast 8 times. Finally, I have got it loaded as I wanted but I am unable to browse... But, I still love ubuntu, the ubuntu community and the freedom... Rather than quitting ... the fun is in surmounting the problems, and eventually gaining mastery over it...

Ask questions and you will be helped.....

---

