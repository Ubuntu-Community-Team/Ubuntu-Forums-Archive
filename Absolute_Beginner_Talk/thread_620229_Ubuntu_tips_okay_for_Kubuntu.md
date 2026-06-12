---
title: "Ubuntu tips okay for Kubuntu?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by VesperJunkie on 2007-11-22
when i search online for what i can do to my kubuntu desktop, post install, i run into many helpful guides for ubuntu. for example i see many online articles entitled "top 10 things you should do after installing ubuntu".

those tips and tricks for ubuntu aren't compatible with kubuntu, are they?

at this point, i don't even understand how i can download something as simple as swiftfox to kunbuntu desktop?

---

### Post by overdrank on 2007-11-22
> **VesperJunkie said:**
> when i search online for what i can do to my kubuntu desktop, post install, i run into many helpful guides for ubuntu. for example i see many online articles entitled "top 10 things you should do after installing ubuntu".

those tips and tricks for ubuntu aren't compatible with kubuntu, are they?

at this point, i don't even understand how i can download something as simple as swiftfox to kunbuntu desktop?

HI the tips for Ubuntu will work also just the command may change a little
Example
gksudo gedit 
would be 
kdesu kate 

[http://www.bellevuelinux.org/kdesu.html](http://www.bellevuelinux.org/kdesu.html)

---

### Post by Happy_Man on 2007-11-22
Unless it's a GUI editing thing, as in, "How to Edit the Menus in Ubuntu", it should be the same. You can even use Synaptic in Kubuntu.

---

### Post by VesperJunkie on 2007-11-22
thanks for replying, but that doesn't really help me at all.

why is it that kubuntu users don't enjoy such support like these forums? what are complete noobs suppose to do?

like right now, i don't even know how to install swiftfox or divx to watch movies online, etc?

---

### Post by Incense on 2007-11-22
Both ubuntu and kubuntu use the same debian base, as well as the same repos so things should work in both. The big exception was already pointed out with gedit vs kate (or kwrite). You also have adept instead of synaptic, but they both use apt-get so your command line code will be the same. 

What kind of problems are you having with swiftfox?

---

### Post by Incense on 2007-11-22
> **VesperJunkie said:**
> thanks for replying, but that doesn't really help me at all.

why is it that kubuntu users don't enjoy such support like these forums? what are complete noobs suppose to do?

like right now, i don't even know how to install swiftfox or divx to watch movies online, etc?

If you want the codecs installed in kubuntu run this command. 

```
sudo apt-get install kubuntu-restricted-formats
```

Kubuntu does have it's own forums, but they are not as popular as the ubuntuforums are. Just ask, and people here will help. We do have a lot of KDE fans on ubuntu!

---

### Post by overdrank on 2007-11-22
> **VesperJunkie said:**
> thanks for replying, but that doesn't really help me at all.

why is it that kubuntu users don't enjoy such support like these forums? what are complete noobs suppose to do?

like right now, i don't even know how to install swiftfox or divx to watch movies online, etc?

HI you can get the same support here for Xubuntu XFCE, Kde Kubuntu, Flux, and so on. Just state your problem and the desktop environment that you use.:)

---

### Post by VesperJunkie on 2007-11-22
thanks for the replies.

well now i have a new problem. when i try to open adept manager, i get this message:

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

---

### Post by skyjacker on 2007-11-22
> **VesperJunkie said:**
> thanks for the replies.

well now i have a new problem. when i try to open adept manager, i get this message:

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem. Do what it says and see if that corrects the problem. If it doesn't, check back...

---

### Post by VesperJunkie on 2007-11-22
i tried both and it doesn't do anything.

i'm kind of pressing for time right now and i need to get back to windows. can someone tell me how i can do that. right now if i restart, it takes me back to kubuntu. how can i get back into windows?

for my kubuntu problem, i'll come back and try it after i take care of business first on xp.

---

### Post by overdrank on 2007-11-22
> **VesperJunkie said:**
> i tried both and it doesn't do anything.

i'm kind of pressing for time right now and i need to get back to windows. can someone tell me how i can do that. right now if i restart, it takes me back to kubuntu. how can i get back into windows?

for my kubuntu problem, i'll come back and try it after i take care of business first on xp.

HI do you see the grub loading? This should allow you to choose between windows and Kubuntu. Did you resize the windows partition when you installed Kubuntu?

---

### Post by VesperJunkie on 2007-11-22
btw, i solved the problem with adept manager.

about windows though...

when i start it doesn't give me the dual boot option. regarding my kubuntu install, i just followed the installation wizard, and i remember that i had kubuntu installed on the same partition that windows was on, but i didn't know i was supposed to do something with windows.

is there any way to get back into windows?

---

### Post by meindian523 on 2007-11-22
what option did you give the installer regarding partitioning...?

---

### Post by overdrank on 2007-11-22
> **VesperJunkie said:**
> btw, i solved the problem with adept manager.

about windows though...

when i start it doesn't give me the dual boot option. regarding my kubuntu install, i just followed the installation wizard, and i remember that i had kubuntu installed on the same partition that windows was on, but i didn't know i was supposed to do something with windows.

is there any way to get back into windows?

HI and I don't know of any way to get windows back if you installed ubuntu on top of it. You will have to partition the hard drive then install windows again. Then you will have to reinstall the grub to be able to dual boot. :(
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by overdrank on 2007-11-22
> **VesperJunkie said:**
> btw, i solved the problem with adept manager.

about windows though...

when i start it doesn't give me the dual boot option. regarding my kubuntu install, i just followed the installation wizard, and i remember that i had kubuntu installed on the same partition that windows was on, but i didn't know i was supposed to do something with windows.

is there any way to get back into windows?

One sure way to see if windows is there is post the out put of this command
```
sudo fdisk -l

``` That is a lower case l not a 1.

---

### Post by VesperJunkie on 2007-11-22
i think i may have installed kubuntu on top. i'm glad i backed up my files. whew

anyway, since i'm stuck with kubuntu.. i really don't get what you guys mean when you tell me to paste some command.

i mean, i know to copy and paste it in "run command" in the K menu. However, aren't you suppose to see something happen after you put in something.

for example, right now i would like to watch some movies that require divx. what do i do? after the command, what am i supposed to be looking for?

and by the way. someone teach me how to install swiftfox, konqueror seems slow compared to firefox. please.

---

### Post by meindian523 on 2007-11-22
well open a terminal....

type ```
xterm
``` in the Run option of the K menu,then you have a prompt of the form

```
user@host-machine:~:
```

Type at that prompt

```
sudo fdisk -l
```

You will get output and the prompt back,copy and paste whatever you see here.....

By the way,

sudo==super user do

fdisk==partition table manipulator

-l==list all partitions on disk

edit:don't jump to conclusions...give us the fdisk -l and we will be sure to tell you whether you have really lost Windows or not....

---

### Post by overdrank on 2007-11-22
> **VesperJunkie said:**
> i think i may have installed kubuntu on top. i'm glad i backed up my files. whew

anyway, since i'm stuck with kubuntu.. i really don't get what you guys mean when you tell me to paste some command.

i mean, i know to copy and paste it in "run command" in the K menu. However, aren't you suppose to see something happen after you put in something.

for example, right now i would like to watch some movies that require divx. what do i do? after the command, what am i supposed to be looking for?

and by the way. someone teach me how to install swiftfox, konqueror seems slow compared to firefox. please.

HI and this links will help with the movies and such
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Sorry cant help on swiftfox, But yes when you enter a command there should be some output. Like the command I gave you resulted in this on my system
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3890    31246393+  83  Linux
/dev/sda2            3891       38889   281129467+   5  Extended
/dev/sda5            3891       16638   102398278+   b  W95 FAT32
/dev/sda6           16639       16893     2048256   82  Linux swap / Solaris
mine@ubuntu:~$ 


```
This link may help with the terminal (konsole ) also
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by meindian523 on 2007-11-22
cool,overdrank......

I just gave the general terminal everyone would have since I've never seen Kubuntu in action.......you seem experienced with KDE.....

---

### Post by Incense on 2007-11-22
> **meindian523 said:**
> cool,overdrank......

I just gave the general terminal everyone would have since I've never seen Kubuntu in action.......you seem experienced with KDE.....

Maybe it's time you gave KDE a go then. ;)

---

### Post by meindian523 on 2007-11-23
Well I've used KDE for a while on Mandriva 07 but not since then.....and that's a little too far back for me to remember......

---

### Post by VesperJunkie on 2007-11-24
Thanks for all the help. Here's my partition info:

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb33eb33e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4777    38371221   83  Linux
/dev/sda2            4778        4870      747022+   5  Extended
/dev/sda5            4778        4870      746991   82  Linux swap / Solaris

---

### Post by meindian523 on 2007-11-24
You are right,you have lost Windows,ie you have installed Kubuntu over Windows.....

---

