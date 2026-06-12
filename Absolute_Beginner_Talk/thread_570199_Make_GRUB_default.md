---
title: "Make GRUB default"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by docinsano on 2007-10-07
Right now my computer is using LILO to boot. How can I switch so that GRUB will be my default loader? Thanks in advance.

---

### Post by malan_in on 2007-10-08
Solution is installing the grub loader. 
1) go to the terminal and type **sudo install-grub**
2) it ask where to install -  > check the MBR (Master boot Record)
3) reboot

---

### Post by malan_in on 2007-10-08
Another method,
 1) boot from ur cd,  under rescue mode
 2) in the click for the boot loader option and install grub

---

### Post by docinsano on 2007-10-08
I tried the terminal and it tells me: install-grub command not found. Anyone know how to do this?

---

### Post by nick_h on 2007-10-08
Type:
```
sudo apt-get install grub
```

---

### Post by docinsano on 2007-10-08
alright i forgot what i typed into terminal but i ended up with something like this:
grub>

what do i do now?

thanks everyone so far for the help.

---

### Post by nick_h on 2007-10-09
From the grub prompt set the root device to the device containing grub, for example if it is the first partition on the first disk type:
```
root (hd0,0)
```
Then install it using the setup command. For example to install to the MBR type:
```
setup (hd0)
```
To exit type *quit*.

There is a good howto [here](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by docinsano on 2007-10-14
> **wernst said:**
> Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different.  Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...

-Warr

When I got to step 4 in the howto this occured: Error 15: file not found. Now Im still stuck with LILO. While im here i just want to ask one question: what makes GRUB better than LILO? will i benefit from using one over the other?
Thanks again.

---

### Post by nick_h on 2007-10-14
Did you run grub as root?

For Ubuntu, step 2 will be to just open a terminal.  For step 3 type:
```
sudo grub
```

---

### Post by docinsano on 2007-10-15
> **nick_h said:**
> Did you run grub as root?

For Ubuntu, step 2 will be to just open a terminal.  For step 3 type:
```
sudo grub
```

Tried them both. As root and not. Still get the same error.

Also, Is it absolutely necessary to use a boot disk? My cpu doesn't have the memory to run the live cd so that's out of the question. BTW, I'm using Xubuntu if that makes any difference.

---

### Post by bodhi.zazen on 2007-10-15
> **docinsano said:**
> When I got to step 4 in the howto this occured: Error 15: file not found. Now Im still stuck with LILO. While im here i just want to ask one question: what makes GRUB better than LILO? will i benefit from using one over the other?
Thanks again.

LILO is a fine ...

I think you need to install grub from the grub prompt. What is your Ubuntu partition ?

see this link (if it helps) : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Run grub as root (sudo grub)

At the grub prompt you only need two commands :

```
root (hdx,y)
setup (hd0)
```

The problem is figuring your Ubuntu partition in rub speak :twisted:

---

### Post by docinsano on 2007-10-15
> **bodhi.zazen said:**
> What is your Ubuntu partition ? :twisted: 

I can only assume that I'm using the first partition, but I'm not 100% sure. I selected the use entire disk option upon installing if that clears things up. Thanks for the help so far.

---

### Post by bodhi.zazen on 2007-10-16
Well if you would be so kind as to list your partitions I think I can help.

Can you post the output of this command :

```
sudo fdisk -l
```

---

### Post by docinsano on 2007-10-18
Heres what it says
Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
     Device   Boot          Start                 End                   Blocks         Id         System
/dev/sda1     *                1                       2413              19382391    83         Linux
/dev/sda2                        2414              2482                   554242     5              Extended
/dev/sda5                       2414               2482                    554211     82         Linux swap/Solaris

That is all. thanks for the help so far bodhi zazen

---

### Post by bodhi.zazen on 2007-10-18
Try this :

```
sudo grub
```

At the grub prompt ...

```
root (hd0,0)

setup (hd0,0)
setup (hd0)

quit
```

Then reboot

---

### Post by docinsano on 2007-10-19
Once i get to the setup (hd0,0) this is the output:

Checking if ¨/boot/grub/stage1¨ exists...no
Checking if ¨/grub/stage1¨ exists... no

Error 15: File not found

What to do? Appreciate the help bodhi z. thanks.

---

### Post by bodhi.zazen on 2007-10-19
>_<

Let me suggest an alternate approach ...

quite grub ...

In the terminal, try this :

```
sudo update-grub
sudo grub-install /dev/sda
```

---

