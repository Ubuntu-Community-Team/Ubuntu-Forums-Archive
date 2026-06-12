---
title: "Odd crash problem, need help muchos"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by deviouskoopa on 2007-03-14
So I was trying to read around on the forums and figure out how to get my screen res up to 1680x1050, and now i cant even boot up in ubuntu. so heres all what happened: 

i saw somewhere that i needed to reconfigure my xserver something or other, i forgot the exact code by now... so i open terminal, get the reconfig walkthrough running, and goes thru all the steps, til i get to the screen res selections menu. i had the lowest 3 selected by default, and i just added the 1680x1050 setting and then hit enter, and finished the reconfig. then i saw that i needed to hit crtl+alt+bkspace in order to restart x. so the terminal returns to normal and i hit those keys, and the screen just goes black... and stays black. i wasnt sure if it was supposed to do that or not, so i waited for about 5 mins to see if it would restart. nothing, so i manually restart my laptop, but when ubuntu starts loading, the orange bar reached near to full and then everything just froze up. i waited to no avail then tried rebooting again, again to no avail... 

so now im on my windows xp partition, asking for your advice!! im not sure why its acting up, i didnt have a chance to adjust the resolution, so maybe i messed up somewhere in the xserver reconfig thing? im really not sure, but i cant boot ubuntu and its frustrating. 

thanks for any help!

ps- i have a gateway tablet pc, with intel duo core, 2 gb ram, and ati mobility radeon x1400... the 1680x1050 is for my external monitor, a samsung syncmaster 225bw 22" widescreen monitor, which i have currently set to 1680x1050 on windows xp pro. i suppose the problem could also lie in the fact im using an external monitor, im not sure if something special needs to be done concerning that...

---

### Post by silhouette on 2007-03-14
I believe the Live CD has a recovery option which presents you with a command prompt, from which you can access your hard drive and ultimately your xorg.conf file. Once you log in that way, simply type

```
fdisk -l
```

to list Linux partitions, then type

```
mount /dev/hdXY /mnt
```

where X is a letter and Y is a number, according to the output of "fdisk -l". Then type

```
cd /mnt/etc/X11
nano xorg.conf
```

to edit your X configuration file. There should be two "Screen" sections, one for the laptop, and one for the external monitor (or perhaps you may find only one for the laptop, I'm not sure if Ubuntu detected the external monitor when you installed it). Anyway, within those sections you should find "Display" subsections, and within those you should find a "Modes" line. Remove all instances of 1680x1050. Save with Ctrl-O, exit with Ctrl-X. I think you can then type "exit" to leave the recovery console.

---

### Post by deviouskoopa on 2007-03-14
ok silhouette, i will try that and see if it fixes the problem, thanks a lot!

---

### Post by deviouskoopa on 2007-03-14
ok well, i tried those instructions, but when i exit and it tries to load, it says no monitor is detected and allows me to see the xserver file to diagnose the problem. the file just says what was in the xconf file but with an error at the bottom saying 'no device detected'. any suggestion?

thanks again!

---

### Post by dstew on 2007-03-14
Did you power off the computer, then power it on with the ext. monitor connected? Maybe your card needs to detect the presence of the monitor by its hardware in order to tell the software that it is there.

---

### Post by silhouette on 2007-03-14
Well if you can see something after the kernel loads you should be able to switch to the first terminal with Ctrl-Alt-F1, then login and run "dpkg-reconfigure xserver-xorg". Yes and make sure that the external monitor is connected.

---

### Post by deviouskoopa on 2007-03-14
ok so here's what i did:

i loaded the recovery kernel which gave me the terminal, no problem there. i followed the steps and opened the xorg.conf file, and then deleted all the [1680x1050] entries. i also renamed my monitor and graphics card to better describe them, which i also later did through the dpkg-reconfigure xserver-xorg procedure. i saved the changes and exited, then exited the terminal. it starts loading Gnome Display but gives me an error, and an option to see the error report, which i accept. it says 'no screen detected', and i tried it both with and without the external monitor plugged in. so i hit ok and it shows me an extended version of the error report, which just shows a very long file with the 'no screen detected' error at the very end of it. after i hit ok, it says it is closing Gnome Display and i must reconfigure my settings thru the terminal and reboot. so i have to log in to my account and i try that using the dpkg-reconfigure walk-through. everything goes thru fine (or so i think?) so i exit that and then reboot, but the same thing happens, the orange loading bar screen freezes when the bar fills all the way.

possible sources of advice:

-i may need to reinstall/update the monitors drivers, and if so how do i do that? do i use the cd that came with it or can i find it in a list? how do i install the drivers using the terminal?

-i may need to rename the monitor in the xorg.conf file, as i said before im not sure if it has an effect...

-i dont mind just using my laptop screen without the external monitor, its just that i dont know how to. maybe i need to reset my screen resolution to its original 1024x768, but i dunno how to do that through the terminal...

thanks a hell of a lot for all the help, i really just wanna get my gnome desktop to work, on either screen, but preferably the 1680x1050 external monitor.

---

### Post by deviouskoopa on 2007-03-14
bump... haha im desparate for help ok?!

---

### Post by deviouskoopa on 2007-03-14
ok never mind i fixed it... i had to reinstall my ati graphic drivers, for those who are wondering.

---

### Post by silhouette on 2007-03-14
Glad you got it worked out.

---

