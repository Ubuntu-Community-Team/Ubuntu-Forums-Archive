---
title: "A few questions"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by bigblackbunny on 2008-01-26
I just downloaded a file called [COLOR="Blue"]ubuntu-7.10-desktop-amd64.iso[/COLOR]
I checked it with MD5 or what ever its called, and it was the same as the website. and then put it on a 700MB 80 minute cd. Now that i have that, i need to install it on both my computer and my sister's computer as she wants it to. I have Windows XP and she has a Mac 10.4

My computer:
[IMG]http://i149.photobucket.com/albums/s74/bigblackbunny/comp-info.jpg[/IMG]

Please tell me exactly how to put it on my computer. I know i have to go into the bio settings on my computer, but im not sure exactly what to do there. Please tell me a way to put it on our computers and make it so that we can use both our regular OSs and ubuntu. I do not want to format my drive or anything.

Oh yeah, i just got another PC from one of my dad's businesses. I want to whipe every little file off of it. It is an XP also.  Can someone tell me how to whipe the drive completely, then install ubuntu?

Thank you for listening to my noobish questions. Please answer them soon.

---

### Post by JoshuaRL on 2008-01-26
Welcome to Ubuntu!  This is a great place to come when you have issues, it's unlike anything you're used to in Windows.  Okay, so for your problems I'm going to answer them in the order that you'll need to do them in.

First, if you want to dual-boot (use more than one OS on a computer) you'll need to defragment the drive so you can tell how much space you have available.  Then you can pick an apropriate size for Ubuntu.  Next, when you reboot you'll want to boot from the CD.  There will either be an option at boot up or you'll have to go into the BIOS settings and change the boot order.  Just look around, you should be able to find it.  When it loads, you'll want to run the Live CD.  From there you can follow the directions here:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

For a dual boot, you would want to use the guided partition.  For a fresh install on the entire hard drive, use the erase entire disk option.

Hope that helps!

---

### Post by spiderbatdad on 2008-01-26
As far as I know, the powerpc (mac) is not supported in Ubuntu 7.10. IDK if this will change in Hardy...due out in April. Dapper Drake 6.06 has a powerpc installation cd and is still supported. You probably do not want the amd64 for your pc either, but the standard cd.
To change the boot order you may not have to enter the bios, often F12 at power up will ask you if you want to boot from a cd.

If you have to get into the bios, usually hitting the esc key or F1 a few times right after you turn on the power will do it.

Once you start a Ubuntu installation you will get the opportunity to resize the disk and make  room for Ubuntu or overwrite the entire disk. If you want to resize, you must defrag windows just prior to installing Ubuntu. There is a good installation guide stickied in the Installation sub-forum of this site.

---

### Post by Sinkingships7 on 2008-01-26
you need to get the x86 version, unless your computer supports 64-bit processing.

---

### Post by bigblackbunny on 2008-01-26
Ok, my computer sayed it doesn't need to be defragmented. I defragment it a lot anyways. Here is the data it has though:
Capacity: 164 GB
Free Space: 93.35 GB (65%)
If i lower the bar to like:
|---------------0----|
would that destroy any of my data on my windows OS?

I am planning to get sixteen 500 GB hard drives from the store and a lot of RAM to go with it (obviously with other new hardware) for a server i am makeing. Would i only need to install ubuntu onto all the drives or just one? I have a few websites of mine that i want to put on there, and a few for my friend. The rest will be used for storage. Then again, would ubuntu be good for that kind of server or a different OS? This is my second time experamenting with this kind of thing.

---

### Post by spiderbatdad on 2008-01-26
you must defrag even though it says you dont need to, and do so just prior to installing Linux.

---

### Post by bigblackbunny on 2008-01-26
Capacity: 164 GB
Free Space: 93.35 GB (65%)
If i lower the bar to like:
|---------------0----|
would that destroy any of my data on my windows OS?

---

### Post by LaRoza on 2008-01-26
> **bigblackbunny said:**
> Capacity: 164 GB
Free Space: 93.35 GB (65%)
If i lower the bar to like:
|---------------0----|
would that destroy any of my data on my windows OS?

No. If data is there, it moves it and make the file system aware of it.

Windows will check itself when it boots, that is normal whenever it detects a change.

---

### Post by bigblackbunny on 2008-01-26
Thank you. I think you have given me all i have wanted to know for now :)

---

### Post by bigblackbunny on 2008-01-26
Ok, i once again defragmented my hard drive C, and this is the message that poped up at the end:

[U][I][B]Defragmentation is complete for: (C:)

Some files on this volume could not be defragmented.
Please check the defragmentation report for the list of these files.[/B][/I][/U]

Is it safe to run ubutu through live cd, or not?

---

### Post by LaRoza on 2008-01-26
> **bigblackbunny said:**
> Ok, i once again defragmented my hard drive C, and this is the message that poped up at the end:

[U][I][B]Defragmentation is complete for: (C:)

Some files on this volume could not be defragmented.
Please check the defragmentation report for the list of these files.[/B][/I][/U]

Is it safe to run ubutu through live cd, or not?

Yes, it is safe. But back up to be sure. I have never lost data when partitioning, but you never know.

[http://www.auslogics.com/en/software/disk-defrag/download](http://www.auslogics.com/en/software/disk-defrag/download) is the best defrager I have seen.

---

### Post by bigblackbunny on 2008-01-26
How exactly do i back up? Is it like makeing a restore point on my computer or something?

---

### Post by LaRoza on 2008-01-26
> **bigblackbunny said:**
> How exactly do i back up? Is it like makeing a restore point on my computer or something?

No.

Save an important files to something else like a flash drive.

I have never lost data partitioning, but if something goes wrong (always possible) it can make life difficult. Although data and partition recovery is possible, I always assume the worst.

If you have recovery disks, or the ability to make them, they are handy.

If you want to proceed and accept the small, but real, risk you can if you choose.

(Don't blame me, this forum, or Linux if something goes wrong which is unlikely)

---

### Post by bigblackbunny on 2008-01-26
I dont think i will be blameing anyone anyways. Im the server/archives room of one of my parent's businesses, we have plenty of extra Windows XPs to plop on my computer, and all my personal stuff on my computer is stuff downloaded from the internet and useless stuff. I will only need to save my gf's pics and my digital encrypted journal :) To hell with the "school" folder! :)

---

### Post by bigblackbunny on 2008-01-26
ugh! Another problem. I thought i knew what to do in the BIOS, but i guess i was wrong. What i did was went to the menu in the BIOS called BOOT. From there, i put CD/DVD at the top of the list. Next i pressed the Save changes and Exit button, and it didnt do it. I veryfyed that i have the corect cd in, and it has the ISO program [COLOR="Blue"]ubuntu-7.10-desktop-amd64.iso[/COLOR] on it. Am i doing something wrong?

---

### Post by LaRoza on 2008-01-26
> **bigblackbunny said:**
> ugh! Another problem. I thought i knew what to do in the BIOS, but i guess i was wrong. What i did was went to the menu in the BIOS called BOOT. From there, i put CD/DVD at the top of the list. Next i pressed the Save changes and Exit button, and it didnt do it. I veryfyed that i have the corect cd in, and it has the ISO program [COLOR="Blue"]ubuntu-7.10-desktop-amd64.iso[/COLOR] on it. Am i doing something wrong?

Did you burn it as an iso? Do you have a 64 bit processor?

---

### Post by bigblackbunny on 2008-01-26
What i did was downloaded it, then i right clicked it and clicked "send to>Disk (E)" Next, i tryed to pop the empty disk out, and a window poped up saying to write it to the disk. I ploped the disk back in, clicked next for it to write it to it, and waited about 7 minutes for it to completely finish. Is that what i should have done? If not, how was i supposed to do it?

How can i figure out what bit processor i have?

---

### Post by LaRoza on 2008-01-26
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Jelmoh on 2008-01-26
The picture you've posted in your first post let's me know you don't have a 64-bits processor, you should download the x86 version of ubuntu.
Then you should burn an image to cd, what you did was burning a normal data-cd, you won't be able to boot with it! 
What program are you using for burning cd's?
If you've got any questions, get back here! ;)

---

### Post by bigblackbunny on 2008-01-26
> **Jelmoh said:**
> The picture you've posted in your first post let's me know you don't have a 64-bits processor, you should download the x86 version of ubuntu.
Then you should burn an image to cd, what you did was burning a normal data-cd, you won't be able to boot with it! 
What program are you using for burning cd's?
If you've got any questions, get back here! ;)

Can you please give me a link to that version?
How do i do that?
Hell! What kind of cd should i use then?! Would it be ok to use a 52X 80 min, 700 mb disk? or a 120 min, 2 gb disk?
I used window's default. Its like Windows CD Wizard or something like that. If that was a bad one, tell me what kind of program i should have used please.

---

### Post by bigblackbunny on 2008-01-26
Ok, so i burned the one i first was planning to use (ubuntu-7.10-desktop-amd64.iso), and set my BIOS settings to boot off of cd. It got to a window that looked like this:

[IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=boot.png[/IMG]

When i pressed enter to the first option, a window poped up saying "something Linux Kernal" with the status bar stuck on 100%. It was just stuck there while my drive was utering a repetative clicking sound. If this is because i got the wrong Linux for my system, please point me in the direction of the one thats best for me.

---

### Post by Sidewinder1 on 2008-01-26
I believe that the file that you should use is: ubuntu-7.10-desktop-i386.iso it should be located at the same ftp-server that you found the other one. Make sure that: you do the MD5Sum check, burn it as "image" to your CD at the slowest speed possible (usually 4X) to minimize errors.
HTH

---

### Post by bigblackbunny on 2008-01-26
Alright, i am downloading that one now.

Was it hard to learn all the commands and how to operate this system for you guys? Im almost afraid of it seeing as i know almost nothing about how to do anything with it. How long did it take you to learn it all?

---

### Post by Sidewinder1 on 2008-01-26
You'll NEVER learn it ALL. You just have to be patient, read every thing fully and completely, 3 times; and most importantly look forward to the learning experience. These forums ...... certainly the BEST place to start. Welcome and good luck!

---

### Post by LaRoza on 2008-01-26
> **bigblackbunny said:**
> Alright, i am downloading that one now.

Was it hard to learn all the commands and how to operate this system for you guys? Im almost afraid of it seeing as i know almost nothing about how to do anything with it. How long did it take you to learn it all?

Normally, you don't need to know the commands, but you'll often get them as anwers to problems.

Once the system is up, you probably won't find a need to use the terminal. I use it, but I also use the command prompt in Windows too.

---

### Post by bigblackbunny on 2008-01-26
I use the command prompt in Windows all the time. I am a freak when it comes to exploring computers and learning how they work, so is there a list of commands and what they o somewhere?

I just built a computer today, but it has an old 80 GB hard drive on it. Can someone please explain how to delete everything? I then will be loading ubuntu-7.10-alternate-i386.iso onto it as the only OS

---

### Post by Jelmoh on 2008-01-26
There are many of those lists... one a little bit better than the other... :)
[Ubuntu Forums: Know Your Terminal Commands](http://ubuntuforums.org/showthread.php?p=990636)
[JustLinux.com: Ubuntu Terminal Commands](http://www.justlinux.com/forum/showthread.php?t=143781) Second post! ;)
[Zolved.com: Usefull terminal commands](http://www.zolved.com/synapse/view_content/28329/Useful_terminal_commands_on_Ubuntu)

And remember, Google is your friend! :)  Almost every problem has been encountered by someone, try to find the solution at Google first. If none is found, come to Ubuntu Forums! :)
Great thing you chose for Ubuntu! :)  I'm using it for two months now and I really enjoy it! :)
Terminal isn't that hard to handle... A **huge** community!
Well.. as the name says: Linux for human beings! ;)

Good luck with getting to know Ubuntu!

Edit:
[Ubuntu x86 version](http://nl.releases.ubuntu.com/7.10/ubuntu-7.10-desktop-i386.iso) You'll be needing this one! :)

---

### Post by bigblackbunny on 2008-01-28
Ive got a little problem. I keep trying to delete these files on my desktop, and it wont let me. Instead, it spits up this message saying: 

Error while moving.
Cannot move "/home/user/Desktop/old pics" to the trash because you do not have permissions to change it or its parent folder.

What can i do to delete them?

EDIT: Never mind. I found the solution on my own.

---

