---
title: "recovering deleted files"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-02-06
can anyone recommend a good data recovery tool for Ubuntu 7.10?  i recently installed a vm on an ext3 filesystem which had been working fine for about a week, then my ubuntu system froze up after some recent updates were installed (which required a reboot) and i was forced to do a hard reset on the machine- when i logged back into the system, all of my vm files were gone!!  it has been suggested that i try using an undelete/recovery tool to see if i can get these files back.  any suggestions would be greatly appreciated.  thanks.

---

### Post by eggdeng on 2008-02-06
You might try photorec. It's included on the System Rescue CD. [http://www.sysresccd.org/Download.en.php]("http://www.sysresccd.org/Download.en.php")

---

### Post by Matt26 on 2008-02-06
thanks- how would i use the photorec application?  i have booted to the CD but i don't know how to access it from there.

---

### Post by eggdeng on 2008-02-06
You can start photorec with the command ```
photorec
``` There is a how-to at
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

---

### Post by bumanie on 2008-02-06
A good data recovery tool is meant to be testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by Matt26 on 2008-02-06
i tried photorec and was able to see my files on the volume- but when i log into ubuntu to and go into that volume, they are not there- gparted even shows the drive as being blank with no data on it... how can this be?  is there some way i can restore these files?

---

### Post by petersonjacob on 2008-02-06
go to the disk at press control+H and if there is a .Trash icon click it and see if the files are there, if not, i dont know what to tell you

---

### Post by eggdeng on 2008-02-06
> i tried photorec and was able to see my files on the volume- but when i log into ubuntu to and go into that volume, they are not there- gparted even shows the drive as being blank with no data on it... how can this be?
This is because your files are still on the disk, they have not been deleted. What *is* broken is the file system table which keeps track of them and this is the reason you can't access them from your OS.
I am sorry not to be able to give you more detailed help but thankfully I have only ever had to use photorec once and it was a while ago. As far as I remember, the first step is to create a folder to save recovered files to. You could do this on a pen drive (you can mount it and create a folder on it from the command line before starting photorec) if you have one with enough capacity. That way, you won't overwrite anything on the disk. Then it's basically a matter of telling photorec what files you want recovered and where you want them saved.
If I were you, I would google a bit to see how other people have used this tool & to familiarize myself a little first. If your files are important to you, it'll be worth the effort.

---

### Post by Matt26 on 2008-02-06
would fsck be able to fix this issue with the filesystem table?

---

### Post by nikoPSK on 2008-02-06
there is the linux time machine as well... 
[http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php](http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php)

nikoPSK

---

### Post by Matt26 on 2008-02-06
correct my if i'm wrong here, but wouldn't this application only be effective in my case if it was installed before this issue occurred?

---

### Post by nikoPSK on 2008-02-06
> **Matt26 said:**
> correct my if i'm wrong here, but wouldn't this application only be effective in my case if it was installed before this issue occurred?

true. I'm just saying for future. :)

---

### Post by Matt26 on 2008-02-06
i used fsck on the volume and it worked to allow me to view my files under the live cd.. when i log back into ubuntu normally, the files are gone again- i even rebooted with the volume unmounted, then mounted it manually and the files were available again- i made the volume auto-mount again, rebooted and logged back into ubuntu- no files again!  any ideas what might be causing this issue?

---

### Post by nikoPSK on 2008-02-06
> **Matt26 said:**
> i used fsck on the volume and it worked to allow me to view my files under the live cd.. when i log back into ubuntu normally, the files are gone again- i even rebooted with the volume unmounted, then mounted it manually and the files were available again- i made the volume auto-mount again, rebooted and logged back into ubuntu- no files again!  any ideas what might be causing this issue?

Odd... :| copy the files under the live cd I guess then. :)

---

### Post by mixtri on 2008-04-18
Hi Guys.
I'm having problems understanding how to recover video files that i accidentally deleted from my hard disk .
I have read a number of threads that advice to use photorec.
I use ubuntu 7.10. 

For a new convert to ubuntu and someone with no knowledge about these things it is difficult to follow any of the instructions. 
Everyone seems to talk in a ubuntu/linux geek talk that i dont understand.
Why can't instructions be straightforward.

I attempted to download the rescue cd containing photorec using this link [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)
 and got this set of instructions at the top of the page on the website

"You should download the SystemRescueCd ISO with wget. That's a very simple and reliable download tool. Just type wget -c address in a console. If there is a problem with the download, try again with option -c, and it will continue. Wget was developed for linux, but there is also a win32 version of wget. Here is the direct download link."

I typed wget -c address in my console and got this 

albert@albert-desktop:~$ wget -c address 
--12:10:48--  [http://address/](http://address/)
           => `index.html'
Resolving address... failed: Name or service not known.

Im assuming it requires the web address to the download. where do i get this and why can't i just click on 1 single link that does it all for me.
This is so frustrating.
I found a windows .exe file on the photorec website that is easy enough for thos who use windows, isn't there an equivalent file type for ubuntu that will begin the download/installation automatically instead of typing commands in the console.

Please help.
Just to note - even the step by step guide at: [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) isn't that straight forward. 
HEEEEELLLLLLLLLPPP!!!!!:mad:

---

### Post by Moop on 2008-04-18
You don't need to use wget to download the cd. Here is a link to the iso file. 
[http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964](http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964)

---

### Post by mixtri on 2008-04-18
Moop!
that was so simple and straightforward, as it should be!
thank you very much!

---

