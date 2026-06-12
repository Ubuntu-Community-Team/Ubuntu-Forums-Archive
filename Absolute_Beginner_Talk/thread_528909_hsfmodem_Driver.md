---
title: "hsfmodem Driver"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-08-18
Howdy:

When I install the Linuxant hsfmodem driver, it kills my sound. I wrestled with it a month ago, and gave up and removed the driver to get the sound back.

I tried again today. Same thing - it kills my sound.
Immediately after installing it, the sound worked, but after restarting, the sound is dead.

Any ideas?

Rich

---

### Post by oilchangeguy on 2007-08-18
it's time to graduate to highspeed internet.
[http://www.qwest.com/residential/products/internet/index.html?refCode=RES000000107&gclid=CJm59YPe_40CFQMYFQodikArKw](http://www.qwest.com/residential/products/internet/index.html?refCode=RES000000107&gclid=CJm59YPe_40CFQMYFQodikArKw)

---

### Post by RichPicker on 2007-08-20
Quest is not available where I live.

---

### Post by oilchangeguy on 2007-08-20
any other company that offers high speed in your area?

---

### Post by RichPicker on 2007-08-20
I am house-sitting. The house has dialup, which is free to me. 
I don't have the permission to install high-speed.
If I can get the modem you work, I won't have to drive to town to use the library to retrieve my email.

---

### Post by RichPicker on 2007-08-20
When I try installing the driver from the Dell site, the installation hangs and it says something about it's looking for a compiler - this way beyond my ability to understand.

The driver from Linuxant.com kills my sound card.

It seems overly difficult to me. What is the reason for the complicated installation of a modem driver? Never mind. Don't answer that. 

Can anyone help me get the modem driver to work?

Thanks.

---

### Post by RichPicker on 2007-08-20
The driver from the Dell site killed my sound card.

I am frustrated and pissed off. if anyone wants to help, I will appreciate it.

---

### Post by RichPicker on 2007-08-20
OK. Back to the original question. When I install the hsfmodem driver, it kills my sound card.

PLEASE do not reply with suggestions of high-speed internet, or other such help. I get too confused trying to follow it.

If you would please help, I would first like to fix why the modem driver kills the sound card. Then I can tackle the next hurdle.

Sorry for the frustration, Please don't ask me to divert from the original question. (Though I realize you are being helpful in the ways you know best.)

Thanks,
Rich

---

### Post by funsport on 2007-08-20
I'm assuming you are using a laptop because you are house sitting. Is it safe to assume then that the sound card and the modem are built into the motherboard?

The only thing I can think of is the modem and sound card are using the same interrupt, IRQ. Open up a terminal and 
       Type :            lspci -v
       Response:     you should look in the list for data related to your sound card(under sound?) and modem (under serial Controller). Check to see if the IRQ are the same. If they are, then you will have sound and modem 'fighting' for the use of the bus lines in the computer. Each device should have an unique IRQ unless the device specifically states it can operate with shared IRQ.

-funsport

---

### Post by RichPicker on 2007-08-21
Excellent. Thank you. I don't see any repeated IRG numbers, but will send the text to the Linuxant tech support folks who are helping.

Seems like the sound card in this laptop is the weakest link - every time I add or change something, it causes a problem with the sound card.

Thank you,
Rich

---

### Post by RichPicker on 2007-08-21
Here's what the Linuxant tech says. What should I do?
--------
Since you are probably have a HDA sound device and probably modem as 
well, it's the reason why it doesn't work anymore, these modules are 
critical for your sound support and you can't load them.

Did you manually installed ALSA? I have seen similar issues in the past
 when users did manually install a new version of ALSA.
--------

---

### Post by funsport on 2007-08-21
if you didn't get a conflict in IRQ numbers, you are so close in getting that modem working.

I searched all over the net and each solution I found was not complete to my satisfaction.Lots of assuming and then hope it works thinking. It took me about 2 WEEKS to digest all those solutions and came up with a solution where there is no guess work! You will get the info of how your computer sees your modem and then you can go from there.

I put the process in my first post on UBUNTU. You should be able to search for my name and find my post describing the process. Just look under the title "USR 5610B dialup modem works"

I'd be curious if your modem works after reading my process.

---

### Post by funsport on 2007-08-21
I just saw your reply when I posted. 

if that lspci comamnd showed that you do not have irq conflict, and also you do not have a port conflict between that sound card and modem, then follow my process in my modem post.

I believe this will make your modem configuration for Ubuntu uniquely separate from your soundcard and therefore your sound card should work.

---

### Post by RichPicker on 2007-08-22
Here is what the Linuxant support person says:
----
can you try with another kernel to see if there is a difference?

Technically, the HDA code in the driver was compiled against the wrong 
kernel headers and this is the reason why it doesn't work. This is a 
known issue when ALSA is manually installed, that code changes the 
kernel modules but not the kernel headers and the result is that 
problem. This is a problem with ALSA, it breaks the assumption that the
 
kernel headers are up to date with the currrntly running kernel and
 modules.
----

I haven't a clue what they are talking about. When I mention how awful Ubuntu is, I get tons of replies about how it's just 'me' and my 'laptop'.  I'll stay with Ubuntu for a while longer, but it certainly is tons of trouble.

Rich

---

### Post by funsport on 2007-08-24
In simplistic analogy, they are basically saying Progam A (the kernel) has part 1 and part2 as a matching pair. Program B (ALSA) overwrote part1 in Program A, causing mismatch.  That is why Program A is not working.

The reason they gave does not make sense because you just installed Ubuntu 7.04 from the disk. All "parts" of the program should match.

I have been assuming too many things. Can you answer questions below and maybe I can look around the net to find a solution to try.

1. What model laptop do you have?

2. Is the soundcard built into the motherboard? And what brand (if known)?

3. Is the modem built into the motherboard or is it a card that you can remove? ( what brand (if known)?

4. With Ubuntu installed, without the modem driver, the sound works. Sound is killed when Linuxant driver is installed, correct?

5.Before you give up on ubuntu, I would try installing another disto, like knoppix, to see if your sound disappears also with the Linuxant driver installed. Also, did Linuxant  send you the right driver version?

---

### Post by RichPicker on 2007-08-24
Thank you very much. I sent a post to Launchpad.net, but they only gave me the URL of where to download the linuxant driver. Oh well... I'm not going to give up on Ubuntu, and I hope that by complaining, maybe some day, the developers will make it as useful as windows or mac.

1. What model laptop do you have?
- Dell Inspiron 1300, Pentium, i386.

2. Is the soundcard built into the motherboard? And what brand (if known)?
- Sigmatel STAC90.

3. Is the modem built into the motherboard or is it a card that you can remove? ( what brand (if known)?
- In the motherboard, yes. Conexant Softmodem. Not sure which model.

4. With Ubuntu installed, without the modem driver, the sound works. Sound is killed when Linuxant driver is installed, correct?
- Yes. the sound works.

5.Before you give up on ubuntu, I would try installing another disto, like knoppix, to see if your sound disappears also with the Linuxant driver installed. Also, did Linuxant send you the right driver version?
- I'm not clear what you are saying here. Yes, I installed the correct driver version. I had it working in June. I'll explain - - -

Here is the history. I had Feisty working, and the modem working. I was following the directions of one of the launchpad helpers (don't remember what I was trying to repair), when they sent the wrong text for a terminal ROOT command, and it caused a file system failure at the next boot. I had o completely rebuild the entire system from scratch. I installed the Edgy CD, went to a wired internet connection and downloaded and installed Feisty, then began building everything else. It took me 1 1/2 days, which I think it pretty good for someone who began using Linux in January this year.

The sound card has been a constant problem with Dapper, Edgy, and Feisty. When I did this recent rebuild, I had more problems with the sound card, and one of the launchpad folks gave me the URL for the  ALSA site, and told me to download the latest driver. Maybe THAT is what is causing the problem I'm having now.

The essential problem is that Ubuntu is difficult to install and use, because the instructions are vague and sometimes inaccurate. And some of the launchpad helpers are not careful enough (or through enough) when they recommend solutions.

In my opinion, all this trouble is unnecessary. Linux is no more complex than any other OS Computer bits are computer bits. The problem is the lack of clear installation and operating instructions, and the fact that the developers don't allow for the various devices - sound cards, video cards, etc. - and cumbersome fixes must be made to force these devices to work. Ubuntu is advertised as "Linux for human beings" but the truth is you need lots of prior Linux experience to successfully install and use Ubuntu.

I like Ubuntu better than window for many reasons. And because I know SO LITTLE about Linux, I feel the best way I can contribute is to clearly state how poor the instructions are, how inconsistent the interfaces are, how cursory the repair instructions are, and how generally difficult it is to use Ubuntu.

I think it is important for society and mankind to have an alternative to windows - an open source, free operating system. I believe this is as important as keeping the internet free of government control.

And it behooves Ubuntu developers, and those who use Ubuntu, to improve the useability of this operating system. The way it is now, it's too hard to use. 

Sorry to pontificate so. Do you think the problem is because I installed ALSA after I installed Feisty? I hope I don't have to re-install Feisty. I don't remember specifically why I had to install ALSA from the ALSA website. But I do remember it was to make the sound card work, which, as I've said, has been a constant hassle with Ubuntu. 

I'll check this post again tomorrow. It's 20 miles each way for me to drive to find an internet connection. That's why I'm trying to get the modem to work. I do have dialup where I am housesitting.

Thank you.

---

### Post by funsport on 2007-08-24
Now that the background is a little clearer to me, it sounds like you did an UPGRADE FEISTY from EDGY and not from a clean FEISTY install.. that's what I did. I have seen problems using the upgrade procedure. I cannot say if this is the problem because I just started this LINUX box just 2 weeks ago and had problems myself getting my modem to work.

You said you had your modem working in EDGY and now it doesn't. We know the sound card works if linuant driver wasn't there. What would you say to getting the modem working first so that you can be on the net at home instead of driving 20 miles away?

The linux system knows your modem only as ttyS# , where #=0,1,2,3 etc.  Let the computer tell you where the modem is. 

Linux also needs a description of how the modem is connected to that ttyS# whcih are the port # and the irq #.

You would have to have that linuxant driver installed first before continuing with steps below.

In the terminal:
    
1.     Type:wvdialconf
     Response:   linux will tell you which ttyS#. Don't worry about all those other numbers it spits out. we are just concerned about the ttyS#

2.    Type: lspci -v
     Response: you did this before and just look for your serial controller (modem). Make note of the the port and the irq numbers.

Now you have the computer telling you everything about the modem. NO GUESSWORK involved.

3.You need to download the setserial command to tie all these info together for the linux system:

[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=setserial](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=setserial)

Install the setserial ( this is a deb file):
    (I renamed the long name of the download to simply setserial.deb)

      Type: sudo dpkg -i setserial.deb
      Now Type: 'which setserial'  ( to verify that setserial was installed)
      Response: it should give a directory path to setserial. i.e.) /bin/setserial

4. Set your modem with the setserial command. As an EXAMPLE, I have used what my computer saw with my modem: 

               ttyS1    (this is case sensitive. make sure not to type ttys1 unless that is where wvdialconf told you)
              port 0xd000     (lspci would have just given me d000)
              irq  11

   Type: sudo setserial /dev/ttyS1 uart 16550A port 0xd000 irq 11 baud_base 115200 spd_vhi skip_test

      Replace YOUR ttyS#, port # and irq #  to the above.

5. The dialup software must know where to link its MODEM command.

      Type:  sudo ln -sf /dev/ttyS1 /dev/modem

You should now be able to dialup to your provider. I don't know how you dialup but I installed Kubuntu and KPPP worked great for me. There is one thing about my system. for some reason on reboot, the link disappears and I had to retype the line in step 5, only. Fortunately I found out how to get that link to execute on boot up. 

******************************************************

When I played any sound on my system I noticed that I had to max out the volume control on the software AND maxout the volume control on my powered speakers to get any decent sound. I'm just wondering if the sound works but volume is so low you just can't hear it.

There may be something that needs tweaking in my system as well.

**********************************************

Can you do a fresh install with FEISTY and not through the upgrade method? I was thinking you upgraded because you mentioned EDGY. I don't know if there is going to be problems with your wifi connection in UBUNTU, but I guess first things first.

---

### Post by funsport on 2007-08-25
In step 5 above, you should put your ttyS# of your computer as in:
             Type: sudo ln -sf /dev/ttyS# /dev/modem

 There is a space between /dev/ttyS#   and /dev/modem

Once this line is typed, you should see a link called 'modem' in the /dev directory. If you reboot and don't find this 'modem' link, the reboot had deleted the link and you have to retype the line link command again. No need to retype the setserial.

---

### Post by RichPicker on 2007-08-25
Okay. That will take me a few days. I'll get back with you next week. Thanks for the education.
Rich

---

### Post by bme on 2007-08-25
It is obvious that your laptop did not come with ubuntu preinstalled. So I assume it came with windows. winmodems are always a problem with Linux so if you encounter problems with it preventing you from using linux then you can do 2 things:
1. Purchase an external serial modem plus a USB to serial cable- I have used this method before or
2. stick with windows.

---

### Post by funsport on 2007-08-27
Hi bme, 
    RichPicker said in message #16, he had the modem working but no sound:

     "Here is the history. I had Feisty working, and the modem working."

So it was a linmodem that he had with an available driver.

*******************

RichPicker,
      I did a search on the net and there were many who had probelms with low volume or no volume when Feisty was installed. I had that low volume problem too. 
A quick check would be to open the sound mixer window, similar to Windows icon. I think you would have to click right mouse button click on the speaker icon. There is a possibility that you may need to increase the slide control of the PCM or the master volume. I had to  adjust mine and now my volume is better.

You may want to do a search on "low volume with Feisty" and see if any info might direct you to a solution for your sound.

---

### Post by RichPicker on 2007-08-27
Not so, bme. I had the modem working with Feisty a couple of months ago.
Once again, the disinformation is rampant.

But thank you for the idea of the external modem. I think I will do that. Thanks.

---

### Post by RichPicker on 2007-08-27
Funsport. I'm going to look into the external modem as a solution.

I'm sure the problem is the conflict with ALSA and the kernel header, I don't want to install Feisty again. I've got too much installed and running for that.

One more thing to bme, and others of that opinion. It sucks that you so erroneously, blindly support Ubuntu in the manner you do - Ubuntu has much room to grow, and many problems. Just take a peek at the thousands of problems the common user has with it. Ubuntu is flawed in many ways. We need to improve it, not condemn the people who discover the problems with it.

Condemning a laptop or the user will NOT improve Ubuntu. Like I said. the modem worked once before with Feisty, but not now. Why?

---

### Post by funsport on 2007-08-27
Rich,
   As I was trying to get my modem to work, I did come across someone posting that when he went from one version to another ( either upgrade i.e. dapper to Feisty or just a different linux distro), the computer saw the modem at a different ttyS#. Nothing has changed with the computer except the OS. He just had to use wvdialconf to find out where that modem is relative to the linux OS version. 

   Good luck with the external modem solution.

---

### Post by RichPicker on 2007-08-29
Thanks. My time is so limited at this  connection, I can't do enough research in this forum. And the launchpad group is ignoring the question. The tech in town recommends the modem that is a card that inserts in the slot in the side of the laptop. I'll pick it up tomorrow and let you, and others, know how it works.

Peace.

---

### Post by m10 on 2007-10-16
I've got quite a similar problem:
I've got Feisty with 2.6.20-16 (32 bit) kernel on an Acer Aspire 5710Z.
Audio card: Hda Intel with Realtek ID 268;
Conexant hda modem.
I installed the Linuxant driver(hsf v. 7.68 ). The modem worked.
To get the audio to work I had to compile the latest Alsa driver (1.0.15rc3)(else no support for realtek 268 chip). Sound worked but the modem stopped working.
I reinstalled Feisty (just to be sure) this time I first compiled the ALSA driver(sound working) then installed the modem driver(neither the modem nor the sound is working). Unistalling the modem driver the sound works again.
So I'm stuck here. Should I try to compile the Linuxant driver or is there a better/sure solution?
Thank you in advance.

---

