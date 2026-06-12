---
title: "USB mouse problems"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by atmartin50 on 2007-04-01
Hello Folks,

I'm a new user of Ubuntu (6.10 Edgy), and the installation process (a dual-boot with XP) went off without a hitch (I think). It's very exciting to have entered the Linux world, I must say!

My main problem is that I'm having USB mice issues. Thinking that I should start out simply, I was using a Microsoft mouse for notebooks. Though it worked initially, it would quit after about a minute, and all 3 of my USB ports would be rendered unusable until I restarted my computer. 

I then decided to try my Logitech MX1000 laser mouse, which I hadn't used for several months. I was delighted to see that it could be used, but after about a half-hour, it unfortunately stopped responding. Curiously enough, it did not kill the other USB ports once it stopped working.

I found a great thread called Configuring Logitech mice (510x, etc.) which mentions my Logitech mouse quite a few times. The instructions look helpful, but they are a bit too technical for this Linux newbie, unfortunately. Could anyone help me by pointing me towards a simple and methodical approach to solving this problem? I really would like to avoid having to use my touchpad. At the very least, I'd like to be able to use my cheap little MS mouse.

Thanks in advance for any help!

---

### Post by 1/0 on 2007-04-01
Well, Logitech has their own drivers and don't seem to develop a GUI for GNU/Linux so I'm afraid that one has to do it the regular way. I don't have that kind of mouse but these guides explain how to install it in a more or less simple way. The first one discusses more than the second one. 

[http://www.thinkl33t.com/2006/09/logitech-mx1000-under-ubuntu-606lts-dapper-drake/](http://www.thinkl33t.com/2006/09/logitech-mx1000-under-ubuntu-606lts-dapper-drake/)

[http://blog.aaltonen.us/2005/08/26/logitech-mx1000-under-ubuntu/](http://blog.aaltonen.us/2005/08/26/logitech-mx1000-under-ubuntu/)

I'm not sure however why the USB ports stop working. Start by configuring the mouse first.

---

### Post by atmartin50 on 2007-04-06
Thanks a bunch, 1/0,

I'll try these links and report back. I hope I'm up to the task---this touch pad is killing me.

All the best!

---

### Post by mvaranda on 2007-04-14
My Toshiba was working fine with 6.06 but USB started freezing after upgrading to 6.10.

The fix that worked for my machine was the following:

sudo gedit /boot/grub/menu.lst

change boot option (red):

kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash [COLOR="Red"]noapic irqpoll pci=routeirq[/COLOR]

I hope it helps.
Take care

---

### Post by atmartin50 on 2007-04-18
Hi mvaranda,

First off, thanks for the reply---I'm eager to try it out! 

However, I do have one question. Which hd shall I edit? I'm scared to edit and save in this window, because when I used one of the methods listed above in this thread, I must have entered something where I shouldn't have, because I had a complete system crash and had to do a reinstall.

Here's what my info looks like after I entered the sudo command:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

Do I edit all of these, or just one? If I'm only to edit one of these, which one? Thanks so much in advance for your help!!! By the way, what is 'hd0,1' anyway? I see that hda1 is the XP side of my machine (which has been untouched for weeks now, haha:) )---so does it simply refer to my Ubuntu partition?

Thanks again! I'm looking forward to using a mouse again.

---

### Post by bagguley on 2007-04-18
Hey

Cant help with the logitec problems, I do however have a Microsoft intellimouse (wired version) which it took several crashes and alot of graft. There are alot of guides out there but the only one that actually worked was Thad Hopkins version. This is the link. Also very many other tips for new users.

[http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#codecs](http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#codecs)

Enjoy.

---

### Post by atmartin50 on 2007-04-19
Hi bagguley,

Thanks for the tip! However, I'm currently running Edgy 6.10 (though I plan to upgrade to Feisty 7.04 soon), and I noticed that on the top of the Thad Hopkins guide he assumes that you're running Feisty. Also, my wired mouse is a simple little Microsoft Notebook Optical Mouse (model 1020), and I saw that his instructions were for an Intellimouse. Due to these two discrepancies, I'm afraid to try his method for fear of messing up my system (again). What do you think?

Thanks a lot!

---

### Post by bagguley on 2007-04-19
Hey

I got my intellimouse to work fine with 6.10 with the instructions Thad gave. I would be carefull though using those instructions if your mouse is no t the same as the intellimouse as i managed to completely screw my system trying to get my mouse working with instructions that were apparently for the same model (but hey it only takes 25 mins to install ubuntu). I may try it if your mouse is similar to mine, have a look at [http://www.amazon.com/Microsoft-D58-00026-Intellimouse-Optical-Mouse/dp/B00005TQ08](http://www.amazon.com/Microsoft-D58-00026-Intellimouse-Optical-Mouse/dp/B00005TQ08)

Good luck, if i think of anything I'll either post or PM you.

---

### Post by bagguley on 2007-04-19
Ps. Update to feisty! It may solve your problems with nothing more than a simple update.

---

### Post by atmartin50 on 2007-04-21
Hi again bagguley,

Thanks for the Amazon link and the further advice! I checked out your mouse, and it seems slightly more upscale than my MS Notebook Optical mouse. Although there may be some similarities between the two, I don't dare try the instructions in the Thad Hopkins guide for fear of causing another system crash (however, you are right when you say that an Ubuntu re-install is quite a speedy thing).

Oh, and by the way, I just upgraded to Feisty. I plugged in my mouse, and managed to happily use it for about 10 minutes. Just when I thought the upgrade fixed all my problems, it died:( .

Any ideas? I sure appreciate your help and prompt replies! I could probably find an MS Intellimouse  for a sweet deal (I'm living in China), but I'd love to be able to use what I have.

Thanks again!

---

### Post by bagguley on 2007-04-21
Which version of feisty did you use to install? There was about 50KB of updates if i remember and I used the 15/04/07 pre-release as i couldnt wait and its worked fine. There was a problem with one of the beta updates that caused my system to crash very much like youre describing.

Anyway back to the point. If your mouse is working fine initially with feisty then Id say all you need to do is get feisty sorted and you're there!

Now if they could find some support for more USB phones..........

---

### Post by atmartin50 on 2007-04-24
Hi bagguley,

To be honest, I'm not sure which version of Feisty I installed (it was a day or two after the official version's release date)....I saw the link for an upgrade at the top of the Forums page and followed it. The process was smooth but took a couple of hours. I did not see anything mentioned about USB or mouse problems during the process, but then again, I did not have anything hooked up to my machine.

I still don't know how to go about solving this problem. I appreciate your input throughout. I think I'm just going to go bite the bullet and buy an Intellimouse and then follow the directions in the Hopkins guide since you said it works.

Thanks again and all the best!

---

### Post by atmartin50 on 2007-04-28
It appears that I am destined to not be able to use a mouse while running Ubuntu....

Rather than buying a MS Intellimouse, I shopped around for several hours in Hong Kong, and purchased a simple optical mouse made by Okion called a Lacion Lightning laser mouse. On the packaged was a picture of Tux, next the Windows logo and the Mac OS-X logo, under which was printed "powered by Linux." The shop owner also assured me that it should work with Linux.

Unfortunately, I'm back to square one. After 20-30 minutes of blissfully using a mouse and thinking that my problems were solved (also, I did a complete system re-install two nights ago....I now see how powerful the Terminal is, and how fat fingers can screw up a system!), it stopped working. 

Does anyone have any ideas? How can I find out if there is a USB port problem with my machine while running Ubuntu (I can use the mouse under XP, last time I checked)? Please help!

---

### Post by atmartin50 on 2007-05-01
Hi Folks,

I think I may have found my problem...now if I can just find a solution (hopefully with the help of you fine Ubuntu users out there:) ), I'll be as happy as a clam!

After I power on the machine, right after Grub does its thing, and just before the Ubuntu startup screen, I'm seeing a message which reads:

MS BIOS error 8254 not connected to timer IO-APIC 
(I'm pretty sure this is it, as it only appears for a moment)

This message seems to ring a bell from other posts I've read in the forum describing similar mouse problems. Any ideas? Thanks SO much in advance!

---

### Post by atmartin50 on 2007-05-02
Hi all,

Correction to my last post....that message should read:

MP BIOS error 8254 not connected to timer IO-APIC

I hope to hear from someone soon! I'm out of ideas](*,) 

Thanks!

---

### Post by atmartin50 on 2007-05-02
PROBLEM SOLVED!!!:) 

Here's a link describing what to do:

[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

It's a simple fix to a frustrating problem! I hope this helps anyone else out there experiencing the same problems.

---

