---
title: "network connection"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by spellico on 2007-01-03
Total newbie. I connect perfectly through my router at home. I then try to connect through a public wi-fi connection. WLAN assistant picks up the connection perfectly, but won't connetc. If I open the wireless connection dialogue, I can't see how to open up and configure a new connection while not touching the home connection that works. Any help?

Thank you

---

### Post by Spinelli on 2007-01-03
I think we need to know what version of Ubuntu you are using. When I used dapper the graphical wireless configuration tools worked great, but when I upgraded to edgy I had a lot of problems with the graphical wireless configuration tools. I usually have to use the command line programs to set up my wireless connection in edgy. Try some of these commands . . . .

```
man ifconfig
```
```
man iwconfig
```
```
man ifup
```
```
man iwlist
```

If you still can't figure it out just post another question in this thread and I will try and walk you through it.

---

### Post by oyvindaa on 2007-01-03
I'm using wifi-radar for setting up my wireless.

```
sudo apt-get install wifi-radar
```

Easy to use program.

---

### Post by spellico on 2007-01-03
Thanks. I'm using Dapper. The graphical configuration tool works fine at home. I just put in the network name and the key and it worked great right away. That is connection ath0. If I click on the arrow, I only see lo. Now I'm out and WLAN assistant sees a wi-fi connection. How do I connect to that connection? Through the graphical config tool? And if yes how do I set up a new connection without having to erase the home connection that works? Is there a tool such as WLAN assistant that picks up the available connection and connects? Or how to make WLAN assistant do what it says (connect) ? Thanks again.

-by the way when I try to connect with WLAN ***, a dialogue comes up " don't have enough permissions, would you like to run as sudo?. I answer yes.

---

### Post by Spinelli on 2007-01-03
Go to System>Administration>Networking. Select your wireless device ath0 and then click on the properties button. This should allow you to select your wireless network. As far as I know you can't save networks or setup up preferred networks with the default wireless configuration tool in Ubuntu. You could try oyvindaa's suggestion and install wifi-radar. I have never used it, but you should give it a shot. I have no idea why the WLAN manager is displaying an error message about lack of permissions. Good luck and let us know if it worked.

---

### Post by spellico on 2007-01-03
Thanks -Thanks. Wi-fi radar works great.

---

### Post by mimsmall on 2007-01-03
> **oyvindaa said:**
> I'm using wifi-radar for setting up my wireless.

```
sudo apt-get install wifi-radar
```

Easy to use program.

I want to connect to open wifi hotspots at the court house, church and public library. What info do I need to put in to the wifi-radar gui?](*,)

---

### Post by zmuth734 on 2007-01-03
> **mimsmall said:**
> I want to connect to open wifi hotspots at the court house, church and public library. What info do I need to put in to the wifi-radar gui?](*,)

It should just show up automatically in the list.  I can see my neighbor's wifi as well as mine in wifi radar.

---

### Post by spellico on 2007-01-03
actually when you hit on the connection you want from the available ones it'll  ask you to put in the connection info such as restricted or open  and if restricted a key etc. it'll do that automatically , easy and smooth. that's how it worked for me.

---

### Post by mimsmall on 2007-01-04
Thanks. I have to be in court this PM and will have a chance to stop at my usual hotspots going to and fro. I'll let you know what results I get. :)

---

### Post by mimsmall on 2007-01-04
At each hotspot both power light and link light were on, even while I was still booting up. The library did not open their front page in a web browser as it should. Opening Firefox and typing in the url did no better. The 'could not locate web site' error message appeared. The church and Pinera bread did not open the web browser. Wifi-radar indicated a connection and had the name of the connection and the ip on the bottom of the window. I have two pcmcia cards, one Belkin, one Linksy, and they operated identical. 

This is very confusing for me. Shouldn't it be working correctly?

---

### Post by spellico on 2007-01-04
If wi-fi radar sees the connection you're trying to use, highlight that connection, click connect , a dialogue box should come up which will ask you if you want to set up a profile, sey yes one more dialogue box will come up enter the appropriate info (wi-fi config mode, auto or ... , channel auto or enter channel, , security open or  key etc.) save it. Should work.

---

### Post by mimsmall on 2007-01-05
> **spellico said:**
> If wi-fi radar sees the connection you're trying to use, highlight that connection, click connect , a dialogue box should come up which will ask you if you want to set up a profile, sey yes one more dialogue box will come up enter the appropriate info (wi-fi config mode, auto or ... , channel auto or enter channel, , security open or  key etc.) save it. Should work.

Yes, that's what I did for each hotspot and was able to get an ip, but the web browser would not connect to any web site. So, I'm connected but not connected.](*,)

---

### Post by siby on 2007-01-05
> **mimsmall said:**
> Yes, that's what I did for each hotspot and was able to get an ip, but the web browser would not connect to any web site. So, I'm connected but not connected.](*,)

I'm having the same problem. My card associates and assigns an IP, however, when I try to browse, no go... any suggestions would be appreciated.

Thanks,

Siby

---

### Post by spellico on 2007-01-06
Well I went to the library and tested it again. It works. I open wi-fi, select the network and put in the right parameters. I'm running Dapper. I had installed Edgy before and had the same problem you're having.

---

