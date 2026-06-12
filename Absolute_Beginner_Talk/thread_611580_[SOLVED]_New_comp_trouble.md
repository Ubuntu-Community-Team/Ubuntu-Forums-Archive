---
title: "[SOLVED] New comp trouble"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by SteveNorman on 2007-11-13
I have just built a comp around a p33g motherboard. I am trying to switch from microsoft to Linux and got the book Ubuntu for non-geeks. I have loaded ubuntu successfully as the only operating system, but cannot get the driver cd that came with the motherboard to install hardware drivers. It was designed to be auto ran from windows. Am I missing somthing? I really dont want to put microsoft on this computer just to get my lan etc to work.

---

### Post by Paul820 on 2007-11-13
Most likely the drivers that came with your motherboard were made for windows. Ubuntu does not read the .exe files like windows does. Nine times out of ten your hardware will just work, what hardware are you trying to get working?

---

### Post by bulldog on 2007-11-13
You don't have to install that driver cd,all should work with the build in drivers,
Just look if everything is functional,internet,keyboard mouse etc.

You can't install .exe anymore like you did in windows.
Linux works some how different.

---

### Post by SteveNorman on 2007-11-13
Well for start my sound card and my lan, But if I can get the computer online I figure I can get the rest of the drivers up.
I have comcast broadband, On the computer I am using now it goes from my external modem into my lan card. I tried that with my new one, but it didnt see a connection.
Steve

---

### Post by PointyWombat on 2007-11-13
That Windows driver disk will be useless to you now so you can put that away.

What components are not working with your Ubuntu install? Do you have networking, graphical display, and sound?

PointyWombat

---

### Post by SteveNorman on 2007-11-13
I think the sound card solution may be in my bios controls, when I try to stop the boot up  process, I cant get into bios. I just get my options for which version of ubuntu, but nothing else

---

### Post by SteveNorman on 2007-11-13
No networking, I see the desktop, and can operate within the gnome, no sound, no internet, I assumed it was because I could not load the cd

---

### Post by PointyWombat on 2007-11-13
what's the output from the following commands:

**ifconfig -a**
and
**lsmod**
and
**lspci**


(from a terminal window)

PointyWombat

---

### Post by SteveNorman on 2007-11-13
Unfortunatly I only have one moniter, keyboard etc. So I have to disconect all that from this one and try my other tower, re-assmble then reply after this one is set up. 
  So I open a terminal, Type in those commands and write down what they say. I' will do that and repost the results in a bit. 
Sorry, I really appreciate the help, this is my first computer build attempt, and I am as confused as I can be
Steve

---

### Post by PointyWombat on 2007-11-13
ewwwww that's gonna be painfull..

ok, for ifconfig -a,  check if there's anything other than a listing for **'lo'**

for lsmod, check if there's a line with any possible reference to networking...such as forcdeth, net, lan,

for lspci, look for references to ethernet, lan, network...

just post these lines..

PointyWombat

---

### Post by SteveNorman on 2007-11-13
for iconfig there is:
lo    then a space then a column of info (8 lines, but lo is the only listing)

for lsmod, I didnt see anything referring to networking


for lspci there is a listing for ethernet controller  it says:
00.04.0 ethernet controller: silicon integrated systems [SiS] 191 Gigabit Ethernet

in gnome I brought up the network page and there was no listing for wireless, only for an unconfigured modem that I dont have. 

With my other computer I can boot from the Cd and get online from ubuntu, so its not my service. Maybe my lancard is not supported by linux?
Steve

---

### Post by PointyWombat on 2007-11-13
Ok. so it seems the OS sees the device, but has no driver for it... I found [this]("http://ubuntuforums.org/showthread.php?t=188060") thread which has info about your ethernet controller... do you see a similar output when you run dmesg? 

Also found [this]("http://ubuntuforums.org/archive/index.php/t-550060.html") thread which may shed some light.

Actually just a google search with "***["191 Gigabit Ethernet" +ubuntu]("http://www.google.ca/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=aF1&q=%22191+Gigabit+Ethernet%22+%2Bubuntu&btnG=Search&meta=")***" revealed quite a bit...

You may be also be able to get a linux driver from the SiS website.

PointyWombat

---

### Post by SteveNorman on 2007-11-13
Im gonna run dmesg when I switch  back to the linux comp. I have an old comp I have been parting out, It has the same lan card as the computer Im using now (which succesfully got online) I will try it and see what happens..

---

### Post by PointyWombat on 2007-11-13
Also, when you run the live CD on this box, does it have working network and sound?

PointyWombat

---

### Post by SteveNorman on 2007-11-13
On this comp yes it does. On my new comp, no it doesnt.  I put a lan card in an  expansion slot of the new one. ubuntu sees it, but I still cant connect. I still get a firefox cant find server message when I try to do anything online. But, in the network settings it now shows a wireless connection, which it hadnt with the integrated sis 191 lan on. I tried going from dhcp in the network settings to static, but still cant get anything. I just got this comp back together and did a command prompt ipconfig and got the IP, Subnet mask and the default gateway from the comp that I am on now.

So In a bit I will take this comp apart and reset-up the linux comp.

I assume the Ip addy, subnetmask, and default gateway is a function of the outboard cable modem and not the computer itself. I am assuming this because This is actually computer number 3 in this process. and I was able to switch from 1 and 3 internet wise with no problems

Computer number1 is a compaq costco beast I was given. 
Computer number 2 is my new one I am building with linux
Comp number 3 is this one, which is also a costco compaq someone gave me, Identical to number one 
part wise.

1 is parted out to 2 and 3
I parted out memory to number 3,
parted out cdr dvd and floppy to number2 (new linux one)
I just put the lan from 1 into 2

So number 3 and the new one have identical lan connections now, eliminating one variable in the process.

Latter tonight when my frustration level has subsided a bit I will have another go.

---

### Post by SteveNorman on 2007-11-14
OK getting there, I am online with the new computer now, the last thing I need to do is get sound.

Silicon Integrated Systems [SiS] Azalia Audio Controller
 is what comes up when I do lspci
kinda lost on what to do now,

---

### Post by SteveNorman on 2007-11-14
I have been searching the threads, found people seem to be having the same problem, however the solutions are out of my do-ability level. I dont know how to reload kernals etc. Is there a step by step solution for idiots  that I can use? ;]

---

### Post by SteveNorman on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=536036&highlight=Audio+device%3A+Silicon+Integrated+Systems+%5BSiS%5D+Azalia+Controller](http://ubuntuforums.org/showthread.php?t=536036&highlight=Audio+device%3A+Silicon+Integrated+Systems+%5BSiS%5D+Azalia+Controller)

solved the sound issue using this thread. put in a Lan card to fix the internet issue.
Thanks for the help everybody!
Steve

---

### Post by PointyWombat on 2007-11-14
Glad to see you got it working.

---

### Post by Inxsible on 2007-11-14
Sweet !! 
Please mark your thread as solved. Thread Tools>>Mark thread as solved.

---

### Post by SteveNorman on 2007-11-15
uuhhh,,sorry how do I do that?

---

### Post by PointyWombat on 2007-11-16
There should be an aption besides 'SOLVED' called 'WORKAROUND' or 'PARTIALLY SOLVED', 'cause it's not really solved, at least with the LAN issue.

To mark it as solved though, just above your first post is 'Thread Tools'.

---

