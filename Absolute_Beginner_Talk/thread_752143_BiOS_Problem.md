---
title: "BiOS Problem"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by slats on 2008-04-11
Hi, I installed 7.10, but now i want to get rid of it and put xp back on until 8.04 comes out and then dual boot. But i am unable to access my BiOS menu to setup boot order, and this was not a problem when i had XP, so it is clearly an effect of Ubuntu. Can Someone help me fix this?

---

### Post by mjwhitfield on 2008-04-11
> **slats said:**
> Hi, I installed 7.10, but now i want to get rid of it and put xp back on until 8.04 comes out and then dual boot. But i am unable to access my BiOS menu to setup boot order, and this was not a problem when i had XP, so it is clearly an effect of Ubuntu. Can Someone help me fix this?Linux nor Windows can effect your BIOS.

---

### Post by slats on 2008-04-11
well before i installed ubuntu i was able to access my BiOS menu and with it on there i can't because it just immediatley boots to Ubuntu

---

### Post by barbedsaber on 2008-04-11
to acces your bios, you have to pay CLOSE attention to when your computer is booting up, right at the start.
it will say press del, or f12 or somthing like that to accecs bios settings.

if that is not what you needed, can you please define unable to acces bios menu, ie what happens at boot up, so we can be more help.

---

### Post by slats on 2008-04-11
i have to enter a password to boot my computer
and i after that i have to hit F2, but when i had XP it would say at the bottom of the screen to press F2 to access BiOS menu, but now it doesnt even say that, and i hit f2 and nothing happens it just boots to ubuntu, and i tried it with my hard drive unplugged and it still wouldnt give me the option, it would just say boot failed

---

### Post by smurphy_it on 2008-04-11
You should start hitting F2 before it gets to the prompt to ask for your password.  Usually if you've made it that far (assuming it is a power on password) you are gone too far.

---

### Post by slats on 2008-04-11
right once i turn it on it asks for my pass
i tried hitting f2 there but it did nothing

---

### Post by slats on 2008-04-11
noone can help me?

---

### Post by Therion on 2008-04-11
This IS your PC, correct? 

If the password prompt absolutely prevents you from accessing the BIOS menu, you're going to have to disable the password prompt, simple as that.

---

### Post by zwygart on 2008-04-11
Hi,

I will try to say some tips that where not mentionned. Try by hitting F10. Any other F key. Before password and until 5 seconds after, don't stop pressing the key. 

If nothing works, it had a ultimate way to solve someone like this : flushing the BIOS.

This way it erase ALL things in the BIOS : Time/Date set, boot sequence, every passwords (user, administrator), and so far. So after you have entire access to the bios and have to settings it.

They are various ways to do that. Some are more hard some are less. Search on the Web and you will find some interesting issues.

I personally used this method one time and it worked perfectly. In the computer it had a little battery. I don't know if yours. Remove this battery for 15 minutes and unplug the computer. This way the machine have not electricity to keep memory of BIOS at live. After put it back and every thing should be disappeared (password, boot screen, etc.) If 15 minutes are not enough, try 12 or 24 hours. 

N.B.: erase ALL on the BIOS means on the BIOS. Your hard drive will not happen anything (lossing data). If it works please post.

---

### Post by stchman on 2008-04-11
> **slats said:**
> Hi, I installed 7.10, but now i want to get rid of it and put xp back on until 8.04 comes out and then dual boot. But i am unable to access my BiOS menu to setup boot order, and this was not a problem when i had XP, so it is clearly an effect of Ubuntu. Can Someone help me fix this?

The installation of an OS will not affect your BIOS.  I access my BIOS my hitting the delete key during POST.

---

### Post by slats on 2008-04-11
> **Therion said:**
> This IS your PC, correct? 

If the password prompt absolutely prevents you from accessing the BIOS menu, you're going to have to disable the password prompt, simple as that.

yes it is mine 
and i cant get rid of the password without getting into the BiOS

---

### Post by wolfen69 on 2008-04-11
sometimes the motherboard will have 2 little metal posts near the battery. connecting the two will reset bios. use a screwdriver to touch both at the same time. or a little plastic jumper. it's easier than removing battery.

---

