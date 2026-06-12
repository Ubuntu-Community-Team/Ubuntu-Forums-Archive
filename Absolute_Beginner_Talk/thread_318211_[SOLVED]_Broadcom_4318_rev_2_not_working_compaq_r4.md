---
title: "[SOLVED] Broadcom 4318 rev 2 not working compaq r4000"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-13
Hello, i installed ubuntu 6.06  on my laptop a few days ago sence then i have been trying to get the wireless to work now luck. i have a broadcom 4318 rev 2. have been looking on the web very hard to find some thing that work. but how ever hard i try i cant seem to get it configured right.

as alwas all help is greatly apresated even if it dosent work lol
thanks

edit---
 well i gess i should have been more clear i have been working on this i got my wireless light to come on but i cant conect to anything at all.
also note that the bcm4318 rev2 has been said not to work with the bcm43xx thats included with the kurnal (something or grater)
i also had it working for a day then harddiver crashed... dam just my luck right, so i got new drive and whent right back to what finaly got it working a patch i found on the ubuntu documantion page on bcm43xx and it said bcm4318 patch well this time on a fresh updated install it didnt work but only got the network light to light

agin thanks for the help

---

### Post by faraazs on 2006-12-13
There are some tutorials on this site to get the card working. I'll get you a link as soon as I can if someone else doesn't do it before I do.

It should be noted that the broadcom chip is one of the most troublesome :(. I have one myself.

---

### Post by compwiz18 on 2006-12-13
Try the link in my signature...if that doesn't work, feel free to ask :D

---

### Post by crimesaucer on 2006-12-13
This forum post worked for me, it turned on my hp pavilion's wifi antenna light on my keyboard: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Then to search for wifi signals I installed wifi radar: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

I am now able to detect my next door neighbor's locked wifi linksys signal, but I haven't had a chance to actually use it in a free wifi coffee shop or hot spot yet, so I don't know how good it actually works.

---

### Post by faraazs on 2006-12-13
Hehe, the link I was going to post was your tutorial. It has helped me with my wireless card so much! I recommend that how to. It's really clearly written and easy to follow.

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-15
hello everybody, i have a compaq r4000 with a bcm4318 rev 02 wireless chip
had it working before my hard drive crashed but now with new dirve instald i cant remberd what i did to get it working :( 

Pleases dont point me to a ndiswrapper howto or even the included bcm 43xx howtos i read a hole bunch and i just not getting something.

Hope fully what ever my problem is can be solve and explaned to me so i can undersand it all so i can help other ppl with simalar problems.

As always thanks for the help in advanced :D

Man this hole problem is giveing me such a head ake.

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-15
well my title kindof sums it up aditionally if any one could walk me through getting may wireless to work, that would be great i dont know what i am missing in the howtos out there 
they all seem very good and simple they just dont work for me

---

### Post by crimesaucer on 2006-12-15
Did you try the 4 step how to I linked you to in your other post? It worked for me everytime, really easy, but it may be different on your computer.

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-15
yepp i tryed that already
flowed every step
ever frustarting, makes me sad 
 Is there any way to see were my system is at and how things are configurd?
i mean all of the wifi setings and compar it to yours or systems that have workin bcm4318 cards

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-15
i think i made some progress now the wireless comes on and if i run 
the code sudo iwlist eth1 scan
i get this output 
```
eth1      Scan completed :
          Cell 01 - Address: 00:13:46:A4:D9:B2
                    ESSID:"Joe"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=100/100  Signal level=-153 dBm
                    Extra: Last beacon: 180ms 

```
i aculy have a singnal i cant get it to concect though
help :) thanks agin

---

### Post by crimesaucer on 2006-12-15
I'm a beginner on xubuntu/ubuntu edgy, so I wouldn't be the guy to ask, but I do have one question, after you installed the 4 or 5 steps, how did you configure your networking settings for wireless connections-->--properties? Was it automatic configuration DHCP?... and did you have your "local host name" in Network Settings-->--General as your computer's name?

See, after I had done all of that, and had seen my computer's antenna light turn on, I still didn't know how to actually detect a signal (still don't) and couldn't find any help. I tried a few different things in the settings but still couldn't figure it out or get it to detect a wifi signal when I knew there was one to detect. I was told that you need to know the isp address of the signal you are trying to connect to, unlike searching for random free signals like on Windows Xp. 

So I was in a forum and someone recommended wifi radar.

After I installed wifi-radar (still had my DHCP for properties in Network Settings and the wireless connection checked), I just followed the instructions on their page and I was able to detect the neighbors wifi signal first time I ran: "sudo wifi-radar -d" in the terminal.

I don't know if any of this will help, so definitely ask an expert.

---

### Post by Doug11 on 2006-12-15
> **<<joe>> said:**
> yepp i tryed that already
flowed every step
ever frustarting, makes me sad 
 Is there any way to see were my system is at and how things are configurd?
i mean all of the wifi setings and compar it to yours or systems that have workin bcm4318 cards

Are you getting the light to come on for your wireless? Did you get that far?

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-16
I did get the wire less light to come on.
and it gets better when i run
```
sudo iwlist eth1 scan 
eth1      Scan completed :
            Cell 01 - Address: 00:13:46:A4:D9:B2
                         ESSID;"Joe"
                         Protocol:IEEE 802.11bg
                         Moe:Master
                         Channel:11
                         Encryption key: on
                         Bit Rates; 54 Mb/s
                         Extra: Rates  (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                         Quality = 100/100 Signal level=-142 dBm
                         Extra: Last becon: 176ms ago
```
But still cant connet or get and internet connection

---

### Post by crimesaucer on 2006-12-16
Did you try wifi-radar?

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-16
alot of the howto said that wifi-radar dosent work with bcm4318
i could give it a shot though

ok just did, kill all internet
luckly i have this comp here

---

### Post by crimesaucer on 2006-12-16
I didn't quite understand your comment, did it work for you?

this was the link for instructions: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-16
no it didnt work 
and it acually killed all of the internetconctions on my laptop wired and unwired

---

### Post by compwiz18 on 2006-12-19
> **<<joe>> said:**
> alot of the howto said that wifi-radar dosent work with bcm4318
i could give it a shot though

ok just did, kill all internet
luckly i have this comp here
This is a misconception: wifi-radar works fine on 4318s.

---

### Post by Cohente on 2007-04-21
Hey JOe!! How did you do it?

 I have exactly the same card and exactly the same problem :-( 

any help will be very appreciated! Thanks!

   Cohente

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-14
well i got it half working
it can connect to unsecured wireless networks
but not incrypted lol
i got it working a week before i moved to my new apartment and i cant uses an unsecured connection here  to get it working i followed the nisdrapper tutorials and the important step i must tell you **is make shur u used the files from a windows install on your computer that has working wireless **  dont uses the one's off the net because they all have the same name but aren't the one you need

O! sorry about the spelling

---

