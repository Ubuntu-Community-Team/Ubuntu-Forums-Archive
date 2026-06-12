---
title: "help! My OS crashed"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-23
I have a laptop with dual boot, Win98 and Ubuntu 7.04. I was working in Ubuntu and all was fine, then I put the laptop on standby as I've already done in Ubuntu a hundred times. When I hit the power button to bring it back up the desktop wouldn't come up. The screen just remained dark. So after waiting a few minutes, I had to hold the power button down to make the computer go off.

When I tried to boot up into Ubuntu again, first Grub came as it should. I chose Ubuntu, and then after the Ubuntu boot screen came up with the progress bar, midway through the following screen came up:

===================================================

/dev/hda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (i.e. without -a or -p options)
fsck died with exit status 4

*  An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*  The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started. After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system. 
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt
bash: apt-get command not found
bash: dircolors: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt
bash: apt-get: command not found
root@swarup-laptop:~#

================================================

Each time I try to boot, this very same screen comes.
If at GRUB's menu I select Win98, then Windows 98 boots up and works just fine. But if I select Ubuntu, then the above screen comes.

WHAT SHOULD I DO? IS THE OPERATING SYSTEM SALVAGEABLE? WHAT HAS HAPPENED?

---

### Post by Cypher on 2007-05-23
At the prompt please type
```

e2fsck -y /dev/hda2

```
once it's done, "exit" to reboot the box and you should be fine..

Because you abnormally powered down the laptop, a bunch of inodes are probably orphaned and other open files weren't closed properly. Thus the error, the OS did not crash.

---

### Post by swarup on 2007-05-23
> **Cypher said:**
> At the prompt please type
```

e2fsck -y /dev/hda2

```
once it's done, "exit" to reboot the box and you should be fine..

Because you abnormally powered down the laptop, a bunch of inodes are probably orphaned and other open files weren't closed properly. Thus the error, the OS did not crash.

That was AMAZING. Thank you so much. I was thinking the OS was a gonner for sure. 

So the follow-up question then is, WHAT DO I DO IN THE FUTURE IF THE COMPUTER FREEZES UP AND I NEED TO POWER IT DOWN. IS THERE A SAFE WAY TO DEAL WITH SUCH PROBLEMS SO THAT THIS SORT OF SCARY ERROR WILL NOT OCCUR AGAIN IN THE FUTURE?

---

### Post by swarup on 2007-05-23
And is it dangerous to use the "standby" command in Ubuntu? Up till today I did not have any problem. But today when the above near-disaster happened, I became quite concerned that I should not use "standby" any more. Is this true?

 Because otherwise, the "standby" command is very convenient for me. If I don't use it, I'll have to power down the computer every time I walk away for 20 minutes.

---

