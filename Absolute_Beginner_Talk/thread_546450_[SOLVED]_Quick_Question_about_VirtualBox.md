---
title: "[SOLVED] Quick Question about VirtualBox"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-09-08
I just got virtual box, and it seems pretty fabulous.
But I was wondering, if I installed Fedora or Ubuntu with VirtualBox, does it install it to my "virtual hard drive", or to my actual hard drive? I really don't want it to install to my hard drive and make more partitions, but if it installed it to the "virtual hard drive", that would be great.

Any thoughts?

Thanks,
Dr Small

---

### Post by Linux_Man on 2007-09-08
In most virtualization software such as Qemu you have a file on your hard drive that is the virtual hard drive that may or may not be the same size of the virtual hard drive. So say you install Windows, it will not overwrite your linux install nor will you be able to boot it as you would a normal Windows install.

---

### Post by Dr Small on 2007-09-08
Ok, thank-you for your response.
VirtualBox does have a file under ~./virtualbox somewhere where my "virtual hard drive" is stored :D

Thanks for the info!
Dr Small

---

### Post by Orbital75 on 2007-09-08
Dr. Small,  I can help you with this.

I am currently running Virtual Box on my XP Pro machine.
in fact, That how I run Ubuntu.

What you will have to do is create a large file on your hard drive.
This will be called your Virtual Hard Drive.
You will then install your new OS into that file.
Example: My file is 8 Gigs and my Ubuntu is installed within it.

Works great...... Make sure you have enough ram
I have 1 gig and it's kinda slow but still runs well.

With Virtual Box you can choose how much Ram you want to give the Virtual Machine.
I ended up giving mine 384 Meg just because XP needs most of it.

If you need more help, I can walk you through it if you like.

---

### Post by Dr Small on 2007-09-10
I installed Feisty in VirtualBox, on a 2.5 GB virtual hard drive, and all went well, with 256 MBs of RAM :p
I only have a total of 512 MBs of RAM, so that's about all I can do. I am thinking about upgrading my RAM to 2 GBs later on, when I get the money, but currently I am doing the best I can do :D

Thanks for the help ;)

Dr Small

---

### Post by Amazona aestiva on 2007-09-10
I advise Virtualbox...
The latest versions are much reliable than the earlier ones.

---

