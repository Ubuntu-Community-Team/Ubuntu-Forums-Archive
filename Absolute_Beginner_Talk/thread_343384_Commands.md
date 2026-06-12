---
title: "Commands"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by opus_az on 2007-01-21
Hello...

I'm considering installing Ubuntu for my home computer and I'm curious which command line tasks I should learn? Assuming the install goes smoothly and all my hardware works correctly, is there really a need for the novice home user to use command lines frequently?

I've played around with an ISO but just to get an idea of the interface. I'm a long-time Windows user with limited exposure to Macs. I use the command prompt in Windows but usually just for network info or ftp. I've built a few scripts but they're all for business use.

Really, I'm just tired of Windows vulernability to spyware and viruses. My needs at home would be almost entirely browsing and email and watching DVDs. I'll probably use Parallels for WinXP but just for a few work apps.

Is there a site that you can recommend that runs though commands that any new user should know?

TIA,
O.

---

### Post by Mystere on 2007-01-21
In all honesty, I've been using Ubuntu fine for several months with basically no knowledge of the command line.  If you *want* to learn them you can check out the documentation at help.ubuntu.com

---

### Post by bulldog on 2007-01-21
You can use your ubuntu,basically without the command line.
But you'll soon find out how easy it is to use,and how much more power full instead of a GUI based app.

Just install Ubuntu and give it a go,and see how long it takes till you want to use the command line as well :lolflag: 

To learn some commands,

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

[http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by opus_az on 2007-01-21
Excellent. =D> That's exactly what I was hoping to hear.

---

### Post by zerhacke on 2007-01-21
> **opus_az said:**
> Hello...

I'm considering installing Ubuntu for my home computer and I'm curious which command line tasks I should learn? Assuming the install goes smoothly and all my hardware works correctly, is there really a need for the novice home user to use command lines frequently?

I've played around with an ISO but just to get an idea of the interface. I'm a long-time Windows user with limited exposure to Macs. I use the command prompt in Windows but usually just for network info or ftp. I've built a few scripts but they're all for business use.

Really, I'm just tired of Windows vulernability to spyware and viruses. My needs at home would be almost entirely browsing and email and watching DVDs. I'll probably use Parallels for WinXP but just for a few work apps.

Is there a site that you can recommend that runs though commands that any new user should know?

TIA,
O.

There's really little need for commandline stuff in Ubuntu if you don't actually want to use them.  Sure, in the future you may need to do a LITTLE command line stuff to edit repositories, but out of the box it should work just fine with little to no command line stuff.  If all you're doing is browsing and email you'll never need to touch the command line.  To enable DVD playback you may need a little command line interaction but that's a one shot deal.

---

### Post by Pobega on 2007-01-21
I've noticed that DEs like Gnome and KDE are heavily focused on visualization. Personally I use Xfce because I find the terminal is so much easier.

So you want to move a file to /usr/bin so that you can run it universally? You can either open up two windows as root and drag and drop the file, or you can do it easy:> sudo mv executable /usr/bin

Though in the end it's all about opinions, but if you just hang around the community you can learn how to use the terminal.

Also you might like to know the basics so:

> cd - change directory
man <command> - Displays a manual about <command> (man cd would show a manual about using cd, for example)
ln - creates a shortcut
cp - copy
mv - move
rm - remove
lspci - shows all attached devices
grep - search results for a phrase
Grep is a special command, that joins another command. For example if you're looking for your wireless card, you would do: lspci | grep Wireless. So the terminal does lspci, and uses grep to search through all of the results for Wireless.

---

### Post by jd65pl on 2007-01-21
Here are some simple commands [http://jamie.dumbill.googlepages.com/ubuntucommands2](http://jamie.dumbill.googlepages.com/ubuntucommands2)

---

### Post by old_geekster on 2007-01-21
I have only been using Ubuntu 6.10 Edgy Eft for three days.  I grew up with DOS so I have a good knowledge of commands with M$, but as stated previously, I could truly get by without using commands.  M$ DOS was an off-shoot of Unix, also.  So the commands are somewhat close in structure.  The way I eliminate the need for commands during this learning curve, however, is by copying the commands and pasting them into the "Terminal".  It works great.

Here is the best site that I have found for help with commands:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I have used it for many of the programs I want to try.

---

