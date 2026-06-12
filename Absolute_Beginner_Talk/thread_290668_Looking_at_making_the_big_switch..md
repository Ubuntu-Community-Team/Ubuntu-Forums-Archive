---
title: "Looking at making the big switch."
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Protopath on 2006-11-01
I've had it with M$. ](*,) I want Linux.

However, I've tried Enlightenment/Elive and Debian.  The computer that I was experimenting on now acts like a old Nintendo, you know the blink on-blink off thing.

I want to put Ubuntu on my primary computer, no dual-boot.  However to do this it must work well and be relatively easy to do.  I'm not a computer expert.

Here is a rough hardware list:

Intel Celeron 2.53GHz
256MB DDR (PC 2100) RAM
40GB HDD
CD-RW/DVD combo drive
Intel extreme Graphics 3D 64MB Shared memory
AC '97 Audio
Intel Pro 10/100 Built in Ethernet
Epson ActionLaser 1100 (old laser printer that I use to print transfers for my circuit boards, I have to have this)

I don't know very much about most of the above, I just use it.



Software that I must have:

OpenOffice(that should be easy to installl)

Geda(should also be pretty easy, I use EagleCad under M$)

JAL v1 (This a PicMicro compiler, primarily for windows systems, the source has been released under the GNU license.  I will have to have help compiling this)

JAL v2 (Same thing, new version that I'm still learning)

XWisp software (This communicates with my hardware chip programmer through the serial port, I believer it was written under Python. It is also GNU)


Software I would like to have:

Preferably a 3D Cad, 2D if neccesary.  I use a really old version of shareware CADVANCE now.

Emacs

Lisp compiler(Neal Stephenson says this is the only computer language that is beautiful, I'd like to start learning it)

C compiler(Took one class on it in high-school/community college, I'd like to start learning that also.)

Gimp


I do not know very much about linux.  Any help would be appreciated, and I'll probably need step-by-step instructions.

Thanks, and sorry for the long post.

---

### Post by raqball on 2006-11-01
I think you will be fine! You might need to use the alternate install CD as it is text based and might work better with your older PC. As far as software goes, not sure about all your selections but OO and gimp come pre-installed :)

---

### Post by think13 on 2006-11-01
Ubuntu comes with OpenOffice2.0, as well as gimp, and I believe gcc is there  by default also, a c compiler.  Emacs is very easy to get from the package manager.

More experienced people will have to help you with some of the tougher things on your list though :)

---

### Post by raqball on 2006-11-01
A few things to help in the transition. try to not cut and paste commands. Type them out when they are offered. It helps you to learn :)

Aslo, read these forums, they are a great source of knowledge! Read books, take a class, and ask if stuck! Most here are awesome when it comes to helping :)

---

### Post by compmodder26 on 2006-11-01
> **think13 said:**
> Ubuntu comes with OpenOffice2.0, as well as gimp, and I believe gcc is there  by default also, a c compiler.  Emacs is very easy to get from the package manager.

More experienced people will have to help you with some of the tougher things on your list though :)

I actually think gcc isn't installed by default.  You will have to install the build-essential package from the repositories.  But that is simple enough to do.

---

### Post by xboxbman on 2006-11-01
I was a linux noob when I made the switch in June, and already I almost feel more comfortable in terminal than I do in GNOME.  These forums are an amazing resource and full of very knowledgeble people.  I can never go back to windows now.  A thought, after looking at your computer specs, it might be wiser to use Xubuntu.  It only need 128 mb ram to install, then 64 mb run.  I actually have it running on my xbox.  Great little distro.

---

### Post by Protopath on 2006-11-01
Xubuntu.  Guess I'll start researching that.

---

### Post by lazyart on 2006-11-01
And please, use Dapper (6.06) and not Edgy (6.10).  If your printer emulates PCL you shouldn't have problems with it.  From what I've read, Edgy is just that ... while dapper seems to be a bit more refined.

---

### Post by Protopath on 2006-11-02
Is it reccomended that I use Xubuntu Dapper 6.06 or Edgy 6.10?

Thanks

---

### Post by lazyart on 2006-11-02
Dapper will get updates and support for 3 years and is considered more stable than Edgy.

Edgy works for many, but being so new it has it's share of issues that are still being worked out.  Leave that for the adventurous, or at least the more experienced folks.

---

### Post by slimdog360 on 2006-11-02
you can use eagle in linux also. Its in synaptic after you enable the extra repositories.

---

### Post by theicyj on 2006-11-02
You might want to try out QCAD for your CAD needs, it look pretty promising.  You could also look into KTechLab for pic simulations.

---

### Post by Protopath on 2006-11-03
Currently trying the live version of Xubuntu 6.06.

This is incredible, this is faster than XP and it is running off a cd!  I love the pager, was going to ask if this was an option, that was one of the things I really liked about elive.  Got my screen resolution close, maybe a tad small from what I normally like.  Sound works.  Obviously I'm online, never that easy with windows.

A few questions:

How do I see if it will recognize my printer? (Epson ActionLaser 1100)  I saw the cups thing, but I've read a horror story about that.

I tried the check cd option, took forever(more like 10 minutes).  Very quickly a message flashed at the end, about the status of the check, and it rebooted.  I didn't have time to read it.  Does that mean it passed?  The MD5sum on the iso image was fine.  

Thanks, this rocks.

---

### Post by Protopath on 2006-11-03
Using the Xubuntu help I have got to the web based admin page of Cups.  A driver was not self evident so I ran a search and found a linux driver.

Downloaded that to deasktop, and used the browse function to select that ppd.  At that point I got: 

413 Request Entity Too Large

HTTP/1.1 413 Request Entity Too Large Date: Fri, 03 Nov 2006 01:54:11 GMT Server: CUPS/1.2 Content-Language: en_US Upgrade: TLS/1.0,HTTP/1.1 Connection: close 

:Is this due to RAM and a live cd?

Thanks, not getting very far yet, but the interface is very intuitive.  Terminal stuff makes me feel like I'm back in the DOS days trying to get Doom to run.

---

### Post by Soarer on 2006-11-03
According to LinuxPrinting.org, your Epsom works 'Perfectly'.

The page with set-up instructions is at: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-ActionLaser_1100](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-ActionLaser_1100)

Have fun :)

---

### Post by Protopath on 2006-11-03
Yeah, that's the page I found.  Downloaded the PPD.  Didn't quite work as I'm doing it.  Not real sure why.

Does this have something to do with Gimp-Print?

Thanks

---

### Post by Soarer on 2006-11-03
I haven't installed that printer myself, but I just use CUPS which is already installed with Ubuntu.

Have a look at the CUPS instructions at: [http://www.linuxprinting.org/cups-doc.html](http://www.linuxprinting.org/cups-doc.html) and see if that helps. 

It seems it isn't autodetected, so you will have to install 'manually' - actually there's a GUI, so its easy. 

To do this, go to  System>Administration>Printing. You can add the printer from there. It will ask you which driver to use - you should be able to choose from its list. 

(I just checked - your printer is in the CUPS db so the driver is already on board).

Make sure its plugged in first :)

---

### Post by Protopath on 2006-11-04
It lives!  Thanks Soarer, after installing xubuntu onto the hard drive everything went fine.  But you were right, that driver was already under CUPS, I just didn't understand.

That was actually a lot less trouble than I had trying to get it to run under xp.

BTW, the export function for firefox bookmarks worked. I have my old bookmarks back.  I didn't see that listed in the faqs, that would be a good thing for newbies like me to know.  Or maybe it's just really obvious.

---

### Post by Soarer on 2006-11-04
That's great. Printing can be a lot easier under Ubuntu - I had to install a huge amount of stuff to get that HP 7310 working under XP.

Glad to hear its working :)

---

### Post by Protopath on 2006-11-05
Thank you all for your help. :cool: 

Everything I had to have is now working.  I have gotten my JAL compiler and Xwisp software working and have tested both down to the chip.  I've got Emacs and Geda also.  I'm going to post about this over at the JAL forum so that others can see this is doable.  

As of now I don't have JAL v2 working.  It will have to be compiled from source, but I'm not in a big rush for it.

I still have some moving around to do, get the compiler and such in the right directories and make them global commands.  However I feel I'm over the big hump.

I'm beginning to see the power in the linux way of doing things.  I don't mind the config files, most of them seem well commented.  And it is nice to get back to the command line.

Emacs looks like it is going to be a hell of a thing to learn.

What a great way to blow a weekend.

Thanks again.

---

### Post by DanSchnell on 2006-11-05
/hijack > Intel **extreme** Graphics 3D 64MB Shared memory

LOL  64MB is very extreme...:) Don't worry, my old computer has that too though, which is what I have linux on 

/endhijack

Just burn the iso to a CD to make it a LiveCD, boot to it, click on the installer, and do some minor configuring, and then relax.

(Unless your me and can't get the LiveCD to work, or the Alternate Installer on my main computer :( My GUI never loads, i just get garbarge, found [here]("http://ubuntuforums.org/showthread.php?p=1701094#post1701094") )

---

### Post by Protopath on 2006-11-05
Actually I'm done for now.  Installed on Thurs, today being Sun, I have finished major setup and customization, even threw in another hard drive and dvd-rom this weekend.  Running Xubuntu 6.06 for my older system.

---

### Post by jbonll05 on 2006-11-05
Stay away from 6.10 Edgy Elf, it is a beta, and a bit edgy. If you are downloading, get 6.06.1, it corrected an update error in 6.06 that caused some of us to lockup or crash. While another 256mb ram would help some, Xubuntu is a smaller package and quicker. I do not know how Xubuntu handles graphics. 6.06.1 has Gutenprint 5+ for your Epson printer and should work.
  My experience has shown good hardware compatibility and stability from 6.06.1. It is on home/office machine. I process several digital picture a week forbusiness and pleasure. I also run 6.10 as a project.  JB, Ubuntu since Oct05 as a user

---

