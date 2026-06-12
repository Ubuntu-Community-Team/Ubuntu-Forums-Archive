---
title: "burning iso"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by richaoj on 2007-05-24
i seem to be having a strange problem . . . 

i downloaded a copy of mac osX panther (it is not sold anymore, and i am attempting to install ubuntu on an old-world mac, which means i have to have some version of mac os on there to boot.)  legalities aside . . . 

the iso's download for the install cd's, but when i attempt to burn them, ubuntu tells me that they are not valid .iso files!?  I would have thought that this was a unique problem to the iso that i downloaded, but since this is the third version of mac os that i have tried to download and burn as an iso. all with the same error message!?

i have burned other iso's using ubuntu, but why won't these burn.? are they formatted differently??

thanks in advance, ojr

---

### Post by Chitownguy885 on 2007-05-24
The files could be corrupt. Have you tried putting the files on another computer and trying to burn them.

---

### Post by richaoj on 2007-05-24
The command line output is: CD-ROM is NOT in ISO 9660 format

---

### Post by thelinuxguy on 2007-05-24
> **richaoj said:**
> The command line output is: CD-ROM is NOT in ISO 9660 format

MAC disk images are in HFS/HFS+ format. You need special software to read this format ([http://club.cdfreaks.com/showthread.php?t=214525](http://club.cdfreaks.com/showthread.php?t=214525))
Linux drivers exist that can read such filesystems ([http://www.mars.org/home/rob/proj/hfs/](http://www.mars.org/home/rob/proj/hfs/)). 
Many windows tools are also available (such as MagicISO at [http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)) for burning MAC disk images to disk but I am finding it difficult to locate a Linux tool.

---

### Post by richaoj on 2007-05-24
does anyone know of a linux tool to do this?
i don't have a windows tool and i don't have a functional mac at the moment.
i ran magiciso under wine and it doesn't have access to the cd burner.

---

### Post by reckless2k2 on 2007-05-24
[http://www.tech-recipes.com/apple_mac_tips1002.html](http://www.tech-recipes.com/apple_mac_tips1002.html)

or

[http://www.uab.edu/it/question-answer/os_osx/burn_iso/index.html](http://www.uab.edu/it/question-answer/os_osx/burn_iso/index.html)

Also try most thing s on this page which more or less point in the same direction:

[http://www.google.com/search?q=burn+iso+in+mac+os+x&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=burn+iso+in+mac+os+x&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by richaoj on 2007-05-24
burning this would be moot if i had osx in which to burn the file. 
is there an UBUNTU tool that would be able to read and burn these files. . .

---

### Post by thelinuxguy on 2007-05-24
> **richaoj said:**
> i ran magiciso under wine and it doesn't have access to the cd burner.

Even as root? 
Can you see the cd burner under Wine?

---

### Post by 3rdalbum on 2007-05-24
thelinuxguy gave you incorrect information - he's a PC user. ISO files will burn to discs regardless of what filesystem is inside it.

I see no technical reason why the Mac OS X disc ISO is reading as invalid. Is there an MD5sum available for the disc, and if so does it check out? The kinds of sites that might host such an ISO may be unreliable.

But all this is moot. You need OS 9 or below on that Mac in order to use BootX. OS X will NOT work with BootX.

---

### Post by thelinuxguy on 2007-05-24
> **3rdalbum said:**
> thelinuxguy gave you incorrect information - he's a PC user. ISO files will burn to discs regardless of what filesystem is inside it.

This was my source of information which I have already posted above: [http://club.cdfreaks.com/showthread.php?t=214525](http://club.cdfreaks.com/showthread.php?t=214525)
And a hybrid HFS/ISO 9660 would have enabled him to read the image file which doesn't seem to be the case.

---

### Post by richaoj on 2007-05-24
anyway, i managed to get a copy of os9 from a friend of mine,--it is a software restore cd for an imac-- managed to get (a fairly broken) copy of os9 up and running on this machine by booting from the cd and copying the .img of a system folder onto the drive.  I have set up a 200mb partiton for os9.

bootx works fine now, but i cannot get past the partitioner in my 6.06 alternate install cd.  it seems the partitioner cannot write to the disk??  it writes the swap partition just fine, and i have tried ext3 and reiserfs filesystems, but neither one seems to take!?  what gives!?  this is a brand new harddrive!? (well, refurbed anyway).  

should i try and update the firmware on the hd?
any other suggestions??

---

### Post by sbubba on 2007-08-19
Hello =)
I've the same problem
I've feisty and I've downloaded 4 iso from ktorrent (however they are *not* iso for mac)
3 of 4 iso don't work. if I try to open them, this is the output:
```
CD-ROM is NOT in ISO 9660 format
```
if I use k3b: ```
seems not be an usable image
```
brasero don't burn them
with the comand "file" on terminal, these iso result "data".

I've tried to download them again but it's the same.
where is the problem?

thanks

---

### Post by sbubba on 2007-08-19
> **elementskaterbla said:**
> come watch the tech question and answer session, with pro ubuntu support reps,

[http://operator11.com/shows/731/episodes/1470](http://operator11.com/shows/731/episodes/1470)
sorry, the link bring me to the home of the site O.o

---

### Post by sbubba on 2007-09-01
hellooooooo
nobody...? :|

---

