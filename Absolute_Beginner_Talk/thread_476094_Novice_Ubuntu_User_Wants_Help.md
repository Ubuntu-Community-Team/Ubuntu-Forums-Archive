---
title: "Novice Ubuntu User Wants Help"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by naji on 2007-06-16
Hi,

I&#8217;ve downloaded &#8220;**Ubuntu 7.04 i386**&#8221; successfully
But after booting with that live CD, just to see how it looks like, and selected the first choice to &#8220;start or install&#8230;&#8221;

Error message came to me, it says:
[B]/bin/sh: can&#8217;t access tty: job control turned off
(initramfs) [  126.199811] ata3.00:  faild to set xfermode (err_mask-0x4)
&#8230; Etc[/B]

Then the PC slows down and periodically sends the same error message. 
And I tried to remove
[B]&#8216;splash&#8217;,
&#8216;quiet&#8217;,
 &#8216;--&#8217; [/B]
after pressing F6 on the main menu and writing &#8216;break=top&#8217; after that I supposed to write &#8216;modprobe piix&#8217; in command line , but the same error message appears and the keyboard don&#8217;t write anything.

I don&#8217;t know what the problem, but the keyboard behavior is weird &#8220;to not accepting writing anything&#8221;.
**Any suggestions?**

---

### Post by deadlikeoscar on 2007-06-16
I think it is supposed to be

live boot=break

and then type at the command prompt:

modprobe piix

exit

---

### Post by naji on 2007-06-16
> **deadlikeoscar said:**
> I think it is supposed to be

live boot=break

and then type at the command prompt:

modprobe piix

exit

Actually when I tried &#8220;live boot=break&#8221;
Then the Ubuntu welcome screen appears and the progress bar freezes. I think with this command things getting worst.
And actually if it worked and I got to the command prompt, I can&#8217;t type anything. Some time it will write only the first letter from what I typed and only once.

---

### Post by deadlikeoscar on 2007-06-16
Actually, I think I am making this too hard. Sometimes this can be a sign of a bad cd. I would try burning another cd (preferably with a different program and preferably with a different brand of cd-r)

---

### Post by kevdog on 2007-06-16
Did you check the md5sum of the disc you downloaded??  Possibly there was an error during download that made a bad disc.  Either check md5sum of disc, or I would probably just download and burn another copy of the installation disc.  If the LiveCD isnt working try the alternate cd.

---

### Post by Sef on 2007-06-16
> If the LiveCD isnt working try the alternate cd.

The alternate cd is not a live cd.   To check out Ubuntu, you need the Live CD.

---

### Post by naji on 2007-06-17
Thanks guys. 

But the problem didn&#8217;t solve yet.

Can anyone tell me, why I can&#8217;t write anything in the command prompt?

---

### Post by Golyadkin on 2007-06-17
Are you using a USB keyboard? Maybe you can try it with a PS/2 ("normal") keyboard.

---

### Post by naji on 2007-06-17
No, my key board is PS/2 (Normal)

By the way, I think my problem is very complex. Because I tried before Mandriva and I found unknown problems in running live CD or installing it.

So, I&#8217;ll write my computer specifications, may it help:
According to cpu-z:
[INDENT]Processor 
	Name = intel Pentium D 930
	Code Name= Presler
	Package = Socket 775 LGA
	Technology= 65 nm
	Specification = intel(R) pentium(R) D CPU 3.00 GHz[/INDENT]
Hard disk  SATA - 200 G
RAM 2 G

---

### Post by Jimmyfj on 2007-06-17
Ok - What about your graphics card? ATI or nVidia? 

Some ATI cards have problems loading the live Cd - Try to choose the second point in the boot-menu:

Start Ubuntu in safe graphics mode - Maybe that will do the trick

---

### Post by naji on 2007-06-17
My graphics card is ATI built in the mother board. My motherboard is (intel D 102)
I tried the second option from the menu and the same problem.

---

### Post by stalkingwolf on 2007-06-17
Try using the check cd option see what it tells you.  What speed did you burn your CD at?

---

### Post by maddot on 2007-06-17
why not try the disc on another system and see if it works. While doing that maybe order a free cd and try that while yer at it. If both don't work it could be a system hardware compatibility problem. if it works, then it could be a cd problem :)

cheers.

---

### Post by beamo on 2007-06-17
I had the same problem but I know my cd was bad because I used the check cd for defects option. I gave up and installed from the hard drive without burning a cd.

[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)

---

### Post by naji on 2007-06-17
My problem not in my CD Rom , its by the way DVD- Rom. 
and choosing the option to check the CD, also gives me the same problem.

**Error message came to me, it says:**
[B]/bin/sh: can&#8217;t access tty: job control turned off
(initramfs) [ 126.199811] ata3.00: faild to set xfermode (err_mask-0x4)
&#8230; Etc[/B]

---

### Post by Roger Gundberg on 2007-06-17
Maybe the CD/DVD unit itself needs cleaning? Here in Socorro New Mexico we have a terrible problem with high winds an blowing sand (silica or raw glass) Every recording session is proceeded with a cleaning of the Read/Write laser. I use a product called Allsop Multimedia CD Rom Lens Cleaner. It looks like a CD with a little brush attached to the bottom of it. I hope this helps.

---

### Post by jagpreet on 2007-07-07
i m having the same problem....

---

### Post by naji on 2007-07-08
I think my problem didnt solved yet, and there is no one can help !!

---

### Post by jagpreet on 2007-07-10
frnd i m also having same prob but u cn use vmware for installing Ubuntu at ur system in that u cn run all the commands of Linux.....

---

