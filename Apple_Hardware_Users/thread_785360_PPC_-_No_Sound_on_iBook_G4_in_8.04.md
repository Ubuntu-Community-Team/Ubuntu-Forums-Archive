---
title: "PPC - No Sound on iBook G4 in 8.04"
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by mchladek on 2008-05-07
Hello All,

I just updated from 7.04 to 8.04 after fiddling with yaboot (thanks to the suggestions on this forum).  However, sound on my iBook G4 isn't working.  When I open up volume control, "default" is listed as the output but there are no controls and obviously no sound.

I got 8.04 up and running late last night so I didn't have much time to investigate it.  I am hoping the solution is similar to the MacBook sound fix.  Of course, since my iBook doesn't have an Intel chipset, the solution will be slightly different.

Anyone have any ideas?

Thanks!

---

### Post by frog_pilot on 2008-05-07
issue```
sudo modprobe snd-powermac
```
if this works, add ```
snd-powermac
```to your /etc/modules to load this module always on startup.

---

### Post by mchladek on 2008-05-08
I figured it was something simple like that.  Thanks a lot!

---

### Post by reverend1313 on 2008-05-09
WHen i try to do that it says module not found? A I missing a step?

Ok tried it again and it worked, got about 2 seconds of the default ubuntu sound and it cut out again... any suggestiosn

---

### Post by ssam on 2008-05-10
looks like [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

the simplest work around is to install the smp kernel

---

### Post by stream303 on 2008-05-10
> **reverend1313 said:**
> Ok tried it again and it worked, got about 2 seconds of the default ubuntu sound and it cut out again... any suggestiosn

I have noticed some strange random audio muting on my box, even when using the gui volume applet and volume-control.

Can you try bringing up alsamixer in a terminal, and making sure that nothing is muted or unbalanced?

quickie alsamixer key tips:
left-right to navigate
up-down to change levels
M to mute/unmute channels
B to balance / lock sliders
ESC to quit

---

### Post by hubertschaeferhoff on 2008-07-17
You helped me too.
hubertschaeferhoff

---

### Post by lukerz8 on 2008-07-17
[QUOTE=frog_pilot;4903142]issue```
sudo modprobe snd-powermac
```


what is supposed to happen when you type this? it didnt give me an error or anything, just entered the command without any verification, just like when you move a file/dir :wink:

---

### Post by cyberdork33 on 2008-07-17
> **lukerz8 said:**
> [quote=frog_pilot;4903142]issue```
sudo modprobe snd-powermac
```
what is supposed to happen when you type this? it didnt give me an error or anything, just entered the command without any verification, just like when you move a file/dir :wink:
does your sound work now?

---

### Post by luke.is.very.handsome on 2008-07-17
It should have made the log in noise when you ran it.  Make sure you aren't still muted.

Running the alsamixer stuff afterwards will let you set up your max volume levels and such as well, those are run in terminal by using, 
```
sudo alsamixer
sudo alsactl
```
or something close to that.  Using this command
```
sudo nano /etc/modules
```
will let you append the snd_powermac line to the end of it and auto start your audio. After you have added it to the end, you can exit the program by pushing ctrl-x and then telling it to save and overwrite what is there already with what you have done.

My big issue though when I do this, is that I mysteriously lose my option to click "Shutdown" or "Off" type stuff and have to manually shut down from terminal.  So I made a button with the shutdown command in it to click on when I'm done with the machine.

```
sudo shutdown -h now
```

---

### Post by lukerz8 on 2008-07-18
ok my sound works now, but it only comes out of one speaker. when the computer makes it's original mac startup sound when you first turn it on, the sound comes out of both speakers. because of this, i assume the problem is a driver issue. does anyone know of a better driver? i guess i just don't really understand what this means:
```
sudo modprobe snd-powermac
```

thanks :)

---

### Post by cyberdork33 on 2008-07-18
> **lukerz8 said:**
> i guess i just don't really understand what this means:
That command loads the snd-powermac module... essentially the "driver".

---

### Post by stream303 on 2008-07-19
> **lukerz8 said:**
> ok my sound works now, but it only comes out of one speaker.

Definitely run alsamixer in a terminal (just bring up Applications > Terminal, and run alsamixer at the prompt.  In the Master channel, be sure to hit the "B" key to balance it out, and bring the missing channel back to life. Arrow up/down to adjust the master volume.

The gui master volume control sometimes does this to me when adjusting it, and only alsamixer can fix it.  I'd have to hunt down the bug report, but for now, you may be having the same problem.

---

### Post by lukerz8 on 2008-07-19
thank you for that, I didn't know there were programs that ran in terminal like that. the only problem is, it didn't fix the problem :)
Is there anything else that could cause that? that anyone knows of?

---

### Post by Jguyer on 2009-01-14
Hey I'm new to the forums and to Linux to tell you the truth. I used the sudo code from the earlier posting, and HURRAY i have sound on my PowerPC Mac however the volume control does not work. The individual volume controls in each app. do work though. any ideas on how to get the main volume control to work? And a bonus if the keyboard buttons work too.

thanks in advance
Jeremy

---

