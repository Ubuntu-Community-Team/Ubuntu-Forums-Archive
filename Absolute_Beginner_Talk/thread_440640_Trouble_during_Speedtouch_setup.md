---
title: "Trouble during Speedtouch setup"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by psanu on 2007-05-11
Hi,

I am new to ubuntu and i installed 7.04 64bit version of ubuntu. I am using the following steps to make the connection working.
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

however i am not sure whether i am doing something wrong i am unable to proceed beyond the following command.

cd speedtouch &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012

all the previous steps have been successful.but at this step i am getting the message no file/folder firmware-extractor found.
I am not very conversant with linux commands.Am i doing something silly? I have checked the spelling and case of the parametres. could not spot anything wrong.
please help

thanks

---

### Post by psanu on 2007-05-14
Hi,

May be i am asking too stupid a question here.

I just try to understand the following command.

> 
chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012


As i understand the command < chmod +x firmware-extractor > makes the file firmware-extractor executable. If i run this command it runs without any message, so I assume  it is successful.  I am not sure about what this is for .

> 
&& ./firmware-extractor ZZZL_3.012]


Any hint will be helpful.

Thanks

---

### Post by aeiah on 2007-05-14
&& ./firmware-extractor ZZZL_3.012 means:

&& - "and then..."

./ - "execute/run"

firmware-extractor - "the software's name"

 ZZZL_3.012 - the file that firmware extractor is to extract (or the location it sends the extraction to. im not familiar with the program.)


i had a lot of problems when i was trying to set up my girlfriends speedtouch, although it may have been an older version. the version she had didnt have a driver compatible with any new kernel, so i ended up ditching it and buying a £10 ethernet modem off ebay. a lot less hastle, and it automatically dials up when you turn the modem on, regardless of the pc being on or even connected, so its hastle free for future upgrades, reinstallations, other pcs etc.

---

### Post by psanu on 2007-05-14
Aeiah,

Thanks for the reply.That makes this clear. Any way i am trying this without any success.may be i am doing something wrong.

Thanks

Psanu

---

### Post by MichaelSM on 2007-05-14
Hello psanu. Maybe you've got things working by now. If not, look at [http://ubuntuforums.org/showthread.php?t=425073](http://ubuntuforums.org/showthread.php?t=425073) which somewhere on page one will show you a link to a French site. You don't have to be able to read French. There are two download links to click on before you get into installing the drivers, which are near the top. One is a SpeedTouch deb, and the other is a bridging facility for countries which use PPPoE. You'll also need to know the code for your location, and you can access a table of information at [http://www.linux-usb.org/SpeedTouch/faq/index.html#q12](http://www.linux-usb.org/SpeedTouch/faq/index.html#q12) That table will also tell you if your location requires the br bridging for PPoE. 
In my case, I saved the SpeedTouch deb and the bridging file to disk, which is Desktop for me. if you do that, they should appear as Desktop files. Minimise your browser, and see if they're there. They should be.

Open up Terminal/Console and type in  cd Desktop.Enter. Remember that it's Desktop with a capital 'D'!!!

Then, forgetting the writing in French, copy and paste each successive line of commands, which are in dark blocks, to your Terminal. Enter after each.Put in your password when requested.

At one stage you'll get a graphical interface where you have to input some information including your VCI/VPI code you got from the link above, plus your username and ISP name in the form of xxxxxx@ISP name. It's a bit fiddly because your mouse won't work, When you want to make an entry, backspace in the blue line, then type in your credentials carefully. Once you're satisfied with your entries each time, hit Tab which will illuminate in red the OK button. Hit Enter as you deal with them. Which will move you on to the next requirement. When it's all completed, re-boot, and you should be on line.

One last thing, which stuffed me up completely. I was using an Ethernet LAN router to access the web when I was trying to get the SpeedTouch USB working. I did everything right EXCEPT to COMPLETELY DISCONNECT anything to do with the router/modem before re-booting. As in plugs for power, telephone line, and the LAN cable. If you have them, throw them out the window. The router takes over the domain and won't let anything else get into the picture. If you're on a network this could be tricky, but if you're a stand-alone user just chuck it all out. Oh, of course, plug your 'phone line into the SpeedTouch cable ...

Hope this helps.
Thanks to a lot of people who enabled me my SpeedTouch. Ubuntu Forums take the cake.
Regards,
Michael.

---

### Post by ken_38 on 2007-05-14
I'm having similar problems to Psanu's only on Edgy. I've been following Usb/AdslModem/Speedtouch guide and have been stuck at the same point, but with these differences:
1] firmware-extractor doesn't download from link but has to be saved as firmware-extractor.txt. 
2] Using this I entered, for a Revision 4 Speedtouch:
          chmod +x firmware-extractor.txt &&
          ./firmware-extractor.txt ZZZL_3.012
and received message
          bash: ./firmware-extractor.txt: cannot execute binary file
entering without the .txt suffix just tells me there is no such file [obviously].

I am on Ubuntu for the first time and appreciating it overall, but am very much new, so don't know what to do next to install modem and get onto internet. The guide doesn't appear to work in my case - but I realise it could be me. If anyone can help me out of this I'll be over the moon.

To let you know how slow I am on this kind of thing - I've had to come into this on a reply, because I can't find out how to post a message direct onto the forum - yes, this is the first I've been on, and the first I've wanted to be part of.

---

### Post by ken_38 on 2007-05-14
Sorry - please ignore the last para of my previous reply. My eyes have been amazingly opened to see the "Make New Post" spot at the top of the page. Duh!!! Rest of communication still stands however.

---

### Post by psanu on 2007-05-14
Hi MichaelSM

Thanks for the link. I will try that and let us see where i go. 

Any way i figured out something. I think apparanetly the firmware extractor that i downloaded is not recognised by the 64-bit Ubuntu i have installed. I tried with the live CD of the 32 bit version and it was working. Am I going in the right direction?

I will try to install the 32 bit version and see where i go.

Ken_38

I still has not got it right.but i hope i will get it right. Will keep posting.

Thanks

Psanu

---

### Post by psanu on 2007-05-15
Hi,

Finally able to make it work. Writing from ubuntu . So far so good. Thanks for all your help. And i think the procedure shown above does not work for 64 bit version.

thanks again for your help.

---

### Post by MichaelSM on 2007-05-16
My apologies for sending an errant post. 
I'll look it up and find out what's the difference between 64- and 32-bit scenarios. Is that related to Apple/MS sharing Intel processors these days? No need to reply. Sorry to send anyone up the garden path. 
Amazing Forum.
Well, if someone wants to send us a quick resume I shan't complain.
Thanks for all the help I get, and it's HEAPS!
Michael.

---

### Post by psanu on 2007-05-17
Michael,

Yes that bugged me lot. Somehow the 64bit version is not recognising the firmware-extractor as a program. My system is Intel core 2 Duo  with 2GB RAM. 

Thanks

Sarada

---

### Post by StevenHarper on 2007-06-04
Hi I have made a 64 bit Speedtouch modem Manager - it works with 64bit versions of Ubuntu and with Speedtouch 330 modem : you can get it here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/](http://www.squeezedonkey.com/svn/linux/trunk/releases/)

And post here for any support you need

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

Steve

---

