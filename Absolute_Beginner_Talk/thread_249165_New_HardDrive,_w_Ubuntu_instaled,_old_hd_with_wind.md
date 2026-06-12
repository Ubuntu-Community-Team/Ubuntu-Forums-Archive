---
title: "New HardDrive, w/ Ubuntu instaled, old hd with windows"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Alias- Human on 2006-09-02
I installed Ubuntu on a new HD by physicaly disengageing my old windows HD.
Now I would like to hook them both up, so that I don't have to open my comp case and change the cable from one to the other like I have been doing. Is this possable?
These HD's are both 'Seagate 7200 80GB' HD's.

I have another question as well. If anybody could help me with it I would realy be greatfull.
I have a 'LexMark X2350' printer/scanner. I bought it when I only had windows and it said on the box that it didn't work with Linux. (they seam to know what they were talking about, lol). Is there a way I can use 'wine' to use my printer/scanner? OR, is there another solution?

(It's my bed time so it will be a few hours till I check back for any answers)
Thanks for any info you can give on the subjects!
AHDRL

I am realy enjoying my Ubuntu! =D>

---

### Post by jorn on 2006-09-02
Let the "mswindows" be the first HD.
To restore grub read this:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Be careful in the part where you do the partitioning and no formatting.

An alternativ is Super Grub Disk:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
where you boot from a floppy each time you start your pc. Not very comfortable.
Thereis also a Bootmanager on the install-cd: cd/install/smb.bin ,called Smart Boot Manager. It works like Super Grub Manager i think.

I found some links about your printer but that's very depressing reading, take a look yourself:
[http://kubuntuforums.net/forums/index.php?topic=8112.msg33464](http://kubuntuforums.net/forums/index.php?topic=8112.msg33464)
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=13;t=13070;st=0](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=13;t=13070;st=0)
Feel free to ask again.

---

### Post by Alias- Human on 2006-09-03
Thank you **jorn**,
The HardDrive problem is solved! I followed several of the links (which I cannot find any longer) and...
 one of them told me how to open some sort of list that I had to copy/paste a description of my second HD and windows into. 
I hooked up my HD that has windows on it, as a slave, and set the jumper to cable-select and then copy/pasted the code lines into a Terminal to get to the list and then copy/pasted the lines into Grubs instruction list.

now if I boot my comp it boots windows unless I press 'esc' and choose Linux even though windows is on the second drive. 
I have no idea where these instructions are in this forum but they worked, If anybody knows what I'm trying to describe could you point to them for other new people that might happen by here? Thanks.

As for the printer... I'm going to get an other one. Getting this to work is much to complicated and I have dreams of building another computer (w/ an AMD64 or some such like) and I want a printer that works with everything.

Thanks again.

---

