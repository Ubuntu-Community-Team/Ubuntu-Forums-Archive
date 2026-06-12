---
title: "1440x900 Resolution Setup for Beginer!"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by tregarton on 2006-07-05
Hello all, I've just dumped Windows and installed Ubuntu (having seen the light!). I've noticed straight away that my resolution of 1440x900 isn't supported.  I've looked further in the forum but don't understand a word that mentioned regarding adding the said mentioned resolution.

Would someone please explained in VERY VERY VERY plain English how I go about adding the res of 1440x900 to the desktop.

Many thanks inadvance,
Rob

---

### Post by xrchris on 2006-07-05
OK first things first - What video card do you have?

---

### Post by tregarton on 2006-07-05
It's the standard onboard video card that came with my dell dimension 5150

---

### Post by MaximB on 2006-07-05
did you install your video card properly ?

---

### Post by tregarton on 2006-07-05
It's onboard the mother board.  When I used Windows XP the resolution was available in the control panel

---

### Post by xrchris on 2006-07-05
[QUOTE=tregarton]It's the standard onboard video card that came with my dell dimension 5150[/QUOTE]

Am i correct in thinking this is the Intel 950?

---

### Post by tregarton on 2006-07-05
Yes

---

### Post by xrchris on 2006-07-05
OK you will need to download the 915resolution package from the repositories. 

Have you enabled the extra universe and multiverse repositories? If not do you know how to?

---

### Post by tregarton on 2006-07-05
I haven't enabled anything and I have not idea what you just wrote!!!

---

### Post by xrchris on 2006-07-05
OK click this link > [https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0](https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0)
and read about enabling repositories and follow the instructions. You wont need to go beyond the section titled 'Adding the Universe and Multiverse Repositories' If you are unsure about anything it says just ask.

---

### Post by MaximB on 2006-07-05
go to the applications(in the upper panel) - add/remove - make sure that you have "show unsupported applications" and "show commercial applications" on (highlight) then click aplay

---

### Post by tregarton on 2006-07-05
OK I've read the documents recommenede to me and ensured the unsupported and commerical apps boxes are ticked.

What now?

---

### Post by tregarton on 2006-07-05
OK, I've found 915resolution files under ADVANCED on ADD/REMOVE programs.  I downloaded and then let Ubuntu automatically install the files.  I didn't get any further resolution options nor when I restarted.  I've obviously missed out a vital part.

Please help!

---

### Post by xrchris on 2006-07-05
Deleted as you already found it.

EDIT 

this link > [https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654](https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654) gives you the instructions on wht to do with the 915resolution.

---

### Post by tregarton on 2006-07-05
I'm sorry, I don't understand, "deleted as you already found it" .What do i have to do now?

---

### Post by tregarton on 2006-07-05
OK i've seen the link.  I've opene a terminal window and typed # sudo apt-get install 915resolution.  Nothing happens.  I know I must be making you frustrated but I might as well be in the dark!

---

### Post by xrchris on 2006-07-05
[QUOTE=tregarton]I'm sorry, I don't understand, "deleted as you already found it" .What do i have to do now?[/QUOTE]

I deleted the long list of instructions i was typing as you had already found the relevant file and installed it. 

Click the link that i posted for the 915resolution as it contains the instructions on how to configure the program for Ubuntu Dapper 6.06.

---

### Post by xrchris on 2006-07-05
[QUOTE=tregarton]OK i've seen the link.  I've opene a terminal window and typed # sudo apt-get install 915resolution.  Nothing happens.  I know I must be making you frustrated but I might as well be in the dark![/QUOTE]

Thats because you have already installed it in the Add/remove programs just carry on from the next step.

EDIT - Also you do not need to put the # in front of what you type in.

---

### Post by tregarton on 2006-07-05
I've tried the link.  Where do I go.  In a terminal window.  When I'm there no comands appear after entering the sudo etc

---

### Post by xrchris on 2006-07-05
type 

```
sudo 915resolution -l
``` 

into a terminal window.

---

### Post by tregarton on 2006-07-05
yes done that and got:
Password:
Intel 800/900 Series VBIOS Hack : version 0.5.2

Usage: 915resolution [-f file] [-c chipset] [-l] [mode X Y] [bits/pixel] [htotal] [vtotal]
  Set the resolution to XxY for a video mode
  Bits per pixel are optional.  htotal/vtotal settings are additionally optional.
  Options:
    -f use an alternate file (THIS IS USED FOR DEBUG PURPOSES)
    -c force chipset type (THIS IS USED FOR DEBUG PURPOSES)
    -l display the modes found in the video BIOS
    -r display the modes found in the video BIOS in raw mode (THIS IS USED FOR DEBUG PURPOSES)
peterpan@peterpan-desktop:~$

---

### Post by tregarton on 2006-07-05
Sorry, inputed the wrong letter, I've now got this:

peterpan@peterpan-desktop:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

---

### Post by xrchris on 2006-07-05
ok now you can follow the instructions from 'Overwrite Resolution' on that link

---

