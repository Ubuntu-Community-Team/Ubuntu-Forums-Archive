---
title: "do i need to install graphics drivers etc ?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-10-30
Hi 
I'm not sure if I need to install/enable graphics on my laptop (Toshiba M50-MX500). The graphics controller information I found is    " Intel® Graphics Media Accelerator (GMA) 900 with up to 128MB shared video memory".

I came across a few posts which mention installing graphics drivers for ATI / Nvidia cards, so I was wondering whether I needed to do similar thing with my system as well.

Also, how can I check the graphics information? For e.g. theres 'fglrxinfo' for ATI cards , but what about mine.

Thanks.

---

### Post by L815 on 2007-10-30
Hey

I'm also new to Linux/Ubuntu but maybe some info I can give may help.

Check System > Administration > Restricted driver manager and see if your graphic card is detected and or enabled.

If neither I think you can search ATI in the Synaptic Manager and see what comes up. That's as far as I can help this way lol (sorry)

You can try and install it using the actual manuf. drivers. Download the right one, save it to where you'd like, open up terminal then drag and drop the file and press enter.

You might have to do "sudo then drag file" (without quotes). 

Hopefully that is somewhat helpful.

---

### Post by genbuntu on 2007-10-30
thanks for your suggestions.
However, since my graphics is not ATI, so I guess installing anything relating to ATI won't work.

The good thing is:  System > Administration > Restricted driver manager mentions
"Your hardware does not need any restricted drivers."

So I guess there is nothing to configure or update. :)

BTW I did install 915resolution through synaptic but again there is nothing to change in that as well.

---

