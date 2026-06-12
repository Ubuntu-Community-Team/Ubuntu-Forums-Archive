---
title: "Installing Super Grub"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-04-04
At the moment to try to get my Windows side of things working again I am installing Supper Grub. However I ran into another problem.

I downloaded the Cd and burned it to disk.

The problem comes when I load the disk and reboot the system.

As far as there web site said I thought I was to come to a language selection screen. instead I get

grub>

What do I do now? 

what happened to that easy set up they explained on the web site? 

Below is a link to the thread that got all of this started.

[The bride is so going to kill me]("http://ubuntuforums.org/showthread.php?t=400209&highlight=sabar")

Thanks for any help you can give
Sabar

---

### Post by ReverendJ1 on 2007-04-04
From the Super Grub website

> When I booted my Super Grub 0.9575 floppy disk I found that I was left at the grub>_ prompt.
I typed the following code after the grub>_ prompt,

```
grub> find /boot/grub/menu.lst
```

```
grub> root (fd0) 
```

```
grub> setup (fd0) 
```

```
grub> reboot
```

Reboot and SuperGrubDisk should work from your floppy disk okay from now on.

---

### Post by Sabar on 2007-04-05
I tried all of them in the order given. none of them worked either could not find file, or something.

any other ideas? wonder if It was a bad burn or a bad download?

Sabar

---

### Post by ReverendJ1 on 2007-04-05
If possible, try making a Super Grub floppy disk. If the same thing happens, then follow those directions and they should work. Here is the link for the [floppy image]("http://forjamari.linex.org/frs/download.php/540/super_grub_disk_english_floppy_0.9589.img"), and the instructions for making one:

> To make a Super Grub floppy disk in Ubuntu
   1) Put your sgd_0.9575_english_floppy.img.bz2 file in your home/username directory if it isn't there already.
   2) Right click on it and click 'extract here'. You should get a new file out of it called super_grub_disk_floppy_english_0.9575.img
   3) Put a blank floppy disk in your machine's floppy disk drive.
   4) Open a terminal
   5)  Use this 'dd' command to write SGD to the floppy disk, or you can copy mine and paste it into your own terminal if you want.
Do not include the herman@red:~$ part, (unless your name is herman and you have a computer named red too).

```
herman@red:~$ dd if=super_grub_disk_floppy_english_0.9575.img of=/dev/fd0
```

That command should make the floppy drive light come on and you should hear some moaning and groaning noises coming from your floppy drive for a minute or so, then you should have a new Super Grub floppy Disk.

---

### Post by Sabar on 2007-04-05
Like alot of people I thought Floppies were dead. didn't know I was ever going to want one. so this computer doesn't have one :( 

Yep thats right saved my self a whole $6.00. Maybe! 

Why is it I could not down load the file from 2 out of the three places listed?

Sabar

---

### Post by confused57 on 2007-04-05
> **Sabar said:**
> Like alot of people I thought Floppies were dead. didn't know I was ever going to want one. so this computer doesn't have one :( 

Yep thats right saved my self a whole $6.00. Maybe! 

Why is it I could not down load the file from 2 out of the three places listed?

Sabar
Hi Sabar,
   The SGD cd works fine for me,  this is the only download link I could get to work:
[http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)

---

### Post by ReverendJ1 on 2007-04-05
Yeah, I feel like a dinosaur when I put them in my newer computers and people always ask why. But, they do come in handy sometime. :-) Anywho, have you tried just hitting Esc? That is supposed to bring up the menu, c drops to the console. 
Try [this link.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Common_Booting_Errors_and_Some_Possible") It seems to have a lot of answers to why grub won't work. You may have to scroll quite a while to find what you're looking for though.
You can also try redownloading/burning and/or try a different version. Check out the link from Confused57 for others. (Thats where I got mine too)

---

### Post by Sabar on 2007-04-05
I Just now hit Esc. but that didn't help either. I am going to check out the other link tonight. 

Wish I knew why the resorce CD called my two hard drives F and G
thought they were C and D 

well anyhow some one said they would bring me a Repair CD to work tonight. Maybe that will work. Worst case scenario. It gets wiped out and started fresh.

Back at yea later all
Sabar

---

