---
title: "Question about memory usage"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by uri on 2005-06-09
I am totally new to Ubuntu and I have a question about the memory usage readings (in the tool where you can see the running processes etc...)

I have 2 x 512 MB of RAM installed in my laptop (I am 100% sure  :wink: ), but when I look at the numbers, it says the following:

Memory : 269 MB out of 885 MB

Swap : 0 bytes out of 1,4GB


Now I think you allready know what I'm going to ask:

Why is there a difference between the actual RAM in MB's I have in my laptop and the amount according to the graffic?

I also tried "free -m" but I still don't get it,..

the output of 'free -m" says:

          total     used     free     shared     buffers     cached
Mem:  885      269       616      0             13            124
-/+ buffers/cache:       131      753
Swap: 1466    0           1466


(I know that the 269 value is because at that moment I had some things running, so it was a normal value considering, but I'm wondering whats with the 885)

Would be great if someone could explain this...

---

### Post by ltmon on 2005-06-09
Firstly "swap" is actually a disk partition that Ubuntu set up to use in the case that you run out of memory.  When this happens the OS will cause the memory to be written to the swap partition.  You can get fancy about configuring what size that partition is when you install, but in general the default setting will be fine.

As for the reading of 885mb for your total memory, I would suggest checking in your bios to see if memory is allocated to an on board graphics card.  Mine works like this, I have 512MB memory, but have allocated 32Meg to onboard graphics.  The operating system only detects that I have 480MB available.

L.

---

### Post by uri on 2005-06-09
[QUOTE=ltmon]Firstly "swap" is actually a disk partition that Ubuntu set up to use in the case that you run out of memory.  When this happens the OS will cause the memory to be written to the swap partition.  You can get fancy about configuring what size that partition is when you install, but in general the default setting will be fine.

As for the reading of 885mb for your total memory, I would suggest checking in your bios to see if memory is allocated to an on board graphics card.  Mine works like this, I have 512MB memory, but have allocated 32Meg to onboard graphics.  The operating system only detects that I have 480MB available.

L.[/QUOTE]
 Hmm, could be, I'll check my bios

---

### Post by clarke.rainey on 2005-06-10
I read somewhere that the standard i386 kernel could mot detect above more than like 800 or 900 MB of ram...

---

### Post by LongTooth on 2005-06-10
Yes. That is correct. i386 does not recognize it. I asked the same question after adding an additional stick of 512M of ram. The solution was as simple as ´apt-get install i686´. That did the trick. My machine now show the whole 1 Gig of ram.

---

### Post by poofyhairguy on 2005-06-10
[QUOTE=uri]
Why is there a difference between the actual RAM in MB's I have in my laptop and the amount according to the[/QUOTE]

I notice this too. Doesn't bug me as long as swapping doesn't start. Maybe Gnome can't see RAM that it essentially uses and needs? I don't know.

---

### Post by uri on 2005-06-10
[QUOTE=LongTooth]Yes. That is correct. i386 does not recognize it. I asked the same question after adding an additional stick of 512M of ram. The solution was as simple as ´apt-get install i686´. That did the trick. My machine now show the whole 1 Gig of ram.[/QUOTE]

I tried this, but I get the message that the i686 package isn't found.

Maybe I'm doing it wrong...

I entered "sudo apt-get install i686"

---

### Post by poofyhairguy on 2005-06-10
[QUOTE=uri]I tried this, but I get the message that the i686 package isn't found.

Maybe I'm doing it wrong...

I entered "sudo apt-get install i686"[/QUOTE]

try:

sudo apt-get install linux-686

---

### Post by uri on 2005-06-10
Aaah  :) 

Now he found the packages indeed.

I rebooted and the total RAM is now correct (1012)  \\:D/ 


Really appreciate the help you guys...

---

### Post by dethwulf on 2005-06-10
I recently upgraded to the i686 images. You'll need a couple actually. I suggest going through Synaptic (sp?).

Just a suggestion, keep your i386 images. Grub should boot with i686 by default after you upgrade, but having a backup image was nice when my sound cut out on me after upgrading. Took me a little while to find drivers to reinstall.

---

