---
title: "I don't know how to install Ubuntu"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by dustinh123 on 2006-08-08
Hello,

I am new to Linux and Ubuntu and I have no idea how to install it. I have already downloaded and burned Ubuntu 6.06 to a CD. I booted into the CD and still can't figure out how to install it.:confused: :confused: :confused: 

Here is some info about my computer if it may help...

Apple eMac
G4 1.42 GHz CPU
512 MB RAM
64 MB ATI Radeon 9600
I currently have Mac OS X Tiger 10.4.7 installed and I want Ubuntu as a secondary boot.

Any light on this subject would be greatly appreciated!!![-o< 
Thanks in advance!

---

### Post by aysiu on 2006-08-08
If you downloaded the Desktop CD...
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

If you downloaded the Alternate CD...
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Note: both guides are targeted toward a Windows/Ubuntu dual boot, but the same principles should apply to a Mac/Ubuntu dual boot.

This may also help you:
[https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC)

---

### Post by dustinh123 on 2006-08-08
I have tried doing what has been stated in the documents that you linked but I don't get to the installation window. It gives me some sort of error message. (I'm sorry, but I don't remember what it said.) Does anyone else have an idea?

---

### Post by aysiu on 2006-08-08
Do you have the Alternate CD or the Desktop CD?

Did you burn the CD as an ISO?
[http://www.psychocats.net/ubuntu/maciso.html](http://www.psychocats.net/ubuntu/maciso.html)

Did you hold down the **C** key during bootup?

Can you say either exactly what the error was or... approximately what it said? What did the screen look like when you got that error? Please, try as much as possible to describe exactly what you did and exactly what happened.

---

### Post by dustinh123 on 2006-08-08
I downloaded the Desktop Ubuntu ISO file and burned the .ISO file. I didn't drag and drop the files onto a CD. And, I did hold down C when i started up. (It did bot from CD) I will post back in a few minutes with the message it gives me.

---

### Post by dustinh123 on 2006-08-08
OK... Here is what I have experienced.....

When I boot from the CD and I see text that says "Welcome to Ubuntu 6.06 (Dapper Drake)..........", I press ENTER and I get this message after it loads Kernel Elf32...
PCI:Cannot loacate Allocation Unit..........   I couldn't read everything it said because it didn't stay up long enough to read. Then, I get the Ubuntu loading thingy. It shows me everything that is loading and says OK next to every one. I noticed that on "Starting PCMIA Services", there was no OK.

Then after it is done loading, I get a message that says-
"Failed to start the X Server (Your graphical user interface). It is likely that it is not set up correctly. Would you like to view the X servier output to diagnose the problem?"
I get and option Yes or NO

Hope this helps!
Dustin

---

### Post by aysiu on 2006-08-08
In the boot options for the CD, is there an option to boot with *no acpi*? If so, try that.

For the "Failed to start the X server" problem... try pressing Control-Alt-F1 and then typing ```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can, then ```
sudo /etc/init.d/gdm restart
```

---

### Post by Metacarpal on 2006-08-08
This might sound like a silly question, but... When you downloaded the install CD, did you download the Mac/PPC version?

---

### Post by dustinh123 on 2006-08-08
Actually, i did download the PPC/Macintosh Version. I will try what you told me to do! Thanks!

---

### Post by junglepeanut on 2006-08-08
I believe your condition is the same as aysiu said.

Do as declared by aysiu on choosing as you think fits *except* when it comes to choose the driver don't choose ati, it has been a while since I did this but I too have an ati card. (Search the forums for "ati driver sudo dpkg-reconfigure xserver-xorg") and it should come up. As to what you need to actually choose I believe it was vesa, but I am not using ppc so I am not sure for you if that will work. But vesa should, or vga etc something old default. 

What you can do is after choosing each one and running throught the processess type **startx** at the terminal and see if it works then try the next etc. Start with vesa though. Then when you have found one that works

Search the forums for install fglrx and it should say how to go about that.
Update it or instead download the ati driver from ati. Many wikis on this.

All said the only reason you want fglrx or ati driver is because the vesa or vga etc one will be low resolution that will just get the job done.

Hope this helps

---

### Post by dustinh123 on 2006-08-09
I tried what aysiu said-
the first and last code that he told me to use didn't work - it's "invalid". Is my eMac supported? It's the Last Gen eMac (1.42 GHz eMac Speed Bump).

Anyways...
I ran through the X server setup and filled in all of the questions. It saved the Config and I typed in the last code. (sudo /ect/init.d/gdm restart). It was invalid. :( I have no idea what to do and I really want to give the penguin a try! ](*,) 

Thanks for everyone who has replied! I appreciate all of the help!!!!

---

### Post by aysiu on 2006-08-09
I'm pretty sure eMacs are supported. It sounds as if there might be some problem with your video card, though. I'm not sure what to do. Maybe some of our video card specialist forum members will jump in on this.

---

### Post by dustinh123 on 2006-08-09
Wht do I do after I configure the X Server?

---

### Post by junglepeanut on 2006-08-09
Did you try 

startx 

?

Although, I guess you have restarted since then and that should be the same so I guess I am at a loss if it is not configured yet.

Guessing you already read these but maybe they will help?(refer to copying config from darwin (terminal on OSX)) 

[http://ubuntuforums.org/showthread.php?t=27546&highlight=emac+video](http://ubuntuforums.org/showthread.php?t=27546&highlight=emac+video)

[http://ubuntuforums.org/showthread.php?t=187813&highlight=emac+video](http://ubuntuforums.org/showthread.php?t=187813&highlight=emac+video)

[http://ubuntuforums.org/showthread.php?t=924&highlight=emac+video](http://ubuntuforums.org/showthread.php?t=924&highlight=emac+video)

---

### Post by dustinh123 on 2006-08-10
I will try that! Thanks

---

### Post by dustinh123 on 2006-08-10
OK....
Once I configured the X Server, I typed in startx and the screen goes blank for a few seconds, comes back up and gives me a bunch of jibberish. (I think it's some kind of error message.) I really hope we can get to the bottom of this and solve the problem.

---

### Post by junglepeanut on 2006-08-11
Do you know exactly what it says?

Also when mine initially starts I get a weird display image then it adjust after half a sec. Still mine is not a mac, though this is appearing to be a ati issue.

Maybe your horizontal and vertical are a little off? I really am guessing here. Did you end up copying your config file from Darwin?

---

### Post by junglepeanut on 2006-08-11
this makes response to emac and seems I may have forgotten a command for some type of update. Hopefully this will help.

[http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fgrlx](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fgrlx)

---

### Post by dustinh123 on 2006-08-13
I really don't think that it is a video card problem or the setup problem. There are no other appropriate settings for the video card. I did what seemed right to do and was best to my knowledge. Any other ideas?

PS-Sorry it took so long for me to reply.

---

### Post by junglepeanut on 2006-08-20
Sorry from me too been studying.

I am at a loss. I hope you get the help you need. 

Jp

---

### Post by dustinh123 on 2006-08-20
I have no idea what to do. I'm begining to think that the eMac is not supported by Ubuntu. I have taken a look at Gentoo and it is a very nice looking Linux OS distribution (But I don't have a clue on how to install it! It's rediculous!)](*,)

---

