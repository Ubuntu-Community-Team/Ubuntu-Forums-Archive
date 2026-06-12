---
title: "Boot Loader and Wireless Questions"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by GMFreak8 on 2006-05-11
I'm completely new to Linux and Ubuntu, although I've had the install CD for awhile now.  I tried installing it on my Laptop but the graphics wouldn't work and I gave up.  Since then I've acquired a fairly new AMD Athlon Compaq Presario 8000z-8QSXE1, and dual booted Windows XP Professional, and Ubuntu 5.10.

The installation went smoothly, and upon booting into Ubuntu for the first time, the updater popped up on the screen, so I went ahead and updated everything, and restarted...  When the boot loader screen comes up, I now have two versions of Ubuntu, and Windows XP on the screen as selections.  I'm completely new as I've said, and I'm just wondering if this is normal, and if so, is there anyway to get rid of the old entry or install (I can't figure out if the two entries are completely different Ubuntu versions, or if they are just two entries that boot into the same install), and just have the newest version listed on the boot screen?  I know it's a minor detail, but it's kinda annoying (I'm a perfectionist when it comes to organization and presentation). 

Now for my second question.....

I have a TRENDnet (TRENDware) wireless PCI card model number TEW-423PI installed into the computer.  When I open up the Network Settings dialog, wireless is listed as one of the connection options, and I can go into properties, enter my wireless routers SSID and activate the connection, it appears to activate, but doesn't connect to the network (I have no WEP, WPA or Mac address security settings turned on in my Router settings).  Now, I figured that because the wireless network card entry shows up in the Network Settings dialog that the driver for the wirelesss network card is already installed.  Am I right to assume this?  Just incase the driver isn't installed, I installed the ndiswrapper-utils package using the Synaptic Package Manager, and apparently this is supposed to install an entry in the administration area called Windows wireless drivers, but I can't find that entry.  From here on, I'm completely lost.  I saw something about using the ternminal too, but I can't figure that thing out for the life of me.

This is really my first true attempt at using Linux, so I'm sorry if these questions are asked a lot, and if I sound like a complete idiot.:oops: 

Hopefully someone here can point me in the right direction, or walk me through what to do.  Also maybe point me to a guide that shows me how to use the terminal, and explains the organization and basics of the file system, and whatnot.  Like where the programs are installed, how to install programs such as flash, java, and update programs like FireFox.  Anyway, hopefully you guys can help me.  I appreciate it. :)

---

### Post by TeeAhr1 on 2006-05-11
[QUOTE=GMFreak8]When the boot loader screen comes up, I now have two versions of Ubuntu, and Windows XP on the screen as selections.  I'm completely new as I've said, and I'm just wondering if this is normal, and if so, is there anyway to get rid of the old entry or install (I can't figure out if the two entries are completely different Ubuntu versions, or if they are just two entries that boot into the same install), and just have the newest version listed on the boot screen?[/QUOTE]
This is normal.  If you look at the kernel versions listed there, it's your most current kernel and the version just previous.  This is in case a kernel upgrade messes you up.  I've never had to use the option, but it's nice to know it's there.

> Now for my second question..... (wireless)
No idea.  Hope someone can help you here.

> Also maybe point me to a guide that shows me how to use the terminal, and explains the organization and basics of the file system, and whatnot.  Like where the programs are installed, how to install programs such as flash, java, and update programs like FireFox.  Anyway, hopefully you guys can help me.  I appreciate it. :)
There are lots of great general tutorials [here]("http://www.tuxfiles.org/linuxhelp/cli.html"), as far as using the command line and the way your file system is organized.  [This]("http://www.linuxcommand.org/") is also one of my favorite sites, and helped me a lot (I still refer to it from time to time).  I'm sure others can give you loads of other links.

Once you're ready to start installing new apps and really start breaking stuff :p come back and post a new thread.  I'm a big believer in the "one question/set of questions per thread" rule, that makes it easier to process info and easier for people to search old threads later.  Best regards, and welcome to the other side!

-pete

---

### Post by jorn on 2006-05-11
This is regarding your boot options. Yes, you can get rid of the old entries on the boot loader. Open your terminal. Applications>Accessories>Terminal. Type:
sudo sudo gedit /boot/grub/menu.lst 
That brings you to the file that is responsible for the what you see on the boot loader screen.
The last entries are listet next to the botton. But a # in front of the lines and they will not show up.
Remember to save after editing.
Make a backup of the file in case of...
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
Example:

# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro

---

### Post by GMFreak8 on 2006-05-11
Wow, thanks guys, quick replies.

Leaving the entries there, does that mean I basically have two Ubuntu installs, or is it for lack of a better comparison like Windows system restore?  Will both versions have my most current programs and settings or is the older one basically frozen in time from when I upgraded to the new kernel?  Am I using more space keeping both entries there?

If I do decide to delete the entry (if I can figure out the command line and terminal), will that just erase mention of the old kernel and will it still be installed, and accessible in some other way, or will it also get rid of all traces of it?

What way would you guys recommend?  Should I just leave it, will it cause any problems down the road?  Will I eventually have a huge list of old kernels to boot into if I keep installing the upgrades?  What I'd really like to do is just uninstall the old kernel and delete the boot option, if that's at all possible.

Hopefully that made sense.  So much to learn, I feel overwhelmed just getting everything setup to make it useable, but I'm sure I can work through it, just as long as you guys don't mind these questions.

I've read so much information on the wireless connection, it's all blending together now, I think I'm more confused than I was. 8-[ :lol:

---

### Post by jorn on 2006-05-11
> If I do decide to delete the entry (if I can figure out the command line and terminal), will that just erase mention of the old kernel and will it still be installed, and accessible in some other way, or will it also get rid of all traces of it?
They are still accessible.
If the kernelupgrade is't funtion in some way, you can decide to use an older one. I would leave them as they are. I don't know how much room they use.

You can use a grafic layout to access the menu.lst. Type in terminal:
gksudo nautilus
Be careful, you are root.
To remove old kernels you must ask someone else.

---

### Post by chettyk on 2006-05-11
[QUOTE=GMFreak8]
I've read so much information on the wireless connection, it's all blending together now, I think I'm more confused than I was. 8-[ :lol:[/QUOTE]

We have all gone through that phase when Linux seems like an impossible mountain to climb. Since you have dual-boot system, take a break when you feel overwhelmed and then come back later and have another shot at the problem.

When I googled "ubuntu TRENDnet", I found the following post:
[http://www.ubuntuforums.org/archive/index.php/t-76600.html](http://www.ubuntuforums.org/archive/index.php/t-76600.html)

The post appears to suggest that the the trendNet site has a 32 bit driver that you could use with ndiswrapper. Maybe you chould check that out.

Good luck!

---

### Post by chettyk on 2006-05-11
By the way, if you haven't done so already, maybe you could take a look at Ubuntu Wiki's "Wireless Troubleshooting Guide":
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by TeeAhr1 on 2006-05-11
[QUOTE=GMFreak8]Leaving the entries there, does that mean I basically have two Ubuntu installs, or is it for lack of a better comparison like Windows system restore?  Will both versions have my most current programs and settings or is the older one basically frozen in time from when I upgraded to the new kernel?  Am I using more space keeping both entries there?
*snip*
What way would you guys recommend?  Should I just leave it, will it cause any problems down the road?  Will I eventually have a huge list of old kernels to boot into if I keep installing the upgrades?  What I'd really like to do is just uninstall the old kernel and delete the boot option, if that's at all possible.[/QUOTE]
AFAIK, it's the same session running on the previous kernel.  And no, you will not end up with a huge list of kernels; it'll always be your present and immediately previous kernels.

---

### Post by GMFreak8 on 2006-05-11
[QUOTE=chettyk]
When I googled "ubuntu TRENDnet", I found the following post:
[http://www.ubuntuforums.org/archive/index.php/t-76600.html](http://www.ubuntuforums.org/archive/index.php/t-76600.html)

The post appears to suggest that the the trendNet site has a 32 bit driver that you could use with ndiswrapper. Maybe you chould check that out.

Good luck![/QUOTE]

Yeah, I found that post too.  I have the install CD with the driver on it for the PCI wireless card, but upon looking at the wikipedia list of compatible drivers (I don't know how updated it is), the Windows driver in Linux isn't capable of using WEP or WPA, and only runs in 11Mbps mode.  It's better than nothing though.

Can anyone give me any advice on how to go about using NDisWrapper, and where to find and how to install ndisgtk, and the NDisWrapper-utils.  I thought I installed it (ndiswrapper-utils) using the synaptics utility, but the entry in "administration" isn't there.  And I don't know where to even find ndisgtk. ](*,) 

I'm sorry about all these questions, but how do you install and update programs?  I'm trying to update FireFox to the latest version, and I have no clue where to start on that either.  I've read the guides, but they didn't help much.  Again thanks for the help, and patience.

---

### Post by GMFreak8 on 2006-05-11
[QUOTE=TeeAhr1]AFAIK, it's the same session running on the previous kernel.  And no, you will not end up with a huge list of kernels; it'll always be your present and immediately previous kernels.[/QUOTE]


Thanks for the information.  I guess I'll just leave it like it is.  It's not hurting anything, just doesn't look as clean.

---

### Post by GMFreak8 on 2006-05-11
I keep getting a error message whenever I try to copy the wireless driver to the ndiswrapper folder.  The error says "you do not have permission to write to this folder".  How do I get permission?

---

### Post by GMFreak8 on 2006-05-11
Sorry for the multiple posts....

OK, so I somehow managed to get passed the denied access, I managed to install ndisgtk, and managed to get the "Windows Wireless Network" gui to show up, now it's a matter of getting it to recognize my card.  It keeps saying hardware isn't present.  God, this is so damn frustrating.  I manage to learn how to solve one problem, and another pops up.  grrr.  Is there any wireless experts here, before my computer ends up at the bottom of the nearest lake! :lol:

---

### Post by catlett on 2006-05-11
You can remove the old kernel with synaptic package manager. It will be listed like any other entry. Just highlight it and choose uninstall. You have 1 ubuntu system installed but 2 linux kernels installed. You don't need more than one. Since you like things orderly, once you start your system with the new kernel and you know nothing is going wrong with the new kernel, you can uninstall the old kernel. The above post about sudo gedit /boot/grub/menu.lst will remove the option from the grub menu but the kernel will still be on your hard drive. 
This recent post had people posting there favorite how to sites [http://www.ubuntuforums.org/showthread.php?t=171491](http://www.ubuntuforums.org/showthread.php?t=171491) I bookmarked it for later reference, thought you might be interested as well. Good luck.

---

### Post by GMFreak8 on 2006-05-11
[QUOTE=catlett]You can remove the old kernel with synaptic package manager. It will be listed like any other entry. Just highlight it and choose uninstall. You have 1 ubuntu system installed but 2 linux kernels installed. You don't need more than one. Since you like things orderly, once you start your system with the new kernel and you know nothing is going wrong with the new kernel, you can uninstall the old kernel. The above post about sudo gedit /boot/grub/menu.lst will remove the option from the grub menu but the kernel will still be on your hard drive. 
This recent post had people posting there favorite how to sites [http://www.ubuntuforums.org/showthread.php?t=171491](http://www.ubuntuforums.org/showthread.php?t=171491) I bookmarked it for later reference, thought you might be interested as well. Good luck.[/QUOTE]


Oh cool, I didn't know that about the synaptics manager (like I would anyway).  Thanks for the info.  I've been slowly reading all the guides as I go along trying to solve this wireless problem.  Everyone has been such a tremendous help, I truly appreciate it. :)


BTW, this was my first post from Ubuntu.  WOOOO

---

### Post by GMFreak8 on 2006-05-11
Here's what I've got so far:

[[IMG]http://img115.imageshack.us/img115/8834/screenshot4vq.th.png[/IMG]](http://img115.imageshack.us/my.php?image=screenshot4vq.png)

---

