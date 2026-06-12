---
title: "need help setting up a projector.  ASAP!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-06-20
hi all.  my friend is doing a presentation today and just found out that she can't use her dad's laptop to show the powerpoint slideshow.  so i'm here to help her with my ubuntu linux laptop.  i don't own powerpoint and i don't plan on installing it, but can't i just play the .ppt file in openoffice?  and should i have any troubles setting up a projector on my intel graphics card?  please help.

---

### Post by Cypher on 2007-06-20
Yes OpenOffice will play the .PPT file and setting up the project should just be a matter of connecting it to the video-out and hitting Fn-F8 or something, isn't it?

---

### Post by locke.dragon on 2007-06-20
on my laptop, it's "FN+F8" is a key labeled "CRT/LCD," is that the one?  i've always wondered what that button did.  :p

---

### Post by Cypher on 2007-06-20
Yuppers..that's the one..that CRT/LCD is basically a way of switching between driving just the LCD, LCD & CRT or just CRT..

P.S, now I'm assuming that the FN-F8 has no special hooks in Windows to do all of this and it's more hardware driven..if not..eek..;)

---

### Post by locke.dragon on 2007-06-20
and what's CRT?

---

### Post by Cypher on 2007-06-20
Cathode Ray Tube..boy..how long you been using computers! :p

In this case, it basically means the VGA port in the back of the laptop to which you'd be connecting the projector..

---

### Post by locke.dragon on 2007-06-20
ok.  cool.  thanks!  and i've been using computers ever since i was four...  let's see...  that's...  almost 12 years...  :p  lol!

---

### Post by Cypher on 2007-06-20
Damn young'uns and their LCDs and fancy shamncy new technology..forgetting what started it all..so you didn't get the appreciate the beauty of Hercules mono-chrome or the sheer beauty of 4-color CGA monitors..:p

Anyway..we digress on being entirely off-topic..:)

---

### Post by locke.dragon on 2007-06-20
lol!  no, i didn't sadly.  :p  but let's use clean language please.  ;)

---

### Post by racso39 on 2007-06-20
In WIndows if you connect a projector it will detect it once and you hit fn-f8 (inmost laptops), does that happens in Ubuntu Linux?

---

### Post by locke.dragon on 2007-06-20
from what cypher has said, yes, but i don't speak from experience.

---

### Post by Cypher on 2007-06-20
And I'm largely speaking from the Windows experience. You should try it out on your laptop right now and see if indeed you can get the LCD to stop working and then work again if you keep pressing that key-combo..

---

### Post by locke.dragon on 2007-06-21
the presentation went great.  thanks!  i would have been totally lost without you guys.  :)

---

### Post by abish on 2007-09-20
it didnt work for me.
i am using HP Compaq laptop with NVIDIA graphics (3425 AU)
when i connect my projector... nothing is displayed... not even after pressing Fn+F4!!
what do i do now..?
any help..?
(PS: I couldnt use Projector today in my seminar.. so every one said.. Ubuntu is of no use :( )

---

### Post by lisati on 2007-09-20
I haven't used it for a while, I think on my Toshiba laptop it's Fn+F4. The last time I tried using the s-video terminal to output a presentation via Open Office on Ubuntu, I had to tinker with the screen resolution as well.....

---

### Post by abish on 2007-09-20
well, now i can use the external display.. but the only problem is that to toggle.. i need to restart... !
is there any simple solution?
the function+f4 doesnt work!

---

### Post by jbiskupiak on 2007-09-20
It requires modifying a file.  See text below.  This is from several sources and works fine for me.

External beamer on laptop
I have a laptop and needed to make a presentation. I spend a lot of time to find the solution to my problem:

How to connect a beamer to a laptop?

The solution depends on your graphic card

Intel cards (i810 driver)

   1. modify you xorg.conf
      Maybe it is a good advice to make a backup before
      Code:

      sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.beamer # Backup
      sudo cp /etc/X11/xorg.conf.beamer /etc/X11/xorg.conf # Restore

      Code:

      sudo gedit /etc/X11/xorg.conf

      find this part and add the three * lines
      Code:

      Section "Device"
              Identifier      "Intel"
              Driver          "i810"
  *           Option    "MonitorLayout" "CRT,LFP"
  *           Option    "Clone" "true"
  *           Option    "DevicePresence" "true"
              BusID           "PCI:0:2:0"
      EndSection

---

### Post by abish on 2007-09-23
by doing that.. can i toggle between the projector and the laptop display?

---

