---
title: "Ubuntu Noob alert - Install Network Drivers"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by konfuzion on 2006-10-12
[FONT="Arial Narrow"]Hi,

My friend has just given me the latest copy of unbuntu and i deceided to load it on my machine.  THe installation went great except for the loading of network drivers.  Can someone tell me how the heck to i install network drivers for my server?

I'm using a old board Intel server board SBC2 and i dont seem to see the drivers for for unbuntu on the intel site.  This is truly a noob question...will linux drivers work with Unbuntu software.

Please dont laugh as i said i truly am a linux noob.  

Thanks in advance 
konfuzion[/FONT]

---

### Post by equal on 2006-10-12
It's hard to say exactly. There's a lot of supported cards, and definitely more than a few that don't have drivers yet. 

Really though, if worse comes to worse, you can always head down to your local store and pick up a $10 DLink network adaptor. The newer cards are almost always supported right out of the box. Might save you a lot of trouble, and for $10, it's probably worth it.

---

### Post by petri on 2006-10-12
Was your PC connected to internet while installing? It should have been.

PAste this in terminal ```
lspci
``` and then paste the output here so we can find out the networkchipset.

EDIT: If you decide buy some hardware because of Linux please take a look at this site and check the new hardware is supported in Linux :) [https://wiki.ubuntu.com/Hardware](https://wiki.ubuntu.com/Hardware)

---

### Post by konfuzion on 2006-10-12
Well i tried to save the output of the lspci to a disk, but i got an error saying that the disk is not a moundable device.  Maybe i will just type it in the screen.

---

### Post by dannyboy79 on 2006-10-12
> **konfuzion said:**
> Well i tried to save the output of the lspci to a disk, but i got an error saying that the disk is not a moundable device.  Maybe i will just type it in the screen.

lspci -v
that's simply gonna give us all the info we need about all your pci devices and controllers within your computer. you need to run it from the terminal immediately after opening the terminal. don't run it from any disk?

also, check this out for mounting network drives.

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by petri on 2006-10-12
Oh no... didn't think about that :confused: 

Just the line with **Ethernet controller**!

---

### Post by konfuzion on 2006-10-12
jklaws@HOTH:~$ lspci
0000:00:00.0 Host bridge: ServerWorks CNB20HE Host Bridge (rev 23)
0000:00:00.1 Host bridge: ServerWorks CNB20HE Host Bridge (rev 01)
0000:00:00.2 Host bridge: ServerWorks CNB20HE Host Bridge (rev 01)
0000:00:00.3 Host bridge: ServerWorks CNB20HE Host Bridge (rev 01)
0000:00:03.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0d)
0000:00:04.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0d)
0000:00:0c.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
0000:00:0f.0 ISA bridge: ServerWorks CSB5 South Bridge (rev 92)
0000:00:0f.1 IDE interface: ServerWorks CSB5 IDE Controller (rev 92)
0000:00:0f.2 USB Controller: ServerWorks OSB4/CSB5 OHCI USB Controller (rev 05)
0000:00:0f.3 Host bridge: ServerWorks CSB5 LPC bridge
0000:01:07.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
0000:01:07.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
jklaws@HOTH:~$

---

### Post by man-man on 2006-10-12
> **konfuzion said:**
> [FONT="Arial Narrow"]will linux drivers work with Unbuntu software.[/FONT]
I took this to mean that the drivers already exist and all the guy wants is to know if they'll work

However, Im not really able to follow what a lot of the subsequent posts are saying (probably too much stuff that you need to actually have on screen..) So maybe thats irrelevant

But if you have drivers that are specifically for linux then they should work with ubuntu - theyre the same thing at the most basic level

---

### Post by dannyboy79 on 2006-10-12
there is a user in these forums with the name uluen who has posted the results of his ethernet card and it is the same as yours. So i would think that your internet should be working. Have you gone thru the steps to configure it? go to system, admin, networking, click on eth0 interface, click either activate or if it's activated already then deactivate it and then reactivate it. see what ip you're getting by typing in ifconfig. it should be working. did you try to disable ipv6? you can search for that in these forums as well and find the answer, i know it has something to do with firefox, typing in blank:config or something like that and then you are brought to the settings for firefox and you can disable ipv6 which has caused A LOT of people's internet to NOT work. good luck

ACTUALLY I FOUND A SOLUTION, HERE YOU GO:
I searched the forum for "Ethernet+Pro+100" and came up with the following thread: [http://ubuntuforums.org/showthread.php?t=209070&page=2](http://ubuntuforums.org/showthread.php?t=209070&page=2)

The thread states that there is a bug with the Intel pro 100 cards, and how to work around the bug. See post number 12 and 13 on the second page.

ALL YOU HAD TO DO WAS USE THE SEARCH FUNCTION WITHIN THIS FORUM AND YOU WOULD HAVE FOUND THE SAME THING I DID. My capital letters are not intended for yelling at you so don't get me wrong, i am simply trying to help you help yourself better. I am glad you are coming over to linux and we'll be here to help if and when you need us but just try to SEARCH and find the answer so that there aren't 20 posts that all have the same question just like it states in the forum rules.

---

### Post by petri on 2006-10-12
> **dannyboy79 said:**
> ...

ALL YOU HAD TO DO WAS USE THE SEARCH FUNCTION WITHIN THIS FORUM AND YOU WOULD HAVE FOUND THE SAME THING I DID. My capital letters are not intended for yelling at you so don't get me wrong, i am simply trying to help you help yourself better. I am glad you are coming over to linux and we'll be here to help if and when you need us but just try to SEARCH and find the answer so that there aren't 20 posts that all have the same question just like it states in the forum rules.

Well, actually it seems like he didn't know which network chips he has. 

The output of lspci shows the drivers are installed, right? AND the network chipset.

There will be a lot of people coming to Linux and Ubuntu soon, believe me. The last thing they need is... no, there is something to all of us in the forum rules. :rolleyes:

EDIT: konfuzion - In Linux there is no longer any need to surf to vendors sites to find a driver or a program, they should be found in Synaptic. 

Or here at the ubuntuforums.org ;)

---

### Post by dannyboy79 on 2006-10-12
> **petri said:**
> There will be a lot of people coming to Linux and Ubuntu soon, believe me. The last thing they need is... no, there is something to all of us in the forum rules. :rolleyes:
Do you have something against me or what, you have something to say everytime I try to help people. I would really like to know where I EVER SAID the word NO in my post. Why don't you worry more about helping people than looking for my posts and picking on everything I say. Good day sir! [-(

---

### Post by dannyboy79 on 2006-10-12
Petri, I'd also like to know what this means, "there is something to all of us in the forum rules" I can't even understand what you are trying to say?????

---

### Post by petri on 2006-10-12
> **dannyboy79 said:**
> ... "there is something to all of us in the forum rules"...

Well english is not my native language so maybe I miss a point now and then. Teh quote above means that even I do wrong here at the ubuntuforums.org and now when I got you annoyed(written right?) I was right about that, I shouldn't be moderating other users.

Written words are straight, there is no way to ease them upp with gestures so if I understood you wrong I apologize. 

I just get the feeling that you have forgotten how hard it is to come to a new OS. Everyting is new, just everything. It is understandable to forget that. Even my one of my idols in Ubuntu did it just recently, I think I saw the problem but nobody listened me in that infected thread.

Every newbie thinks my problem is special and does not even think to make a search. It takes about 300 posts here to become aware of that ;) Did you know that google has an linux-part? It's found at [www.google.com/linux](www.google.com/linux)

People who come from another Linux distribution, they already know about CLI, the structure of catalogues on hdd, and they do know about the search functions. It's just the details that confuse them, just a little.

Windows user is like a city slicker who moves to the forrest, not just to take a hike but to live. They can't even see the forrest for all the trees.
.. you know the forrest of Sherwood? ;)


EDIT: Now I see you got it wrong at > The last thing they need is... no, there is something to all of us in the forum rules. that is two sentences. First one is stopped by the three dots and the second one confirmes I stopped what I was saying and starts all over again with saying: "... no, there is something..." I think that those three dots are quite international mark of pausing in middle of speaking and should be understood by people in written language.

---

