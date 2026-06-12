---
title: "Another Internet connection problem"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Tribull on 2007-08-20
Hi all,
Please have pity on me as I am very new at this.Only my second day playing with Linux.I have done a search, and seen others with connection problems, but mine seems a bit different.I have only used the live cd so far, and have not installed it yet.The problem is every time I boot up with the cd I can't connect to the internet until I go to the terminal and enter "sudo pppoeconf", and after the hardware scan, and answering all the questions I can connect.
The problem is when I boot up again in live cd mode I have to do that all over again.Is this some thing that will go away after I actually install on the hard drive?Also I have to say what a high quality os this is, after spending what seems like for ever in windows I can't wait to start using this all the time.I just need to figure out this one problem, and I will be ready to install.

My specs
Amd 3000+
1.5 memory
verizon dsl with westell wirespeed modem

---

### Post by Happy_Man on 2007-08-20
> **Tribull said:**
> Hi all,
Please have pity on me as I am very new at this.Only my second day playing with Linux.I have done a search, and seen others with connection problems, but mine seems a bit different.I have only used the live cd so far, and have not installed it yet.The problem is every time I boot up with the cd I can't connect to the internet until I go to the terminal and enter "sudo pppoeconf", and after the hardware scan, and answering all the questions I can connect.
The problem is when I boot up again in live cd mode I have to do that all over again.Is this some thing that will go away after I actually install on the hard drive?Also I have to say what a high quality os this is, after spending what seems like for ever in windows I can't wait to start using this all the time.I just need to figure out this one problem, and I will be ready to install.

My specs
Amd 3000+
1.5 memory
verizon dsl with westell wirespeed modem
Once you install, I suppose you would only have to do this when you reboot.... and as Linux systems are built to stay up for a VERY long time (think servers --> the same code is in here), that shouldn't be very often.

---

### Post by Jverse on 2007-08-20
Being new as well, I would think that using the Live CD, the driver is stored in memory and when you reboot it loses it. When you actually install on the HD it should then store the driver in physical format and not need to be reloaded. But that is just my guess....:confused:

---

### Post by Tribull on 2007-08-20
Thanks, that does make a lot of sense.I don't usually keep my computer on 24-7 so if there is a way around this that would be great if not I guess I can deal, my wife on the other hand I'm not sure.Just saw the other post yes it would make sense the driver being stored in memory I didn't think of that.Ahhh... so much to learn

---

### Post by Happy_Man on 2007-08-20
Hey, that is what makes it so fun! The thrill of learning something completely new.... it must feel like the cavemen learning how to cook food. :D

---

### Post by lgcabarcas on 2007-08-20
After you install on HD all of your configurations willl remain, as live CD stores them on RAM you have to go along the process every time you boot, but this will not happen when you install Ubuntu on your HD.

Don't worry be happy

---

### Post by Tribull on 2007-08-20
Thanks so much this is what I was hoping, Also instead of starting a new thread how do I make a folder hidden?

---

### Post by st33med on 2007-08-20
> **Happy_Man said:**
> Hey, that is what makes it so fun! The thrill of learning something completely new.... it must feel like the cavemen learning how to cook food. :D

I really couldn't cook any food... So I just banged pots and pans together to wake up the neighbors :D

Edit: I am an idiot, I will come back with an answer

---

### Post by Happy_Man on 2007-08-20
You just put a period in front of it. So, instead of a folder named "folder", you would make it hidden by changing its name to ".folder" .

---

### Post by st33med on 2007-08-20
add a '.' to the beginning of a filename/folder

---

### Post by str8line on 2007-09-06
If you are still using the Wirespeed modem (I am assuming the 2110 model) then you will need either a software connection or a hardware connection to establish the PPPoE connection.  The new modems from Verizon all have built in router functionality and would mean that either from the liveCD or from full install you would never need to use the pppconf again as the connection is now not on the computer but stored in the modem/router.

---

