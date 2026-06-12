---
title: "installing to dvd-rw"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by otterbob on 2006-09-29
Greetings , 

Have been running ubuntu 6.06 on home computer and liking it . 

I know It may sound weired but I would like to use this as a "bootable DVD-RW" so that I can use it on the office computer without adding it to the Office HD . This way all my files and work will remain in my position { not supposed to install ANY software to the company { win xp computer } } . Is there any way to install to a DVD-RW and be bootable ? 
Live cd is fun but cant save or configure without access to a drive . 

Otter Bob

---

### Post by bullfrog2 on 2006-09-30
you might want to try PUPPY LINUX.it runs in windows. what you download it installs in either to a folder in windose or back to disk, either cd or dvd. hope this helps

---

### Post by K.Mandla on 2006-09-30
There's a nifty little doodad called [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") that will allow you to customize an Ubuntu live (desktop) CD. I don't know that it works with DVDs, but I imagine it's possible.

If you have access to a USB port on your work computer, then a USB flash drive for saving your files would be preferable to trying to reburn the DVD while it's running the live system. Does that sound like an option?

---

### Post by otterbob on 2006-09-30
> **K.Mandla said:**
> There's a nifty little doodad called [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") that will allow you to customize an Ubuntu live (desktop) CD. I don't know that it works with DVDs, but I imagine it's possible.

If you have access to a USB port on your work computer, then a USB flash drive for saving your files would be preferable to trying to reburn the DVD while it's running the live system. Does that sound like an option?

I will look at the reconstructor to see if I can change where ubuntu installs . 

as for the usb , I do have usb access and have a usb hd but I was trying to keep the size down to a single DVD . 
The standard dvd will give me more then enough space and the duel layer would give me an excess of storage space . 

Live Cd works great but The idea is to add gnucash , gftp ,html editor ,  gimp , open office , skype and an email program . 

Otter Bob

---

### Post by K.Mandla on 2006-09-30
Right on. I know with Reconstructor you have the option of adding some programs to be installed along with the standard Ubuntu order of battle, which means you *might* be able to tack on the ones you want before burning the CD. (I'm thinking space would be an issue for a CD, but you're right in saying the DVD would be spacious. ;) )

---

### Post by otterbob on 2006-09-30
> **K.Mandla said:**
> Right on. I know with Reconstructor you have the option of adding some programs to be installed along with the standard Ubuntu order of battle, which means you *might* be able to tack on the ones you want before burning the CD. (I'm thinking space would be an issue for a CD, but you're right in saying the DVD would be spacious. ;) )

I took a quick look at reconstructor and it "appears" that all it does is let you change the cosmetics . 

what is needed is the live cd burned to a dvd so that once it boots ubuntu would setup the hardware automaticly like the live cd does , then allow to burn additions and configs and files back to the RW without lossing the auto-config feature .

But that is a little beyond me .

For me it would be like an HD in a sleeve or jewel case .

Are there any good programs that would allow me to burn a cd ISO to a dvd to see what would happen ? 
I will see if my nero will do it .  

Otter Bob

---

### Post by otterbob on 2006-09-30
> **otterbob said:**
> 
Are there any good programs that would allow me to burn a cd ISO to a dvd to see what would happen ? 
I will see if my nero will do it .  

Otter Bob

Nope ,,, Nero Spit out the dvd and ask for a cd . 

Otter Bob

---

### Post by otterbob on 2006-09-30
Could not find one , but is ubuntu offered as a live DVD ?

Otter Bob

---

### Post by K.Mandla on 2006-09-30
> **otterbob said:**
> Could not find one , but is ubuntu offered as a live DVD ?
If you boot the [DVD version]("http://old-releases.ubuntu.com/dapper/"), it should come up in a live environment, not unlike the live (desktop) CD. 

To be honest, I've never heard of anything for Ubuntu that does what you're describing.

On the other hand, there are some lightweight distros that do something similar ... giving the opportunity to customize the boot disc to include additional software. [DSL]("http://www.damnsmalllinux.org/") and [Slax]("http://www.slax.org") are two with that ability. I don't think they'll write back to the DVD, though.

---

### Post by revoltism on 2006-10-12
Here is the description of Reconstruktor and it seams to support program adding.... "For example, create a custom Live CD with blender, inkscape, etc."  ....It means it should support half of your wishes.

------------------------------------
What is Reconstructor?  
  Reconstructor is a Live CD creator for Ubuntu Linux.

It uses the Ubuntu Linux Live CD as a base, and then allows customization of boot screens (usplash), gnome settings, and software (you can also use the chroot environment to make other changes before creating the live cd).

Reconstructor does not create separate distros.  It keeps the solid Ubuntu foundation, and just allows for customization.  For example, create a custom Live CD with blender, inkscape, etc. included for a friend in graphics, or simply use reconstructor to re-brand your environment (wallpaper, fonts). 

Reconstructor is written in python and is licensed under the GNU General Public License (GPL)

---

