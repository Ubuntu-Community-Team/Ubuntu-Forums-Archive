---
title: "Duplicating my UBUNTU setup on 2nd COMP."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by cryo4.rm on 2007-07-26
after having spent many (far too many) hours fine tweaking the shadows and kerning of my desktop......... having achieved what can only be described as an aesthetic ubuntu nirvana  (an obsession which i sometimes fret is going to cost me my degree) -- after finally getting amarok working JUST right, and, well you get the picture..... im now facing setting up a second computer with ubuntu --------- thing is i reckon i will actually fail my exams if i get sucked into this whole thing another time around........ can i burn "MY" ubuntu settings onto a disc and just paste em on the next machine,,,,,,,

 please........ please... PLEASE tell me i can........



ps..... its FEISTY 7.04

pps.... i'm running 32 bit mode on centrino duo processor..... does that mean i have to use 32 bit version on the other CPU???????  can i use 32 bit version with ANY processor or do i have to choose the computer with a suitable hardware,,,,

---

### Post by aspen_dv on 2007-07-27
I am not sure if you would be able to clone 2 machine with different hardware. You probably could but then the second machine won't work, since kernel is generally customized to exact hardware....I don't know....Hope someone will have a solution cause I would like to know as well.

---

### Post by girishv on 2007-07-27
From your post, it seems that you have not touched the kernel and most probably changed only the look and feel of Ubuntu. In that case, a simple way of cloning the desktop will be to make an image of the existing OS (using partimage) and restoring the same on the new desktop (using live CD)
Though you have to repeat this for all the partitions you have, this saves much of your time than trying to redo everything on the new machine

Girish

---

### Post by cryo4.rm on 2007-07-27
actually i had to change to the generic kernel to make use of the dual processor.... 

 furthermore, as much as the aesthetic angle, i have downloaded a fair few programs which --- as part of the ideal solution i search for --- i would like to not have to download again.. (my internet connection isnt that fast) .. as well as small but numerous liitle things like adding new source libraries, adding MP3 codecs etc etc

   can these little things be cloned with partimage too?

 thanks.

---

### Post by wolfen69 on 2007-07-27
you could save your /home folder. then alot of settings will transfer. ive always been a big fan of clean installs. it's no big deal for me.

---

### Post by Blutack on 2007-07-27
Use simplehomebackup - I was fiddling with it recently and noticed it generates an apt list along with a list of change files and then you can restore that into a new system - basically it will apt-get install what you added, remove what you removed but on top of a fresh install.  If you backup your home directory it will also keep all the themes etc the same.  Only thing to watch is stuff like your xorg.conf.

---

### Post by FleetAdmiral74 on 2007-07-27
I suggest PartImage. While I can't guarantee it will work with the new hardware, this is designed to make images of the entire disk and then mirror that onto other machines.

---

### Post by Benoone on 2007-08-16
If your computer chipsets and monitors and hard drives are the same then you have 8 out of 10.

Substract 7 points if you have different chipsets.  Subtract points for USB drives, IBM laptops and Vista.  Subtract points if you can't boot from a live CD or floppy to do the clone or image/restore.

I'm now pulling my hair out because I only have 8 and can't seem to get to 10.

Acronis 8, 9, 10 and Ghost and R-Studio do not clone my tri-boot drive as they error-out or just plain fail to copy/restore the critical GRUB bootsector on primary partition #3 - really ugly it is.

Hence, I can not boot my Ubuntu on the cloned drive but I have no problem with the Windoz partitions.

I'm now going to try gparted live CD which had a nice writeup in linux.com.

BTW, I'm using Maxtor 500g sata drives in NewEgg/Rosewill eSATA enclousures with double shielded eSATA cables - If you want fast that's what ya gotta do.  I even put handles on the enclusures which makes it a nice portable (always in sync) setup that connects in seconds here at work or at home.  

Now... if I can get a good clone or two.

I have another problem because, after the good boot,  the Ubu screen goes dark if I use the drive on a cpu that has a glass CRT (Compaq FS7555 or Compaq P910) CRT rather than the original Dell LCD.  For now, I don't know how to fix this.  Maybe later?

Oh yeah,  the rule is: 
Clone the drive.  Put the original in safe keeping and don't use it.  Only use the cloned drive and make it your new master.

I'm told to make a big /home partition to put all my stuff so if I move I can at least take that with me - For whatever that's worth? 

Hope this helps.

Benoone

Vista... The best thing that ever happened for Ubuntu!

I found the Trinity Rescue Kit 3.2 (TRK) and it has both dd and ddrescue on the Linux boot CD.  Becareful because there is a both a ddrescue and dd_rescue in the wild and mis-named all over the place.  From what I can read you want the newer ddrescue.

I used #  dd  if=/dev/sda  of=/dev/sdb  and it worked one time with speed of about 10gig/min or 2.5 hours for a 500g drive which is good for a bit copier.  The clone was flawless and I'm using it now.  

But, I can't remember which CPU I used and worse yet, I can't repeat the process as now I'm lucky to get 1g/min and sometimes 1g/hour.  ddrescue does not seem to be any faster.  Now, for me, it's not a data problem but a speed problem.

I'm now looking at CloneZilla  and ./g4l (G4L)...

---

### Post by expatCM on 2007-08-16
Does this help ...
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)


But could you not also 

Save list of installed apps
dpkg --get-selections > installed_applications


Reinstall saved installed apps
sudo apt-get update
sudo dpkg --set-selections < installed_applications
sudo apt-get -u dselect-upgrade

I think you would need to copy over the home directory and the /etc folder as well but perhaps someone else can advise ......

---

