---
title: "get me started"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by bigskyjack on 2008-02-05
ok, i wud like 2 try ubuntu, so i spent ~8hrs last nite d/l'ing v7.10 from the ubuntu web page.  then i burned it onto a cdrom.  what do i do with it now?  i have put it into the drive - windows sez "cannot open, file type not recognized".  i changed the bios to boot from the cdrom, & rebooted the laptop with the cd in the drive - nothing, goes strait to winxp.  i can find nothing on the web sites or any of these forums that talks about this most basic issue...   how do u start ubuntu?
thanx!
big sky jack

---

### Post by LowSky on 2008-02-05
you have to burn a bootalbe CDROM, you can just burn the file to a disk.


follow these instructions

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by Nythain on 2008-02-05
it sounds like you burned a data disc containing the iso
what you need to do is burn the iso image to disk...
the difference, one is a disk containing the one iso file on it ilke it is on your computer
the other takes the iso image file (consider this a cd zip file) and puts the contents of that image onto the cd.

you will need to find software that will "Burn ISO Images"... in windows i use Nero, but i dont know if they have a free version that will do this or if you need a registered version... a google search for something like "free windows iso burning software" should give tons of results though for programs wich are hopefully, free :)

---

### Post by bigskyjack on 2008-02-05
ummmm, ok
sounds like u r telling me that the file i d/l'd wont function in its current form?  why isnt this mentioned anywhere - i wonders?

i have this:
ubuntu-7.10-desktop-i386.iso
all 712MB of it, which only JUST fits on a cdrom...

Windows has the following information about this file type. 
File Type: CD-ROM Image 
File Extension: .iso 
Description: This file is a CD-ROM image. 

it sounds like u r saying i need an "image"...
this sez i have one
i think i'm confused
(what am i thinking?  ofCOURSE i'm confused!)

i need some other piece of software to convert this to a 'bootable' disk?
how do normal ppl do this?
(okok, no such thing.)

---

### Post by ubutufan on 2008-02-05
Download deepburner which is free software.
You may use it to burn the iso to the cd

---

### Post by bumanie on 2008-02-05
What are you using to burn the cd with in windows?

---

### Post by wolfen69 on 2008-02-05
an iso ***IS*** an image. you have the correct one. burn  ubuntu as an image, not data.

---

### Post by mangurt on 2008-02-05
It sounds like you have the correct file, you just need to put this file onto the CD-rom the correct way.  The way you describe what you have on the disk you burned is a data disk, you need to burn that ISO image to a disk.  If you are using windows, you can use NERO, CD-Creator or any number of programs out there to accomplish this.  What you need to look for is write iso image to cd.
Hope that helps you.

---

### Post by gunksta on 2008-02-05
Here are some suggestions:

1) Slow Down
2) Breathe
3) Follow LowSky's link. I looked at it and it will get you where you want to go.

If you don't like any of those options download [InfraRecorder.]("http://infrarecorder.sourceforge.net/?page_id=5")

I don't know where you downloaded your CD from, but the typical starting point is [here]("http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fmirrors.cat.pdx.edu%2Fubuntu-releases%2F&debug=&download-button="). For the sake of this post, I am assuming that you downloaded the .iso file from the Ubuntu page I linked to above. If you did, there were detailed instructions on what to do on the page you downloaded from. If you follow the first link it will give you detailed instructions on how to burn the iso correctly so you can boot from it.

But, you're going to have to follow the link and read . . . . 

**Need Help?**

 Here are some tips for ensuring a successful Ubuntu experience. You may want to print this page for your reference.
 [LIST]
[*]Learn how to create a CD from your newly downloaded file: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[*]Learn how to verify that your CD download ok: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[*]Read the Ubuntu documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
[*]Get help:
[*] [LIST]
[*]Visit the Ubuntu forums: [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)
[*]Ask questions via e-mail: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-users](https://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
[*]Instant help via online chat: [https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)
[*]Commercial, paid support: [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)[/LIST]
[*]Join the Ubuntu community, there are many ways to [get involved]("http://www.ubuntu.com/community/participate").[/LIST]

---

### Post by bigskyjack on 2008-02-05
wooo whoooo
ok - yes i did d/l from the getubuntu page
i just went to the instructions page u recommended
tried to d/l infraburner
it crashed my browser, which in turn locked up my puter
so, now, after a cold boot, i think i will try a different 1

maybe this is just not my day?
okok - just breatheeeeee

---

### Post by gunksta on 2008-02-05
Breathing is usually a good thing.

Don't know about your problem with Infraburner. I've used it on several Windows computers and I've never had a problem.

---

### Post by jrothwell97 on 2008-02-05
Try ImgBurner. That's quite good in my experience.

Should you be having serious difficulties, you might like to try [Wubi](http://wubi.sourceforge.net/faq.php#internals) (with health warning attached).

---

### Post by bigskyjack on 2008-02-05
well - i tried 'lowsky's suggestion, d/l'd 'iso recorder', installed it, couldnt find it, reinstalled, repaired install, deleated it, reinstalled it again - then burned a NEW cd (it offered me Noptions), then after 15min, it crashed:  "Operation has failed.  Code 8004020e, Reason: A generic  error occurred."  so, i have uninstalled it again.

next?  'imgburner'?  ok....
i spose all the thousands of ppl using ubuntu have gone thru all of this already?
why do we do this to ourselves?!?!?

---

### Post by jrothwell97 on 2008-02-05
It's actually quite a lot simpler than it looks.

The .iso file is a simple and direct dump of everything that is on the CD. As in, it's actually a bunch of zeroes and ones.

This can be burned to a CD using said applications. Alternatively, you can, as I suggested, try Wubi. I highly recommend it, as it doesn't touch your partition table.

---

### Post by gunksta on 2008-02-05
> **bigskyjack said:**
> well - i tried 'lowsky's suggestion, d/l'd 'iso recorder', installed it, couldnt find it, reinstalled, repaired install, deleated it, reinstalled it again - then burned a NEW cd (it offered me Noptions), then after 15min, it crashed:  "Operation has failed.  Code 8004020e, Reason: A generic  error occurred."  so, i have uninstalled it again.

next?  'imgburner'?  ok....
i spose all the thousands of ppl using ubuntu have gone thru all of this already?
why do we do this to ourselves?!?!?



I've seen people ask how to burn bootable CD's from .iso files before but I don't believe I've ever seen someone struggle quite this hard with it.

Perhaps you should go back to the Ubuntu page and get Canonical to send you a free CD that already has Ubuntu burned onto it.

---

### Post by stchman on 2008-02-05
> **bigskyjack said:**
> ok, i wud like 2 try ubuntu, so i spent ~8hrs last nite d/l'ing v7.10 from the ubuntu web page.  then i burned it onto a cdrom.  what do i do with it now?  i have put it into the drive - windows sez "cannot open, file type not recognized".  i changed the bios to boot from the cdrom, & rebooted the laptop with the cd in the drive - nothing, goes strait to winxp.  i can find nothing on the web sites or any of these forums that talks about this most basic issue...   how do u start ubuntu?
thanx!
big sky jack

I have a tutorial on how to make a bootable Ubuntu CD from a .iso.

[http://www.stchman.com/create_cd.html](http://www.stchman.com/create_cd.html)

---

### Post by bigskyjack on 2008-02-05
wow - thanx guys (& gals?) - it finally worked! (16hrs later),
i took a wag in imgburn & got a disc that will actually boot in the lappy!
luckily, i had a black cd!, well, its only about 2/3rds black...  but it worked! ;-)
appreciate all the help!
i'm sure i will b bak...
later
jd

---

### Post by timbounceback on 2008-02-05
maybe try [Isorecorder]("http://isorecorder.alexfeinman.com/")? I should probably add, you won't have to worry about things like your browser locking up when on Ubuntu, it's nice and stable and rarely crashes :-).

---

