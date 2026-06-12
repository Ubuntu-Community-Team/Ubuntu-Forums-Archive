---
title: "Uninstall Ubuntu from laptop?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2007-02-27
Well seeing as I cant get Ubuntu to work on the Acer laptop, I need to uninstall it.  I installed it to duel boot with xp, and I know that I could just delete the partition, but seeing as I can't see anything on the screen, I can't use gparted.  I can use the recovery mode so is there any command I can use to delete the Ubuntu partition and return it to windows?

---

### Post by Ek0nomik on 2007-02-27
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

[http://www.michaelstevenstech.com/r_c_cmds.htm](http://www.michaelstevenstech.com/r_c_cmds.htm)

Hope this helps!

What couldn't you get working w/ Ubuntu?

---

### Post by annda on 2007-02-27
you can use the gparted boot CD (gparted.sourceforge.net) to remove the ubuntu partition.

you will still have to remove grub - the bootloader. you will need a windows install CD - not recovery! to do that easily. see links above from Ek0nomik.

if you only have a win recovery cd, this will get a bit more complicated.

---

### Post by Russty of Oz on 2007-02-27
Thanks for the help.   Pity about not being able to install it on the laptop.

---

### Post by annda on 2007-02-27
> **Russty of Oz said:**
> Pity about not being able to install it on the laptop.

Yes, it is. Try again soon! It's all getting better almost day by day.

---

### Post by Russty of Oz on 2007-02-27
Out of desperation, I just tried a Freespire CD on the laptop and it WORKS!!!  Now, I want to run Ubuntu not Freespire, so now that I have got something on the screen, and I can see the Ubuntu files there too, is there anything I can do to be able to get Ubuntu to boot properly?  see my other thread about trying to get it to work to see what I have done so far [http://ubuntuforums.org/showthread.php?t=369824](http://ubuntuforums.org/showthread.php?t=369824)

Russty

---

### Post by annda on 2007-02-27
for starters, if you really want ubuntu, try the latest live CD (DO NOT INSTALL yet)

[http://cdimage.ubuntu.com/releases/feisty/herd-4/](http://cdimage.ubuntu.com/releases/feisty/herd-4/)

download, burn and boot. see if your hardware is supported. if it is, use the live CD for a while to figure out any issues you might have.

---

### Post by Russty of Oz on 2007-02-27
I have tried the live CD's for Edgy and even Breezy but after the initial loading the screen turns off.  However, seeing as Freespire works, I will give Feisty a try as you say.

---

### Post by Russty of Oz on 2007-02-27
I have now tried Feisty Herd4 but the screen still turns off.  I know Ubuntu is working, it is just that I can't see anything!  :(    

Anyhow, I found that seeing as Freespire works, I can use gparted in that to remove Ubuntu.  I might try installing Freespire and see if it works similar to Ubuntu.  

If anyone can suggest anything else to try to get Ubuntu working properly, I will be keen to give it a go.

Russty.

---

### Post by shellhrs on 2007-02-28
What type of Acer laptop do you have?

I installed Ubuntu Dapper in a friend's Acer Pentium M laptop, and it worked. Well, the screen is still not in the correct resolution (slightly squashed in the widescreen monitor), but sound etc. worked.

I suggest checking the screen selection (set it to main monitor only, not to external monitor or dual monitor setting). Check it in the BIOS also. If I'm not mistaken, Acer let the setting to be active during boot-up.

If it still doesn't work, try adjusting the boot-up option in the boot selection screen of the Ubuntu LiveCD (you have to press F4 or something).

---

### Post by Russty of Oz on 2007-02-28
The laptop is an Acer 1691 Pentium M.  It is a friends, so I don't know too much about it.

I will try what you have suggested and see if it helps.  It seems strange that Freespire works without any problems at all, but Ubuntu wont!  These things are sent to try us! ](*,)

---

### Post by steven8 on 2007-02-28
In the past few months I have tried about 40 distros on my computer.  There are some that just plain will not work.  All the Ubuntu's work, but puppylinux, DSL, and a few others do just what you are describing.  I've tried so many boot options I got dizzy, but comes a time after repeat tries, I gave up.  If Freespire flies for you, give it a go.  I liked it myself, but I like Ubuntu better.

Best of luck!

---

### Post by Russty of Oz on 2007-02-28
Yes it looks like I will have to try Freespire.  The only thing is that I am putting it on a friends laptop and I would have preferred to use Ubuntu because I am now used to how it works, but if Freespire isn't too different in how things are done it should be ok.

---

### Post by a.v.l on 2007-02-28
> **Russty of Oz said:**
> Yes it looks like I will have to try Freespire.  The only thing is that I am putting it on a friends laptop and I would have preferred to use Ubuntu because I am now used to how it works, but if Freespire isn't too different in how things are done it should be ok.

I've had difficulty installing Ubuntu on my laptop and had similar results to yourself, XUbuntu on the other hand worked perfectly.

---

### Post by Russty of Oz on 2007-02-28
Just tried that but Xubuntu doesn't work on this laptop!  Oh well it will have to be Freespire :(

---

### Post by bcmiller on 2007-02-28
Well if it's any consolation I think the next Freespire will be based on Ubuntu anyway so maybe it'll be close enough.

---

