---
title: "help installing Ubuntu7.10 on a separate hdd"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by quattroo on 2007-11-20
hello,
i am completely new on this, i have a copy of Ubuntu7.10 live cd and working properly as a live cd but i cant instal is on a separate hdd i have vista installed on a 2x 250gb RAID0 and i have a 500gb SATA hdd formated and ready to use but every time i instal ubuntu nothing happens no dual boot i just boot in to vista as if i only have one OS also the 500gb hdd just disappears from vista !!! i have to format  it again to show up in again .

i tried many times, at one attempt i had dual boot but when i select i only get Grub>_

---

### Post by Skefflock on 2007-11-20
The second drive disappears from Vista, because Vista can't mount drives with Linux file systems.
What about the problem, try to use a flag at the last page of Ubunbu installation config. It should be a little button called "Advanced". On what drive to put the grub. Cause you have Vista's one as a primary, then you need to choose that one. I guess, if you have a hardware level raid, than it won't be very different from just two separate HDDs. Then should work.
And also here's nice post [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by quattroo on 2007-11-20
thanks, ok in Advanced tab it says mount grub: hd0

---

### Post by quattroo on 2007-11-20
anyone!!! im beginning to hate Linux :(

---

### Post by quattroo on 2007-11-22
anyone!!!!!!!!!!!!!!!

---

### Post by natehatewindows on 2007-11-22
ill tell you one thing well maybe two but only one for sure.

to use liux you must be a little patient. your situation is fairly uncommon and i dont think a lot of us know how to solve this. have you tried to google? earch other forms? ask on other forum? 

[www.linuxquestions.org](www.linuxquestions.org) is a good forum to try along WITH the ubuntu forum. 

the seco thing is that you might need some other kind of boot loader, maybe one that has its own partition or something. I havenever worked with raid and i have never worked with this kind of boot loader but it make sense to me. The boot loader partition would load when you turned on your computer and then you would tell it where to boot. Its just more idependent that say grub. i guess they are kinda like thier own little OS. so maybe start to look at these and ask about them. I have actually kind been wating to use one because i have heard they are very cool, dependable and have a great graphical interface. 

i hope you dont give up on ubuntu or linux. Vista is so far bihind the times and i really thing that if you give linux a chance you will be wiping vista in the near future. just rememeber that you need to have patients and dont get frustrated if it take a week or two to figure out your problems, all of us have had to wait and atleast you have another os to use. You should not start posting "where else can i get help" or whatever just because your in a hurry..there are lots of other people who need help too and if you want to find more support thats why there is google. dont take anything i say personally, i understand you want ubuntu but just give it mmore than two days for your situation. 

thanks and best of luck!

---

### Post by natehatewindows on 2007-11-22
also please give me the details of you set up and what the different HD's are used for and ill see if i can help you a little about what skefflock was talking about.

---

