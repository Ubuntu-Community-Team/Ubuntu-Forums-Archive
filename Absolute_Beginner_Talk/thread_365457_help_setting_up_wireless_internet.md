---
title: "help setting up wireless internet"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by PHNX1 on 2007-02-19
I am new to Ubuntu (actually linux) and I switched from windows because it refused to install on my pc and lack the $$ to fix it right now (It's looking like i won't even want too).
any way

I can't seem to get my wifi to work, i have used ndisgtk to install the driver for my card i beleive its an Texas Instruments ATX 111 54mb 802.11, wich the list said was supported. I followed the instruction on setting it up (Basic Instructions as it keeps calling it) but when I open up firefox it wont open any websites.

could someone plz help me out here

also it would be great if someone could give me some software ideas that would it easier for me to get the hang of linux (How exactly am i going to use my games and other programs?)

thanks in advance

edit** i have the standard ubuntu 6.10 idk what the difference is btwn this one and dapper or edgy, could somebody fill me in on this?

---

### Post by solar george on 2007-02-19
Try automatrix

[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

Don't actually - this proves that you should not try answering two posts at the same time.

Or perhaps I should have read the name of the thread that I was posting to before clicking 'Submit Reply'

---

### Post by sharperguy on 2007-02-19
Was the guide you read [this one]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")?

Because if not I recommend it because it has some ubuntu specific stuff in it which you have to do.

Also Automatix wont fix this.

All it does on the wifi front is install ndisgtk, which you've already done.

---

### Post by jermor on 2007-02-19
Messed up this post.  See the next one.

---

### Post by jermor on 2007-02-19
Wireless cards can be pretty frustrating.  What's the ouput of this command?

```
iwconfig
```

---

### Post by kevin niebuhr on 2007-02-19
You need ndiswrapper, follow this link:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29) 


Hope this helps you.
Kevin

---

### Post by PHNX1 on 2007-02-19
kevin:

i have ndisgtk, is there any real differance btwn the two?

jermor:

when i typed in iwconfig it displayed lo, wlan0 sit0 and eth0 and all said no active connection er sumthin like that

sharperguy:

no i opened up the help file and searched for connecting and used the instructions there
I did however find this tut [here]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111?highlight=%28WifiDocs%2FDriver%29") but it says its for Ubuntu Dapper, I dont think i have this version (i just downloaded standard ubuntu) im going to try it now see if it works, after all it says its for my wifi card specifically so, meh we'll see

---

### Post by solar george on 2007-02-20
> i have ndisgtk, is there any real differance btwn the two?

ndisgtk is just a graphical front end to ndiswrapper.

If you have ndisgtk installed ndiswrapper should also be installed.

---

### Post by PHNX1 on 2007-02-20
ok ive reinstalled ubuntu, and started from scratch

i used the ndisgtk
used the driver that came with the card - TNET1130.INF
when installed ndisgtk displays tthe driver on the left and below says hardware present - Yes
I opened terminal and typed iwconfig
-displays card status under wlan0 (i dont understand some of it)
I restart the machin and check again, all the same
I open firefox and try to open a webpage but nothing

what steps am i missing if any?or is it the driver perhaps? i tried others but they didnt recognize the hardware (said hardware present - No)

also in iwconfig it says signal strength or whatever is only 18/100 could that be the problem? (the other one said 41/100) ill try moving it closer to the router next.

---

