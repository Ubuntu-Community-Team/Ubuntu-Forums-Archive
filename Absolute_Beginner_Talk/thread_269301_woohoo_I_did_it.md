---
title: "woohoo I did it"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by sanjito on 2006-10-01
I want to thank everyone on the boards for all the info I have gathered here. I have left windows on my main system, and was able to figure out how to format it so I have my 18gb drive as my dumping ground. One question I do have is when you format a system to dual boot, can you have win xp be the default system? What I mean is when you start up system you do not have to choose what one to boot too. I can not seem to get wife to switch to linux, and we have a shared laptop. I am thinking of completely switching it to linux, but our couch is not that comfortable for sleeping on :). And I want to keep using linux as much as possible. Thanks again for all the help everyone.

---

### Post by wpshooter on 2006-10-01
To answer your question, yes I believe that can be done by editing the GRUB file, so that Windows is moved into the default boot position but I don't remember exactly where the GRUB file is located.  Maybe someone else can give you that info.

---

### Post by uk_sphinx on 2006-10-01
i think you have to go to bios to choose which o.s is default to boot to.
i couldnt understand your question too well if thats not the answer your looking for.

---

### Post by bulldog on 2006-10-01
> **sanjito said:**
> I want to thank everyone on the boards for all the info I have gathered here. I have left windows on my main system, and was able to figure out how to format it so I have my 18gb drive as my dumping ground. One question I do have is when you format a system to dual boot, can you have win xp be the default system? What I mean is when you start up system you do not have to choose what one to boot too. I can not seem to get wife to switch to linux, and we have a shared laptop. I am thinking of completely switching it to linux, but our couch is not that comfortable for sleeping on :). And I want to keep using linux as much as possible. Thanks again for all the help everyone.

Well first of all welcome to Ubuntu :D 

Then for the info you gathered,wait till you get the bill.........

About windows to boot up by default you have to alter your menu.lst.

Open your menu.lst ```
gksudo gedit /boot/grub/menu.lst 
```
and look for this section near the top 
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		2
```

Then count at which entry your windows is located,but remember,counting starts at 0,so you count 0,1,2,3,4, and so on till you reach your windows.
That number you set where the 2 is [my default boot option]

And it should work.

---

### Post by raphha on 2006-10-01
Well, bulldog was faster, I hadn't seen his complete post, anyways... good luck! 8) 

Hi,
edit the following file (as root) with you prefered editor:
/boot/grub/menu.lst

search for the entries starting with title (at the bottom).
Count the "title something" entries until you reach windows.

Search for the "default  0" line (futher up) and change it to (numer of the windows entry - 1).

So, if the Windows entry is at position 4 (say, after first Ubuntu, second ubuntu recovery, third, ubuntu memtest), then change the "default 0" line to "default 3".

Reboot and enjoy!
raph

...But then again, keep working on helping your wife to discover the nicer way of using your laptop and undo your changes... ;)

---

### Post by ron999 on 2006-10-01
Hi sanjito

Bulldog's spot on, and raphha too - just don't forget to save it!:rolleyes: 

There's a full write up about GRUB in this link:-
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

---

