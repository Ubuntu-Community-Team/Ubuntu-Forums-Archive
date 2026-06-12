---
title: "how can i restore my Ubuntu 7.04 ? it is crash now"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by DO55 on 2007-07-06
hi

im tried to fix the problem with my pci wireless card by this method 
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

but now after i restart the computer Ubuntu stop respond and show me only the brown color desktop 

in windows i can restore it by safe mode also i can repair it by windows CD    but in  Ubuntu   there is no such thing 

help

---

### Post by p_quarles on 2007-07-06
Yeah, there is, but it uses the command line. If it's a dual-boot, choose the second Ubuntu option. If not, you'll have to press escape while GRUB is loading.

You can also try to repair things using the live CD.

---

### Post by DO55 on 2007-07-06
i tried  second Ubuntu option 
and i dont no how to fix by live CD!! :(

Ubuntu mest do something , they must add easy restore method like windows

---

### Post by santy_kushwaha on 2007-07-06
as far as i remember ubuntu does have the safe mode but u should know the commands to write there bcoz that is only command promnt OR use ur ubuntu cd and tried to fix using that i think it is third or fourth option to fix

---

### Post by DO55 on 2007-07-06
[QUOTE=santy_kushwaha;2975509t i think it is third or fourth option to fix[/QUOTE]

dose this remove all my data ?

---

### Post by p_quarles on 2007-07-06
> **DO55 said:**
> i tried  second Ubuntu option 
and i dont no how to fix by live CD!! :(

Ubuntu mest do something , they must add easy restore method like windows
Using the live CD *is *the easy method for restoring things. Boot it up, look for the file that is causing problems, and do what you can to fix it. If you don't know what needs to be fixed or how, ask. 

And it's definitely not easy on Windows. My win partition got corrupted the other day, and all of its user-friendly tools were completely useless. Even scandisk didn't find a single problem.

---

### Post by DO55 on 2007-07-06
im very new with linux 

i dont know how can i find the problem if i used the live cd

---

### Post by twiceasworn on 2007-07-06
Well for starters could you tell us what you did to try and get the wirless card to work?  Did you edit any configuration files?  Even the smallest change could easily make things unhappy.

---

### Post by DO55 on 2007-07-06
> **twiceasworn said:**
> Well for starters could you tell us what you did to try and get the wirless card to work?  Did you edit any configuration files?  Even the smallest change could easily make things unhappy.


yes

i do all of this change 
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

### Post by santy_kushwaha on 2007-07-07
i don't think it will erase the data but just to make sure back it up 

this will help to learn something new and then in future u can help someone else so i would suggest that just try it out

---

### Post by chris_n00b on 2007-07-11
I am having a similar problem. I edited my network interfaces file/driver/whatever.  I can' tboot to the GUI (it just hangs at the Nework Interfaces check *where it says OK or Fail*)  I can hit Cntrl+Alt+F1 I believe and get to a full screen terminal but I cant seem to edit the file back. I haven't been able to use this computer for like 3 months now since I can't get into it.  Can I use the Live CD to change it back? People keep giving me instructions to change / edit the file but none of it is working at all. 

If when its booting and I hit Print Scrn when it hangs, it will Fail that check and then boot up to my normal log in window of the GUI. Then when I log in it just sits at a dark brown screen and I can only see the mouse.  Is there a correct way to by pass that network file? or black list it?  So that I can get in normally, and then change that file back to how it was?  It CANT be that hard to reedit the file.  But that one file editor gedit or whatever doesn't work and pico doesnt work either. I guess there is  a basic file edit comment 'vi' I think... that lets me see the file but I canot edit it.

What do I do?

---

### Post by DO55 on 2007-07-11
i formated and installed fedora 7  , because  its very very very  hard to repair the  linux OS (not like windows that i fix it  many times by using restore in safe mode) and still i have the same problem with the wireless card 
so i formated again and install windows xp 

now im very happy using the intrnet  again with windows xp 

there is many Threads  about   Linksys WMP54G but no one solve the problem even i report the bug in launchpad  but no one replay for more than week  !! 

so i back to windows because its better in network drivers

---

