---
title: "Questions before leaving Windows completely: sharing files / replace Macromedia Flash"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by RavUn on 2008-02-17
I installed Ubuntu on this computer and I mainly use this computer now.  I have another computer with Windows which used to be my main computer until I built this one.  I rarely use my computer with Windows and when I do it's so frustrating because it randomly slows down and my scroll wheel on my mouse does weird things.

I mainly use my Windows PC to get to various files and to design things in Macromedia Flash 8.0 Professional.  I believe that if I merged my files to my Ubuntu computer and could find a replacement for Macromedia Flash, I could leave Windows for good... (Maybe I'd get it around in case I find something only Windows could handle) but I could move my KVM switch to my other Ubuntu PC.

My two questions are:
1) How could I setup my Ubuntu computer to share files with my Windows PC?  They are right next to each other and are both connected to a linksys router.  I know that with my two windows computers I could just hook them up to each other and share files, but I don't know how to do it with Ubuntu.  Is there a simple guide/tutorial for this?  Then I could just merge the files over, or.. better yet, just leave the files on my windows PC and get to them whenever.

2) Is there anything like Macromedia Flash 8.0 Professional for Ubuntu?  I use it quite often and I'd like to find something I could use in Ubuntu (although, I do like using Flash).  I know there's GIMP for editing pictures and stuff, but I like messing with actionscript and being able to create .swf files, also.

Thanks :)

---

### Post by sb12 on 2008-02-17
> **RavUn said:**
> I installed Ubuntu on this computer and I mainly use this computer now.  I have another computer with Windows which used to be my main computer until I built this one.  I rarely use my computer with Windows and when I do it's so frustrating because it randomly slows down and my scroll wheel on my mouse does weird things.

I mainly use my Windows PC to get to various files and to design things in Macromedia Flash 8.0 Professional.  I believe that if I merged my files to my Ubuntu computer and could find a replacement for Macromedia Flash, I could leave Windows for good... (Maybe I'd get it around in case I find something only Windows could handle) but I could move my KVM switch to my other Ubuntu PC.

My two questions are:
1) How could I setup my Ubuntu computer to share files with my Windows PC?  They are right next to each other and are both connected to a linksys router.  I know that with my two windows computers I could just hook them up to each other and share files, but I don't know how to do it with Ubuntu.  Is there a simple guide/tutorial for this?  Then I could just merge the files over, or.. better yet, just leave the files on my windows PC and get to them whenever.

2) Is there anything like Macromedia Flash 8.0 Professional for Ubuntu?  I use it quite often and I'd like to find something I could use in Ubuntu (although, I do like using Flash).  I know there's GIMP for editing pictures and stuff, but I like messing with actionscript and being able to create .swf files, also.

Thanks :)

as far as sharing files you would use samba, I am sure there is a howto somewhere on the site or on google, I dont believe you can create swf files though, maybe if you tried running through wine.  Alternatively you could dual boot or maybe run windows in a VM

---

### Post by Hospadar on 2008-02-17
Probably the best solution for macromedia flash would be running it in a VM.  this can be a little tricky to set up, but once you get it working it will almost certainly work just fine.  You could certainly try installing it in wine (check the wine appdb first for tips) but I suspect a big commercial application like that is not going to play very nice with wine.
The trouble is that flash (swf) is a (very complicated) closed format.  There is an experimental open-source flash player called gnash that is attempting to reverse-engineer swf, so I would guess they might have some dev tools, but for sure nothing even close to the features, stability, and polish of macromedia flash.

---

### Post by MONODA on 2008-02-17
Well I use Samba to share my files over a network. just search samba in the add remove menu and install which ever frontend for samba you like. 
to make animations you can use GIMP. I have done this several times and saved the files as GIF. there is an animation feature under the filter menu I think. check it out.

---

### Post by BLTicklemonster on 2008-02-17
To share files, look at the link in my sig. Took me two years to get to where I can share files back and forth.

---

### Post by Ardrias on 2008-02-17
If you're looking to just transfer them over from Windows to your Ubuntu machine, you could also use [WinSCP]("http://winscp.net/eng/index.php") to do that.

---

