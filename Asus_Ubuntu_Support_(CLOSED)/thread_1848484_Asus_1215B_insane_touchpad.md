---
title: "Asus 1215B insane touchpad"
date: 2011-09-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by s3l3ct on 2011-09-22
So, Ive got most of functuality up and running, though i cannot use hibernate OR suspend (quite annoying) and my touchpad is absolutely insane... whenever i tap it seems to think im right clicking, the pointer is extremely difficult to control, and sometimes seemes to belive im trying to scroll instead of just moving the pointer, even though i have it set on two finger scroll:confused:

PLEASE tell me there's a simple command to fix this??? It's literally driving me maaaaad!

---

### Post by Linuxisfast on 2011-09-22
Turn off C6 in CPU features of BIOS and it will hibernate fine. As for touchpad, did it behave the same with Windows? Have you added latest ATI drivers via x-swat ppa.

---

### Post by s3l3ct on 2011-09-24
I went looking for C6 in BIOS, but could not find it, any clues would be much appreciated! :)

No, it did not behave this way with windows (although to be honest I only had it on windows for about two hours, I just hate windows...) I haven't added any drivers since i got it, which is only like two weeks ago. Are the drivers found on the ASUS website, do you know?

Thanks for helping!

---

### Post by Linuxisfast on 2011-09-24
You will find the C6 feature in advanced CPU feature page of the BIOS. To add x-swapt ppa, open terminal and paste the following commands.

sudo add-apt-repository  ppa:ubuntu-x-swat/x-updates

then do

sudo apt-get upates

After thats finished, open up the system setting and select additional drivers, enable ATi driver.

I didn't even last one hour with the Win7 starter that came with my 1015B netbook, made it crawl like molasses.

---

### Post by aliaomt on 2011-10-05
did your sleep problem solved i have the same issue and also the same touchpad problem:

[http://forum.eeeuser.com/viewtopic.php?id=89461&p=1](http://forum.eeeuser.com/viewtopic.php?id=89461&p=1)

---

### Post by cric2085 on 2011-11-22
> **s3l3ct said:**
> I went looking for C6 in BIOS, but could not find it, any clues would be much appreciated! :)

No, it did not behave this way with windows (although to be honest I only had it on windows for about two hours, I just hate windows...) I haven't added any drivers since i got it, which is only like two weeks ago. Are the drivers found on the ASUS website, do you know?

Thanks for helping!

Hello there,
    Did you get the sleep problem solved?  if so can you please share your success stories.  And also I have problem activating my divers.  I returns me an error message and will not let me activate.  

BTW where did you find C6 in BIOS?  I could not find it in BIOS.  

Thanks,

---

