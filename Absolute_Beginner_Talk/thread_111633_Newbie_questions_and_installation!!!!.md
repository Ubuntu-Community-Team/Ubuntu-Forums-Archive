---
title: "Newbie questions and installation!!!!"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-01-02
hello,

  I'm interested in dual booting either ubuntu 5.10 or dapper drake 6.04(safe?) along side of my windows xp.

  I have 43 GB left on my disk. I downloaded the DVD of 5.10 install/live dual option disk from the image download section from the ubuntu page of DVD installs.

  After saving the image i386 dvd to all programs file, I then used Sonic DVD to 'burn image' onto a DVD+R DL disk.

  I thought that I would be able to run the 'LIVE' disk install by just putting it in my cd/dvd drive and installing like other software cd's.

  I KNOW I'M WRONG!!! 

  Then I wasn't too sure of my next procedures. I had disk fragmented my computer the night before and knew I had room on the C:drive. I then shut down my system and restarted it, then I inserted the newly burnt dvd and nothing happened, and nothing was on my D:drive when I tried to open the D:drive in 'my computer'.

  How do I dual Boot? How do I Set a Partition? And how would I try the 'LIVE' Boot trial form? Step by Step instructions for an idiot like me would be nice.

  Also, if I Dual Boot, what are the start up times each time I turn my Notebook on? Does ubuntu become my default start up desk top or do I have to choose between Windows xp and ubuntu every I start up, and then wait for a rebooting of my settings?

  I'm totally new to this, but I want to learn. I messed around with library internet computers and other friends p.c.'s for years, doing remedial tasks like using word to create resumes(chef/line cook) to post on craigslist, and also your run of the mill web surfing and concert ticket buying(burnigman).

  Anyway, I finally got a computer this late October and since then have started learning html/css, and now have my eyes and thoughts leaning toward xhtml/xml/css/ and java for the direction of study I want to take. I also discovered that I preferred Firefox 1.5 to IE, as well as Thunderbird Mail instead of outlook, Nvu to replace M$ frontpage, and FileZilla as my FTP.

  My last statement is that it seems that I'm pretty much already using the tools and programs of an ubuntu desktop, and what really makes me want the ubuntu OS is that I need a freeware photoshop program for my amateur web design practice and your OS has gimp which I think is what I will need for designing my own gif image headers for my web log page. I also am interested in learning C++(?spelling?) to fully use the open source programming options of a free minded Linux OS community.

 So can anyone help me with my questions about this new experience for me, in the realm of Linux/ubuntu installation. I don't want to lose Windows xp, but I don't mind storing it somewhere on my C: drive and giving Linux ubuntu default status since I'm already a default Firefox browser user and the only programs I use on xp are basic OS files/start up/desktop/disk cleanup/defrag  and basic things I'm sure are better or getting better through development on ubuntu/Linux and the whole open source community.

  thank you, and 'PimpZilla' rules!

---

### Post by Zelut on 2006-01-02
It sounds like maybe either 1) it didn't correctly burn the .iso to your CD.  You may want to check & verify that you've got the install.iso &/or the live.iso burned to a CD.

Secondly, when you first boot your computer head into your BIOS (DEL or F1/F2) and check the boot sequence.  You'll need to make sure your computer is set to boot to CD-ROM, & then HDD.

Thirdly, I wouldn't try Dapper yet.  It is still far from being finished & wont be a very useable solution for you in the meantime.  Be excited for its April release though! :)

Assuming you've got those previous steps taken care of you can boot to your live CD and play around just fine.  If you want to install a dual-boot its almost just as easy.  Use the install CD and it'll walk you thru the setup.  At the 'partition' section it'll ask you if you'd like to 'resize existing & create Linux partition' which will be perfect for you.  It'll just take a chunk of your free space & create everything for you.

Try those first few out until you are able to boot to the live CD and if you have other questions let us know...

---

### Post by crimesaucer on 2006-01-02
cool, thanks, I'll try those suggestions.

   And I'm wondering if I dual boot the 5.10, will I have to uninstall when the dapper drake comes out or will it be an upgrade on the 5.10 like a Firefox extension.

 thanks for responding so fast.

---

### Post by Zelut on 2006-01-02
upgrading is fairly simple so I wouldn't worry about that.  A lot of users simply backup their /home folder & do a fresh install though.  That is what I've done.. I'm sure we can walk you thru that when its time :)

---

### Post by Jukey on 2006-01-02
i'm not sure, but i think all you have to do is update it using apt-get. i don't know how so don't ask me. you won't have to download another .iso file.

---

### Post by pmaury on 2006-01-02
1st step you might try ISOrecorder, free download for windows, to burn the image of the ISO to CD.

---

### Post by Jukey on 2006-01-02
another download is Deep Burner. the free version allows ISO burning and some basic burning options.

---

### Post by crimesaucer on 2006-01-02
hello everybody and thanks for the info.

  To catch everyone up to my situation, I'll start with a simple ordered list.

1) First I checked the dvd I downloaded and it had ubuntu 5.10 on it and was full of data. Whether or whether not it had the correct and finished download on it I don't know, and don't know how to check it other than the fact it took an hour to save to C:\program files and then another 20 minutes on SonicDVD using the "burn image" function to put it on to a DVD+R DL(?I don't know if that was what I was supposed to do?).

2) Then I tried to dual boot by inserting the disk, powering OFF, then starting and pressing the f1/f2 keys as mentioned in a reply. It didn't work so I read my hp dv4230us manual on Adobe and it said some discouraging things about other operating systems that I figured is required by Microsoft as part of a contractual monopoly propaganda between the big companies. After reading how to repair and reinstall windows xp home using the Operating System CD provided by HP I proceeded on attempting to get to the boot menu( if that's even what I'm supposed to do?) by doing four different things, since nothing was working.
    (a)I tried to press the f10 key to enter because the hp Intel screen to start the boot, flashes a menu of the three options
    (b)I tried to press the f12 key to boot from LAN?????
    (c)I tried to press the esc key to stop the regular windows boot up.
    (d)I tried to press any key to stop the regular boot up and start the install page.

  NOTHING WORKED!! So I went to my online support for hp and asked why I couldn't get to a screen to configure a dual boot for an added OS and they gave me all this grief about Linux won't be supported blah blah blahh, and how my notebook could only function with one OS (Windows xp I assume? Ha!) and I said I have researched this for days and know it's totally possible to have a dual boot installed on a computer and my disk space of 60GB is only using 17GB  right now and I have all this empty disk space.

  So after all that I did a system repair of xp and then I tried to install the ubuntu again and still couldn't. 

  I did however wind up on a Operating System data info and settings page using the f10 key and I searched through all the options and couldn't find an area of partition configuration or new OS installation.

  I know I'm doing something wrong since I'm a beginner, yet I'm trying to work through this and learn at the same time. This is what I want to download the Linux/ubuntu OS for in the first place since it's more of a hands on intellectual OS, rather than a windows OS designed for a money spending EBay shopaholic who wants only the easy answers rather than the complete knowledge of the inner workings of programming, writing code, and hacking.

 In short, I know some of the things I've posted are pretty idiotic, but keep in mind I have only owned a computer for 2 and a half months and am learning on my own from free forums and tech pages and the more you can share the more I learn. In fact the moment I found Firefox, my learning in html/css web development increased and I think ubuntu and Linux will be the same for learning basic hacks. I'm really into it now and I find myself not even using the web for anything other than learning web design and researching the best free ways of doing it.
 
 thanks and sorry for writing a novel.

---

### Post by Sef on 2006-01-02
To go into the boot: often delete or F2 are used.  Just gently tap one of them once you start up your computer.   Look for something that says set up on the first screen that you see.  

Generally the boot sequence is a few pages back, so you need to check each each page.  Be careful about changing any other settings, since you you can really mess up your system if you change the wrong thing.

---

### Post by crimesaucer on 2006-01-03
thanks sef, I'll try that using the delete and the f2, maybe it will boot after all that other mistakes I've made.

  Anyway I just ordered a ubuntu 5.10 disk from Launchpad in case I have further troubles over the next couple of days/weeks of attempting to dual boot. Plus it would be nice to have their finished cds for back up or gifting someone with a new internet operating system.

 thanks again foe the replies

/**5 minutes latter and I tried both f2 and delete and neither of those buttons got me to a first boot screen, so i"ll probably just try and get another free download from a different distro when I go and buy some CD's to download onto, or I'll just wait and be happy with my Firefox/xp combo. It's still better than Internet Explorer.**/

---

### Post by Bartender on 2006-01-03
crimesaucer -
you're trying to do too many things at once and getting yourself mixed up.  You're not gonna find a dual-boot option in your BIOS, which HP calls Setup.  So let's get back to square one.  Let's make sure that your computer can be set to boot from the CD or DVD drive instead of the hard drive so you can try the LiveCD.  I pulled up the .pdf for the dv4000 series.  BIOS (or "Setup" if you will) is accessed by pressing the F10 key after pushing the "go" button and before you see the Windows splash screen.  Since you don't know exactly when the computer will accept the F10 key, most people just repeatedly tap the key until the computer gets the message and takes the detour.  If you see "Windows is starting" you missed it.  Hold down the power button for five seconds and try again.  The BIOS is a set of instructions stored on a chip on your motherboard.  The computer goes there for basic information telling it what to do and how to do it before looking to your hard drive for an OS to start (or boot - the source of that term) up.
According to page 38 of your manual, boot options (that's where you'll find the place to change your boot order) is tucked under the "Advanced Menu" section of your BIOS.  So it looks like you'd enter the BIOS (the F10 key), then find Advanced Menu, then enter "Boot Options", then find the "boot order" settings.  If you haven't screwed around within your BIOS before it can be unnerving trying to figure out how to make changes.  From what I've seen of boot order menus, you'll use the up and down arrow keys to pick the device which you want to move around, then use the "+" and "-" keys to shuffle the device.  So you'd pick the CD or DVD drive, then move it to the top of the boot order.  Write this stuff down so it won't be so scary the next time.  Then the next trick is getting out of BIOS and saving your changes.  They're all different but they're all kinda the same.  Very often "Esc" will back you out, but there's always some keystroke or combination of keystrokes to make sure you saved your changes.  Look for this and make note of it.  In the Award BIOS that I'm familiar with, the F10 key takes you right to the "Exit and save changes" menu.  You click "Enter", the computer restarts, you toss that LiveCD in the tray (better yet, have it in there BEFORE going thru all the rigamarole I just described above) and hopefully the computer will try to boot from the CD drive.  Watch for the lights to blink and the drive to spin up.  If it didn't and the computer moved on to your hard drive, then you've gotta go back into BIOS and make sure the boot order was actually changed.
As some of the other folks mentioned, be careful in BIOS.  You want to make sure that the changes you made were the ones you wanted.  You can leave the boot order as is or change it back to HDD 1st when you're done.  If you leave it CD drive 1st the computer will always look there first for a second or two.  No problem as long as you don't leave something in there.  If you do, still no prob, the computer will tell you "incorrect operating system disc" or something like that and you'll know to open your drive, remove the CD, and try again.
BTW, my half-year old computer refused to run the LiveCD.  I don't know why but the DVD drive would sample the Cd then give up and go on to the hdd.  I wish you better luck than I had!

---

