---
title: "Reboot setup"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Mauler5858 on 2008-03-19
Ok here is what im wanting to do:

I currently use Ubuntu for pretty much everything besides gaming.  I have stripped my Windows XP of most services except what i need to make it play games.  What i need is to be able to execute a script in Ubuntu to change my Grub values to reboot to that grub menu entry automatically and without a timer at the grub screen.  Also, i know there is functionality in windows to reboot and NOT have to go through the POST.  Is there any way i can make this work like that so when i want to game it reduces some of my hassle?

---

### Post by Diabolis on 2008-03-19
You can change grub values in this file:
```
sudo gedit /boot/grub/menu.lst
```

look for this lines:
```

default          0
timeout          0 

```
**default** is the option that you want to be used by default. If you have 2 operating systems, your options are 0 and 1.

**timeout** is the time that grub will wait for you to pick an option. If the time expires, it will use the default option.

---

### Post by Mauler5858 on 2008-03-19
Ok that helps, im really looking for a script that i can execute that do this in this order if possible.

Start Script

Possibly Prompt with "would you like to reboot" and tell it yes or no.

Change grub to boot to my xp partition with no countdown.(preferably 
only once, or there will have to be a corresponding script in windows)

And then reboot directly to grub bypassing the POST system startup.




This may be a tall order, but would really rock if possible.

---

### Post by Diabolis on 2008-03-19
Maybe I'm not getting your idea, a step by step explanation would help, but as I understood grub already does that. When the grub menu appears you can press **c** to go to a command line. There you can change values or reboot, which I think would be pointless because it will restart the bios and then the grub menu will show up again.

---

### Post by Mauler5858 on 2008-03-19
What im saying for the script is for it to initiate when you are in linux, not at the grub screen.  Making it a faster way to reboot between operating systems

---

### Post by Dr Small on 2008-03-19
It is possible with the help of zenity and sed.
Currently I am going to bed, but maybe tomorrow I will work on it.

---

### Post by Mauler5858 on 2008-03-20
Ok thanks, any advice would really be awesome.

---

### Post by Diabolis on 2008-03-20
Yeah shouldn't be too hard with a script. The script should change default to 1 (if that is the number of your windows installation) and the timeout to 0. The problem is that grub will always boot very quickly into windows making it a bit harder to boot into ubuntu. So you will have to modify the file again from windows, but you can use the same script for that.

@ Dr Small
I attempted to write the script, but I couldn't figure out how to write back to the file using sed. I read the man page and every time I tried, I erased the whole file lol. So I'm not sure anymore if I was going into the right direction. Now I am thinking that I just went through the hard(wrong) way. Here is what I wrote:
```
#!/bin/sh

#The file that you want to modify
targetFile=menuTest.lst

echo "modifying: "$targetFile

#Changing timeout
awk '
{
	x = index($0,"timeout         10")
	if ( x != 0) {
		print "Line number: "NR" "$0
		if( $2 == "10" ) {
			$2 = "0"#must write to the file
		} else {
			$2 = "10"#must write to the file
		}
	}
}' $targetFile

#Changing default
awk '
{
	x = index($0,"default         0")
	if ( x != 0) {
		print "Line number: "NR" "$0
		if( $2 == "0" ) {
			$2 = "1"#must write to the file
		} else {
			$2 = "0"#must write to the file
		}
	}
}' $targetFile
```

---

### Post by Mauler5858 on 2008-03-20
An idea is that maybe a script could be written in windows to reverse the actions of this one.?  Is there also a way to force a reboot and have it bypass POST, pick up grub right off, and boot this modified menu.lst?

---

