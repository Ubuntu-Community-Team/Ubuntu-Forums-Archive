---
title: "[SOLVED] help i did critcal updates today......"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-09-25
and my sound card has disappeared again.
this happened when i first installed ubuntu about 2wks ago.
when i click the speaker on the top toolbar it says  this:
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

iv tried uninsatalling and reinstalling alsa then configuring it only to be told this:
 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!


billym@billym-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
billym@billym-desktop:~$

---

### Post by remick182 on 2007-09-25
I, too just did my critical updates and lost my sound.  I have only one soundcard, and it's listed under System > Preferences > Sound.  However, despite changing volumes, and whether or not anything is plugged into the headphone jack, I get nothing.  Alsamixer lists my card (HDA ATI SB with the generic 11c1 Si3054 chip.  All volumes at 100% and no channels muted.

I did a:  **sudo apt-get remove alsa**, followed by a **sudo apt-get install alsa** with no joy.  Is there a log that I can pull up to see what critical updates were just performed?  I know one was an image update because I was given the 'Must restart system' alert.

---

### Post by Skidpad on 2007-09-25
I had this happen a few months ago.  While searching for a fix, I found an informative thread that helped me fix it, [Here]("http://ubuntuforums.org/showthread.php?t=407863&highlight=sound").  You may want to read through that thread, and the actual "fix" thread linked therein.

Sorry I can't offer more help than that.

---

### Post by maryjanua on 2007-09-26
thanks anyway but iv tried a few things and it says i dont even have a soundcard! yet it was working yesterday.
when this happened before i ended up compiling my own driver but i dont think i could do it again on my own as i got a lot of help last time.
is this normal behaviour when so-called critical updates are done- the updates break your pc?
i have(or did have) intel hda sound and the actual driver no. was alc888 can anyone help me fix this?

---

### Post by maryjanua on 2007-09-26
iv tried booting to the other kernel and this is what it says:
billym@billym-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
billym@billym-desktop:~$ 
 the 1st time i did aplay -l i got my soundcard listed but now its disappeared because i restarted
i'll try the newer kernel again and post

heres what the newer kernel that was updated says:
billym@billym-desktop:~$ aplay -l
aplay: device_list:222: no soundcards found...
billym@billym-desktop:~$

---

### Post by remick182 on 2007-09-26
That's strange.  I've fixed my problem.  Sound works after doing some reconfiguring of alsa.  I'll post a more in-depth fix after I get back from school tonight.  I have some questions about the image updates and writing my own shell script to aid in updates.

In the meantime, if you read this **maryjuana**, list what kind of pc you are using, type of soundcard, whether it's integrated or an individual component, etc.  All of that info will help us to troubleshoot.

---

### Post by maryjanua on 2007-09-26
desktop: mobo: asrock 4core dual sata2
               cpu: celeron d 352+  3.2 ghz
               soundcard: onboard realtek hd audio  7.1 driver alc888
               videocard: ati radeon X1550 agp
               RAM: 512mb ddr400 (2x 256)
               hdd0 : seagate 160gb ide (2 partitions 1st xp pro,2nd ubuntu feisty 7.04)
               hdd1 : seagate 80gb ide - xp data
               cd : nec dvdram 16x

---

### Post by kast on 2007-09-26
Well i did this update, and now i get a   1962: no operating system found after restart :-)  anyone else getting a more serous error besides missing hardware? Or have seen this.
  
      This is freaking crazy!

---

### Post by mali2297 on 2007-09-26
I hesitated before I went along with the kernel update.  These updates can give you problems, especially if you have compiled programs yourself. Fortunately for me, I didn't experience any problems this time.

@maryjanua:
I'm confident that we will be able to fix your sound once again. 

Hopefully, sound will work out of the box in Gutsy, in which case you don't have to repeat the same compilation procedure for each kernel update.

@kast:
Can't you boot Ubuntu at all? 

When running the update, I got some warnings about grub. Might the problem be there?

---

### Post by kast on 2007-09-26
I didn't have much time to mess with it before i had to get to work, i will look further when i get home and post back. 

           Thanks!

---

### Post by maryjanua on 2007-09-26
thanx guys. wow kast yours is worse than mine--not even booting!

---

### Post by kast on 2007-09-26
I know! :) it just might be a grub issue we will see.

---

### Post by maryjanua on 2007-09-26
looking through the forum we r not the only 1s :)

---

### Post by kast on 2007-09-26
I have been checking back once in awhile to see if anyone has an extreme case like myself no luck yet, its tough having to wait till i get home to fix this! i new i should have installed updates before work :)

---

### Post by maryjanua on 2007-09-26
it knows i have a soundcard look!:

80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: ASRock Incorporation Unknown device 0888
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

thats the sound portion of what comes out when i type  :   lspci -v


so why doesnt it see it???:confused:

---

### Post by mali2297 on 2007-09-26
> **maryjanua said:**
> iv tried booting to the other kernel and this is what it says:
billym@billym-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
billym@billym-desktop:~$ 
 the 1st time i did aplay -l i got my soundcard listed but now its disappeared because i restarted
i'll try the newer kernel again and post

heres what the newer kernel that was updated says:
billym@billym-desktop:~$ aplay -l
aplay: device_list:222: no soundcards found...
billym@billym-desktop:~$

Did you try to repeat the same thing as last time?
[http://ubuntuforums.org/showpost.php?p=3379876&postcount=66](http://ubuntuforums.org/showpost.php?p=3379876&postcount=66)
What does *aplay -l* say after this?

Then compile again...
[http://ubuntuforums.org/showpost.php?p=3390143&postcount=106](http://ubuntuforums.org/showpost.php?p=3390143&postcount=106)

---

### Post by maryjanua on 2007-09-26
str8 away on the 1st line there was an error:
billym@billym-desktop:~$ rm /home/billym/.asoundrc
rm: cannot remove `/home/billym/.asoundrc': No such file or directory

---

### Post by mali2297 on 2007-09-26
> **maryjanua said:**
> str8 away on the 1st line there was an error:
billym@billym-desktop:~$ rm /home/billym/.asoundrc
rm: cannot remove `/home/billym/.asoundrc': No such file or directory

Well, that's fine. Continue...

---

### Post by maryjanua on 2007-09-26
billym@billym-desktop:~$ aplay -l 
aplay: device_list:222: no soundcards found...
billym@billym-desktop:~$ 


still nothing

---

### Post by mali2297 on 2007-09-26
> **maryjanua said:**
> billym@billym-desktop:~$ aplay -l 
aplay: device_list:222: no soundcards found...
billym@billym-desktop:~$ 


still nothing

Did you reboot?
Anyhow, continue with the compilation.

---

### Post by dwhitney67 on 2007-09-26
I took a peek at my Ubuntu notebook this morning (usually I just connect to it using SSH).  Anyhow, I noticed that "updates" were available.  I know from experience that if my system is working properly, there is no need to upgrade the kernel (and related packages such as headers, glibc, etc.).

Some may argue that updating the kernel is essential because it may contain security fixes.  Well, maybe so, but I rather have a _working_ system with a security hole (which is unlikely to ever be compromised).

Next time you are presented with updates, and one of them is a kernel, ask yourself if you really need it.  Time and time again a new kernel will not contain the proper support you enjoyed in the past, _or_ it may require you to uninstall and then install again drivers (such as Alsa for the sound card).

---

### Post by maryjanua on 2007-09-26
thanx 4 that

---

### Post by mali2297 on 2007-09-26
> **maryjanua said:**
> thanx 4 that

How did the compilation go? Did you receive errors?
:popcorn:

---

### Post by maryjanua on 2007-09-26
sorry mali i meant the other dude who was just pointin out the obvious

---

### Post by maryjanua on 2007-09-26
i got this far b4 an error is this ok and i'll continue:

billym@billym-desktop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
billym@billym-desktop:~$

---

### Post by mali2297 on 2007-09-26
> **maryjanua said:**
> i got this far b4 an error is this ok and i'll continue:

billym@billym-desktop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
billym@billym-desktop:~$

Sorry about that, I typed it wrong earlier. :oops:
It should have been **`** instead of **'**. Better yet, make it
```

sudo apt-get install linux-headers-$(uname -r)

```

---

### Post by maryjanua on 2007-09-26
do you mean run that line then run the aforementioned or replace a line with that because it still says the same?

---

### Post by mali2297 on 2007-09-26
> **maryjanua said:**
> do you mean run that line then run the aforementioned or replace a line with that because it still says the same?

Run
```

sudo apt-get install linux-headers-$(uname -r)

```
**instead of** the earlier. Then there should at least not be an error like
> 
E: Couldn't find package linux-headers-uname -r


---

### Post by kast on 2007-09-26
Back up! ran the generic recovery, it cleaned my file system and then restarted. seems that this issue i had wasn't with he updates after all. my sound works also. maryjanua how is your sound coming along?

---

### Post by maryjanua on 2007-09-27
sound is back...i had to recompile alsa thanx again mali
heres the ouptput of this :  
billym@billym-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
billym@billym-desktop:~$ 


theres another 2 updates waitin but now i'm suspicious...should i take them??

---

### Post by mali2297 on 2007-09-27
> **maryjanua said:**
> sound is back...i had to recompile alsa thanx again mali
heres the ouptput of this :  
billym@billym-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
billym@billym-desktop:~$ 


theres another 2 updates waitin but now i'm suspicious...should i take them??

Are they kernel updates (concerning packages like linux-image)?
In that case, I would advice you to instead wait for Gutsy.

But I think it's fetchmail and elinks this time, that should not cause any problems if you update.

---

### Post by maryjanua on 2007-09-27
says they are:
update-manager
GNOME application that manages apt updates

and

update-manager-core
manage release upgrades

---

### Post by mali2297 on 2007-09-27
> **maryjanua said:**
> says they are:
update-manager
GNOME application that manages apt updates

and

update-manager-core
manage release upgrades

That should be safe to upgrade. 

As I said, it is mainly updates of the kernel that can give you problems. That is, linux-image with accompanying packages.

---

### Post by maryjanua on 2007-09-27
ok thanx i'll keep that in mind

---

### Post by kast on 2007-09-27
What are they?

---

### Post by mali2297 on 2007-09-27
> **kast said:**
> What are they?

What are what? :-s

---

### Post by kast on 2007-09-27
hahaa sorry! I guess I missed the part where the names of the updates where listed.

---

