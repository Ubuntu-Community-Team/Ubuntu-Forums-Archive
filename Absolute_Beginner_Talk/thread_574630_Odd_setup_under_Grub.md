---
title: "Odd setup under Grub"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by jeff4760 on 2007-10-13
I upgraded to ubuntustudio today and the following error is now apparant on my machine:

when I reboot the computer a new copy of Ubuntu is created in the loader ( I am dual-booting with XP).  It is complete with it's own recovery boot option.  Any ideas why this is there?  There is another thread with the same problem and no one answered it, so hopefully some one can give me a hand.

[http://ubuntuforums.org/showthread.php?t=27264]("http://ubuntuforums.org/showthread.php?t=27264")

Grub is on it's own partition /boot, and I used the Grub Super CD to set it up.

---

### Post by forestpixie on 2007-10-13
can you post your menu .lst

```
cat /boot/grub/menu.lst
```

---

### Post by jeff4760 on 2007-10-13
Well I can't actually do that now:

I should give a little more backstory on what is going on so maybe that can help you help me more. After upgrading to Ubuntustudio, I went searching and installing the best I could all those gstreamer files and restricted format packages (there really is no one good page that explains that the clearest- if you know of a link for that so I can use in the future, I would appreciate it). Then I found Envy and let it find my nvidia card and install it.  I am dual booting with Windows, and after all that, last night ( as I stated before-another instance of the Ubuntu kernel-with it's own recovery mode- showed up under Grub. Then this morning nothing will load up. The low latency kernel says that the X server is screwed up. The first instance of the normal kernel Ubuntu will get to the gdm, let me log in and then freeze up. The second one also says the X server is messed up. I am getting tired of this X server crap. It messed up after I installed the graphics card drivers under the 64 bit version of Kubuntu. And the 64 bit version was so unsupported that I realized I would need 32 bit to save my time the headache.

I can get into to DOS looking screen, that is in a sense Linux without the GUI.  I put the command in that you told me, put it shows too fast and doesn't let me scroll back up to look at all of it.

Any help would be appreciated, because I am really frustrated (almost wiped the Linux partitions clean this morning), and any help that will keep this from happening again with future reinstalls would be much appreciated.

---

### Post by jeff4760 on 2007-10-13
I tried to reconfigure the xserver using the sudo command but it doesn't work.  I did uninstall evolution last night, and everything I could find that was attached to it.  Would that have anything to do with it?

I can't seem to get into linux, so it seems to me that I might have to reinstall it.  Any help again would be appreciated.

---

### Post by jeff4760 on 2007-10-13
I finally got access to the file.  How do I modify it to remove the excess entries?

Thanks.

---

### Post by louieb on 2007-10-13
Don't worry about the extra entries they are there for your protection. If the 1st doesn't work you have the 2nd to use. 

Lots of ways to get rid of the extra entries. Remove the kernel with the package manager or just delete the entry from menu.lst. 
[Grub From the Ground Up]("http://www.troubleshooters.com/linux/grub/grub.htm")

---

### Post by jeff4760 on 2007-10-14
I tried to delete the entry but it wouldn't let me save my choices.  How do I delete it under administrator?  Do I sudo a certain text editor that will give me administrative privilages to delete the extra entries?

There is now an extra low latency kernel entry too.

---

### Post by louieb on 2007-10-14
Kinda aggravating  isn't  it. Stick around and you''ll get use to it. Just got to get rid of that windows way of thinking.   
```
gksudo gedit /boot/grub/menu.lst
```:lolflag: if you break it you get to keep both pieces,  Make a backup.

---

### Post by Ferri on 2007-10-14
Instead of deleting entries it may be safer to comment the line out. Just put this character before: # . GRUB will ignore this lines (the same it's true for any other text file in linux).

---

### Post by Soarer on 2007-10-14
> **louieb said:**
> Kinda aggravating  isn't  it. Stick around and you''ll get use to it. Just got to get rid of that windows way of thinking.   
```
gksudo gedit /boot/grub/menu.lst
```:lolflag: if you break it you get to keep both pieces,  Make a backup.

If you don't have a GUI (i.e. you are working is a 'dos-like box' that won't work.

Try:

```
sudo nano /boot/grub/menu.lst
```

BACK IT UP FIRST THOUGH (as suggested).

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.keepsafe
```

:)

---

### Post by jeff4760 on 2007-10-14
Well....I wish I would have caught the "don't forget to backup" before I did forget to backup.  Crap, this OS switch is much harder than I thought.  My major problems/annoyances right now seem to be all related.  Like I said in the first post, I installed ubuntustudio as a fresh install.  I have extra low latency and normal kernel options under the grub boot menu.  That may not be a big deal but it just looks messy.  I deleted the exta entries and now the norma kernel (the one I left to boot into) won't let me into the GUI...it's says it's an x server problem.

How can grub have that kind of impact.  I really wish there was someone who would be willing to hop on an IRC chat or IM with me sometime in the future and help me out.  

I also cannot get-even before the grub incident- into the low latency kernel.  I think I was able to get into the low latency when I first installed ubuntustudio, but I after I installed the nvidia drivers, via Envy, I could not get back in there.  It kept saying that the x server crashed.  I installed the drivers under the normal kernel...should I have done it under the low latency?

I assume I must be missing a step or two for why these problems keep happening, so I need some expertise.  I was going to pay for technical support, but I don't the $250 right now ubuntu is asking for support.  I like the "free" mentality of linux, but now I see the catch 22.  It's only free till you need problems fixed.

If there is anyone in Austin, Texas that is seeing this, then I will definitely take you to dinner ( and not fast food) for some help.

---

### Post by LowSky on 2007-10-14
> **jeff4760 said:**
> Well....I wish I would have caught the "don't forget to backup" before I did forget to backup.  Crap, this OS switch is much harder than I thought.  My major problems/annoyances right now seem to be all related.  Like I said in the first post, I installed ubuntustudio as a fresh install.  I have extra low latency and normal kernel options under the grub boot menu.  That may not be a big deal but it just looks messy.  I deleted the exta entries and now the norma kernel (the one I left to boot into) won't let me into the GUI...it's says it's an x server problem.

How can grub have that kind of impact.  I really wish there was someone who would be willing to hop on an IRC chat or IM with me sometime in the future and help me out.  

I also cannot get-even before the grub incident- into the low latency kernel.  I think I was able to get into the low latency when I first installed ubuntustudio, but I after I installed the nvidia drivers, via Envy, I could not get back in there.  It kept saying that the x server crashed.  I installed the drivers under the normal kernel...should I have done it under the low latency?


If there is anyone in Austin, Texas that is seeing this, then I will definitely take you to dinner ( and not fast food) for some help.


Yuo have two issues, one is grub the second is X server. It seems like you fixed Grub so lets work on X.

First boot into recovery mode, that should be possible. the type ```


sudo dpkg-reconfigure xserver-xorg
```

repick your video drivers and everything should be ok


I live in NY so I guess you'll have to fly up here to take me out to dinner....lol

---

### Post by jeff4760 on 2007-10-14
I appreciate your response, but I already tried that.  I found that fix from a thread when I crashed the x server about four days ago.  At that time I was trying out the 64 bit Kubuntu and realized that 64 bit Linux isn't well supported yet by vendors.  The x server crashed when I installed the nvidia drivers.

The x server let me do the reconfigure but it didn't change anything.  I did the reconfigure in both the low and normal kernels under their recovery modes.  I keep wondering if maybe I am not putting in the right mouse or monitor configurations, and that could be a possibility for the crash.  I choose the first option for mouse because I don't know what either three are, although a fresh install of ubuntu(anything) will automatically recognize my wireless keyboard and mouse.

I think my main problem is the nvidia drivers.  I have the GeForce 7600 GT, and I am always choosing the new glx drivers.  I install them and they work fine under the normal kernel but it always screws up the x server under the low latency kernel.

I also have the grub/boot on it's separate partition.  Don't know if that could be part of it either.  

If I can just get the nvidia drivers to work on a fresh install (if that is what I need to do) for both the low and normal latency kernels then I will be fine.  If multiple instances of those kernels show up under grub then I will either try Ferri's idea of adding a # symbol before the entry, something, else, or just leave it for now.  I think the grub mess is the least of my worries.  The major problem is why the nvidia drivers keep crapping out the x server.

---

