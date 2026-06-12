---
title: "Feisty Fawn for President! (Actually a modem question)"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Hayl on 2007-07-26
So I did it finnally, cut my infernal chains with microshaft and upgraded to Linux.  I didnt even bother to set up dual boot I just nuked my 1505 and went with a clean install of Fiesty Fawn.  And I love it.  Beryl is so awesome it left me saying aero what? neways, cunfused by my vigor to destroy Vista, I didnt look where my modem was, now when I try to get online using dial-up I have serious probs.  The other forums Ive read say I need to use a windows based app (scanmodem or soemthing) to find out where it is, but due to the fact that I do not dual boot this is a problem...Ohh and one more thing, I have an external HD (USB) and I can read files from it but I cant write to it, is that because its NTSF? Does Feisty know what to do with that file structure? Any help would be awesome!

---

### Post by Rocket2DMn on 2007-07-26
I can't help you with your modem problem, but I can with your hard drive.
If you formatted the hard drive in Windows, it probably has NTFS as it's file system which is why you can't write to it.  If you haven't yet, get ntfs-3g, then run ntfs-config and enable writing.  You can also find the config under Appliations->System Tools->NTFS Config (or something similar, I'm not in front of my linux machine to double check that)
```
sudo apt-get install ntfs-3g
sudo ntfs-config
```

Here is a more detailed approach, though probably not necessary beyond what I've mentioned: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Bartender on 2007-07-26
Take a look at post #4
[http://ubuntuforums.org/showthread.php?t=508270](http://ubuntuforums.org/showthread.php?t=508270)

This might help you.  If it does, please post back.  It'd be super if Dell's drivers work

---

### Post by Paulmd on 2007-07-27
> **Hayl said:**
> So I did it finnally, cut my infernal chains with microshaft and upgraded to Linux.  I didnt even bother to set up dual boot I just nuked my 1505 and went with a clean install of Fiesty Fawn.  And I love it.  Beryl is so awesome it left me saying aero what? neways, cunfused by my vigor to destroy Vista, I didnt look where my modem was, now when I try to get online using dial-up I have serious probs.  The other forums Ive read say I need to use a windows based app (scanmodem or soemthing) to find out where it is, but due to the fact that I do not dual boot this is a problem...Ohh and one more thing, I have an external HD (USB) and I can read files from it but I cant write to it, is that because its NTSF? Does Feisty know what to do with that file structure? Any help would be awesome!

How come almost everybody in this forum who might have a hardware/driver problem never mentions what the hardware is? If you don't know, can you provide us with what info you do know about your system? From there it is sometime possible to determine the rest.

---

