---
title: "Sound Problem"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by sgtbob on 2007-12-22
I do not seem to be able to hear any sound when I use 7.10 on the internet - i.e., I have a web site that I built with music on it and I can hear the music if I am on PC's away from home; however, no sound emanates when trying it here.  

The system plays cd's, music files and sounds of opening and closing, etc., just no internet sounds (happens on Windoze and on Ubuntu). I included the following 'lspci' file suggested elsewhere:

[B]00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
05:02.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
05:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
[/B]

Any suggestions.

Bob

3 GB RAM, Dell XPS 400, Dual Boot on 2-160 GB HDD's

---

### Post by Gazz777 on 2007-12-22
Hi Bob, no answers, I have exactly the same problem.

Have a good one

Gary

---

### Post by sgtbob on 2007-12-26
I can't believe that we are the only two in the universe with this problem... :)

Bob

---

### Post by Gazz777 on 2007-12-26
> **sgtbob said:**
> I can't believe that we are the only two in the universe with this problem... :)

Bob

Bob it looks that way, I asked a few times now without success, if I manage to get to the bottom of it, will keep you in mind, can you do the same :)

Kind Regards
Gary

---

### Post by gupta_sumesh63 on 2007-12-26
Try this link
> [http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html](http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html)
I hope it solves your problem.

---

### Post by sgtbob on 2007-12-26
Gupta_

I tried all the suggestions in the reference but I still do not receive/hear the music I have included in a web page I built.

Check out  [http://members.cox.net/an248]("http://members.cox.net/an248") and tell me if a song plays on your system?

Bob

---

### Post by Cypher on 2007-12-26
The issue is one of browsers and not of Linux in general. I went to your website with Firefox on my XP machine and go nothing, I went to it with IE and got the music playing. The issue is with your use of <bgsound> which isn't standard HTML 4.0 compliant. You want to use the <embed> tag instead.

So something like the follow might work better.
```

<embed src="images/amerbeautiful.mid" autostart=true repeat=true>

```

As a side note, it is usually unadvisable to add music/sounds to a website without having the option for the user to turn it off if they don't want it. People will promptly leave a website's that play music without being asked to..

---

### Post by gupta_sumesh63 on 2007-12-26
sgtbob
The link you mentioned takes me to ALBERT NEESE LODGE #248
Am I at the right place?
Where can I find the songs there to try?

---

### Post by Gazz777 on 2007-12-26
> **sgtbob said:**
> Gupta_

I tried all the suggestions in the reference but I still do not receive/hear the music I have included in a web page I built.

Check out  [http://members.cox.net/an248]("http://members.cox.net/an248") and tell me if a song plays on your system?

Bob

Bob not a sound how was it for you :)

---

### Post by Gazz777 on 2007-12-26
> **Cypher said:**
> The issue is one of browsers and not of Linux in general. I went to your website with Firefox on my XP machine and go nothing, I went to it with IE and got the music playing. The issue is with your use of <bgsound> which isn't standard HTML 4.0 compliant. You want to use the <embed> tag instead.

So something like the follow might work better.
```

<embed src="images/amerbeautiful.mid" autostart=true repeat=true>

```

As a side note, it is usually unadvisable to add music/sounds to a website without having the option for the user to turn it off if they don't want it. People will promptly leave a website's that play music without being asked to..

Hi I tried the commands, this is what I got 
gary@Linuk-DeskTop:~$ embed src="images/amerbeautiful.mid" autostart=true repeat=true
bash: embed: command not found

---

### Post by Cypher on 2007-12-26
> **Gazz777 said:**
> Hi I tried the commands, this is what I got 
gary@Linuk-DeskTop:~$ embed src="images/amerbeautiful.mid" autostart=true repeat=true
bash: embed: command not found
This is not a Linux command, but rather an HTML tag that you would use to embed a sound into your webpages..

---

### Post by sgtbob on 2007-12-26
Cypher - Wierd happenings!  You are right about the option that I should allow the person entering the web page to turn on/off the music.

 I used the data you suggested, went to Windows, changed the line I had in my .shtml file and a box appeared that allowed turning on/off the music.  This worked in Windows when I was testing it.  Then again in Windows, I went to the site, and music played, but not the option to turn on/off.  Strange.  Then I went to the web page when I got back to Ubuntu and no music.  

I'm sure it is some coding in Frontpage that I do not understand.  I am new to such items, and am taking the site down anyway.

Thanks to all who replied, 

Bob:confused::confused::confused::confused::confused:

---

