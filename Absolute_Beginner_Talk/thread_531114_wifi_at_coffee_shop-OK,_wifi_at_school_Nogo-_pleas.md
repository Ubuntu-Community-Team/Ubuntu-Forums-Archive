---
title: "wifi at coffee shop-OK, wifi at school Nogo- please help"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by JeanneBean on 2007-08-21
Good morning!
I recently installed Ubuntu 7.04 to my old, used Gateway Solo PentiumIII laptop.  It had ME on it but the IT people at my college (St. John Fisher College in Rochester NY) didn't want me using it here since I could no longer get firewall/antivirus for ME.  My brother-in-law suggested Ubuntu and so far, I'm LOVIN' IT!  

THE PROBLEM: My wifi card is working, sort of- I get connected no problem, and have successfully been surfing,  and performing downloads etc. using free and unsecured networks at local coffee houses, restaurants and I've even connected to an apparent unsecured neighbor's network (they really ought to secure that!)  however, at my college, although I'm seeing the network - at full or near-full strength, for the love of God, I can't get onto the freekin' network.  

I'm using NetworkManager 0.6.4 and it tries really hard to connect, I sometimes even get one of the two green lights but after about 40 tries over 3 days, every attempt times out.  I'm told that the network should be accessible and that only if I try to leave the college's main website will I be prompted for userID and password; but I can't even get that far.

I tried different locations at school that didn't help.  I tried the tech support people at school but, no surprise, they only support Windows, and sometimes Mac.

After viewing a bunch of other posts, many of the fixes are for similar, but not identical issues, i.e. for different versions of Ubuntu or not being able to keep a connection, so - I thought I'd throw out the problem I'm having and see if anyone has any ideas.

THANKS BUNCHES!

---

### Post by timcredible on 2007-08-21
you'll have to ask the tech support what type of security they have on their network - wep or wpa or what, then configure that in ubuntu, and it should work.

---

### Post by JeanneBean on 2007-08-21
Hmm, I did ask them yesterday about that and Mr. tech-guy said it didn't matter...claims that if I can connect at coffeehouses, I should connect there too.   Guess it's time to ask someone else.  Tiptoeing lightly, not wanting to annoy people who's help I might need later in the semester...

Thanks!

---

### Post by arron on 2007-08-21
when you try to connect to the school, do a 

```
ifconfig
```

 in a prompt, and see if its getting an ip (compare that to the last network you connected to, post it here if you like), then it may just be a dns thing for their network setup.

I had a lot of problems with network manager and switching networks.  Set network manager to manual, and install wifi radar, and use that to try to connect.

---

### Post by gatman3 on 2007-08-21
Useful commands to try to figure out what's going on with wi-fi are (from a terminal window):

> sudo iwlist scan

which will scan for wi-fi access points, tell you the signal strength (Quality) and whether or not they are using encryption, and:

> sudo iwconfig

which will tell you additional information about which access point (if any) your card is currently talking to.  If the "Link Quality" is 0/100 then they are probably using encryption of some sort.

If there are unencrypted access points available you should be able to force your wi-fi card to connect to them using

> sudo iwconfig wlan0 essid "<access point name>"

You may need to replace "wlan0" with the interface name of your wi-fi card, as reported by the iwconfig command.

After that (and sometimes just in general) you may need to cycle your interface up and down as follows:

> sudo ifdown wlan0
> sudo ifup wlan0

(or whatever your card's interface name is).

---

### Post by JeanneBean on 2007-08-21
This is what I got so far. Can anybody translate it into English for me?
Thanks

jeanne@ubuntu-weber:~$ sudo iwlist scan
lo        Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning : Operation not supported
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:E6:DB:72:1F
                    ESSID:"SJFC Wireless"
                    Mode:Master
                    Frequency:2.437 GHz
                    Signal level=-154 dBm
                    Encryption key:off
                    Extra:tsf=0000072185cd2309


jeanne@ubuntu-weber:~$ sudo iwconfig
lo        no wireless extensions.
wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
wlan0     IEEE 802.11g  ESSID:"SJFC Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:E6:DB:72:1F   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
jeanne@ubuntu-weber:~$

---

### Post by JeanneBean on 2007-08-21
And whats with the cutsie smilie faces?  I didn't put them there!!  Man, that auto-stuff bugs me sometimes.  If I wanted smilie faces, I'd have put 'em in myself!

Ok, I'm being silly.  Too much caffeine I think.

---

### Post by gatman3 on 2007-08-21
> **JeanneBean said:**
> This is what I got so far. Can anybody translate it into English for me?
Thanks

jeanne@ubuntu-weber:~$ sudo iwlist scan
lo        Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning : Operation not supported
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:E6:DB:72:1F
                    ESSID:"SJFC Wireless"
                    Mode:Master
                    Frequency:2.437 GHz
                    Signal level=-154 dBm
                    Encryption key:off
                    Extra:tsf=0000072185cd2309


jeanne@ubuntu-weber:~$ sudo iwconfig
lo        no wireless extensions.
wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
wlan0     IEEE 802.11g  ESSID:"SJFC Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:E6:DB:72:1F   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
jeanne@ubuntu-weber:~$


Cool.  Looks like you have an available access point called "SJFC Wireless" and it's not encrypted!  My guess is that your wi-fi manager isn't setting the essid properly (I've had this problem too.  Sadly, Ubuntu still needs some work on wi-fi management).

Try this:

> sudo ifdown wlan0
> sudo iwconfig wlan0 essid "SJFC Wireless"
> sudo ifup wlan0

And see if you get signal.  (You can tell from another "sudo iwconfig" command... please post the result.  You're looking for a "Link Quality" greater than 0).

---

### Post by gatman3 on 2007-08-21
> **JeanneBean said:**
> And whats with the cutsie smilie faces?  I didn't put them there!!  Man, that auto-stuff bugs me sometimes.  If I wanted smilie faces, I'd have put 'em in myself!

Ok, I'm being silly.  Too much caffeine I think.

The "cutsie smiley faces" are "emoticons" and you put them in with certain key combinations (a standard smiley is a colon followed by a right-parentheses).  The forum software is interpreting the listing you copied in as having some of these key combinations and automatically sticking in the emoticons... which you didn't intend, but it's OK.  There's probably way to avoid that but I don't know what it is.

---

### Post by JeanneBean on 2007-08-21
Sorry this takes so long - I'm swapping my flashdrive between laptop and school PC w/ internet connection.  Thank you so much for your persistence!
Jeanne

anyway - here are the results:


jeanne@ubuntu-weber:~$ sudo ifdown wlan0
Password:

ifdown: interface wlan0 not configured
jeanne@ubuntu-weber:~$ sudo iwconfig wlan0 essid "SJFC Wireless"

jeanne@ubuntu-weber:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

jeanne@ubuntu-weber:~$ sudo iwconfig
lo        no wireless extensions.
wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
wlan0     IEEE 802.11g  ESSID:"SJFC Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:E6:DB:72:1F   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
jeanne@ubuntu-weber:~$

---

### Post by gatman3 on 2007-08-21
Hmmm...  Bummer.  Link quality is still 0 after manual configuration.  That's not a good sign.  I have to get going, but here are a few other possibilities:

1. Make sure that your wi-fi manager is set to "Manual" mode, and try the ifdown/iwconfig/ifup stuff again.

2. Your specific wi-fi card may not like the SJFC Wireless access point for some compatibility reason.  You might try either borrowing someone else's wi-fi adapter (USB wi-fi adapters are very convenient, maybe you can find someone who has one and try it out).  Or go to a big box store like CompUSA or CircuitCity and buy on for $20 or $30 and try it out; if it doesn't work just use the "no questions asked" return policy and take it back.

3. You truly have little or no signal where you are at.  Try moving closer to the access point (if you can figure out where it is physically) and try all this again.

4. Go hang out at a computer lab and find the geekiest looking person, ask them if they know anything about "linux" and try to get some help.  :)

Gotta go.  Good luck!

---

### Post by JeanneBean on 2007-08-21
Gatman3  -  You have been a great help.  Thanks for sticking with me.  I'll try what you have suggested and let you know when I get connected.  I know its just a matter of time...
Jeanne

---

### Post by gatman3 on 2007-08-21
OK, one more thought I had on the way out the door.

If your school's IT people normally configure the students' computers for them to use the SJFC Wireless, but they say they only support Windows or Mac, maybe they also grab the computer's MAC address and add it to the list of approved MAC addresses.  (The MAC address is a unique number that every wireless interface in the world has, and it identifies your computer's network interface uniquely throughout the world).

Ask the IT people if they use MAC address filtering?  If so, you can get your MAC address with the "sudo ifconfig" command (look for something liek Address: xx:xx:xx:xx:xx:xx)

Good luck.

---

### Post by JeanneBean on 2007-08-21
Oh, and regarding step 4 - at this moment, I AM the geekiest looking person in here... Sad, but true.  When the semester begins in two weeks, that may change.

---

### Post by gatman3 on 2007-08-21
Whoops.  Stupid emoticons again.  Point is, if they say they do use MAC address filtering, show them the output of "sudo ifconfig wlan0".  I just double checked, and it should be in the first line, after "HWaddr".  It's a long shot, but what the heck.

---

### Post by gatman3 on 2007-08-21
> **JeanneBean said:**
> Oh, and regarding step 4 - at this moment, I AM the geekiest looking person in here... Sad, but true.  When the semester begins in two weeks, that may change.

Then find the second-geekiest looking one, you're sure to get some help!  :lolflag:

Gotta go!

---

### Post by JeanneBean on 2007-08-21
Outstanding.  I'm heading to a different part of campus - to see if signal is better in the 'internet cafe' versus the lab.

If that doesn't work, I'll go find a friend with a working wireless and make sure they can get on.

Then, I'm going to try contacting my geek brother-in-law to see if he can help too.

Thanks again to you and everyone else who posted helpful ideas.

SEEYA!

---

### Post by Delkster on 2007-08-21
Off-topic:
You can select the "Disable smilies in text" checkbox somewhere below the text area when posting or replying. Screenshot attached.

---

### Post by JeanneBean on 2007-08-21
Well, if I had looked a little lower and read a little slower... I might have see that option to de-select.

I appreciate the tip - No More Smilies for me, no sirreee!  ;-)

---

### Post by JeanneBean on 2007-08-26
PROBLEM SOLVED!!
Thanks to all for your posted ideas/suggestions.  

Trying a different location helped - I took my laptop to the campus of my community college (Monroe Community College) where I still have alumni privileges and tried to get onto their network and I got right in.  Hmmm.  

So, I took the advise given here  - I went and spoke with this very helpful GeekSquad employee at BestBuy and (btw - he had Linux on his own PC) he showed me his preference in wifi cards that he knew would work with Ubuntu.  So I got a more powerful wifi card (D-Link WNA-2330 Rangebooster G) and went back to St. John Fisher College computer lab, and Bam! I was surfin' like crazy.  

The $40 wifi card was a better investment than a $300 OS I can't stand; I think. (The dang wifi card is powerful enough to pick up a network nearly a block away from me.  Yikes - too bad it's a secured one!)

I'm so happy now I've got dancin' feet!  THANKS!

---

### Post by gatman3 on 2007-08-26
Wonderful, JeanneBean!  Glad you got it working.  Thanks also for sharing the final solution with the community.  Sometimes these networking problems can be very hard to diagnose, your saga is a good example of how you may head down some false avenues before you finally nail a good solution.

Good luck with school, and happy surfing!

---

