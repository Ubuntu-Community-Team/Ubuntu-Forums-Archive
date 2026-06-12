---
title: "wusb54g wireless config help please"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by TokingBowl on 2007-02-02
boy am i a n00B, i need help with my wireless config . im running ubuntu 6.10 and am having a tough time with it. i know very little linux tho im willing to learn if someone is willing to walk me through this. i have a linksys wusb54g and i dont think i have a driver installed for it tho it shows up in my network. i think i have to start from scratch. any help will be a god send. Thanks in advance

---

### Post by phossal on 2007-02-03
Open a terminal, and c&p the output to:
```
iwconfig
```

---

### Post by TokingBowl on 2007-02-03
ok, you'll have to explain "c&p the output" please. like i said im really new to all of this. sorry if im a pain in the butt. i ran the code but really dont know what im looking for or at. im a 40 year old plumber that can repipe your house but when it comes to this im a little lost. hopefully i can pick this up soon. Thanks again for your help.

---

### Post by phossal on 2007-02-03
I'm sorry. C&P is just web-shortened lingo for "copy and paste". If you have an Internet (Cat-5) connection from the computer you're trying to install the wireless device on, you can copy and paste the output from the terminal commands, which makes the experience of working through the issues much less painful. Run the commands. Paste the terminal output back in your posts.

---

### Post by TokingBowl on 2007-02-03
thats the bummer, im on my ibook right now. my buddies call me a stage 1 geek because of my linux and ibook. my pc is not online tho im right next to it. if it makes it easier you can hit me up on aim or yim. username TokingBowl420, otherwise ill watch for your posts. again thanks. i know im a pest. lol! ok here's what i got:

eth1    IEEE 802 . 11b   ESSID: " "
          Mode:Auto  Channel=1 Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal Level:0  Noise Level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by phossal on 2007-02-03
That output indicates you have a valid driver. Your system seems to have recognized the interface. I recommend disabling WEP/WPA if you've enabled it on your router. I also recommend that you avoid using the GUI tools to set up your network, and that you leave configuring /etc/network/interfaces until after you've established connection. Get it running first, and then configure it as you need to.

Okay. Step one is to familiarize yourself with this command: iwconfig. 
You can use this command to read about it:
```
man iwconfig
```

Here is how you configure you interface (eth1) using iwconfig. Essentially, you want to use sudo (root privileges) when issuing it. Again, with WEP/WPA disabled, the format of the command is like this:
```
sudo iwconfig eth1 essid <YOUR_ROUTER_ESSID> channel <YOUR_ROUTER_CHANNEL>
```

Tip: When you replace <YOUR_ROUTER_ESSID> and <YOUR_ROUTER_CHANNEL>, you won't include the brackets. So it will look more like this:
```
sudo iwconfig eth1 essid LOCKDOWN channel 2
```

---

### Post by TokingBowl on 2007-02-03
ok my router should be wide open so will i still need to identify a channel? . as far as :"my router" do i input the model # of the router or am i just calling it something for identification purposes?

---

### Post by phossal on 2007-02-03
> **TokingBowl said:**
> ok my router should be wide open so will i still need to identify a channel?

I don't think it's *necessary*, but I *would* do it.

> **TokingBowl said:**
> as far as :"my router" do i input the model # of the router or am i just calling it something for identification purposes?

I'm not sure I understand. Your router has a value called ESSID, which is the name it broadcasts. It's essentially the name of the "wireless network". Set essid and channel. That's all you need.

---

### Post by TokingBowl on 2007-02-03
ok the the eesid would be the same as the wireless network name on my ibook if i understand you correctly.

---

### Post by phossal on 2007-02-03
Yeah. It's just the name of the network. It's set on the *router*. Your iBook would use the same one to connect that your Ubuntu will.

---

### Post by TokingBowl on 2007-02-03
ok i tried that and i get:
error : unrecognised wireless request "1"

---

### Post by phossal on 2007-02-03
Post the command you used, verbatim. And try it without setting the channel.

---

### Post by TokingBowl on 2007-02-03
ok i tried it without setting a channel and get no errors, in fact it tells me nothing. is that a good thing? i think my last prob was a space between eth and 1 because i left out the space and the error went away

---

### Post by phossal on 2007-02-03
Correct. There shouldn't be a space. *eth1* is the *name* of the device/interface. It's the name assigned to your hardware (sort of). Now you want to try:
```
sudo dhclient eth1
```

---

### Post by TokingBowl on 2007-02-03
ok i did that and i see a lot happening. at the end i get: 

No working leases in persistant database-sleeping
after it went trough DHCPDISCOVER

---

### Post by TokingBowl on 2007-02-03
and  No DHCPOFFERS recieved  above the No working leases

---

### Post by phossal on 2007-02-03
Okay. Well, you've done everything correctly, I think. Now it's an issue of searching the forums (and Google) to find information on your specific hardware. I'm sure there is a tutorial out there somewhere. Perhaps you need ndiswrapper, etc. There isn't much else for us to do except research. :(

---

### Post by TokingBowl on 2007-02-03
ok,what kind of info am i looking for? what is ndiswrapper?i know its late here and i dont want to keep you tied up but you've been a world of help... Thank You

---

### Post by phossal on 2007-02-03
ndiswrapper is a compatibility layer. It's a program written to translate communications between your device and your Ubuntu system. It allows for installation of Windows drivers in Ubuntu, to support various devices - which are usually networking devices. You may not need it, but it's common.

You're looking for a "HOW-TO" on your hardware. You need to search the forums using your device name. For example, I would search for: wg111. It's the hardware I use (and for which I wrote a tutorial). 

Basically, you're trying to find someone else who's already done the legwork for you, and can verify that your device will work. You want to copy them.

---

### Post by TokingBowl on 2007-02-03
ah i see. thats going to be fun and i might not do that till tomorrow. thanks for all of your help to this point and if you happen to see something in you travels send it this way for me. Thanks again! ill be sure to post an update here.:)

---

### Post by phossal on 2007-02-03
I'll keep an eye out. I'm disappointed you weren't able to get up and running, but don't lose hope.

---

### Post by TokingBowl on 2007-02-03
no hope lost here. i knew it might be a tough one to do or so i was told but that wont stop me. i found a couple how to's  but im not sure those are the ones i need, anyhow i need some sleep. ill pick up on it in the am. maybe someone will leave a link over night:)

---

