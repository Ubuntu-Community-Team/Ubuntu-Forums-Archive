---
title: "Single boot Ubuntu 9.10 on Macbook 2.1 (no refit, no osx) - start up delay fix?"
date: 2010-03-09
forum: Apple Hardware Users
---

### Post by katejones on 2010-03-09
[FONT=-moz-fixed]I unscrewed my macbook 2.1, formatted the disk to FAT32 with Vista (with  an external sharkoon SATA dock), put the disk back in and installed  Ubuntu 9.10 on my Macbook using the whole disk. Surprisingly the Macbook  is not falling apart (have some leftover screws, and there was a rubber  padding strip next to the harddisk that somehow got stuck and folded  double and so I pulled it out) and it's running great! 

I haven't had much experience with Ubuntu so I'm still figuring things  out, but the wiki helped me set things up and everything is running fine  (including wireless internet, right click with the touchpad, and sound through my  headphones after unmuting them  :)  ) 
Shut down is in seconds. (I did manage to make the 'shut down/user' menu  vanish from the top bar??) 

The only thing I'm not completely happy with so far is that there is  quite a delay when I boot up. 

There is a grayish blank (mac boot color but no apple or spinning thingie) screen  for about 20 seconds, and then it finally starts searching for something  bootable that's not Mac OSX (at least that's what it seems to be doing  from what I read online), and then it will load GRUB2 etc. and start up  in a few seconds. 

I am NOT using rEFit, this is a true single boot with nothing else on  the disk but Ubuntu, so after the delay I don't have to choose what to boot. 

I read online that I should 'bless' this disk from a Mac OS to get rid  of the boot delay, but that walkthrough assumes that I HAVE some OSX installed on the  same disk, AND that I AM using rEFit. 
Both of which I'm not using.

I there another way to fix this?? 
I do have another machine with OSX (but no way that I know of of connecting that to my macbook??)
Also Id rather not screw open (/up) my macbook again.

Thanks! 


[/FONT]

---

### Post by cesarse on 2010-05-04
Have you read [this]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8940677")? Mac OS doesn't need to be installed to bless work.
I'm not using a GPT partition scheme (I'm pure MBR and I think you are too because you've used Windows to format HD) so even rEfit isn't necessary.

---

