---
title: "ibook g4 hardy heron boot problems"
date: 2009-01-28
forum: Apple Hardware Users
---

### Post by devrele on 2009-01-28
I wanted to start a new thread for this problem in hopes it would come to the attention of someone who might know the solution.

I installed 8.04 on my ibook G4 14" using the 8.04 alt PPC disc. When I boot Ubuntu I get a screen with colored pixels which eventually fades to black. If I press "tab" from the boot prompt I do not get a list of options. If I try to issue the command "live-nosplash-powerpc" I just get an error message ("no such file or directory") I have also tried "linux nosplash" but it doesn't work either.

However, I just downloaded the 8.04 live desktop disc. I found that if I booted from this disc without issuing any commands, there is the same result as I described above, when trying to boot from my Ubuntu installation. However, here I am able to issue commands and if I issue "live-nosplash-powerpc" Ubuntu will boot, and I will get the desktop.

So I am able to access Ubuntu through the live CD, but not through my installation.

From the live CD I am able to access the partition where I installed Ubuntu. So I am wondering if there is a way for me to edit a file so that it boots with "live-nosplash-powerpc"?

Can anyone instruct me on what file I need to edit and how I need to edit it in order to get my installation to boot?

Thanks in advance.

---

### Post by avtolle on 2009-01-28
From the boot: prompt, input Linux video=ofonly nosplash and press Enter. As I recall, I had to do this with my G4 Cube to get going on Hardy.

---

### Post by mkvnmtr on 2009-01-28
I have been thinking about your problem and it seems similar to some threads where people had problems with a xorg configure file. I never did but there some people that come on the forum that know how to edit the file and what file it is. I would think if you are booted up from the live disk then the same configuration would work on your system. I just don't know what file it is. You can probably copy the file off of the disk and replace it in you own file. Lets hope some one that knows sees before you try a reinstall.

---

### Post by devrele on 2009-01-28
Avtolle, thanks for the suggestion. Unfortunately it didn't work.

But after reading many different posts and experimenting with many different combinations I finally found something that got me access to the desktop:

Linux video=ofonly modprobe ide-core

The only problem is I don't know what that means or why it worked!

Hopefully somebody out there will be able to tell me why this particular combination worked for my system, and what I need to do to make the permanent change so it always boots.

I haven't played around with it much yet, but things seem to be working ok, with the exception of sound. I get the message: "The volume control did not find any elements/devices to control." For whatever reason, this didn't happen when I booted off the livedisc, but is happening now.

---

### Post by devrele on 2009-01-28
Well, it seems I may have spoken too soon. That got my to the desktop once, but I rebooted, and it didn't work again.

Now once again I am just getting strange colors all over the screen. The only difference from before is that there is also a light-colored horizontal line across the screen as the colors change.

And now I just tried "Linux video=ofonly nosplash" and this time it DID work. Strange that things that aren't working when I input them once, then work another time...

I still get the strange colors and the horizontal line when using "Linux video=ofonly nospalsh" but they disappear pretty quickly, replaced by the Ubuntu login screen.

---

### Post by mkvnmtr on 2009-01-28
I have installed from 6.06 to 8.10 on my Ibook maybe 30 times and never had those problems. I have helped maybe 10 people install on Ibooks and never seen that type of problem. On several distro to boot the disk to install I have had to use the live nosplash or another option to boot the disk but after the install I was fine rebooting from my hard disk. I have seen the modprobe command given in the threads and it worked to stabalize. The strange thing is that something works for you one time and not another. If it was me I would reinstall off of the live disk but it would be better if someone can help you fix whats wrong. It sounds like some file is corrupted.

---

### Post by tiresia on 2009-01-28
Yaboot, the PC bootloader, gives you at the first prompt to pass some 'arguments' to the kernel in order to boot the kernel in the right way for your computer.

When you install it, you have several options, that the developer already made for you. To know them hit TAB, and you will see them (e.g. live-nosplash-powerpc or power64 etc.)

You already installed Ubuntu. If you want to customize the boot process, so that you don't need anymore, to type 'video=ofonly', you must edit the file /etc/yaboot.conf
1. Backup that file
```
sudo cp /etc/yaboot.conf /etc/yaboot.conf.bak
```

2. Edit the file 
```
sudo nano /etc/yaboot.conf
```
add the options you need after the line 'append=' (if you don't see it add it at the end of the first block - after 'defaultos=' or 'initr=')
```
append="quiet nosplash video=ofonly"
```
When you are ready hit ctrl+X to escape, you will be asked, if you want to save the changes. Say 'yes' and run
```
sudo -ybin -v
```
This is important, otherwise yaboot will not update this configuration.
I suggest you to try different solutions (maybe at first only "video=ofonly" etc). Don't be afraid, since you made a backup of that file, you can always take it back, just running
```
sudo cp /etc/yaboot.conf.bak /etc/yaboot.conf
```
The old yaboot.conf will overwrite the changed yaboot.conf (don't forget to run always ybin)

Have a look on this forum, to see which solutions other people found for your mac. You will most probably need to edit the /etc/X11/xorg.conf file, to fit X to your grafic card

This link will help you to find a solution for the sound
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by devrele on 2009-01-29
tiresia,

Thanks for your helpful post. One problem I am encountering is that I do not get any option menu when hitting tab at either of the boot prompts. If I do it at the prompt for boot choices, nothing happens. If I do it at the second prompt, before trying to load Ubuntu, I just get the message "Linux old"

mkvnmtr,

What you say about corruption sounds like a possibility to me, because the behavior is strange and random. Why will it boot if I enter "Linux video=ofonly nosplash" one time, and then the next time not boot? It doesn't seem to make sense.

Maybe It would be a good idea for me to reinstall using the Live disc. Since I have seen at least that Ubuntu works perfectly from the desktop when I boot from the Live disc, maybe there is hope that an installation from the Live disc will fix the problems I'm experiencing.

I have a question about reinstalling and the partitioner. I read a guide that told me to use the partitioner to delete the Ubuntu partition, so that there is empty space, and then reboot the disc, and run the installer again, and it should suggest to install Ubuntu in the empty space.

Well, I did delete the parition. Ubuntu told me there was empty space there. But when I rebooted and ran the installer again, the installer was seeing that partition as containing an Ubuntu system, not as empty space, and not allowing me to install there. 

So apparently the paritioner didn't really delete my Ubuntu parition?

---

### Post by tiresia on 2009-01-29
> **devrele said:**
> One problem I am encountering is that I do not get any option menu when hitting tab at either of the boot prompts. If I do it at the prompt for boot choices, nothing happens. If I do it at the second prompt, before trying to load Ubuntu, I just get the message "Linux old"
Yes, this is normal. I meant that you get different options only when you start the computer from the installer CD

> I have a question about reinstalling and the partitioner. I read a guide that told me to use the partitioner to delete the Ubuntu partition, so that there is empty space, and then reboot the disc, and run the installer again, and it should suggest to install Ubuntu in the empty space.

Well, I did delete the parition. Ubuntu told me there was empty space there. But when I rebooted and ran the installer again, the installer was seeing that partition as containing an Ubuntu system, not as empty space, and not allowing me to install there. 

So apparently the paritioner didn't really delete my Ubuntu parition
You don't need to boot again, after you delete the partition. I don't know how you deleted the partition, but it looks like you did not confirm that action. You delete a partition in two steps, first you choose what you want to do, second you do it. 
Use the Ubuntu Hardy Live CD, open the Partition Editor (System > Administration) and delete the partition, then start the installer using the free space.
You will most probably need to configure your audio after the installation, but the hardy installer is very reliable. For the audio see the link I gave you in the post above.

---

### Post by devrele on 2009-01-29
latest update:

I was able to delete the partition using iPartition.

After this, I installed from the 8.04 Live Disc and it looks like I finally have a good install at last.

Everything is working perfectly. Ubuntu loads without any need for additional commands. I get the splashscreen and it looks great--whereas it never even appeared before. Audio works. 

What a relief!

And I now have a system that runs one hundred times faster and smoother than it did under Leopard!

So I guess my system just didn't like the alternate install disc for some reason. Either that or the installation got corrupted somehow. I don't know.

Anyway, thanks again to all of you who has given me assistance during the long process of getting Ubtuntu set up on my iBook!

---

### Post by mkvnmtr on 2009-01-29
That's great. You are now an expert on installing on a G4 Ibook and will be expected to help others that have problems installing. have fin.

---

