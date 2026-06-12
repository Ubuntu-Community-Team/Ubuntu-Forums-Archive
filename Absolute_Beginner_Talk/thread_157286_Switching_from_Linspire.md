---
title: "Switching from Linspire"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by StandardsDT on 2006-04-08
So after a couple days of having it installed I've had nothing but problems. Upon reboot or shut down you get pink bars. Apparently this is a known issue but still hasnt fixed. My soundcard is compatible but the OS for whatever reason messes up the settings so I have to go and fix it manually in the KConsole in order for it to work. I tried installing gimp and other software through apt or synaptic and nothing but problems. It would cause Gaim to stop working and who knows what else. They basicly try to confide you to CNR. If CNR didn't cost a peny for free apps then I'd use it. But now I'm just absolutely fed up with Linspire. I didn't pay for Linspire as I had the coupon code when they had the freespire thing going on. I just never got the chance to install it. Any how now that, that is out of the way I have some questions about ubuntu. How hard is the learning curve for ubuntu? I have no issues learning something new. How long does it generally take to install? And if you feel ubuntu is not for me what are some other Linux OS that you suggest?

---

### Post by aysiu on 2006-04-08
[QUOTE=StandardsDT]How hard is the learning curve for ubuntu?[/quote] Coming from Linspire...? Well, the setting up will be a big learning curve. The use will not. > I have no issues learning something new. Then you'll be fine. > How long does it generally take to install? Install? About 30-40 minutes. Configure afterwards--hours, especially if you don't know what you're doing. > And if you feel ubuntu is not for me what are some other Linux OS that you suggest? PCLinuxOS and Mepis.

---

### Post by elmore on 2006-04-08
It should be easy for you to switch to ubuntu, you shouldn't need to learn anything more than what you need in Linspire(depending on your hardware and what experience you have).
Be sure to try the live cd first to make sure everything is smooth.  
I switched from Linspire because I didn't like being tied to CNR-I had to edit my source.lst to get apt-get working.  I did like the default themes, I haven't found another distro that is as polished as that one.

---

### Post by StandardsDT on 2006-04-08
[QUOTE=elmore]It should be easy for you to switch to ubuntu, you shouldn't need to learn anything more than what you need in Linspire(depending on your hardware and what experience you have).
Be sure to try the live cd first to make sure everything is smooth.  
I switched from Linspire because I didn't like being tied to CNR-I had to edit my source.lst to get apt-get working.  I did like the default themes, I haven't found another distro that is as polished as that one.[/QUOTE]

yeah i hear ya about CNR and editing source.lst. the default themes were very nice as well.

---

### Post by xael on 2006-04-08
Another exLinspire  user here, so I can understand  completely what you're thinking about learning new things. I've been hanging around for a while & must tell you this a # 1 community. You can ask anything related to Ubuntu or GNU/Linux & someone'll aswer that in a flash.

---

### Post by trent dillman on 2006-04-09
Also, if you're not happy with Ubuntu for whatever reason, Mandriva's pretty easy on beginners.

---

### Post by Sef on 2006-04-09
Xandros is also an easy one for beginners.

---

### Post by StandardsDT on 2006-04-09
Thanks guys I'll deff be sure to check those out as well. I'm keeping my choices open right now for what Linux OS to use. I'll probably test each one out using a live cd.

---

### Post by OBnascar on 2006-04-09
[QUOTE=StandardsDT]How hard is the learning curve for ubuntu? I have no issues learning something new.[/QUOTE]

I made a transition from WinXP, to Linspire Five-0, to Lycors Destop 1.4, to Ubuntu. The only thing for me that I was uncomfortable with at first was the file system. But what was the most difficult for me was the file permission/sudo thing, I have had enjoyment learning these over time.

Other than the Linux distros that already have been mentioned, I have used Suse 10.0 (more than worth a try), Kubuntu (I really like that one) and Vector Soho 5.0.1 (this works good even on old computers, is light wieght, doesn't hog much memory or space)

Welcome to the forums StandardsDT, and enjoy using the Live CD's, you are doing the correct thing.

---

### Post by StandardsDT on 2006-04-10
alright so i have made my decision to go with mandriva. im going to be installing the one cd beta they offer. now i have a few other questions. can i just over write my linspire installation? will mandriva overwrite the grub that linspire put in place? if not how do i get rid of linspire with out reinstalling xp? i went to the linspire website and these were the instructions given.

> 
II.  To remove Linspire 4.5/5.0 from a computer with a dual-boot configuration with MS Windows 95/98/ME/2000/XP

If you have both MS Windows 95/98/ME and Linspire 4.5/5.0 installed, choose to boot into MS Windows at the Linspire 4.5/5.0 boot menu and press and hold F8 to open the Windows boot menu.  Choose to boot into Command Prompt and use Fdisk to remove the Linspire 4.5/5.0 partitions (NOTE: in Fdisk, the Linspire 4.5/5.0 partitions will not be identified as Linspire 4.5/5.0 partitions).

If you have both MS Windows 2000/XP and Linspire 4.5/5.0 installed, you can use the Disk Management tool in MS Windows to remove the partitions.  To open the Disk Management tool, click on Start >> Settings >> Control Panel (might be able to skip "Settings" if using Windows XP) >> Administrative Tools >> Computer Management (If using Windows XP, in Control Panel, switch to classic mode to see Administrative Tools.).  Under the "Storage" tree on the left pane, click on "Disk Management".  Right click on the partitions on the right pane that are being used by Linspire 4.5/5.0 and choose to delete/remove the partition.

Note that the methods mentioned in Part I (above) will work as well.

The next task is to remove LILO (the Linspire 4.5 bootloader) or GRUB (the Linspire 5.0 bootloader) from your Master Boot Record (MBR) . . .

If you have MS Windows 95/98/ME installed, click on Start >> Run.  Type in "command", without the quotes, and press Enter.  At the command prompt, type in the command "fdisk /mbr" to reinstall the Windows bootloader into the MBR.

If you have MS Windows 2000/XP installed, you will need to have the Windows Installation CD.  Insert the Installation CD into your CD-ROM drive and reboot your computer.  When Windows Setup loads up, follow the onscreen instructions to open the Recovery Console.  When it loads, it will ask for the system administrator password (the password you set when you first installed it; if you didn't set one, leave it blank.).  At the Recovery Console command prompt, type in the command "fixmbr" to reinstall the Windows bootloader into the MBR.

I unfortunately don't have the XP disk. Can I use the same step for Win 98?

I have chosen Mandriva simply cause of the easy of use. I will work my way up ubuntu when I get more advance in Linux. I plan on still being active here as the support and answers have been awesome so far.

---

### Post by StandardsDT on 2006-04-10
anyone please?

---

### Post by az on 2006-04-10
Mandriva easier than Ubuntu?  No way!


I don't know about Mandriva, but if you install ubuntu using your linspire partition, that will work fine.  Just manually edit the partition table and use the existing partition, but reformat it and mark it as "/".  Grub willbe installed and your windows OS will be detected and added to the list.

---

### Post by StandardsDT on 2006-04-10
[QUOTE=azz]Mandriva easier than Ubuntu?  No way!


I don't know about Mandriva, but if you install ubuntu using your linspire partition, that will work fine.  Just manually edit the partition table and use the existing partition, but reformat it and mark it as "/".  Grub willbe installed and your windows OS will be detected and added to the list.[/QUOTE]

well ive never used Ubuntu before and my understanding is that its hard to install if you dont know much about linux as a beginner so I'm starting off where I feel is right for me. Any other help besides the suggestion mentioned before is greatly appreciated. Right now I don't want to take risks on messing up my system. I don't have the XP install cd my tech does so messing around with it isnt an option.

---

### Post by StandardsDT on 2006-04-10
is everyone too busy to help me out here? or is there something everyone holds against people who tried out linspire? i see topics in here who have been posted after mine and are getting faster responce time and mine just sits there and gets pushed back until the second page.

---

### Post by az on 2006-04-10
[QUOTE=StandardsDT]is everyone too busy to help me out here? or is there something everyone holds against people who tried out linspire? i see topics in here who have been posted after mine and are getting faster responce time and mine just sits there and gets pushed back until the second page.[/QUOTE]
I don't know what you are expecting.  Why do you think Mandriva is less risky than Ubuntu?  With either one, you have the same risk of deleting your windows partition.

You don't have your windows cd, so if you really want to keep windows, you have backed yourself into a corner.  I am confident that Ubuntu will install fine for you.  But ultimately it's up to you.

---

### Post by mstlyevil on 2006-04-10
[QUOTE=StandardsDT]is everyone too busy to help me out here? or is there something everyone holds against people who tried out linspire? i see topics in here who have been posted after mine and are getting faster responce time and mine just sits there and gets pushed back until the second page.[/QUOTE]

People have not responded probally because they have not used Mandrivia before. No one holds the fact that you used Linspire against you. Ubuntu is very easy to install. The installer is one of the easiest to use. I know for certain that Ubuntu will overwrite the Linspire grub, but I have no clue if Mandrivia will. In fact Mandrivia may use lilo instead of grub. I just have no clue.

Sorry if you are not getting a timely response. It is easy for post to get lost in a forum that is this busy.

---

### Post by StandardsDT on 2006-04-10
[QUOTE=mstlyevil]People have not responded probally because they have not used Mandrivia before. No one holds the fact that you used Linspire against you. Ubuntu is very easy to install. The installer is one of the easiest to use. I know for certain that Ubuntu will overwrite the Linspire grub, but I have no clue if Mandrivia will. In fact Mandrivia may use lilo instead of grub. I just have no clue.

Sorry if you are not getting a timely response. It is easy for post to get lost in a forum that is this busy.[/QUOTE]

dont worry about it and thank you for your responce. i guess i just get so frustrated with no responces cause of the fact that im an admin/mod on another forum for a hosting company and am just used to really fast responce times. i also sometimes just get the impression that most people dont care. but your probably right about the whole mandriva thing. i posted in a mandriva forum hopefully theyll be able to tell me something about the lilo/grub thing. i did see installation screenshuts and the person who posted the installation screen shots said "wheres the grub installer". so you may be right. if i have them telling me the same thing then i shall use ubuntu instead :)

---

