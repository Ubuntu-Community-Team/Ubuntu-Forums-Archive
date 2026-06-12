---
title: "Compile .tar.gz files."
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by xequence on 2005-09-09
Ever since I started ubuntu a month ago I wanted to know how to compile .tar.gz files so I can install them. I have the (trial I think...) file for VMware.

/home/patrick/Desktop/VMware-workstation-5.0.0-13124.tar.gz

I unzipped it and there is a perl installer file but clicking it doesent do anything. (I tried run, and run in terminal.)

I decided to get this because I couldent find a way to open up qemu after installing it. I want to run windows 98 in ubuntu so I can do the windows things I need, and sine it is the one that needs the least RAM/Processing power out of the modern windows versions, I thought it would be good. (I dont think many applications work well with windows 95.)

I havnt asked a question in awhile, so, thanks alot =)

---

### Post by Stormy Eyes on 2005-09-09
You can't click it. You have to open a terminal, go to where the perl file is, and then run **perl $INSTALLERFILE**.

---

### Post by mlomker on 2005-09-09
You need to have kernel headers and the compiler installed.  Open Synaptic and download build-essential.  Then do a search for linux-headers.  You'll have to download the one that matches the kernel that you are running.  If you aren't sure which one, then you can run **uname -r** at a command prompt. 

Once you've got those installed then you can try the VMWare install.  Change to the correct directory from the command-line and then type **su** to sudo to the root login (same as your password).  Then you should be able to type **./vmware-install.pl** to start the install.  You should be fine if you take all of the default settings.

---

### Post by tageiru on 2005-09-09
[QUOTE=xequence]
I decided to get this because I couldent find a way to open up qemu after installing it. I want to run windows 98 in ubuntu so I can do the windows things I need, and sine it is the one that needs the least RAM/Processing power out of the modern windows versions, I thought it would be good.[/QUOTE]

Quick guide for running windows 98 in qemu:

# Create a disk image
qemu-img create win.img 3G (change 3G to your preferred size)

# Install windows
qemu -cdrom /dev/cdrom (or iso file) -hda win.img -boot d (add -user-net if you want network)

# Run windows
qemu -hda win.img -user-net

Easy as pie

---

### Post by xequence on 2005-09-09
> Quick guide for running windows 98 in qemu:

# Create a disk image
qemu-img create win.img 3G (change 3G to your preferred size)

# Install windows
qemu -cdrom /dev/cdrom (or iso file) -hda win.img -boot d (add -user-net if you want network)

# Run windows
qemu -hda win.img -user-net

Easy as pie 

I dont know if I have qemu installed right. I did it in synaptic, it said it needed to download 2 MB and use 7 MB of space. I heard somewhere it is more then that... Like 30 or something.

And the first command... The disk image, what is it? Does it create a virtual drive for win98 or something?

> You can't click it. You have to open a terminal, go to where the perl file is, and then run perl $INSTALLERFILE. 

How do I go to where the pearl file is with the terminal? I think ive heard something about a "cd" command to do that...

> You need to have kernel headers and the compiler installed. Open Synaptic and download build-essential. Then do a search for linux-headers. You'll have to download the one that matches the kernel that you are running. If you aren't sure which one, then you can run uname -r at a command prompt. 

Once you've got those installed then you can try the VMWare install. Change to the correct directory from the command-line and then type su to sudo to the root login (same as your password). Then you should be able to type ./vmware-install.pl to start the install. You should be fine if you take all of the default settings. 

I got the build essential ones. Ill get the headers also when I get back on my ubuntu computer :)


Ok, thank you for all the help everyone. I cant do it right now as I am not on my ubuntu computer (our family has two computers, one with XP, and one that is mine and has XP and ubuntu. We switch the internet so I can go on ubuntu a coupel hours or so a day. I often post from the XP computer but that stops me from doing things online on the XP/Ubuntu one.)

---

### Post by tageiru on 2005-09-09
[QUOTE=xequence]I dont know if I have qemu installed right. I did it in synaptic, it said it needed to download 2 MB and use 7 MB of space. I heard somewhere it is more then that... Like 30 or something.

And the first command... The disk image, what is it? Does it create a virtual drive for win98 or something?[/QUOTE]
No, 2mb is the correct size. The disk image is a big file where you create a filesystem for the os, probably what you mean by "virtual drive".

---

### Post by xequence on 2005-09-09
Yes, thats what I meant.

Funny how this was moved to absolute beginner talk... I am past a beginner yet I am just starting to learn this now. This is not for beginners in my opinion =O

> This particular forum is for people who are new to Linux or new to computers in general. If you have previous experience with Linux (even if it just a little bit) or you have ever used the command line in your life to do tasks, then please find the appropriate forum area for your question. 

Heh, some little things just annoy me ;)

And what about kqemu accelerator... I heard that qemu makes the guest OS 1/10th the speed of your processor. Thats very slow for me... 700/10=70. And it said somewhere that kqemu accelerator doesent work with windows 98...


Also, could I resize the disk image if I wanted later?

---

