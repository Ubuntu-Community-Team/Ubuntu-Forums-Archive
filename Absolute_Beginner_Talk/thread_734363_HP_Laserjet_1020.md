---
title: "HP Laserjet 1020"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2008-03-24
I installed Ubuntu 7.10 a few times before and noticed that my Hp Laserjet 1020
would never work correctly. Ubuntu would see and recognize my printer but every
time I tried to print, it would go to the Que but never print anything out, Basically
It would just sit there forever until I canceled the print job.  Has this issue been fixed?  
I just reinstalled Ubuntu again but I haven't connected my printer up yet.......  

Thanks guys :)

---

### Post by stchman on 2008-03-24
> **Orbital75 said:**
> I installed Ubuntu 7.10 a few times before and noticed that my Hp Laserjet 1020
would never work correctly. Ubuntu would see and recognize my printer but every
time I tried to print, it would go to the Que but never print anything out, Basically
It would just sit there forever until I canceled the print job.  Has this issue been fixed?  
I just reinstalled Ubuntu again but I haven't connected my printer up yet.......  

Thanks guys :)

You need to update the foo2zjs driver that comes with Ubuntu.  I have a procedure that will do this.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Make sure you select Gutsy and not the older Feisty, Edgy, or Dapper.  Works great on my Feisty box.

---

### Post by Orbital75 on 2008-03-25
Thank you,  I'll have a look.....:)

---

### Post by Emily on 2008-04-13
> **stchman said:**
> You need to update the foo2zjs driver that comes with Ubuntu.  I have a procedure that will do this.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Make sure you select Gutsy and not the older Feisty, Edgy, or Dapper.  Works great on my Feisty box.

Thanks for writing out such detailed instructions. I tried running your script and it asked me to insert the Gutsy install disc. I burned a new copy and did that, but it's gotten stuck on the test page. The last line it printed was "Printing custom test page /usr/share/system-config-printer/testpage-letter.ps," but nothing prints. Then the script ended. Any idea of why that would happen?

---

### Post by Manaus on 2008-04-14
Hello stchman,
I carefully followed the instructions you posted on [http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)
but I experienced exactly the same problem Emily described. Printer is correctly detected but it hangs on test page printing job. and in the conole I just see:
"Printing custom test page /usr/share/system-config-printer/testpage-a4.ps"

(I changed the format in a4 since it is the one I need) 

Could you please give any additional hint? Probably Emily and I have the same problem.  Could you please shade some light on us?

Thank you in advance!
Bye
Manaus

---

### Post by Manaus on 2008-04-14
Hello stchman,
I would just to say thank you! Your script worked for me I just needed to switch off and on my printer to start printing properly! 
It may sound stupid but you could add this (apparently) useless step at the end of your instructions! 

By the way you script worked fine for me so thank you!

Regards,
Manaus

---

### Post by Emily on 2008-04-14
LOL, that worked for me, too! Thanks to both of you.

---

### Post by stchman on 2008-04-14
> **Manaus said:**
> Hello stchman,
I would just to say thank you! Your script worked for me I just needed to switch off and on my printer to start printing properly! 
It may sound stupid but you could add this (apparently) useless step at the end of your instructions! 

By the way you script worked fine for me so thank you!

Regards,
Manaus

I tell you at the end of the tutorial about 3/4 the way down to cycle power on the printer and reboot the computer.  That step has always been there.

> 
Your Zenographics based printer should now function under Ubuntu as well as it does under Windows.  Cycle power on the printer and reboot your computer.  Happy printing.


What I need to do is put an echo message in the script telling you to cycle power on your printer and then hit any key to reboot.

---

### Post by LowSky on 2008-04-14
[http://localhost:631/](http://localhost:631/)

enter this web address into your web browser and set up your printer... couldnt be easier

or use HPLIP, both do the job like champions

---

