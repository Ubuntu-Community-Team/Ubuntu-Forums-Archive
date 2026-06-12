---
title: "[b]please Help! Want To Install Ubuntu[/b]"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by ubnub2k6 on 2006-05-14
I want to install ubuntu on my laptop but the bios does not support booting from usb drive (cdrom). Updating bios is not an option. I can install win xp fine thru dos drivers, so I was hoping the same could be done with linux. Is there some sort of linux boot disk that will allow me to load my usb drive so I can install ubuntu?

---

### Post by catlett on 2006-05-14
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)  I saved this link from someone elses post. I have not used it but they it works. This is the home page with a little more detail.[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

P.S. Now that I'm looking at it, I don't know about USB booting. The thread I got it from said it allowed booting from ant media but I don't see it on their website. You might want to download it on to a floppy and boot to it just to see if it works. It doesn't touch your hard drive or anything so if nothing else works you might want to give it a try. I'll try to find something else. Sorry for the confusion

---

### Post by tc10b on 2006-05-14
What sort of laptop do you have, and is your cdrom drive usb or you trying to install from a USB drive?

You don't need to put BBCode in your title as it will appear bold to those who haven't read it.

Try that link above, it should work for you.

---

### Post by ubnub2k6 on 2006-05-14
my laptop is a toshiba portege 7200 it does not have a cd rom drive thats why im using an external usb cdrom to try and install

---

### Post by ubnub2k6 on 2006-05-14
thanks for the tip but unfortunately sbm cant boot from a usb drive unless the bios is able to as well.

any other recommendations?

---

### Post by Kvark on 2006-05-14
[QUOTE=ubnub2k6]any other recommendations?[/QUOTE]
Well, there is a [howto about installing Ubuntu without using a CD]("http://www.ubuntuforums.org/showthread.php?t=28948"). It seems pretty complicated, maybe there is an easier way, but if not then that howto looks like it should do the trick.

---

### Post by tc10b on 2006-05-14
What does your bios support other than hard drive and floppy (presumably)

---

### Post by ubnub2k6 on 2006-05-14
the bios supports hd, floppy, and cd rom

---

### Post by tc10b on 2006-05-14
Kvark posted something before me so try that and come back if there is still a problem.

---

### Post by catlett on 2006-05-14
Here's a wild idea. Can you run the Dapper Live cd with a daemon tool? And if so can he run the install from the live cd while running the iso with a daemon tool? I don't know but it seems in theory you can do it, or am I missimg something?
Here is my favorite daemon for XP. And it's free [http://www.slysoft.com/en/virtual-clonedrive.html](http://www.slysoft.com/en/virtual-clonedrive.html)

---

### Post by Kvark on 2006-05-14
[QUOTE=catlett]Here's a wild idea. Can you run the Dapper Live cd with a daemon tool? And if so can he run the install from the live cd while running the iso with a daemon tool? I don't know but it seems in theory you can do it, or am I missimg something?
Here is my favorite daemon for XP. And it's free [http://www.slysoft.com/en/virtual-clonedrive.html](http://www.slysoft.com/en/virtual-clonedrive.html)[/QUOTE]
Is it really possible to boot from a virtual CD provided by a daemon tool?? If so then it's amazing!

---

### Post by catlett on 2006-05-14
I don't know but in theory can't it happen? I think I'm going to try and see what happens.
My logic is, 
If you are running the live cd and it can run the install then why can't the daemon run the live cd and the install as well. My only sticking point in wondering is the hard drive being mounted and the live cd couldn't make changes because it was running off a mounted hard drive and not a cd

---

### Post by ubnub2k6 on 2006-05-14
i tried using kvarks idea and everything goes right up until its detecting the ubuntu mirror that has an archive. Can I have it search on my hard drive for the cd image/ unextracted files on the image or is this strictly a network boot?

---

### Post by tc10b on 2006-05-15
What is the problem that is occuring? 
I know that sometimes it takes a little longer when I install on computers not connected to the network, but it should install fine without a network connection.

---

### Post by ice60 on 2006-05-15
hi, maybe one of these links will help :confused: 
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)
[http://www.dslreports.com/forum/remark,15974957](http://www.dslreports.com/forum/remark,15974957)
[http://www.daniweb.com/techtalkforums/thread2932.html](http://www.daniweb.com/techtalkforums/thread2932.html)
[http://www.daniweb.com/techtalkforums/thread12681.html](http://www.daniweb.com/techtalkforums/thread12681.html)

BTW, here's a link to the MS virtual cd drive which is freeware
[http://download.microsoft.com/download/7/b/6/7b6abd84-7841-4978-96f5-bd58df02efa2/winxpvirtualcdcontrolpanel_21.exe](http://download.microsoft.com/download/7/b/6/7b6abd84-7841-4978-96f5-bd58df02efa2/winxpvirtualcdcontrolpanel_21.exe)

---

### Post by ice60 on 2006-05-15
i was just looking at some RSS feeds and saw this one
[Install Linux Over the Internet](http://www.pcworld.com/howto/article/0,aid,125512,00.asp)
> This method also lets you install Linux on devices that lack a CD or DVD drive (like ultraslim notebooks), so you could boot from a USB thumb drive or other bootable USB device
i haven't read it so i don't know how helpful it will be :rolleyes:

---

### Post by catlett on 2006-05-16
[QUOTE=ice60]i was just looking at some RSS feeds and saw this one
[Install Linux Over the Internet](http://www.pcworld.com/howto/article/0,aid,125512,00.asp)

i haven't read it so i don't know how helpful it will be :rolleyes:[/QUOTE]
This link came from that link. [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

