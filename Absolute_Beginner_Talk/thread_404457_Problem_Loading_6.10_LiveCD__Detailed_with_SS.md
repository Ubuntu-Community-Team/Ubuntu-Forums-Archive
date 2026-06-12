---
title: "Problem Loading 6.10 LiveCD / Detailed with SS"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Kohbo on 2007-04-08
First off, I want to apologize on the quality of my ss's. My camera kept adding a giant white blur at the bottom.

This is now Day 2 of trying to install Ubuntu, or even run it, on my computer. I haven't even gotten the thing to reach the Ubuntu "desktop". Anyway here is what's been going on. Yesterday I downloaded Fiesty and burned the image using Alcohol 120%. The menu came up an I pressed enter to "Run or install Ubuntu.." It loaded the kernel and flashed a screen saying bios bug and whatnot. Then, it continued to the loading screen. It did it's thing and then white text kept saying

Buffer I/O error on device hda

I figured this was something with my hard drive but couldn't find anything about this problem in the forums. After continuing to look I decided to install Edgy instead, since it might be more stable. So, I went along and d/l'd Edgy, burned, etc. I pop in the Edgy cd and it comes up to the menu:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29289&stc=1&d=1176054023[/IMG]


 Like usual, I hit enter and it continues to the splash screen. The hd light shows activity and sooner or later it moves. Unfortunately the only thing it goes to is a black screen with a white underscore blinking in the top right, like so:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29288&stc=1&d=1176054023[/IMG]

The screen is unresponsive to mouse movement and ctrl alt f1,f2,etc don't work. I figured I might just need to wait, so I leave it at this screen and go to sleep. Wake up the next morning, still there. It does respond to ctrl alt del and restarts the comp.

I come back to the forums and see if I can find a solution. I see that "noapic nolapic" had fixed several hardware issues and attempt this. Same thing. I keep looking and take up the suggestion of deleting quiet splash to see where it stops loading. So, I delete it from the command and add-in noapic nolapic. It loads up to this point:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29286&stc=1&d=1176054023[/IMG]

As you can see I'm still getting some sort of error at the bottom:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29287&stc=1&d=1176054023[/IMG]

When it comes to this point it stops loading and I am able to type. Pressing ctrl alt f1 posts "^CCCA" so it's responding to key combinations. Unfortunately, it's not where I want to be. Pressing ctrl alt del restarts the system and I try it again and again. Sometimes it loads to the black screen and sometimes it just stops. Either way, it's not geting into Ubuntu.

I'm concidering doing the alternate cd install.

Further Info:
I'm on a Acer Aspire 5100 70 gig hd with a windows ntfs partition occupying the entire hd.
System is AMD Turion 64
1 gig DDR2 ram
ATI Xpress 1100
Windows XP

I'll be happy to give any info if it would help in solving this problem. I'm completely new to linux and only have this site as my guidance. So, if someone could point me in the right direction it would be much appreciated.

---

### Post by trent dillman on 2007-04-08
...

---

### Post by Kohbo on 2007-04-08
Roger sata, I'll try that. I'll post when I find out.

Edit: just did checksum of the desktop iso. It came out fine, still waiting on d/l of server version.

---

### Post by maneesh77 on 2007-04-08
I had a similar problem where the .... buffer I/O packageXXXXXX error occured. I think it was because the OS was unable to load hardware drivers.

As it turned out I had bad sectors on my hard drive

I'm no expert with ubuntu but follow the steps

1. check if CD burned properly
2. Run a memtest for 1-2 hrs
3. fdsk or scan disk your hard drive

These are just suggestions but since your trying Linux , I'm guess your already adventurous

---

### Post by Kohbo on 2007-04-08
guess I could try that while I'm d/l the server version. I would understand getting these errors for the install but I'm getting this during the LivdCD session.

---

### Post by trent dillman on 2007-04-08
...

---

### Post by Kohbo on 2007-04-08
ah ok, well then, let me try that before I try any of the other things. I did burn it at x2 speed though. But, this does seem like the logical explanation. Guess I'll be back in a while. XD

---

### Post by Kohbo on 2007-04-08
Ok justs did cd check, surprise surprise. It said:

Test completed, 1 checksum failed. guess I should burn it again? use a dif program?

---

### Post by trent dillman on 2007-04-08
...

---

### Post by Kohbo on 2007-04-08
Used alcohol, guna try another program.

---

### Post by R3linquish3r on 2007-04-08
You have bad sectors on your hard drive. Do a low level format which will write 0's to every sector of your hard drive. In other words it will make it like you just got it outta the box. Do a google search for Seagate's Low Level application which boots from CD and use the zero fill option and you'll be good to go.

Note: zero fill takes a LONG time. My 120g drive took roughly 12 hours.

---

### Post by trent dillman on 2007-04-08
...

---

### Post by Kohbo on 2007-04-08
im burning the cd right now and willl do a checkcd furing boot. Hopefully there'll be no errors.

Edit: R3linquish3r, thanx for the advice. I think I'll try other methods before I resort to erasing my entire hd though.

---

### Post by R3linquish3r on 2007-04-08
ahhh my mistake. i didnt see the discussion about it being a SATA.

---

### Post by Kohbo on 2007-04-08
Well, I used a dif program to burn the fiesty image (decided to try it again) and here I am on Ubuntu. It runs smooth off the cd-rom and I'm definately going to install it. Surprisingly I had no problem connecting wirelessly, as I thought I would. So, the problem was a bad burning program. Thank you very much you two.

---

### Post by trent dillman on 2007-04-08
No problem!

---

