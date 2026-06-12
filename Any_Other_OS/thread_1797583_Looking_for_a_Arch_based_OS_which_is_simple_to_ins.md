---
title: "Looking for a Arch based OS which is simple to install"
date: 2011-07-05
forum: Any Other OS
---

### Post by DeadlyAlex0 on 2011-07-05
Hello there,

Anybody know any good Arch based OS's which are easy to install?
(I would install the main Arch OS but last time I tried I completely failed!:mad:)

---

### Post by handy on 2011-07-05
The benefit of following the [**_Beginners' Guide_**]("https://wiki.archlinux.org/index.php/Beginners%27_Guide") (to the letter) is that it gives you a hands on introduction on how Arch works. Which imho is a necessity, as Arch is different.

If you do end up installing Arch, (whichever way) I've got some how-to's which provide extremely useful knowledge especially when you are just starting out with Arch. They can be found in the following link, they are the last three on the page; look for **[Arch]** at the beginning of the thread title:

[http://spiralinear.org/forum/viewforum.php?f=17](http://spiralinear.org/forum/viewforum.php?f=17)

---

### Post by Perfect Storm on 2011-07-05
Where did you fail installing Arch? It would be better to find a solution to your problem.

---

### Post by shobon on 2011-07-05
The best part of Arch is installing it and setting it up yourself. Having a prebuilt Arch distro would ruin the experience.

---

### Post by el_koraco on 2011-07-05
Stuff is kinda different with Arch as opposed to most distros. When you install Ubuntu, you get a ready made system and learn stuff as you go along. With Arch, you learn most of the stuff while installing it, so you're mostly ready to hit the road once it's installed. You'd probably be better off trying to install it a couple of times.

---

### Post by mips on 2011-07-05
There's Archbang & Chakra but I suggest you go vanilla Arch.

---

### Post by snowpine on 2011-07-05
Welcome to the forums!

Arch is a distro that "helps those who help themselves."
Respectfully, it is a warning sign to me that you signed up for Ubuntu Forums specifically for help with Arch. Why not sign up for the Arch forums and post *specifically* where you ran into problems with the install process? They can help you get Arch installed... Be prepared to answer questions like: "Which step of the Beginner's Guide are you stuck at? What have you tried so far? What are the exact error messages?"

To answer your specific question, installing the "Arch way" using the Beginner's Guide is part of the fun. I don't recommend any of the "easy to install" Arch alternatives.

Good luck!

---

### Post by kazuya on 2011-07-06
I would recommend the latest archbang distro. This is the fastest way to have a ready to use archlinux installation with GUI desktop environment already there along with flash, chrome, and all other base things you would need.
 
It sort of takes you through a similar path as archlinux, but I find it much more functional out the box.
 
The installer is a little like arch. It is text-based. I believe.
 
Chakra is the easiest to install, but it has steered off arch slightly. Chakra is KDE-centric with an easy to use gui package manager front-end like synaptic (debian) for installing packages.
 
I prefer archbang since it is a faster install, totally compatible with archlinux, starts out with openbox as Desktop environment and community while small is very friendly. More importantly, I can add other things. 
 
I was frustrated in the beginning with updating system first time after installation. Now I am so used to it that I do not skip a beat.
 
(1) pacman -Syu - sadly you have to upgrade pacman first.
(2) You are forced to pacman -R X(name of troubling package)
(I merely copy and paste error message to google browser - and voila I see answers)
 
(3) In the install steps, when asked to edit configurations in nano/vim , I type Ctrl+X and then type "y" for yes.
 
It may be a good idea to get familiarized with archlinux install first as it would make you appreciate archbang more. Another key thing is that archbang includes packer along with pacman. packer is great as it serves as a wrapper or front-end for AUR as well as pacman.
AUR is the access to all the other bundles of community softwares not normally accessible by pacman. It is a life saver.
 
(4) I replaced slim with gdm so I can automagically have other new DE s show up.
(5) Nvidia install was tricky as with typical archlinux install. REFER TO ARCH WIKI GUIDE
 
Good luck.

---

### Post by handy on 2011-07-06
I think ArchBang is great for people that are already familiar with Arch, as it is a quicker primary install. It still doesn't teach a new Arch user about Arch like using the Beginners' Guide does. Which means that it will take a new user longer to understand how this new system works.

Courses for horses of-course... ;)

---

### Post by Bart_D on 2011-07-07
These are some Arch Linux installation videos:

[http://www.youtube.com/watch?v=PlO876LT66k](http://www.youtube.com/watch?v=PlO876LT66k)
[http://www.youtube.com/watch?v=UV0krka1hn4&feature=related](http://www.youtube.com/watch?v=UV0krka1hn4&feature=related)
[http://www.youtube.com/watch?v=RjTTl_9aUXc](http://www.youtube.com/watch?v=RjTTl_9aUXc)

WARNING: Do NOT follow these videos blindly since YOUR hardeare WILL be different from that of the people who posted these videos. If you follow it blindly, and then experience problems, you will only have YOURSELF TO BLAME.

Oh, by the way, telling someone to go BACK and re-read the Arch Linux Beginner's Guide is NOT helping them. Most of the people who post these sorts of questions are beginner-average Linux users....we are NOT geniuses like the rest of you. We do not find that suggestion to be very helpful AT ALL!

---

### Post by snowpine on 2011-07-07
> **Bart_D said:**
> Oh, by the way, telling someone to go BACK and re-read the Arch Linux Beginner's Guide is NOT helping them. Most of the people who post these sorts of questions are beginner-average Linux users....we are NOT geniuses like the rest of you. We do not find that suggestion to be very helpful AT ALL!

I disagree. It is called the "Beginners Guide" for a reason. :)

---

### Post by kvv_1986 on 2011-07-07
I am kinda stuck in the first step itself. :(

When I go to set up custom partitions, it gives me a huge list of choices and unfortunately I don't know what they are and what to choose. For instance, some of the choices are Linux, Solaris, Swap (I know what this is) etc.

What do I choose to get a btrfs root partition?

---

### Post by snowpine on 2011-07-07
> **kvv_1986 said:**
> I am kinda stuck in the first step itself. :(

When I go to set up custom partitions, it gives me a huge list of choices and unfortunately I don't know what they are and what to choose. For instance, some of the choices are Linux, Solaris, Swap (I know what this is) etc.

What do I choose to get a btrfs root partition?

At the risk of angering Bart_D ;) you want "Type 83 Linux" (Type 82 for swap) as described here:

[https://wiki.archlinux.org/index.php/Beginners'_Guide#Partition_Hard_Drives](https://wiki.archlinux.org/index.php/Beginners'_Guide#Partition_Hard_Drives)

Instructions for btrfs are also included. :)

---

### Post by kazuya on 2011-07-07
> **Bart_D said:**
> These are some Arch Linux installation videos:
 
[http://www.youtube.com/watch?v=PlO876LT66k](http://www.youtube.com/watch?v=PlO876LT66k)
[http://www.youtube.com/watch?v=UV0krka1hn4&feature=related](http://www.youtube.com/watch?v=UV0krka1hn4&feature=related)
[http://www.youtube.com/watch?v=RjTTl_9aUXc](http://www.youtube.com/watch?v=RjTTl_9aUXc)
 
WARNING: Do NOT follow these videos blindly since YOUR hardeare WILL be different from that of the people who posted these videos. If you follow it blindly, and then experience problems, you will only have YOURSELF TO BLAME.
 
Oh, by the way, telling someone to go BACK and re-read the Arch Linux Beginner's Guide is NOT helping them. Most of the people who post these sorts of questions are beginner-average Linux users....we are NOT geniuses like the rest of you. We do not find that suggestion to be very helpful AT ALL!
 
I totally agree with you Bart and a big thanks for these video link ups.

---

### Post by mips on 2011-07-07
> **Bart_D said:**
> 
Oh, by the way, telling someone to go BACK and re-read the Arch Linux Beginner's Guide is NOT helping them. Most of the people who post these sorts of questions are beginner-average Linux users....we are NOT geniuses like the rest of you. We do not find that suggestion to be very helpful AT ALL!

> **kvv_1986 said:**
> I am kinda stuck in the first step itself. :(

When I go to set up custom partitions, it gives me a huge list of choices and unfortunately I don't know what they are and what to choose. For instance, some of the choices are Linux, Solaris, Swap (I know what this is) etc.

What do I choose to get a btrfs root partition?

You don't need to be a genius, you just need to follow the guide.

[https://wiki.archlinux.org/index.php/Beginners%27_Guide#Prepare_Hard_Drive](https://wiki.archlinux.org/index.php/Beginners%27_Guide#Prepare_Hard_Drive)

> Choose New -> Primary and enter the desired size for root (/). Put the partition at the beginning of the disk.
**Also choose the Type by designating it as '83 Linux'**. The created / partition shall appear as sda1 in our example.

And a few lines further on it says,

> Set Filesystem Mountpoints
Specify each partition and corresponding mountpoint to your requirements. (Recall that partitions end in a number. Therefore, sda is not itself a partition, but rather, signifies an entire drive)
Filesystem Types
Again, a filesystem type is a very subjective matter which comes down to personal preference. Each has its own advantages, disadvantages, and unique idiosyncrasies. Here is a very brief overview of supported filesystems:

---

### Post by kvv_1986 on 2011-07-07
Thank you! Guess I should actually rtfm. It is indeed given there quite clearly.

I am doing a trial run in Virtualbox before actually doing it on my laptop. :P

---

### Post by handy on 2011-07-07
> **kvv_1986 said:**
> Thank you! Guess I should actually rtfm. It is indeed given there quite clearly.

I am doing a trial run in Virtualbox before actually doing it on my laptop. :P

With Arch it is not a matter of "***_guess_*** I'll rtfm", if you don't follow the Beginners' Guide to the letter (& read further into topics on the Arch Wiki if required - unlikely) you will fail. Unless you are a very experienced distro/BSD user.

---

### Post by mips on 2011-07-08
> **handy said:**
> With Arch it is not a matter of "***_guess_*** I'll rtfm", if you don't follow the Beginners' Guide to the letter (& read further into topics on the Arch Wiki if required - unlikely) you will fail. Unless you are a very experienced distro/BSD user.

+1

I started a fresh install on my laptop 2 days ago and due to being rusty I had to consult the wiki. I noticed the beginners guide has undergone a lot of changes from when last I looked at it.

---

### Post by handy on 2011-07-08
> **mips said:**
> +1

I started a fresh install on my laptop 2 days ago and due to being rusty I had to consult the wiki. I noticed the beginners guide has undergone a lot of changes from when last I looked at it.

I think we owe Misfit138 a debt of gratitude for the consistent work he puts in behind the scenes over there.

---

### Post by FormatSeize on 2011-07-08
I was going to ask what was so hard about installing Arch Linux (I haven't tried it yet), but after seeing what's involved, I think I got my answer. My new question is: is Arch, as a distro, "worth" the hassle of the installation process? Or is it more of a 'congratulations, you are officially Good At Linux' sort of thing?

---

### Post by snowpine on 2011-07-08
> **FormatSeize said:**
> I was going to ask what was so hard about installing Arch Linux (I haven't tried it yet), but after seeing what's involved, I think I got my answer. My new question is: is Arch, as a distro, "worth" the hassle of the installation process? Or is it more of a 'congratulations, you are officially Good At Linux' sort of thing?

Only you can make that decision for your needs. 

If you have a fast internet connection, well-supported hardware, and a pot of coffee, you should be able to install Arch in an afternoon. If you learn something and/or spend a few hours enjoying your hobby and/or end up with a finished install you're happy with, then yes, I think it is worth it. :)

---

### Post by mips on 2011-07-08
> **FormatSeize said:**
> My new question is: is Arch, as a distro, "worth" the hassle of the installation process?

Only you can answer that.

---

### Post by el_koraco on 2011-07-08
Haven't tried to install it, but from what I've seen, the install process doesn't seem to be hard for a user who's had like a year's worth of experience with Linux.

---

### Post by wojox on 2011-07-08
> **FormatSeize said:**
> My new question is: is Arch, as a distro, "worth" the hassle of the installation process?

It's not a hassle. It's a learning experience. :p

---

### Post by FormatSeize on 2011-07-08
> **snowpine said:**
> If you have a fast internet connection, well-supported hardware, and a pot of coffee, you should be able to install Arch in an afternoon. If you learn something and/or spend a few hours enjoying your hobby and/or end up with a finished install you're happy with, then yes, I think it is worth it. :)
Well, then. I guess it is worth it. The learning part is what's fun for me, as I do computers as a hobby, so I think I'll try it out (don't know about the one afternoon part, though).

---

### Post by handy on 2011-07-08
The installation is your 1st initiation into Arch. After that there is more to learn & it takes a while to get used to it.

Some people find they really don't like it. Others (like me :)) go ah! Home at last.

For me, Arch is the lowest maintenance easiest OS I've ever used, which suits me fine as I'm a really lazy user these days.


Whatever happens whether you like it or not, you will get a good dose of learning.

---

