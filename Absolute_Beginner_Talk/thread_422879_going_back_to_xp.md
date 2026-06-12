---
title: "going back to xp"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by mayday56 on 2007-04-25
how hard is it to reformat my harddrive and re-install xp...ubuntu just isnt ready for a total non geek like me.....I really wanted it to work out maybe ill try again when some of the bugs get worked out...is there anything special i have to do to the harddrive to be able to reinstall xp?

---

### Post by oilchangeguy on 2007-04-25
are you using a factory restore disc? or a windows only disc?

---

### Post by mayday56 on 2007-04-25
i have my windows xp install disk.....

---

### Post by Nythain on 2007-04-25
just tell it to delete all the partitions and create a new one formated with ntfs during the install process... windows will nuke grub on its own i believe and you should be golden

ps... you dont have to be an uber geek to run ubuntu/linux... my girlfriend loves it... you just have to have the motivation and patience to look up solutions to any problems you encounter

---

### Post by oilchangeguy on 2007-04-25
ok, simply boot from the cd and follow the prompts until you get to where it shows the partitions already on the drive. and use the option to delete the partitions. then you'll see unpartitioned space and this is where you'll reinstall xp, just follow the prompts, format the drive and you'll be on your way.
sorry about the problems you're having with ubuntu. what version are you using?

---

### Post by canadianwriterman on 2007-04-25
Hi Mayday,

I notice in recent posts you were having problems with your network drive connection, in particular typing the suggested code. As a former XP user and GNU/Linux noob, I completely understand where you're coming from. I usually copy and paste the code that people post into my terminal, so I don't have to figure out how to type it correctly.

If you want to try that technique before you go back to XP, you might have more success. This week, I completely erased my Windows partition and am now using Feisty as my only OS. I'm very happy, but sometimes I have to be patient when working through issues.

Hope that helps.

---

### Post by justin whitaker on 2007-04-25
I did that recently, using factory install disks. Spent about a day in XP, got fed up, and came back.

---

### Post by mayday56 on 2007-04-25
thanx for all the replys....If I could just get my video right I could deal with the other minor stuff. most times when I reboot ubuntu it comes back at 640x480 with no option to select anything else. after a couple of reboots it comes back to 1280x1024. my video card is nvidia.I tried a little program that was suppose to go and get the latest driver and auto install but it said it didnt recognize what type card I have.another guy told me to use synaptic to uninstall then reinstall but its still doing the same thing...any suggestions?????

---

### Post by mayday56 on 2007-04-25
I almost forgot...I do that to..I copy and paste from the firefox web browser to a terminal..canadianwriterman I ried to figure that out (the command line stuff )but I could never get it to work....I want to learn but I think I need a properly operating system to learn on..I never had these type of problems in windows xp...but Im willing to give it one more try.....

---

### Post by eeverson on 2007-04-25
I have an NVidia card in my desktop at home... i just installed Automatix2 and selected to install the Nvidia drivers and now it works a dream... It also makes installing a whole bunch of other programs very simple!

---

### Post by oilchangeguy on 2007-04-25
you've still not said what version of ubuntu you're using.

---

### Post by mayday56 on 2007-04-25
Im sorry..Im using 7.04 fiesty fawn

---

### Post by oilchangeguy on 2007-04-25
take a quick look at all of the the recent posts about problems with 7.04. is this the first version of ubuntu you've tried? i suggest you use 6.06, at least until 7.04 is more stable.

---

### Post by jcconnor on 2007-04-25
I fought the whole nvidia thing too.  

Don't know if this will help, but I installed the nvidia drivers using the nvidia installer.  

My machine won't load the graphical interface when I'm using my add-in Nvidia card so it's a bit of a pain.  But this may help you.  

First, I uninstalled the nvidia driver using Synaptic (the package manager) - did a search on nvidia and told it to completely remove all that were installed.  You may not need to do that (I was running on the on-board Intel at the time so I could do this safely).

Then this is what I did:

1) I downloaded the latest Nvidia driver installer from:

>  [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html) 

2) I copied it to my home directory.

3) Shut down the machine.

4) Reinstalled the Nvidia card

5) Rebooted. When X failed (which I knew it would) I dropped down to a prompt (Alt-F1) and logged in.

6) Changed to my home directory and then, drum roll, ran the installer with the command:

> sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

7) It asked me a bunch of questions which I just answered yes to all of them.

8) Rebooted and voila - Gnome session.

9) I added the Nvidia X Server Settings to the system menu with the System - Preferences - Menu Settings command.

10) The Nvidia X Server settings program recognized my monitor and allowed me to set the video resolution to 1280X1024.

Hope this helps.  Good luck.

John

---

### Post by Talon2 on 2007-04-25
> **mayday56 said:**
> thanx for all the replys....If I could just get my video right I could deal with the other minor stuff. most times when I reboot ubuntu it comes back at 640x480 with no option to select anything else. after a couple of reboots it comes back to 1280x1024. my video card is nvidia.I tried a little program that was suppose to go and get the latest driver and auto install but it said it didnt recognize what type card I have.another guy told me to use synaptic to uninstall then reinstall but its still doing the same thing...any suggestions?????

What nVidia card is it?

Which version of Ubuntu are you using?

---

### Post by oilchangeguy on 2007-04-25
also read post #10. the user is right on with using automatix to install software. [www.getautomatix.com](www.getautomatix.com)

---

### Post by slayerboy on 2007-04-25
You said you are using Fiesty Fawn, is it a fresh install or an upgrade?

---

### Post by jmagsho on 2007-04-25
Mayday,

Sounds like your xorg.conf file is possibly messed up.

Try this from a terminal window:

sudo dpkg-reconfigure -phigh xserver-xorg

It should recreate the xorg.conf file and give you the option to choose the highest resolution it detects.   When it's finished, reboot and then see what you've got.

I had a problem similar to this with an older Nvidia card I had on an older machine and was able to get the resolution set where I wanted it with some minor tweaks to the xorg.conf file.

---

### Post by kelvin spratt on 2007-04-25
before you give  up the ghost ask yourself if xp does not reconise your your card and it will not without the drivers do you give up no you don't because its windows you just e-mail your friends and brag about it. my xp is different to yours and then spend days trying to find drivers as i did then windows does an update then something else does not work more e-mails another week fixing but thats just windows for you and we pay moneyfor the inconveniance this is free after 5 or 6 insalls due to my thinking i new it all fiesty really does work well and as for xp it just feels like win 95 after fiesty but it takes time to get it right and loads of cockups remember what cocked it up i can now get the cube spinning in all directions and all angles when first tried i wiped out edgy totally now the cube is stable as is fiesty sorry to be hard if you want to try something a bit easyer try ubuntu ultimate 1.3 it has all you need to start i mean everything it does upgrade to 7.04 you can change everything on the interface the theme is crap but that can be changed it  1.9 gig and as i said works very well don't try the gamers as its not as stable

---

### Post by Nythain on 2007-04-25
make sure you are installing the correct driver for your card, there are 3 now... nvidia-glx-new for newer cards, it uses the 755x drivers... then there's nvidia-glx for a wee bit older but not old cards... it uses older drivers that give better 3d support for certain cards... then there's nvidia-glx-legacy for really old cards, it doesnt offer 3d support though...

also make sure you enable them, i think its like sudo nvidia-config or something like that, you can find the exact command somewhere though...

finally make sure that the driver nv is changed to driver nvidia in you xorg.conf

and one last idea, check the bit depths and metamodes in your xorg.conf to make sure that the res you want is listed, if not, and you know your machine can handle it... add it before the others and see what happens...

i know this all seems complicated, but its actually much easier in feisty than i've ever had luck with in dapper or edgy

---

### Post by kittyhawk63 on 2007-04-25
kelvin spratt,
Have you heard of the invention of the period. lol

Edit: I'm sorry Kelvin Spratt. There is a period toward the end of the second line. I thoroughly apologize.
kh

---

### Post by slayerboy on 2007-04-25
> **kittyhawk63 said:**
> kelvin spratt,
Have you heard of the invention of the period. lol
:lolflag:

---

### Post by kittyhawk63 on 2007-04-25
.

---

### Post by jcconnor on 2007-04-25
> **kittyhawk63 said:**
> kelvin spratt,
Have you heard of the invention of the period. lol

I rather liked the stream of consciousness of it.

---

### Post by xpod on 2007-04-25
Do not go gentle into that dark light...rage rage against the dying of the x server:wink:

---

