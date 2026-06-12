---
title: "virtual drive in Ubuntu?"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-14
Hi, I have read many similar questions and the answer that you can mount an iso through terminal or console. That is great and I have found many different ways to do so. The question I and many other people have posted is, "is there a virtual drive program". The purpose of a virtual drive is so that when you tell it to mount an iso, it is like you just put one in your real drive. Program disks automatically run the splash screen and dvd's automatically open in your default dvd player. 

I haven't tried all the other ways yet but am working on it. The problem is, if I use something like acetone or gisomount to mount it, how do I tell totem, vlc, or mplayer to play it as if it was a actual dvd in an actual drive. There are countless programs free for windows that do this and they show up in My computer as a real drive. Other programs like Nero, and Roxio include the option to create virtual drives. Does anyone know of a program for ubuntu that i'm not aware of that will actually do this? Please don't reply that it is not nessesary to create a virtual drive cause I can just mount it and go to the file I want. That is not the point of this question. Virtual Drives are convenient and fast and require no terminal commands or browsing to a file. They just play. If not anything at the moment, does anyone know if there is a future plan to include something like MagicISO or Alcahol for Ubuntu?

Thanks :-)

---

### Post by billgoldberg on 2008-03-14
This kind of thing has been asked before and I always think (and now suggesting to you) why you just don't open the iso in vlc?

Am I missing something? 

Just open vlc, pick open file and select it. Or right click the iso file, go to properties and choose vlc in the open with tab.

---

### Post by SpenceMakesSense on 2008-03-14
> **billgoldberg said:**
> This kind of thing has been asked before and I always think (and now suggesting to you) why you just don't open the iso in vlc?

Am I missing something? 

Just open vlc, pick open file and select it. Or right click the iso file, go to properties and choose vlc in the open with tab.

This worked for me also.

---

### Post by Duck2006 on 2008-03-14
To mount an *.iso

sudo mount -o loop /path/to/file.iso /path/mount/point

To make a mount point

mk/dir /home/your-account/name

And "billgoldberg" post will to it may be easy to do it that way.

---

### Post by myddewji13 on 2008-03-14
go to add remove programs.... install gmount -iso...ta da....

---

### Post by iansane on 2008-03-14
OK well mounting it in vlc is as close as it gets for dvd's to being a virtual drive. But it doesn't mount other types of cd's and dvd's. Suppose I or someone created a package and a splash screen with install options like you see in windows all the time, only for Ubuntu to install a .deb or several .debs. I want to make it so you can just put the cd in a drive and the splash screen will open automatically from an auto run file. Only difference is, I want this to happen simply by clicking on a mount button and browsing to the iso   I realize this is not windows and I hope it never get's to much like windows but I don't understand why it doesn't seem to be accepted in the linux community that to have a virtual drive would be very convenient. 

As far as media play, I am confused and probably don't know what I'm doing because in order to play every kind of file I come across I have to have mplayer, totem, , timidity, and a ton of gstreamer plugins. I also use mozplug to make my browser able to use which ever one is capable of playing a certain file type.  Now I have to install vlc too, to be able to play an iso like a normal dvd. In windows, I just installed a mega codecs pack and it uses media player for everything. How convenient.

---

### Post by HermanAB on 2008-03-14
Waaaal, laak de maan sed a couple posts up: Run synaptic and install "gmount-iso"

---

### Post by iansane on 2008-03-14
> **HermanAB said:**
> Waaaal, laak de maan sed a couple posts up: Run synaptic and install "gmount-iso"

LOL waaaa! Laak de original post sed! Dats no virtual drive!! 

No but seriously, I mounted a dvd iso to a folder with gmount-iso..... So what now. It's a folder with a bunch of .vob, .bup and other files in it. Not a dvd. When I click on the first vob it plays but none of the dvd menu options work. That's why it needs to play like a real drive.

---

### Post by PeterJS on 2008-03-14
Linux doesn't diffentiate between where it's byte streams come from. A byte stream at /dev/cdrom that happens to conform to the iso9660 standard is the same as a byte stream at /home/user/something.iso that also conforms to the iso9660 standard. I think the crux of the miscommunication is that iansane is looking for a tool that will invoke the hal removeable media handlers on the images after he mounts them. I don't know of such a tool, but hopefully this will refine the discussion for someone who does.

---

### Post by iansane on 2008-03-14
> **PeterJS said:**
> Linux doesn't diffentiate between where it's byte streams come from. A byte stream at /dev/cdrom that happens to conform to the iso9660 standard is the same as a byte stream at /home/user/something.iso that also conforms to the iso9660 standard. I think the crux of the miscommunication is that iansane is looking for a tool that will invoke the hal removeable media handlers on the images after he mounts them. I don't know of such a tool, but hopefully this will refine the discussion for someone who does.

Yes I think that refines it, if that translates to me just mounting it and it autoruns or autoplays. I am semi-newb and not sure but hal removeable media handlers sounds right.

---

