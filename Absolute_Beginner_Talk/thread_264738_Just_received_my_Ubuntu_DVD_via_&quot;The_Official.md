---
title: "Just received my Ubuntu DVD via &quot;The Official Ubuntu Book&quot; how do I..."
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by newbie8 on 2006-09-25
Just received the above-mentioned via Amazon. Now just a couple of newbie questios:

1. How do I boot the computer via the dvd to try the live version? (please note that I do not understand what Bios is)

2. Since I am willing to start Ubuntu from scratch on one of my computers, how do I install the full-install to the whole hard drive even though there are files already?

3. Should I erase all the files first before the installation or will the installation erase the HD automatically (which is better for me)?

4. I work a lot with Picasa and I upload lots of pics to my computer using an Olympus digital camera, will this be easy with ubuntu?

I love the book and I can't wait to get Ubuntu running smoothly.

Cheers!

---

### Post by siacs on 2006-09-25
1. In your BIOS setup (there's usually a message when you boot how to access it) there is a Boot menu item and Boot Device Priority, make sure  CD or DVD is the first device, then reboot with the DVD in that drive.

2. [Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing.html")

3. See above

4. I have an Olympus C-3000 Zoom and it's detected automatically

---

### Post by gn2 on 2006-09-25
First, is there an operating system and data on the computer you want to keep?

If the answer is yes, you need to back up your data to removable media before you do anything.

BIOS is the BasicInOutSystem. It resides in a chip on the computer's motherboard and gives it instuructions about how to run.

To open it and configure which drive to boot from you need to press a key, often "Delete" or a function key (it varies from make to make) this will take you to a basic screen where there are options for various things (most best left alone) one of them is the Boot Device Order. You need to arrange this so that the DVD drive boots before the Hard drive. You also need to make sure that Boot from CD(DVD) is enabled.

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

Be VERY careful if you are setting up a dual-boot system on one hard drive, Ubuntu will write it's own boot-loader over the Windows Master Boot Record.
This is potentially disastrous.

My advice would be to either dual-boot on two hard drives, with the Windows one unplugged during install (then select boot device using F8 at boot time)

Or better yet if you don't need it erase the Windows install.
Be careful it will delete your data with it.

Ubuntu has simple to use software for picture transfer.

Good Luck.

---

### Post by newbie8 on 2006-09-25
Thank you very much for the helpful replies. This is the main reason as to why Ubuntu is tops. ...it's the community behind the great product!

Keep up the good work guys!

---

### Post by Rhubarb on 2006-09-25
If you can't get into the BIOS (or don't know what button to press) on computer start up, try my little trick:
Press these buttons one at a time fast repetitively:
F2 F10 F12 Del
Press all the buttons above until you're into the BIOS (you'll know because you'll be presented with usually a simple text based menu on a blue background).

Then do as Siacs said above, change / verify that it will try to boot off CD / DVD before the hard disk.

The Ubuntu installer (an icon on the live destop) will let you wipe your hard drive clean for you (if you want).
Please make sure you've backed up any of your documents / media, as this will be deleted.

You can get picasa to work in Ubuntu, I can't say how exactly, as I haven't tried myself.  But I know it does work.
For this you'll need to install "wine" (wine allows some windows programs to run in Linux), then using wine install then run picasa.  You'll need to have a search around the forums here to learn how to do this (it's nothing too hard, but you'll need patience and a little work in the terminal to figure it out).

You won't have any problems with your digital camera in Ubuntu.
If you think picasa is a little tricky to get running, then I recommend you use GIMP (it's allready there in the applications menu).

If you need help, give me a yell in this thread.

---

### Post by macdo on 2006-09-25
You don't need to install wine for Picasa - there is a Linux version! (based, it is true, on Wine - but it installs the bits it needs, you don't need to worry about it).

[http://picasa.google.com/linux/]("http://picasa.google.com/linux/")

You can also install [Automatix]("http://www.getautomatix.com"), which has an option to install Picasa.

Have fun!

---

### Post by hyper_ch on 2006-09-25
It may even well be, that you can already boot from your DVD without altering the BIOS. As far as I know a retail pc normally has the boot from cd/dvd option enabled.
So, before going into the bios just put in your dvd into the dvd-drive and then start your computer. If it boots into Ubuntu you'll notice :)

---

