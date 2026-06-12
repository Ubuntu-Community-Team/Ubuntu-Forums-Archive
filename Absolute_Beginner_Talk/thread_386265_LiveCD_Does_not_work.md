---
title: "LiveCD Does not work"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by gk_terato on 2007-03-16
Hi,
I've been trying to use the LiveCD of Ubuntu. I have tried 64bit, x86 of the 6.10 release, both the CD and DVD versions. All of them do not work on my computer. The 64bit version has a black and white loading screen, while the x86 version has a colour one but after it loads, the graphics are all buggy (it's got lines all over it, looks like each line is misaligned or something) and I can't get anywhere. I can only make out a window in the centre of the screen. I can move my cursor but there's nothing to click. I have updated my bios, my drivers. My comp specs: Asus A8N 32-SLI Dx (mother board), AMD Athlon X2 4200+ (cpu), nVidia Geforce 7800+ gtx, 250gb WD SATA2 HDD. Creative X-fi sound card. I have tried looking up on Google but all of the responses seem to be issues with errors. I didnt see any errors. I want to get the LiveCD to work first before i decide to install Ubuntu. Thanks in advance! 

I have attached 2 pictures. The colour one is my attempt with x86 DVD version, the black and white (notice the load bar) is my attempt with 64bit.

Edit: Also, the bars stop moving at the very positions in the picture. It just freezes and after 10minutes i gave up and rebooted.

---

### Post by teaker1s on 2007-03-16
look here
[http://ubuntuforums.org/showthread.php?t=379807]("http://ubuntuforums.org/showthread.php?t=379807")

also
you most likely have a common problem with "apic."

Solution: When given boot options for the LiveCD, press F6 for other options and you should see a command line with commands already entered. Simply add any or all

NOAPIC NOAPCI 

to the end of the line and press enter. The system should now boot without stalling.

---

### Post by wpshooter on 2007-03-16
First thing - have you checked the integrity of your CDs by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you burn your CDs at 4X or less ?

I would suggest that you stay away from the 64bit version at this time.  To many possible challenges to overcome, according to what I understand.

Have you tried booting in safe video mode ?  Try that on the 32bit version of Edgy after you have verified that the CD is good.

I that does not work then use the F4 key to choose and set video parameters manually and see if it will boot.

If none of that works then try the 32bit version of Edgy ALTERNATE (text based) version.

Good luck.

---

### Post by teaker1s on 2007-03-16
64bit is fine for duel core systems-look at the link I provided-it's the graphics card model that causes the issue and there is a way to cure it

---

### Post by gk_terato on 2007-03-17
wow this seems promising. I'm going to try it now. Thanks for the prompt replies!

---

### Post by gk_terato on 2007-03-17
It works, thanks alot!:guitar:

---

### Post by gk_terato on 2007-03-17
sorry guys. After i got it to work once i havnt been able to do it again. it always stops after loading ....some commands which end with number 1. I'll go take another pic if need be. I'm gonna keep trying a few more times. btw is pressing restart so many times bad for the computer..?thanks!

---

### Post by gk_terato on 2007-03-17
Nothing moves after that point.

---

### Post by Kateikyoushi on 2007-03-17
Rebooting won't kill your pc it will become obsolate sooner than that, and after you installed ubuntu you won't need to restart it anyway. ;)

So you could make it run once try the same commands what were recommended in this thread already, if you liked it then go for the alternate install cd to install it would be easier.

---

### Post by teaker1s on 2007-03-17
at grub screen (you may need to hit esc) select recovery kernel

if it boots to commandline then
```
sudo dpkg-reconfigure xserver-xorg
``` check the driver is still vesa

---

### Post by gk_terato on 2007-03-17
I tried install in text mode, but after the loading kernel box it just shows that little flashing _  , but i can't input anything. I also think i rebooted so many times my windows is getting messed up..Alot of the icons arn't loading. Anyway I'll try the alternate install. Thanks.

---

### Post by gk_terato on 2007-03-17
that screen which i posted earlier is seriously giving me a big headache. I found out that it happens randomly (so it seems), and if i get in im just lucky. I got in like once every 7 times. It happens with the live cd, and it happens after i install it, and it happens when i try recovery mode. I can not type anything when i reach that screen, only option i can find was to press reboot button. Any help appreciated, thanks!

edit: when i try the regular without recovery mode, the load bar does not move.

---

### Post by teaker1s on 2007-03-17
try this but keep an eye on cooling fans 
at grub hit "e" to edit then you will see a long line at the end is ro splash
edit so you insert
[COLOR="Red"]NOAPIC NOAPCI [/COLOR]ro splash

try this editing for serveral boots, if and when you are happy it cures issue then boot.
terminal
```
sudo update-grub
```
makes it permanent

---

### Post by gk_terato on 2007-03-18
why keep an eye on cooling fans? What if i use water cooling =/? Thanks.

edit: okay well that didnt work either. Id only get in like on my 5th try everytime. I just fixed the MBR and ripped ubuntu out. If anyone has anymore ideas on how to get past that freaking (!!!!!!!) usb assigned number one sh*%, please tell me. This entire thing is making me very agitated, sorry. I've already spent too much time on it than I would have liked to end up ripping it out. Thanks.

---

### Post by teaker1s on 2007-03-19
ref cooling- on heat sensing hardware such as laptops, sometimes the kernel must interact to control cooling-on occassion I has been  known for some hardware to not start fans on linux.
I can only suggest you search the forums and maybe someone will have some idea, I remember white box flashing posted by several users

---

### Post by gk_terato on 2007-03-20
alright thanks teaker, been a great help.

---

