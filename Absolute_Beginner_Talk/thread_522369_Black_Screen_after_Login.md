---
title: "Black Screen after Login"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-10
After I input my username and password into the login screen the screen goes completely black. i also tried it with another user, but this still happens. Help Plllease.

---

### Post by CapitanYochua on 2007-08-10
At this point I have no hope. I'm thinking of completely installing ubuntu from nothing again. But, there is a really important open office document that I need to get from my desktop. Is there any way I can do this through the recovery mode terminal?? I want to get it from there to put into a USB device to move into the new ubuntu that I would install. I *can't* lose it.

---

### Post by Pragmatist on 2007-08-10
When you get to the login screen, type this:
```
CTRL-ALT-F3
```

You should now be on a black screen with white writing prompting you to login.  Login with username and password, and then type this:

```
sudo dpkg-reconfigure xserver-xorg
```

When you are finished, type:
```
exit
```

and then,
```
CTRL-ALT-F7
```

You should now be back at the graphical login screen.  Login and see if it works.

---

### Post by CapitanYochua on 2007-08-10
Can I do that with root user in recovery mode? Seems like that is the only place I make progress. For odd reasons my username is pretty much useless with the terminal even with sudo (super odd).

---

### Post by Pragmatist on 2007-08-10
Use a LiveCD, such as Knoppix or Ubuntu's LiveCD, and you can get your OO document that way.  Then just reinstall and see if things work better next time.

---

### Post by CapitanYochua on 2007-08-10
Well. I tried it as root user in recovery mode. clicking all the defaults in the xconfiguration. Nothing worked. I'm really pessimistic. I don't mind having to reinstall linux as long as I can get that document to a USB device somehow. Help.

---

### Post by Pragmatist on 2007-08-10
I just explained how.  You use a LiveCD.  The LiveCD has nothing to do with your current situation, it is a separate operating system that runs off of the CD.  Try it and see if it works.  If it does not work, then reinstalling Ubuntu might not be the most important issue right now.

---

### Post by CapitanYochua on 2007-08-10
Sorry about that. I must have been typing it while you posted it. I'll look for my live CD and get back if I have any problems.

---

### Post by CapitanYochua on 2007-08-11
Sorry for the time to post back. I had to get a new ubuntu live CD. Anyways, now that I have it. How can I get my OO document to a USB Device with it?

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> Sorry for the time to post back. I had to get a new ubuntu live CD. Anyways, now that I have it. How can I get my OO document to a USB Device with it?

You navigate to /media and you should see your hard drive and the USB device mounted.  Just navigate them as you would any drive and copy the file(s) from the hard drive to the usb drive.  Remember, the OS is running from the CD now, so your hard drive is just like any mounted device.

---

### Post by CapitanYochua on 2007-08-11
I'm not really sure where my OO document would be located with the liveCD. I previously had it on my desktop. And couldn't find anything in the media folder of my disk.

---

### Post by CapitanYochua on 2007-08-11
Scratch that I found it. Thank you so much! I'm just going to put it on a USB device and test it on another computer to make sure everything is fine.

---

### Post by CapitanYochua on 2007-08-11
When I clicked on the OO through the liveCD I got Access was denied... Would I have a problem with reading and writing to the document after I transfer it with a USB device as well?

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> When I clicked on the OO through the liveCD I got Access was denied... Would I have a problem with reading and writing to the document after I transfer it with a USB device as well?

You shouldn't.  Did you get a copy to the USB device?  It is probably a permissions issue.  I am guessing that you are using the GUI to move the files.  Try using a terminal with the sudo command:
```
sudo cp /path/to/oo-file /path/to/usb-device
```
Obviously you need to replace these paths with the real ones :)

---

### Post by CapitanYochua on 2007-08-11
Couldn't I have just done that through recovery mode too?
  Oh. And I'm using a labtop that runs on windows. Would I be able to test the document here? I'm really sure about that... SO I thought I would just ask.

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> Couldn't I have just done that through recovery mode too?
Sure, you can try.  I always use a LiveCD since I know it will work.

> **CapitanYochua said:**
>    Oh. And I'm using a labtop that runs on windows. Would I be able to test the document here? I'm really sure about that... SO I thought I would just ask.

Did you get the file to the USB device??

---

### Post by Pragmatist on 2007-08-11
If it is saved as OpenOffice format .odt and you want it saved as .doc, you can just open it in OpenOffice on the LiveCD and choose "save as" and you will have a choice of formats including .doc

---

### Post by CapitanYochua on 2007-08-11
How am I able to change the format if the LiveCD isn't even allowing me to read the file?

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> How am I able to change the format if the LiveCD isn't even allowing me to read the file?

Ok, let's step back for a minute.  We were working on copying (not moving. this means you will have a copy in both places) the file to the USB drive.  What happened?  Could you copy it to the USB drive using the commands I gave in the previous post?:
```
 sudo cp /path/to/oo-file /path/to/usb-device
```

---

### Post by CapitanYochua on 2007-08-11
Says "cp: cannot stat 'then oo path': no such file or directory. "

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> Says "cp: cannot stat 'then oo path': no such file or directory. "
No, you need to type in the actual path to the file.  Ok, let's get methodical :)

Post the output of each of these commands:
1.) ```
whoami
```

2.) 
```
su
```
and now post the output to this:
```
whoami
```

---

### Post by CapitanYochua on 2007-08-11
whoami gives an output of 'ubuntu'
su asks for a password which I don't know. Incorrect password leads to su:Authentication failure sorry.
so whoami gives the same output.

P.S. Sorry for my incompetence =/

---

### Post by Pragmatist on 2007-08-11
On the previous post I asked you to type : **su**  This is not relevant for the Ubuntu LiveCD, but it is for other LiveCDs.  Type this and wait a few minutes for it to finish:
```
sudo updatedb
```
When it finished (you get a prompt again), type:
```
locate **filename**
```
YOU MUST REPLACE THE WORD **filename** WITH THE ACTUAL FILENAME OF THE OPEN OFFICE FILE!
Post the output here.

---

### Post by CapitanYochua on 2007-08-11
locate filename (with the actual filename doesn't give me output) e.g. locate eurosummerassignment.odt
I also tried it without the .odt still no output.
Let me back up. I think you misunderstood me when I said 'then oo path'. That isn't what I *actually typed* I just didn't want to type the whole path there.
What I did exactly was...
sudo cp /media/disk/home/joshua/Desktop/eurosummerassignment.odt  /media/disk-1
I also tried it without the .odt to see. I got this output exactly...
cp: cannot stat '/media/disk/home/joshua/Desktop/eurosummerassignment.odt': no such file or directory. 

I found the path through the GUI my doing properties and looking at location.

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> locate filename (with the actual filename doesn't give me output) e.g. locate eurosummerassignment.odt
I also tried it without the .odt still no output.
Let me back up. I think you misunderstood me when I said 'then oo path'. That isn't what I *actually typed* I just didn't want to type the whole path there.
What I did exactly was...
sudo cp /media/disk/home/joshua/Desktop/eurosummerassignment.odt  /media/disk-1
I also tried it without the .odt to see. I got this output exactly...
cp: cannot stat '/media/disk/home/joshua/Desktop/eurosummerassignment.odt': no such file or directory. 

I found the path through the GUI my doing properties and looking at location.
Try this:
```
find -P /media/disk -name *summer*
```

---

### Post by CapitanYochua on 2007-08-11
Okay. Tried it. Listed a bunch of thing, but not the file that I am talking about... Seems odd because I'm looking at it in the GUI...

---

### Post by Pragmatist on 2007-08-11
Try it this way:
```
find -P /media/disk -name eurosummerassignment*
```

---

### Post by CapitanYochua on 2007-08-11
Still no... Anyway I  can get access to it to cp it through GUI?

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> Still no... Anyway I  can get access to it to cp it through GUI?
You mean you got no output?  On the previous command we ran:
> find -P /media/disk -name *summer*
you said the output contained results, just not your file.  What were the names of some of the files from that output?

Right now I can only help you using the command line (i.e. the terminal)

---

### Post by CapitanYochua on 2007-08-11
Oh I did get output. um... They were a lot of results... All had permission denied. Most were like .programs at the end of the path like .mozilla or .gaim. The only one that seem some what related was a .openoffice.org2

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> Oh I did get output. um... They were a lot of results... All had permission denied. Most were like .programs at the end of the path like .mozilla or .gaim. The only one that seem some what related was a .openoffice.org2
Are you sure that /media/disk is what we want?  Please give output from this:
```
ls /media/disk
```

---

### Post by CapitanYochua on 2007-08-11
bin   fat_files   lib    opt  sys  valinuz.old
boot   home   lost+found   proc  tmp   windows
cdrom  initrd   media  root  usr
dev     initrd.img   mnt   sbin   var
etc   initrd.img.old   ndisk=gtk_0.6-0ubuntu1_all.deb   srv  valinuz


That;s all.
I should have probably mentioned this earlier, but I don't have internet on the LiveCD because I use D-Link or whatever (but I already know how to fix this). Well, my brother knows, but he will be back soon. Should I have that capability before I can do all this or is it not necessary?

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> bin   fat_files   lib    opt  sys  valinuz.old
boot   home   lost+found   proc  tmp   windows
cdrom  initrd   media  root  usr
dev     initrd.img   mnt   sbin   var
etc   initrd.img.old   ndisk=gtk_0.6-0ubuntu1_all.deb   srv  valinuz


That;s all.
I should have probably mentioned this earlier, but I don't have internet on the LiveCD because I use D-Link or whatever (but I already know how to fix this). Well, my brother knows, but he will be back soon. Should I have that capability before I can do all this or is it not necessary?
It is always helpful to have internet access when troubleshooting.  Then you can cut-and-paste your exact output. You don't have to if you don't want to.
Sorry to keep having you type this command, I should have been more accurate:
```
ls /media/disk/home
```

---

### Post by CapitanYochua on 2007-08-11
ls /media/disk/home
joshua me nathaniel shellscript.sh

I also did ls /media/disk/home/joshua and ls /media/disk/home/joshua/Desktop just to give you more info.
ls /media/disk/home/joshua
Desktop  ipodd  music
diskmounter.1  jdk-6u2-linux-amd64.bin   nautilus-debug-log.txt
dmesg.txt    jdk-6u2-linux-amd64.bin.sdm
examples    jdk-6u2-linux-i586.bin


ls /media/disk/home/joshua/Desktop
chocolate!   Euro Summer Assignment.odt  sulfur hexafluoride
clap.jpg  pics   un chien andalou
deluge    screenshot.png


Hopefully that gave you some ideas.

---

### Post by Pragmatist on 2007-08-11
> **CapitanYochua said:**
> ls /media/disk/home
joshua me nathaniel shellscript.sh

I also did ls /media/disk/home/joshua and ls /media/disk/home/joshua/Desktop just to give you more info.
ls /media/disk/home/joshua
Desktop  ipodd  music
diskmounter.1  jdk-6u2-linux-amd64.bin   nautilus-debug-log.txt
dmesg.txt    jdk-6u2-linux-amd64.bin.sdm
examples    jdk-6u2-linux-i586.bin


ls /media/disk/home/joshua/Desktop
chocolate!**   Euro Summer Assignment.odt**  sulfur hexafluoride
clap.jpg  pics   un chien andalou
deluge    screenshot.png


Hopefully that gave you some ideas.
The reason the previous commands did not work is for two reasons.  The main reason is because the file has spaces in it.  The next reason is that there are capitals (Summer is not the same as summer).  Now we try the commands with the proper filename and path (see next post)

---

### Post by Pragmatist on 2007-08-11
```
sudo cp /media/disk/home/joshua/Desktop/"Euro Summer Assignment.odt" /path/to/usb/drive 
```
replace: /path/to/usb/drive with the actual path

---

### Post by CapitanYochua on 2007-08-11
Okay no output. I checked the USB device through GUI and saw the OO in there. How do I test to see if everything is fine before I reinstall ubuntu? I want to be extra safe. Looks good so far. Thank you (: Just last bit to do.

---

### Post by CapitanYochua on 2007-08-11
Yeah. It worked! Thank you so much!

---

### Post by Pragmatist on 2007-08-11
You are sure you have a copy on the USB drive?

In any case, we are going to open the copy on your hard drive, using the LiveCD's  Open Office program, and save as .doc  You will then have 3 files.  One with .odt file on the hard drive, one .odt file on the USB and one .doc file on the hard drive.  Then we will copy this .doc file to the USB.  Finally, you will take the USB drive to a windows machine that has MS Word and test that the file is what you need.

1.) Start Open Office and use it to open the file called 
[B]/media/disk/home/joshua/Desktop/"Euro Summer Assignment.odt"

[/B]2.) Go to **File-->Save As** and there will be a drop down box with file types, choose something like "word 97, 2000" or whatever corresponds with your version of MS Word.  _**Use a name without spaces.**_  This makes your life easier.  If you want to keep the name the same in every other way, just insert the underscore character (_)  The file would look like this:
**Euro[COLOR=Red]_[/COLOR]****Summer[COLOR=Red]_[/COLOR]****Assignment.doc**  Save this file to the same location (or if you use a different one, remember where it is!)

3.) Copy this new file from the hard drive to the USB drive using the same exact method we used before.

4.) Test .doc file with MS Word on a Windows machine.

---

