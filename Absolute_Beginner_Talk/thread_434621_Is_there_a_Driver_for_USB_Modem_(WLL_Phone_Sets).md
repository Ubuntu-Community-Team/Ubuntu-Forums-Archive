---
title: "Is there a Driver for USB Modem (WLL Phone Sets)?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by ishaqmalik on 2007-05-06
Hi,

        I have everything working fine on my system, but I can't seem to find a driver for my USB Modem. I use a WLL Phone Set (LG LSP 3500 to be specific) which also works as a USB modem but I can't find a driver for Linux (I have already checked the LG site)

       any help would be very appreciated...

Regards,
Ishaq

---

### Post by rfs1970 on 2007-05-06
Hi there,

I had a very bad time to set up my usb (cable) modem,
and I am not sure if you could use the same method 
to fix your problem, but... If you wanna try:

[http://ubuntuforums.org/showpost.php?p=2603397&postcount=3](http://ubuntuforums.org/showpost.php?p=2603397&postcount=3)

r.

---

### Post by ishaqmalik on 2007-05-07
Thanks Bro, Let me check your method... I'll let u know of the outcome...

---

### Post by eye4u on 2007-05-28
I am looking for VISTA supported driver of LG LSP-3500 USB modem . Please advise.....?my e-mail is [email]amer_7300@yahoo.com[/email]

---

### Post by divali on 2007-05-28
I' m not familiar with your modem. but when I had a usb modem I the found the  'eagle-usb.org' drivers worked. And the forum to be very useful and help solve my difficulties trying to get my Sagem modem to work. Give my regards to Benny the Mainman at Eagle-usb.  I Hope this helps.

---

### Post by ishaqmalik on 2007-05-28
Dear Aamir,

            I only have a modem that came on the CD (also available from the internet) when I purchased the USB dongle, that works fine with XP, I don't konw if it works on Vista as well (I don't have Vista). If you need it, I can send it to you...

Regards,
Ishaq Malik

---

### Post by ishaqmalik on 2007-05-28
@ rfs1970: I have not been able to compile the kernel as of yet (have been busy in office work lately), I hope to compile it this weekend...

---

### Post by zabi_rauf on 2007-05-31
Hello ishaq .I am hoping that you are either using a worldcall or v-ptcl connection.This is the link where you can configure your modem.it is for v-Ptcl

[http://sbjaved.blogspot.com/2007/04/getting-internal-modems-winmodems-to.html](http://sbjaved.blogspot.com/2007/04/getting-internal-modems-winmodems-to.html)

it originally came on spider magazine but thanks to this guy.He changed it into an online version.And if you want to use it for world call then these are the changes you are going to make

in wvdial.conf add the following lines while writing other lines.

Init3=at+crm=1;$lgpkt=3

and replace the user name and password by wcall.(where ever it is in the guide)

these are the changes for worldcall.
Enjoy surfing net on Ubuntu

---

### Post by ishaqmalik on 2007-06-05
Thanks, It sure helps... (means I should resume my subscription with spider ;) )

---

