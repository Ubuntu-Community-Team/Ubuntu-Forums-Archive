---
title: "Setting up a network"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-07-19
how do i set up a wireless network for ubuntu. is it ok if i have a windows wirless usb reciver?

---

### Post by funkydan2 on 2005-07-20
You'll have to give more information about your setup.

What hardware do you want to use, what does your network look like?

[http://www.google.com.au/search?hl=en&safe=off&c2coff=1&q=wireless+network&btnG=Search&meta=](http://www.google.com.au/search?hl=en&safe=off&c2coff=1&q=wireless+network&btnG=Search&meta=)

Daniel

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=jasonpeinko] is it ok if i have a windows wirless usb reciver?[/QUOTE]

Maybe...what kind?

---

### Post by jasonpeinko on 2005-07-20
[QUOTE=poofyhairguy]Maybe...what kind?[/QUOTE]
 ok i am using my dads computer right now because out network is not working. so here is what it looks like.

Dads computer with modem. -> D-link router -> my computers usb reciver.

my reciver is called: Microsoft® Broadband Networking Wireless USB adaper MODLE: MN-510

we have comcast if any of you have heard of it and an RCA modem.

Our router is a D-link DL-614+

so how can i get this to work if it will work?

thx for the help sooo much

---

### Post by funkydan2 on 2005-07-20
Well I'm not familiar with your particular wireless card, but from a few seconds on Google I've worked out that it should be Prism II based.

Maybe [this thread over at linuxquestions.org](http://www.linuxquestions.org/questions/archive/18/2005/01/4/177767) might help.

Or search this forum for "Prism II".

---

### Post by poofyhairguy on 2005-07-20
Prism 2 should work out of the box. Try it and see.

As a rule, if a wireless card doesn't work out of the box you need ndiswrapper:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by jasonpeinko on 2005-07-21
[QUOTE=poofyhairguy]Prism 2 should work out of the box. Try it and see.

As a rule, if a wireless card doesn't work out of the box you need ndiswrapper:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)[/QUOTE]
 im confussed by this step.
3. Call "sudo ndiswrapper -i foobar.inf" where foobar.inf is the path to your inf-file (windows wireless-lan driver).
i have no idea what to put instead of the -i footbar.inf

---

### Post by Jussi Kukkonen on 2005-07-21
[QUOTE=jasonpeinko]im confussed by this step.
3. Call "sudo ndiswrapper -i foobar.inf" where foobar.inf is the path to your inf-file (windows wireless-lan driver).
i have no idea what to put instead of the -i footbar.inf[/QUOTE]

You need to replace *foobar.inf* with the filename of the windows driver you've got from your wlan adapter driver CD.

But you only need the driver if you use ndiswrapper. Did you try prism 2 first, was there a problem?

---

### Post by jasonpeinko on 2005-07-23
i dont understand what prism 2 i think it is a chip set. but i have read they the should work out of the box. but mine does not.

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=jasonpeinko]i dont understand what prism 2 i think it is a chip set. but i have read they the should work out of the box. but mine does not.[/QUOTE]

Tis....did the installer not recognize it?

---

### Post by jasonpeinko on 2005-07-23
[QUOTE=poofyhairguy]Tis....did the installer not recognize it?[/QUOTE]
 what installer?

---

### Post by jasonpeinko on 2005-07-24
help

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=jasonpeinko]what installer?[/QUOTE]

The ubuntu installer. Before it partitions the disk, it works out the network stuff.

---

### Post by jasonpeinko on 2005-07-25
[QUOTE=poofyhairguy]The ubuntu installer. Before it partitions the disk, it works out the network stuff.[/QUOTE]
 i had my dads friend son hook me up with linux and he did the installing and he could not get it to work so he is going to come over soon and hope fully help me get it to work unless u guys can help me.

---

### Post by jasonpeinko on 2005-08-01
lets start all over shall we. I am using a diffrent card now. A Linksys Wireless -G pci adapter. So in the Ndiswrapper link poofyhairman gave me i dont know what the path to my windows drivers thing is. Can you help me?

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by jasonpeinko on 2005-08-02
if u guys cant help me here is there another forum that can?

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=jasonpeinko]if u guys cant help me here is there another forum that can?[/QUOTE]

sure. good idea. Just because wqe don't know, don't quit.

The smartest are at the Gentoo forum. Searching there is good. But the answer might be over your head (me too).

Also the Fedora Forum is nice. Good idea....we wish you luck....ndiswrapper works the same in every Linux.

---

