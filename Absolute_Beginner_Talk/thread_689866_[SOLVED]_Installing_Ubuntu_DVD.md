---
title: "[SOLVED] Installing Ubuntu DVD?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-06
Alright, so I burnt Ubuntu to a DVD, I went on my laptop, pressed F12 and then I choose the CD icon it booted from the DVD I installed Ubuntu to my laptop success, then I put the DVD into my Desktop computer, it read the DVD on Windows XP, so I restarted my computer pressed F12, then pressed 4, because the number 4 beside it says boot from CD, I did that, but it does boot and says press F1 to try again. Now I know this has something to do with my DVD drive, I have two drives, I have tried it in both drives, but somethings wrong with them I guess? Maybe the bios? I don't know, but also when I go to my computer it shows both the Drives, and ones called CD Drive (D:) the other is CD Drive (F:) Notice how they both say CD? Yet they are a CD/DVD drive? Yeah I believe thats the problem, anybody wanna help me fix this?

Edit wait theres a third drive, that's in my computer that says, DVD/CD Drive (E:), Now I only have two DVD drives built into my computer yet theres three showing in my computer.

---

### Post by randy78 on 2008-02-06
Enter you bios, select Boot From (name of dvd drive) as the first device to boot from and re-try.

After that, it's as simple as clicking the Install icon on the Desktop and following the prompts.

Good luck and welcome to Ubuntu!

---

### Post by Metalbuntu on 2008-02-06
I also had to setup my bios to boot my CD/DVD drive 1st when I installed Ubuntu.

---

### Post by blasteryui on 2008-02-06
How do I get to my bios? 
I have also noticed this.
When I put the DVD into my first DVD tray, it does not read the DVD.
When I put the DVD into my second DVD tray it does read the dvd * this is on windows xp*
then when I restart my computer and try to boot from DVD, if I put it in the first tray it trys to read it and tries for about a 1 min, then it says press F1 to try again, AS SOON AS I put the DVD into the second tray, it will instantly say Press f1 to retry, so by the sounds of it, it must mean that it's not reading the second DVD tray at all, so yeah how do I get my bios?
I have a Dell Dimension 4550.
I checked for Dell dimensions and it says press F2 to access your bios, and I have done that but I don't see anybody Boot from DVD.

---

### Post by randy78 on 2008-02-06
I'm not familiar with your setup, but after you enter the Bios, look for something similar to "Boot Sequence" and then enter that dialog... It may be under an "ADVANCED" tab, if your Bios has one showing.

You will be able to set the order in which your devices are booting through that.

After you have finished, be sure to save your changes as you exit Bios.

Basically, your computer isn't set to boot from the DVD drive and will only boot from the hard drive, until you change the order in Bios.

---

### Post by blasteryui on 2008-02-06
> **randy78 said:**
> I'm not familiar with your setup, but after you enter the Bios, look for something similar to "Boot Sequence" and then enter that dialog... It may be under an "ADVANCED" tab, if your Bios has one showing.

You will be able to set the order in which your devices are booting through that.

After you have finished, be sure to save your changes as you exit Bios.

Basically, your computer isn't set to boot from the DVD drive and will only boot from the hard drive, until you change the order in Bios.

Thanks a lot, it worked.

---

### Post by randy78 on 2008-02-06
> **blasteryui said:**
> Thanks a lot, it worked.

Awesome

Please remember to use the Thread Tools and mark your post as SOLVED so others can use the info 

:guitar:

---

