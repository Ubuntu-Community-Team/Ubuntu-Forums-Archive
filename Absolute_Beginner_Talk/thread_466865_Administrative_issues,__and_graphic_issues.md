---
title: "Administrative issues,  and graphic issues"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by fergatron on 2007-06-07
1. First off I'd like to say I am VERY new to ubuntu (today) and am having three issues. I apoligize for being noobish and posting repeated questions. 

Yes, I am a windows user...not Linux

I logged in for the first time after installing ubuntu, I restarted and up loaded "grub" and I seleted generic boot and I got a blank screen, no nothing, my monitor had shut off. ! However I did get into Ubuntu when I went into recovery mode and typed "gnu", I believe... 

  I have a ATI Radeon X850XT and I read[ ***_this_***]("http://ubuntuforums.org/showthread.php?t=414194") sticky about the simple flaw on those cards but I didn't know how to do step 4

"Update package list and upgrade any packages needed."

Does that mean I need to go into the kernel (which currently I don't know how to do from here)
and enter in these changes?

By the way, I also* cannot* access the switch user screen without my monitor shutting off as well.

"I also tried installing the linux driver for my card...it's a .run file...I can't find any help on google because it won't execute it says

 "Could not open the file /home/fergatron/Desktop/…ler-8.37.6-x86.x86_64.run."

2.So now that I am in ubuntu I wanted to change my theme settings and edit boot files, but apparently I don't have administrative privileges to make these changes. I went into recovery mode and typed

 adduser fergatron admin or somthing like that...

 and it said I was already an admin! I go back into ubuntu and sure enough, no changes I cannot make any administrative changes. I only made one account and nobody except me will be using this computer anyway...what do I need to do?

3. I don't know what all you linux users call the "taskbar" on the bottom with the option to have separate desktops and hide everything and show your desktop...well it's gone! It totally went away while I was typing! how do I make it come back?! theme changes or somthing?

* I am sorry I am not very good at this operating system, I had always wanted to learn how to use Linux and the shell because I will be working on these in college.***_[SIZE="3"][SIZE="3"] If anybody out there could help or show me with at least ONE of these or[/SIZE][/SIZE]_*** links to other forum posts that might help that would be MUCH appreciated. Thank you for your time to read this long inquiry.

Other notes... I am running Ubuntu 7.04, Feisty Fawn and a dual core intel cpu with a gig of ram. on a 15 gigabyte partition.

---

### Post by mlentink on 2007-06-07
To perform administrative taks in ubuntu you have to let it know that you can and want to do so. The GUI apps that need to know if you're an admin will ask you to type in your password. In terminal, you precede commands with the command 'sudo' which means something like 'as superuser do....' followed by the reular command.

So, let&#347; say i wanted to create a directory:
```
sudo mkdir newdirectory
```

As to your other questions, I have to look more and I am certain I can't answer all of them

---

### Post by sandwitch on 2007-06-07
What the page says is this: Go to text mode (do that by hitting Ctrl alt F1) log in and run those commands with sudo. Al needed drivers will be installed. Btw blame ATI for this. Google for ati and linux and you will learn words that make your mother blush ..
goodluck

---

### Post by mlentink on 2007-06-07
> **fergatron said:**
> I logged in for the first time after installing ubuntu, I restarted and up loaded "grub" and I seleted generic boot and I got a blank screen 
Do you remember which version you installed? Did you do the i386 or the generic? What hardware do you have?
> **fergatron said:**
> "Update package list and upgrade any packages needed."
in the terminal, do the folllowing:
```
sudo apt-get update
sudo apt-get upgrade

```
That's all
> **fergatron said:**
> Does that mean I need to go into the kernel (which currently I don't know how to do from here)
As a noob, do not touch your kernel. I know I wouldn't. It is not necessary unless you want to build a custom version of linux

---

### Post by fergatron on 2007-06-07
I did all the things that was told of me (update packages etc.) Still no luck getting my graphics card to respond at generic boot. I still need to go into the kernel and type "gdm" before getting anywhere.

---

### Post by fergatron on 2007-06-10
I got the boot to work now by installing the 32bit version of Ubuntu Feisty!

---

