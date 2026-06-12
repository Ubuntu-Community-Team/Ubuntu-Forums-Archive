---
title: "Vista won't start! Help needed"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by eddie_gordo on 2007-10-27
Hi there..

I'm completely noob on Ubuntu and all Linux... But today I tried to install Ubuntu 7.10 as it looked nice in the LiveCD. I installed it and everything went ok! The only problem is that now I cannot boot into Vista.. When I choose Vista Loader in the grub, my laptop just restarts and goes back to grub again... Anyway I can fix this? I'm freeking out here as I really don't know what to do!

Thanks in advance!

---

### Post by wheredidrealitygo on 2007-10-27
Do you still have your Vista DVD?

Or even the "anytime upgrade" DVD?

Either should work, if you insert it, and boot the installer, don't go into the installer itself, but there's a "system repair" section, it has a way of repairing startup.

You WILL however have to reinstall GRUB (for booting into Linux, if you still want to that is).

---

### Post by eddie_gordo on 2007-10-27
And how do I reinstall Grub after that? I'm really a noob... :P And if I reinstall it then, won't the problem appear again?

I read about the [SuperGrubDisc]("http://supergrub.forjamari.linex.org/"), would it help in my case? Would I still have to reinstall grub?

Thank you

Edit: Oh, and repairing Vista boot won't affect any of my files or anything? It just repairs the boot? Thanks again

---

### Post by wheredidrealitygo on 2007-10-27
Repairing Vista boot does just that, repairs the boot.

SuperGrubDisc is exactly what you would be wanting, but it has to be done in the order of

1. Vista boot repair
2. SuperGrubDisc

Not the reverse.

Vista will overwrite Grub, but not the reverse.

Repost if you need any help or are unsure of which option to pick in Vista, I've not used the supergrubdisc (only reinstalled grub with my Ubuntu cd itself) so I can't help on that front, but I'm sure it's straightforward.

No prob ;)

---

### Post by eddie_gordo on 2007-10-27
Thank you, I'll just have to look for my Vista DVD and I will try it and then post here again!

---

### Post by wispygalaxy on 2007-10-27
Hi, will this help?  It sounds similar to what you are going through:

[http://ubuntuforums.org/showthread.php?t=405515](http://ubuntuforums.org/showthread.php?t=405515)

Good luck!  :KS

---

### Post by eddie_gordo on 2007-10-27
> **wispygalaxy said:**
> Hi, will this help?  It sounds similar to what you are going through:

[http://ubuntuforums.org/showthread.php?t=405515](http://ubuntuforums.org/showthread.php?t=405515)

Good luck!  :KS

That is a similar problem, but not quite the same... 

Meanwhile, I tried the repairing through Vista DVD, and it won't repair... The only option available is automatic repair, and somehow it doesn't recognize the problem, doing nothing at all!

Now I tried through SuperGrubDisk, and I already boot into Vista, but I still didn't fix the problem (I think!).. There's just some option in SGD that lets us boot from one chosen partition... I'll try to fix the problem through SGD now... Then I'll let u know if I fixed it!

Thanks guys.. :)

---

### Post by eddie_gordo on 2007-10-28
I'm freeking out really here! I ran the SGD, it uninstalled the Grub, and fixed windows boot, but it won't boot! Some prompt appears sayin' "Windows 98 is starting", or something like that! Now I just can boot to Windows through the SGD application, otherwise nor Windows nor Ubuntu! 

HELP! I don't know what to do!! :(

Edit: It says:

> Starting Windows 98...
Type the name of the Command Interpreter (e.g., C:\WINDOWS\COMMAND.COM)
A>

---

### Post by wheredidrealitygo on 2007-10-28
Try this:

load your vista dvd, upon boot, go to "repair your computer" on the bottom left, then go to "open a command prompt"

Type:```
 bootrec.exe /FixMbr
```

Case sensitive.

Refer to [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392") for more info on this particular tool (you may want to print it) than I feel like typing lol. But you should be fine with the code I typed above. (I tested it in a VM and worked fine)

Then, if you can only boot into Windows Vista afterwards (which is to be expected) run the supergrub disc again to restore Linux and let me know.

---

### Post by eddie_gordo on 2007-10-28
Well I managed myself to get to automatically boot Vista... Through one of the options on the SuperGrubDisk, it was trying to boot from another partition that not the one from Vista... As it is a laptop, it was trying to boot from the recovery partition from Asus. Somehow I managed to set this partition manually and now it boots directly to Vista! :) I'm kind of afraid to restore Linux again and it all happens again... Yeah, I'm supposed to know how to fix it now, but it has just scared the crap out of me! :)

Maybe tomorrow I'll try that... Because the Linux partitions don't appear in Vista and I want to recover that information there...

Thanks everyone! Tomorrow I'll give you guys some updates! :)

---

### Post by wheredidrealitygo on 2007-10-28
Glad you figured it out (for now) !!

[http://www.fs-driver.org/download.html]("http://www.fs-driver.org/download.html")

That's a link to a program called Ext2 IFS for Windows. While ugly, it's functional, and  it'll allow you to extract all of the information/files you may have saved to your Linux partition onto your Windows drives.

That way, if you don't want to worry about reinstalling Grub to get access, you can just take what you need and then blast the Linux partition to start again from scratch :)

---

### Post by eddie_gordo on 2007-10-28
Yes, but I believe that if I start again from scratch, the same thing will happen! I got a little time now, I'll try to reinstall grub and see if I can get access to both Linux and Windows! :)

---

### Post by eddie_gordo on 2007-10-28
As I expected, I've restored Grub and the same thing happened again... Is it possible that there's no way to keep Vista and Ubuntu together?!

Thanks

---

### Post by eddie_gordo on 2007-10-29
Anyone? I would really like to have both OS in my laptop working without having to boot it through SGD to access Ubuntu... Any sugestions?

Thanks in advance

---

### Post by eddie_gordo on 2007-10-29
Well I've been thinking and I think that maybe the problem is about the partitions that I've created... This is a screenshot of my partitions that I'll explain:

[IMG]http://img459.imageshack.us/img459/5215/screenparticoesvj4.jpg[/IMG]

The first partition of 1.8gGb is the Asus Recovery partition, C: is where Vista is installed, D: is where I keep all my documents, pictures, music, whatever, and the other two partitions are to Ubuntu, where the one of 7Gb is the one where it is installed and the 1Gb one is the Swap partition... Is it possible that the conflict has to do with the fact that I've created this two last partitions from D:, a "Logical Drive"?

Thanks in advance, I would really like some help here... :)

---

### Post by wheredidrealitygo on 2007-10-29
We never got your screenshot :(

Whenever I installed Ubuntu, I always use Primary,  for my partitions, [logical]("http://en.wikipedia.org/wiki/Logical_Volume_Management") is of much better use on servers.

I'm not sure what effect having it as a logical volume could have, so I'd rather not say anything definitive.

---

### Post by eddie_gordo on 2007-10-29
Can't you see the screenshot? It shows up here...

Anyway, thanks for the answer... but it didn't help very much! :P Anyone got any sugestions? I'm sad as I can't have both windows and linux in my laptop! :(

Thanks

---

### Post by ppl on 2007-10-29
Hi, another Newbie here, hope I can help.
I think you could edit file /boot/grub/menu.lst to manually specify which partition your Vista lays on.

--------------------------------------------------------------------------------------------------------
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
  
That is the last part of my menu.lst.
Your should be different as yours are Vista, but you can just modify yours to something like:
 root      (hd0,1)

I think hd0 means first physical hard drive and second 1 is for second partition which is your Vista boot section. 

Good luck!

---

### Post by eddie_gordo on 2007-10-29
I will try that when I get home! Thank you! :) I'll let you know here if it worked out..

---

### Post by wheredidrealitygo on 2007-10-29
Sorry about the confusion, the screenshot was always there, I forgot about proxies at work lol. 

ppl's advice seems very sound. Here's hoping it works :)

---

### Post by Kaji on 2007-10-29
Wow, this thread amazes me.

While Microsoft is funning at (us) Linux users, you guys sit here helping someone that wants to actually use vista, (our) "competitor." Thats awesome guys, just awesome.

---

### Post by DeadToad on 2007-10-29
Ain't that sweet, Linux users helping Windoze users!
I had a similar problem.  After 6 attempts with the SuperGrubDisk, I could boot back to Vista, then restored GRUB for Linux Ubuntu 7.10
Keep trying.
DeadToad

---

### Post by DBAlex on 2007-10-29
Kaji:

Thats because believe it or not some people have to use certain OS's because of circumstances... when I can run Visual Studio on Linux then call me OK? And please don't tell me about WINE... ;)

Ill take your post with a bit of a pinch of salt but not everyone installs Windows because they want to... Plus Vista isn't that bad, at least MS is taking some stance to try and secure there user base... Although I prefer MacOS's graphical pseudo sudo implementation better as I can see people in the future clicking on UAC prompts without reading them... :(

Anyway, just think before you speak somtimes...

---

### Post by DeadToad on 2007-10-29
eddie,
on one of my laptops, I have WinXP on one partition, and Linux Ubuntu Gutsy 7.10 on another.
GRUB dual-boots fine.  Works like a charm.
So, yes, you can have your cake and eat it, too!

I also have the same setup on one of my desktops, no problems.

Here's what I would do, and this will work!
1. Use the SuperGrubDisk to boot to Win Vista. (actually, you don't need to boot to Vista, just turn on the PC and put the Ubuntu LiveCD in the cdrom drive, then reboot the PC again).
2. Put the Ubuntu LiveCD in the cdrom drive.
3. Reboot the PC.
4. Click "install Ubuntu" on the startup screen.
5. After the LiveCD has loaded Ubuntu, click the "Install" icon on your desktop.
6. This will reinstall Ubuntu completely, just install it on the same partition (primary) as before (not the Win Vista partition).
7. After installation, GRUB will be reinstalled.
8. Now it's back to normal, and GRUB will allow you to dual-boot Ubuntu or Vista as usual.
That's what I did after it went FUBAR while reformatting the partition with Ubuntu on it.
You are not touching the Vista partition at all, so you don't loose any Vista data.
Good luck.
DeadToad

---

### Post by DeadToad on 2007-10-29
> **eddie_gordo said:**
> Hi there..

today I tried to install Ubuntu 7.10 as it looked nice in the LiveCD. I installed it and everything went ok! The only problem is that now I cannot boot into Vista.. When I choose Vista Loader in the grub, my laptop just restarts and goes back to grub again... Anyway I can fix this? I'm freeking out here as I really don't know what to do!


eddie, one last question?
After Ubuntu installed to your hard drive, did you click "OK" or "Yes" (during final installation) to install the GRUB loader?
If you selected "No", I could see why you did not have a choice to boot back to Vista on reboot, and the computer would only boot to Ubuntu.
By selecting "OK" or "Yes", GRUB will be installed and you have the choice of dual-booting to Vista or Ubuntu.
Make sure you install GRUB during the last few minutes of installation this time.
Just a thought.
Good Luck.
DeadToad

---

### Post by eddie_gordo on 2007-10-29
**DeadToad**, I had Grub appearing, with the option to boot to Windows Vista when I turned my laptop on... It just wouldn't boot to Vista when I selected it to, it just rebooted and grub appeared again, forcing me to go to Ubuntu... 

Maybe I'll try that, but I believe it won't work as I reinstalled grub through the terminal and it appeared back again, but the same thing happened, I chose Vista and it reboots... Weird, hã?

I still need to try to edit the menu.lst file from grub like **ppl** said before, today I won't because it's getting late and I need some sleep... :P Tomorrow I'll try to fix this! If I can't, I'll just keep booting to Ubuntu with the SGD and to Vista normally...


Thanks everyone!

PS - Yes, I really need Windows... And those who are trying to help me are welcome in this thread! You can't blame me for needing Windows for some applications! I'm sure I'll spend most my time in Ubuntu, though..

Thanks again

---

### Post by DeadToad on 2007-10-29
eddie,
If the ppl fix doesn't work, just reinstall Ubuntu over your existing installation.  This will fix GRUB, by reinstalling it at the end of the installation.
I did that on another PC that Ubuntu went FUBAR on, and it dual-booted correctly without any problems.
Something must have went south during your original installation of Ubuntu.
Good luck.
DeadToad

---

