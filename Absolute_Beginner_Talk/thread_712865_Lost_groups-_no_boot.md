---
title: "Lost groups- no boot"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by TooRight on 2008-03-02
I was called away from my comp yesterday for several hours and had just left it going. Upon coming back, i saw that my screen hadn't darkened to black as it should have, and the browser seemed sluggish, so I conrtol+alt+backspace to restart my session. It gave me and error message that i reallyyy wish i had paid attention to, so then I simple turned off my comp and restarted it. However, the kubuntu screen only showed the colour on the loading graphic moving about an inch, and then it disappeared and went to a text booting interface where it detected something wrong with the files and started to scan them, said there were errors, restarted, and it went through it all again, this time checking things and saying it would scan again and for me to hit control-D at the end of it.... there were a bunch of files (different kinds of "groups") listed as missing, and  and then it just stopped and showed the root prompt, ending in the #.

Nothing will make it boot... it's ubuntu, so there's GOT to be a way for me to find the problem and fix it without having to format my system, lol. Any suggestions? ( having to use my windows partition is killingggg meeeee, lol ) :D

---

### Post by Happy_Man on 2008-03-02
At the root prompt, did you try ```
startx
```? If you did and this still doesn't resolve, your're screwed. Sorry. Reinstall. If it does help then Ubuntu's just putting up a fuss. :D

---

### Post by scorp123 on 2008-03-02
> **TooRight said:**
>   there were a bunch of files (different kinds of "groups") listed as missing, and  and then it just stopped and showed the root prompt, ending in the #.  You have a filesystem error on the " / " partition where /etc/groups is located, the file that defines which user belongs to which group (this includes system processes and their accounts too). Without that file the system is unable to authenticate you and apparently automatic repair measures have failed, that's why the boot process is dropping you into a root shell (with the " # " prompt) so you could repair the filesystem corruption. You most likely caused this with the unclean shutdown of your PC.

What I'd suggest:

- Boot the live CD
- once it's booted open a terminal
- become "root":  **sudo su -**
- once you're root execute this:   **fdisk -l**  ... this should list all harddisk partitions.
- check each and everyone of them that are marked as being "Linux":  **fsck.ext3 -f /dev/hdX** ... or **fsck.ext3 -f /dev/sdX**   (whatever the system said where your Linux harddisks are).

Be patient here, this could take a while. Once it's finished all the checking reboot and try if your system will now properly restart again.

---

### Post by scorp123 on 2008-03-02
> **Happy_Man said:**
> At the root prompt, did you try ```
startx
```?  On a corrupted file system, logged in as "root" ?  **Bad idea**.  [COLOR="Red"]Don't you ever do this![/COLOR]

---

### Post by TooRight on 2008-03-02
lol, thank you for the warning scorp123!! I'm going to go try what your previous post said, wish me luck!! :)

---

### Post by TooRight on 2008-03-03
Well, it wouldn't boot, even using the disk, so I ended up pulling out my Gparted CD and formatting all of it, my entire dual booted hard drive. After that I grabbed my gutsy cd and installed that again; works like a dream!! Now to get my system back to how it was with all the programs and kubuntu and all my own icons for everything. I tell ya, even though I will have to redo alot of work that had on my system.... it sure is nice to be able to use my entireeeee harddrive for ubuntu and not have half of it going to waste as a windows partition that I never used, lol.

Thanks so much for the help!! :)

---

