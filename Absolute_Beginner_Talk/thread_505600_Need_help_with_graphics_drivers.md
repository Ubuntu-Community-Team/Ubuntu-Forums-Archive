---
title: "Need help with graphics drivers"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-07-20
Ok... I'm still kinda a noob at Ubuntu, and I thought I could easily install the new graphics drivers that ATI put out. So I downloaded it from the website and then proceeded to install it. After I ran the script to install it it said i should restart, so i did. when I booted back up, compiz wasn't working in X or XGL, and i couldn't figure out why so i gave up and uninstalled the driver using ATI's instructions. I rebooted, and this left me with an xorg.conf file that said to use the fglrx driver which wasn't available. So now I am stuck with the command line and at a loss for what to do...

I either want the previous fglrx driver that I was using with XGL and Compiz, Or the newer fglrx driver that I think works with X and Compiz. If someone could help me with this, it would be great. Im guessing my first step would be to give me a GUI by specifying the default driver in the xorg.conf file, but I'm not quite sure how.

Thank you in advance! :)

Bohlio

---

### Post by mikewhatever on 2007-07-20
Is there a backup of xorg.conf? Look for it with the following command
> ls /etc/X11

---

### Post by Bohlio on 2007-07-20
Im pretty sure that I didnt make a backup, But even if I did, It would still be using fglrx, as that is what I was using before. Right now I am in windows because I cant get a GUI in Ubuntu... Cant I just change an entry in the xorg.conf file to point to the default driver that comes with ubuntu? from there I could have a GUI in ubuntu and It would be alot easier to work from there instead of constantly booting between windows and Ubuntu.

Thanks :)
Bohlio

---

### Post by jawinterton on 2007-07-20
to edit your xorg.conf file type into terminal (can be accessed in safe mode):

sudo nano /etc/X11/xorg.conf

---

### Post by Bohlio on 2007-07-20
thank you, I didnt know what the command line editor is :)

so what do i change "fglrx" to? is it just something like "default driver" or what?

---

### Post by jawinterton on 2007-07-20
You know what... I'm not even entirely sure.  I've been having a similar headache with my nvidia card.  If I hear of anything I'll let you know though.  If you have any other really basic questions, I might be able to help.  I'm also a noob though.

---

### Post by qamelian on 2007-07-20
> **Bohlio said:**
> thank you, I didnt know what the command line editor is :)

so what do i change "fglrx" to? is it just something like "default driver" or what?

You should be able to change it to either ati or radeon instead of fglrx. That should swith you to the open source ATI driver.

---

### Post by Bohlio on 2007-07-20
Ok, Before i read your previous post, I realized that I still had the FGLRX install script, so from the command line I installed that and now I am back into Ubuntu. Now the problem is that when I start an XGL session, nothing is readable because the graphics are so messed up. If I can successfully run Compiz in X with the fglrx drivers, I wouldnt even have to worry about the XGL problems.

I read somewhere that the most recent fglrx driver will allow you to run compiz in X, but I cant figure out how...

---

