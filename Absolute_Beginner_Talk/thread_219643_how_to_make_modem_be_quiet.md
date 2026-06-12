---
title: "how to make modem be quiet"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Handyman's Special on 2006-07-20
Hello,

While I struggle through all the setting up/downloading a constant annoyance is the racket my modem makes when it connects. I have an external Hayes Optima 288. In the Modem properties under Network settings I have selected "OFF." This selection is either ignored or over ridden. 

In Win there were several places that needed to be checked before silencing the modem, if I only knew where these spots are in Ubuntu, I would feel like less of a bungler.

Appreciate all the help and advice given to everyone who posts. I am searching the forum for clues to my setup issues. Downloaded Automatix the other day (or should I say, days - on dial-up here). Just found a thread about UbuntuPlus. Wonder how long a download that will be?? Don't like running a crippled copy. Will propably try and get it.

Quieting the modem will go a long way towards imporving my Ubuntu experience.

Cheers,
Handyman's Special

---

### Post by slimdog360 on 2006-07-20
if you have the motherboard manual handy you can look through it and find the pins which connect the speaker. It only 2 pins but sometimes they come in a 4 pin connector but with only two wires attached.
For me it was down the bottom of the motherboard and near pins for the hd led and the pins for the front usb connectors.
 Thats what I did, though maybe I might be a little more computer proficient. But guessing from your username your pretty handy.

---

### Post by Handyman's Special on 2006-07-20
Hello slimdog360,

The 'proficient' one is my husband, Handyman, he gave me this handle. 

Are you speaking of the modem board or the computer? The noise comes from external modem. It is in it's own case.

I had no problem with it when I ran Kanotix, only in Ubuntu.

cheers,
HS

---

### Post by az on 2006-07-20
What init string are you sending to the modem?  ATL0 will turn the speaker volume to zero, if the command to turn off the speaker does not work (ATM0, I think - not sure...)

Those are zeros (0) and not o's (O)

---

### Post by Handyman's Special on 2006-07-20
Hello azz,

Where would I go to enter that data?  I will keep searching and check back here a little later.
Thanks,
HS

---

### Post by az on 2006-07-20
I'm not in front of an Ubuntu box, nor a modem right now.

Maybe this helps?

[https://help.ubuntu.com/community/DialupModemHowto#head-c2e5e02fc299ef02bf3484aa89654a40e8ba2d2a](https://help.ubuntu.com/community/DialupModemHowto#head-c2e5e02fc299ef02bf3484aa89654a40e8ba2d2a)

---

### Post by Handyman's Special on 2006-07-20
Thanks, I will try that next time I boot to Ubuntu

HS

---

### Post by Handyman's Special on 2006-07-20
Extreme frustration here!! I just downloaded automatix and things have all seemed to have changed.

I am unable to make folders in my filesystem. The option is grayed out.

After all that downloading I still can not play a MIDI file, or a DVD.

I really, really want this OS to work for me. I could do without the MIDI & DVD but this is a new computer. I could have just used the old one and saved the money I spent for this one - if I wanted to run a crippled system.

I thought I could at least stop the noise the modem makes when it dials but even that is too complicated for me.

Can anyone ease me towards a success of any small amount?

Thanks,
HS

---

### Post by b1g4L on 2006-07-20
I thought external dial-up modems usually had a switch on the back for speaker on/off. Maybe not, but I thought it might be something to check into.

edit: check this website out. You select which options you want and it gives you the exact init string to enter.
[http://www.uga.edu/~ucns/telecom/modsos.html](http://www.uga.edu/~ucns/telecom/modsos.html)

---

### Post by Handyman's Special on 2006-07-20
Thanks for searching for and providing that interesting link.

I will play around with that a bit.

later,
HS

---

### Post by Handyman's Special on 2006-07-21
No luck with anything I have tried tonight. Rats!

Maybe by tomorrow morning someone will have posted to tell me where to go to enter these commands for the modem.

Maybe I will just use it noisy as it is.

I am tired and that makes me feel more discouraged than I should.

until then,
HS

---

### Post by eeried on 2006-07-21
Hello Handywoman ;-)

1. Have you tried this (from Ubuntu wiki the link was given in a previous message)?

```
To quiet or silence the connection noises (dialing, negotiation, etc.), follow these steps:

   1.

      Open a terminal (Applications > System Tools > Terminal) and type

       $ sudo nano /etc/chatscripts/provider

   2.

      Locate the line marked 'OK-AT-OK'.
   3.

      Change 'ATDT' to 'ATxxDT', where 'xx' is one of the following:
          *

            M0 Silence the speaker
          *

            L1 Low volume
          *

            L2 Medium volume
          *

            L3 High volume

            For example: ATM0DT. Leave the rest of the line unchanged.
   4.

      Save the file (Ctrl-o) and exit (Ctrl-x).

```

2. What's you bigger problem, Automatix or your noisy modem?

Automatix I should think think, though Automatix looks good. Is Automatix really useful with Ubuntu Dapper? Anyway there's a lot of documentation on this forum and you can find out how to uninstall Automatix modules and the wiki will help you with sound problems.

I haven't installed Ubuntu Dapper because it's a bit too cumbersome for my computer (I've switched to a minimal install of Debian) but even Breezy was fine without Automatix, but with the addition of some apps and stuff. 

My modem too is noisy but I'd rather leave it alone because the racket tells you it's working properly and dialling out. The led isn't so explicit. But of course the racket is a bit irritating.

Good luck!

---

### Post by colsinc on 2006-07-21
open up the modem and, if you have a soldering iron it should be pretty easy to remove the buzzer.  that's what I did to solve a noisy modem.  

sorry I can't help with a software fix

---

### Post by Handyman's Special on 2006-07-21
Hello eeried,

Perhaps you haven't considered just how confusing it is to be an _Absolute Beginner_.

you write:
> 1. Have you tried this (from Ubuntu wiki the link was given in a previous message)?

**If I knew what a wiki was, maybe I would have tried it.**

and this:
[CODE]To quiet or silence the connection noises (dialing, negotiation, etc.), follow these steps:

   1.

      Open a terminal (Applications > System Tools > Terminal) and type

       $ sudo nano /etc/chatscripts/provider

   2.

      Locate the line marked 'OK-AT-OK'.

**this is what I get using that command:**

GNU nano 1.3.10        File: /etc/chatscripts/provider

# This is the chat script used to dial out to your default service provider.
# Please customize the entries enclosed in parenthesis to match your setup.
# Only the "provider" file will be handled by poff and pon (unless with
# extra command line arguments).
#
# Remember to edit /etc/ppp/peers/provider accordingly.
#
# ATZW2 as a default init string
# - On all hayes compatible modems, W2 will correctly report the connect
#   speed.
#
ABORT        BUSY
ABORT        "NO CARRIER"
ABORT        VOICE
ABORT        "NO DIALTONE"
""           ATZW2
OK           ATDT<put phone number here>
ogin         <put login name here>
word         \q<put password here>
                               [ Read 19 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

**Even should I change anything in that stuff above, there is no option to save it.**   

> 2. What's you bigger problem, Automatix or your noisy modem?

**My BIGGEST problem is cryptic replies.**

> Automatix I should think think, though Automatix looks good. Is Automatix really useful with [COLOR="Red"]Ubuntu Dapper[/COLOR]? Anyway there's a lot of documentation on this forum and you can find out how to uninstall Automatix modules and the wiki will help you with sound problems.

I haven't installed Ubuntu Dapper because it's a bit too cumbersome for my computer (I've switched to a minimal install of [COLOR="Red"]Debian[/color]) but even [COLOR="Red"]Breezy[/color] was fine without Automatix, but with the addition of some apps and stuff. 

My modem too is noisy but I'd rather leave it alone because the racket tells you it's working properly and dialling out. The led isn't so explicit. But of course the racket is a bit irritating.

[b] This just tells me that you are not able to shut your modem up either, so why have you posted here? What have you helped me accomplish? Nothing. You have just added to my confusion. I trust your intentions were to be helpful and informative but you were neither. Your text highlighted in red only added to my confusion. 

I installed Ubuntu from the Live-CD. There was no mention of Dapper, Debian, Breezy, wiki, gnome, wine, or anything else. I just clicked on the install and it did. At first boot the screen resolution was perfect, the modem (external) connected easily, howbeit noisly.

Automatix promised installation of all I needed to run MIDI & DVD movies. But that is another thread.

When I first got into computers it was with Win 3.1. We bought a used computer and a big stack of back issue PC Computing magazines. Everything we needed to learn about setting up the computer was covered in those magazines - in detail.

My problem with Ubuntu is not the OS, it is my source of instruction. The HELP files on my computer are not complete (for my needs, anyway). The information coming from this forum, while at times being excellent, at other times is dismal. I feel like I am trying to break into a secret organization and am being given a runaround.

Reading some of the other posts on here lately, I am not the only one feeling like this.

I really, really, really want this OS to work. I do not want to have to keep running back to Windows to do things. If I am going to do have to deal with the devil (M$) part of the time, I might as well, submit and stay.

Perhaps, this post will illuminate the depth of my feelings for moving to Ubuntu. Plus, show my determination to persevere in setting it up to completely replace M$ on my computer.

regards,
Handyman's Special[/b]

---

