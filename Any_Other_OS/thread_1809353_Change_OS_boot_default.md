---
title: "Change OS boot default"
date: 2011-07-21
forum: Any Other OS
---

### Post by woodeye3 on 2011-07-21
HI 
I've got Ubuntu 10.10 and win7 on 2 partitions of a hard drive

This computer has been my toy until the household pc broke.

Now I need to use this pc as our only pc until I get the other one working

Right now Ubuntu is the default OS that boots 

My wife doesn't want to use Ubuntu, she uses Win7

I know I can show her how to choose the OS during the boot up processes but it would be easier to just change the boot default to Win7 and I'll change it when I want to boot into Ubuntu

How do I change the default boot OS

More detailed steps are best as I have only a basic computer background and it's been a while since I was into the guts of my computer

Thanks Jeff

---

### Post by Bucky Ball on 2011-07-21
[Grub Customizer]("http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.htmlCustomizer") is your friend.

Start-up Manager apparently does the job as well, but some have complained that changes aren't sticking. ;)

---

### Post by woodeye3 on 2011-07-21
Thanks for your response
I clicked on Grub Customizer and got a message that the page couldn't be found
Any other suggestions

I was reading around and saw at "absolute beginners talk" a post from WA3ERQ Jim ABOUT 40 MIN AGO RE A SIMILAR SITUATION HE IS HAVING WITH 11.04
I read the responses but they're over my head
I also googled "how to change which os boots as default and was directed to HOW-TO-GEEK
There they said something about "sudo gedit/boot/grub/menu.1st" and changing the default number
It sounded alot like the post in beginners talk but still over my head
Does any of this make sense to you

---

### Post by drs305 on 2011-07-21
Click the 'Customizer' link in my signature line. That should work and will describe the way GC works. From there, the link to the Launchpad site works, although I didn't try the actual download.

To edit the Grub files manually, you can click on the 'Tasks' link.

---

### Post by woodeye3 on 2011-07-21
well now I screwed it up
I tried to install grub-customizer ran into some problems and now I can't boot into win7 at all
Windows tries to repair it'self and can't.
I tried system restore but no luck
So I put the windows7 disk in thinking that I would format the drive and start over but now when I choose windows in the loader it says "windows is loading files", repair starts, says cannot repair comp automatically, I click finish and computer shuts down
I can still boot into ubuntu 
How do I just wipe out the drive and start over
Jeff

---

