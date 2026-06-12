---
title: "downloading/installation of Photorec on Ubuntu gutsy"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by mixtri on 2008-04-18
Can anyone help with installing photorec on ubuntu gutsy?

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
--12:10:48-- [http://address/](http://address/)
=> `index.html'
Resolving address... failed: Name or service not known.

Im assuming it requires the web address to the download. where do i get this and why can't i just click on 1 single link that does it all for me.
This is so frustrating.
I found a windows .exe file on the photorec website that is easy enough for thos who use windows, isn't there an equivalent file type for ubuntu that will begin the download/installation automatically instead of typing commands in the console.

Please help.
Just to note - even the step by step guide at: [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) isn't that straight forward.
HEEEEELLLLLLLLLPPP!!!!!

---

### Post by northern lights on 2008-04-18
Download [this]("http://www.cgsecurity.org/testdisk-6.9.linux26.tar.bz2") file. Install the following packages: ```
apt-get install build-essential e2fslibs-dev libncurses5-dev libntfs-dev libjpeg62-dev libreiserfs0.3-dev uuid-dev
``` You should now be able to compile using ```
make
sudo make install
```

I don't think it comes with a configuration script...

---

### Post by mixtri on 2008-04-18
Northern Lights to the rescue!!

Thanks mate for the speedy reply.
I managed to download the file which now resides on a folder i created called downloads within my home directory.

Upon running the script i got the following - 

albert@albert-desktop:~$ apt-get install build-essential e2fslibs-dev libncurses5-dev libntfs-dev libjpeg62-dev libreiserfs0.3-dev uuid-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
albert@albert-desktop:~$

---

### Post by spiderbatdad on 2008-04-18
a potentially dangerous program...it can put literally 10's of 1000's of files in your home directory, that you will not have permission to open.
newcomers should beware.

---

### Post by mixtri on 2008-04-18
Thanks for the advice SpiderBatDad. But where does that leave me? and why is everyone professing the advantages of this program if it is potentially dangerous?
Is there an alternative method to solving my problem?

i just want to recover video files i accidentally deleted from my HD within ubuntu. About 15GBs worth
I haven't saved anything to disk since deleting a couple hours ago, well, apart from the photorec files i downloaded. hopefully my lost files will not be overwritten yet.

 I bought a 320 GB hard 6 weeks ago for sole purpose of installing  ubuntu on it, so i'm guessing there shouldn't be too much deleted files to recover/scan through other than those deleted in the last 6 weeks which isn't much, apart from the files i lost today of course.

---

### Post by spiderbatdad on 2008-04-18
Only a warning to newcomers who might think...cool I'll run that and see what happens...like me a couple of years ago. It put around 20,000 files into my home directory, and I did not have permission to open them nor even move them to trash...well I learned about permissions...and mass file manipulation...
So, just a light warning...be prepared to see a lot of files if your computer has been heavily used.

---

### Post by northern lights on 2008-04-18
As for the error "are you not root?":

"apt-get" ought to be run with "sudo", i.e. ```
sudo apt-get...
```

---

### Post by mixtri on 2008-04-18
Thanks guys for your help in this matter.
i have succeeded in downloading the file.
but now as always, another problem has cropped up.

i am unable to burn the file to a cd rewritable disk.

i have a couple of CD-RW's with files on them which i want to delete to make room for the fresh burn but i keep getting error messages - 

Error while deleting.
"/media/NEW/...er, UF.avi" cannot be deleted because it is on a read-only disk.

the disk is rewritable.

Whats more, I cannot seem to access my external hard disk as ubuntu refuse to mount it.

Phew what a pallava.:lolflag:

---

### Post by mixtri on 2008-04-18
I forgot to mention the external hard disk make is called MENTOR. It's USB portable with a size of 20Gb

---

### Post by bumanie on 2008-04-18
I would tend to get the live cd of test disk&photorec - live cd's of recovery software are always handy.
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

