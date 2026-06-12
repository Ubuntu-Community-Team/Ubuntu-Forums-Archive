---
title: "installing lubuntu on eMac G4 (usb2.0)"
date: 2018-12-14
forum: Apple Hardware Users
---

### Post by weldum on 2018-12-14
hi, i have just registered because i was given a emac g4 as a gift. i like old computers but this one seems to be particularly hard to work with
i've downloaded the ubuntu 16.04 netinstall iso and booted from there, then installed and selected Lubuntu, now when it should start it gives me a black screen and it locks
i've tried various commands in yaboot for loading linux and the most i could do was to get a purple cursor on screen, it responds at the mouse movement, but nothing else happens

i've readed and searched but most posts are about g5 or imac g4, in this machine these solutions didn't work.

what can i do?

---

### Post by howefield on 2018-12-14
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by gsahli on 2018-12-14
Which model eMac is it? Find info here:
[https://everymac.com/systems/apple/emac/index-emac.html](https://everymac.com/systems/apple/emac/index-emac.html)

---

### Post by gsahli on 2018-12-15
Oh, I think you did tell us it's the USB 2 model. In that case it uses an ATI Radeon 9200 graphics card.
I'd try this at the Yaboot prompt:
Linux radeon.agpmode=-1 modprobe.blacklist=ams
(it's all one line with two spaces)

---

### Post by weldum on 2018-12-18
thanks for the answer, sadly i can't test it because my only dvd reader passed out and the combo drive on the mac doesn't work, so i can't boot on linux at all, and this mac doesn't support usb boot

---

### Post by jharris1993 on 2018-12-24
A couple of questions:
First:  Does it work properly with a Mac O/S installed?
You can download older, unsupported, Mac software here to test: [https://www.macintoshrepository.org/](https://www.macintoshrepository.org/)

Once you've downloaded a Mac O/S and verified the system completely functional, you can approach troubleshooting the Lbuntu install with the confidence that there are no underlying hardware issues complicating things.

Can you get to an alternate screen terminal?  (i.e. try CTL-ALT-F1)  This will allow you to login, view logs, and try various things from a command prompt.  Also it will allow you to shutdown the system properly! 8-[ ;)

Once you get to a terminal screen, you can try editing /etc/yaboot.conf and commenting out the "quiet splash" line.  This will allow you to see boot messages/errors before the screen goes brain-dead.  Since you are on a text screen, you're stuck with vi as an editor.  After you edit the yaboot.conf file, you have to run "sudo ybin -v" to write the changes to the boot-loader and make it permanent.

I am having the exact same problem with my graphical display on an iBook G3. (Ref: [https://ubuntuforums.org/showthread.php?t=2408820](https://ubuntuforums.org/showthread.php?t=2408820)) You may wish to review/try some of the suggestions made there too.

Jim "JR"

---

### Post by weldum on 2018-12-25
gsahli: the commands you said to me didn't change anything
jharris1993: the mac does indeed work correctly, i've got to enter to the alternate terminal and changed several files
i've checked the file xorg.1.log and it says
[COLOR=#2E1A05](EE) No devices detected.
[/COLOR][COLOR=#2E1A05]Fatal server error:
[/COLOR][COLOR=#2E1A05]no screens found

but the desktop never shows up, one thing i did that (somewhat) worked was booting with "radeon.modeset=0", that way the cursor did appear but it looked purple, then pressed CTRL-ALT-F4 and got to the terminal, then i put "startx" and the desktop showed albeit with strange colors. aside from the color problem everything worked right.

i don't want to use mac os x because is really hard to find software for it.[/COLOR]

---

