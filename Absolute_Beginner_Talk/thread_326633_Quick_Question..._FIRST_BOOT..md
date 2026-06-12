---
title: "Quick Question... FIRST BOOT."
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by harrington on 2006-12-27
_This is in reference to a past post I was reading..... He is having the exact problem I am having._

Hi I'm new to Linux and Ubuntu. I down loaded the lastest Ubuntu (6.06.1) Burned the Iso image to a CD and then Rebooted. Well the LiveCD will go through the entire process boot my machine but when it gets ready to finsh and go into the Desktop the sceen turns completely black and then I hear the Theme music in the back ground. I looked at my monitor and the Active light goes from Green to Amber like it's in standby. It seems to be the OS is booted and ready to go but can't display anything. What can I do to solve this. I just want to use it as a live CD for right now to get use to all the linux programs.

Further in the thread it had a link

[B]This is the fix( I havent tried it yet) Does this apply if I want to be able to use it as a live disk to try it out, or does it have to be installed. A quick reply will be greatly appreciated, I am learing allot from you guys thanks again.
[/B]
**[http://www.hotubuntunews.com/blog_03.shtml]("http://www.hotubuntunews.com/blog_03.shtml")**

---

### Post by harrington on 2006-12-27
Can anyone HELP?

---

### Post by Ocxic on 2006-12-27
if that is your problem you don't have to re-install at all, boot your computer in recovery mode (push esc when grub says to as you computer boots, and choose recovery mode)

then login and type this:

sudo nano /etc/X11/xorg.conf

find the screen section and delete all the resolutions you see there that you monitor can't handle. then push ctrl+x, then the letter Y, then push enter, and reboot.

alternativly you can run

sudo dpkg-reconfigure xserver-xorg, and select the resolutions from there.

---

### Post by rs3 on 2006-12-27
if you're not averse to running the edgy eft desktop cd (6.10) instead of dapper (6.06.1) you might have better luck with edgy by selecting "safe graphics mode" (second option in the cd boot menu).

a less easy solution would probably be to follow the fix, but adjust it appropriately for using the live cd.

when you hear the desktop appear, press **CTRL+ALT+F1**.  you should see the text-mode console appear, where you can type **sudo dpkg-reconfigure xserver-xorg** then follow the directions in the fix you posted from there.  please let us know whether that works!

---

### Post by towsonu2003 on 2006-12-27
it is [SIZE="5"]dangerous[/SIZE] to use refresh values taken from some random site. it can damage your hardware (crap out the monitor, for good). you have to find the refresh rates for your monitor make and model, most probably from the manufacturer or by googling. 

in that page, it says:
> 
select the recovery mode for the kernel you are using
There is no "recovery mode" for the LiveCD. But there may (hopefully) be a choice to get you to the text mode (which will drop you to the terminal, without any graphics. In there, login, do the dpkg-reconfigure xserver-xorg thing, and when it is done, type startx to start the graphical environment. When you are done, the command to reboot is, well, sudo reboot... 
> 
Finish the xserver configuration wizard, and reboot your computer. Your monitor should now be forced to stay within range.
instead of restarting, hit ctrl+alt+backspace to restart X. if you restart the computer, all changes you did will be lost.

---

### Post by harrington on 2006-12-27
Thanks for the replies. I believe that I have edgy installed. I created a image of the first download on the download page for windows 32 bit. I have tried safe graphics mode

referring to this: if that is your problem you don't have to re-install at all, boot your computer in recovery mode (push esc when grub says to as you computer boots, and choose recovery mode)

How do I get recovery mode and grub??? 

Do I have to do this first???

[http://www.theeldergeek.com/recovery_console.htm]("http://www.theeldergeek.com/recovery_console.htm")

I am new, please explain

---

### Post by towsonu2003 on 2006-12-27
before going any further, are you sure you installed ubuntu? you previously said you only booted with the liveCD and that's all. if you did not explicitly told the liveCD to install, it's not installed.

I'm trying to find out, for now, whether you have an installed system, or a LiveCD environment... solutions will change according to that...

> Do I have to do this first???
[http://www.theeldergeek.com/recovery_console.htm](http://www.theeldergeek.com/recovery_console.htm)
No.

---

### Post by rs3 on 2006-12-27
> **harrington said:**
> 
How do I get recovery mode and grub??? 


unless you are using a non-standard boot configuration, you should have GRUB by default; also, "recovery mode" is simply a boot option to jump straight to a console as superuser to repair issues that may be preventing you from booting normally.  if ubuntu is your only operating system, you need only press **ESC** when you first see GRUB starting at the bottom of your screen, then select the recovery console (should be the second option) to invoke it.

but be very careful when using it, because it grants you immediate superuser permissions--meaning that if you do something, it won't ask you for confirmation before doing it, right down to demolishing your installation.

anyway; from the recovery console, you can most certainly apply the fix intended; but as mentioned above (quite sagely) it is dangerous to use refresh rates that exceed your monitor's own specifications, so err on the side of caution when putting in that information. :/

---

### Post by taurus on 2006-12-27
As I understand from his previous thread and this one, he only wants to run Ubuntu from the LiveCD to check it out before he installs it on his machine.  Therefore, recovery mode and GRUB are out of a question.  

The only thing you can do now is to press <Ctrl><Alt>F2 to get to a console and reconfigure X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then press <Alt>F7 to see if you see the GUI login screen!

---

### Post by harrington on 2006-12-27
No all i did was get the iso, burned image to cd, change boot sequence in bios to boot from cd. and tried every boot option from the main screen. Thats where im at....

---

### Post by harrington on 2006-12-28
I just wanna be able to try it, see it for the first. I have the worst luck with linux. First time about a year ago I removed the windows partition... please help me get this live cd going.

---

### Post by towsonu2003 on 2006-12-28
okay :) 

try taurus' instructions. 

**ignore** my message below:) 
taurus: doesn't s/he have to restart X? does sudo dpkg-reconfigure -phigh xserver-xorg restart X automatically?

---

### Post by taurus on 2006-12-28
> **towsonu2003 said:**
> okay :) 

try taurus' instructions. 

**ignore** my message below:) 
taurus: doesn't s/he have to restart X? does sudo dpkg-reconfigure -phigh xserver-xorg restart X automatically?
I think you need to get back to GUI login screen first with <Alt>F7.  Then, restart X with <Ctrl><Alt>Backspace...

---

### Post by towsonu2003 on 2006-12-28
okay than, to sum up:
[list]
[*]ctrl+alt+f2
[*]sudo dpkg-reconfigure -phigh xserver-xorg
[*]input your [SIZE="5"][COLOR="DarkRed"]own[/COLOR][/SIZE] refresh rates there (don't use random numbers from some random site, it is [SIZE="5"][COLOR="DarkRed"]dangerous[/COLOR][/SIZE]*)
[*]when done, ctrl+alt+f7
[*]then ctrl+alt+backspace and the graphical stuff is supposed to come up
[/list]
if it doesn't, I would just try another distro's live CD. distrowatch.com is a nice place to check out for various linux distros. you can also do custom distro searches (like[ this one]("http://distrowatch.com/search.php?category=Live+CD&origin=All&basedon=All&desktop=GNOME&architecture=All&status=Active"), which shows live CDs with gnome as the desktop environment, similar to Ubuntu). 

PS. I would try [knoppix]("http://www.knoppix.com/").

You might also want to google for either 
[list]
[*]your graphics card name
[*]your monitor model and make
[/list]
Use this link to google these: [www.google.com/linux](www.google.com/linux)


*sorry for the big colorful letters :)

---

