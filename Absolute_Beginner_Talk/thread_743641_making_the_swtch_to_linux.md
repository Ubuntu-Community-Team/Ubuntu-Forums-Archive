---
title: "making the swtch to linux"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by x NZERO x on 2008-04-02
I will start from the top. I have been wanting to jump into the world of Linux for sometime now. I tried Open Suse 7 or 8 months back and after a week of pulling my hair out tying to get my wifi card to work. I finally got it to work but couldn't get any encryption to work on it. After that I got fed up and went back to XP. Well Now I'm building a new computer(links below for what I'm putting in it) and I want to give Linux another try.

(new build links)
[Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138075")
[Power]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817101013")
[Memory]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820220227")
[Video card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102152")
[CPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115017")

Anyways, I have only a couple of things that I use on a day to day basis that I would really like to work on Linux, everything else I can come to when I get there.:) The two biggest things are I want to share music and video to my 360's in my house. I have heard of trevisty ( i think its called) and Ushare, but have no idea of how well they work. The second biggest thing is I have a [WinTV-PVR-150 MCE]("http://hauppauge.com/Pages/products/data_pvr150mce.html") tv tuner card. I don't know if it works on Linux. anyone that could help me out on how to get it set up would greatly help. Oh yeah and if anyone could get me some points on how to get a driver installed for WMP54gs wifi card my hair (whats left:lolflag:) would thank you may times, me and ndiswrapper don't seem to get along. 

My reason for moving to Linux is well XP is ok, Vista well that is another ME (enough said), but mainly its time to move on and learn something new. 

Thanks for any help you can give me on the switch.

---

### Post by ichi@YUKI on 2008-04-02
hi, i'm new to linux too so were pretty much on the same boat. Sorry but I'm not quite sure about the hardware issues. However, I did encounter the same trouble of getting my wireless card on after I switched to Ubuntu 7.10.. it even took me a while just to get this code:

sudo modprobe ndiswrapper

to run, since I kept on getting fatal errors. In any case, I am enjoying linux now, and maybe you're right. It's about time we learn something new.

---

### Post by Crafty Kisses on 2008-04-02
To be honest, I'd stay away from ATI if you're going to use Linux, get nVidia.

---

### Post by Tatty on 2008-04-02
> **Codename said:**
> To be honest, I'd stay away from ATI if you're going to use Linux, get nVidia.

+1

Nvidia supports its linux drivers much better than ATI, so getting a nvidia card working is usually much less problematic

---

### Post by xelapond on 2008-04-02
Welcome to Ubuntuforums!

Anyway, check this website for hardware compatibility.  It has a nice list of TV tuners and how to get them working, as well as everything else you  can imagine:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Good Luck!

Alex

---

### Post by Crafty Kisses on 2008-04-02
> **Tatty said:**
> +1

Nvidia supports its linux drivers much better than ATI, so getting a nvidia card working is usually much less problematic

Yep, I have a nVidia GeForce 6800 GT, and it works flawlessly.

---

### Post by x NZERO x on 2008-04-02
I already have the card installed in the new machine. The only thing I am waiting on is the CPU.

---

### Post by xelapond on 2008-04-02
I personally prefer ATI, because of the open drivers.  I think most Nvidia cards below an 8400 work fine, above you have to do some special tweaking.

---

### Post by Crafty Kisses on 2008-04-02
> **x NZERO x said:**
> I already have the card installed in the new machine. The only thing I am waiting on is the CPU.

In some sense yes, but nVidia natively supports Linux. To be honest more people have problems with ATI cards, yes. That's not to say you'll have problems, it may work perfect for you, it just depends.

---

### Post by x NZERO x on 2008-04-02
Thanks for the hardware compatibility link.:)

---

### Post by x NZERO x on 2008-04-02
Is there any other programs that I could use to share music and video with my 360's other then UShare that I should look at?

---

### Post by x NZERO x on 2008-04-02
I almost forgot, which OS should I go with 32bit or 64bit? since my wifi card and tv tuner card only have 32bit drivers.

---

### Post by Crafty Kisses on 2008-04-02
> **x NZERO x said:**
> I almost forgot, which OS should I go with 32bit or 64bit? since my wifi card and tv tuner card only have 32bit drivers.

I'd probably go with 32bit.

---

### Post by x NZERO x on 2008-04-02
well so far everyone that has posted a reply has made my day I seen that I won't really have to really do anything to get my tv tuner up and running. things are already looking better then the last time i made this attempt to switch. Thanks everyone

---

### Post by Tatty on 2008-04-02
> **xelapond said:**
> I personally prefer ATI, because of the open drivers.  I think most Nvidia cards below an 8400 work fine, above you have to do some special tweaking.

There are open drivers available for both manufacturers i believe...  Its what ubuntu defaults to using.

---

### Post by x NZERO x on 2008-04-02
Anyone use Openwrt? I have been thinking of using it to setup a wireless bridge. If I  can even do that with it. My friend said it should but haven't had anytime to look into it. I live in a two story apartment and don't like the look of cables on the floor and can't drill holes in the floor. that and the wife won't let me run wires every where.

---

### Post by x NZERO x on 2008-04-02
Yet another question I forgot to ask.  How much memory is Ubuntu able to see? I'm putting 4gb's of memory in my new machine just wanted to know if it all will be seen.

---

