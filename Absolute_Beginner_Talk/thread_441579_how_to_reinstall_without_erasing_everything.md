---
title: "how to reinstall without erasing everything?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-05-12
hello, 
I accidentally erased my nvidia drivers and after recgonfiguring my xorg/conf I'm getting a White screen as a result. 
I already posted a thread but noone seems to be able to help me
 (just in case: [http://ubuntuforums.org/showthread.php?t=440506]("http://ubuntuforums.org/showthread.php?t=440506") )
I'd like to know whether there is a command line that can reinstall feisty without having to install it again through the cd thus erasing everything, hoping that after the installation my graphic environment will be restored. 
If there is such a command, since I'm not able to enter the terminal, should I run the recovery mode and run it from there?
please help..

---

### Post by floke on 2007-05-12
There is no such command but you could try 'sudo dpkg-reconfigure xserver-xorg' and see if that helps

---

### Post by Morkhaar on 2007-05-12
thanks for the quick reply, but if you see the thread, i did just that and now i'm getting a white screen...
can you think of anything else before I install everything again? I really cannot...

---

### Post by bobplano on 2007-05-12
go into recovery mode and do that. i don't think you need sudo then as its recovery mode. all you really need is a terminal and there should be a fail-safe terminal option somewhere

---

### Post by orb9220 on 2007-05-12
Did you try the envy script? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It wil uninstall and reinstall your video driver's and fix alot of problems.

---

### Post by Morkhaar on 2007-05-12
I tried reconfiguring again in recovery mode and in an older version of the kernel but still nothing. 
I t just occured to me that I while following the guide, I didn't press **Ctrl+alt+F1** before
** sudo /etc/init.d/gdm stop**. could that be of a major importance?

also, thanks for the link, it seems promissing, but I have to enable the extra repositories (I'm preety sure I haven't done it, don't know how to find out ) and as I lack a graphical interface, the -quite large to be true - text I should copy paste in order to update the repository list, is really dificult to write by hand without making any mistakes... is there a quick way to do such a thing?

if i went to the command line and tried to do again what I was trying to do with the thread a little more careful this time, would ita  have a chance to work? or now that I used dpgk-reconfigure it's destined to fail?

thanks for the replies so far... please don't give up on me!

---

### Post by Morkhaar on 2007-05-12
...

---

