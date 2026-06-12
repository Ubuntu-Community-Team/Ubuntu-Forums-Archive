---
title: "Wireless internet"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Touch.Code on 2006-07-30
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:932 (932.0 b)  TX bytes:932 (932.0 b)

```

That is when my wireless card is plugged in without any internet access! I need help please...

---

### Post by x64Jimbo on 2006-07-30
do this:
ifconfig -a
that will list all interfaces, turned on or not.
find your wireless interface name (probably something like wifi0, wlan0, etc)
sudo ifconfig <interface> up
sudo dhclient <interface>

---

### Post by Touch.Code on 2006-07-30
Hmm, it doesnt find any wifi stuff!

---

### Post by x64Jimbo on 2006-07-30
Then you're probably missing the driver. What kind of card is this? Look up the model number on Google and search for people using it with Linux. They'll probably detail the method(s) they used.

---

### Post by Touch.Code on 2006-07-30
Ok Xd!

---

### Post by x64Jimbo on 2006-07-30
Make sure you keep this thread up to date though, especially if you get frustrated elsewhere. The strength of Ubuntu is its support community. We want you to learn through experience, but not to give up if you can't get it on your own.

---

### Post by Touch.Code on 2006-07-30
Good you said that, because I cant find anything!

---

### Post by x64Jimbo on 2006-07-30
Ok, what's your card model number?

---

### Post by Touch.Code on 2006-07-30
OK, before I say anything else... Desktop>>Admin>>Wirless Driver

I found that, and added the .inf file it said hardware found. It was connected, the light was flashing. But when I tried the internet, it didnt work.

SO.. I restarted my laptop, now it says Configuring Network Interfaces...

Then after about 2-3 mins it changes to the black screen and says the same thing, whats wrong with it? Its been like that for about 5mins now!

---

### Post by x64Jimbo on 2006-07-30
sounds like a possibly bad driver, or maybe the wrong version. Can you hit Ctrl+C to kill that particular startup process?

---

### Post by Touch.Code on 2006-07-30
Yeah its skipped it now!

---

### Post by x64Jimbo on 2006-07-30
Once you get up and running, please post the model number of your wifi card.

---

### Post by Touch.Code on 2006-07-30
OK, it skipped all the files. I logged on and nothing has happend, I just get he crimson background colour?

---

### Post by x64Jimbo on 2006-07-30
I'm not too experienced with Gnome... Not sure why your GUI would be affected by a wireless driver gone awry.

---

### Post by Touch.Code on 2006-07-30
Hmm.. What should I do? Re-Install Ubuntu? Anything?

---

### Post by x64Jimbo on 2006-07-30
You could try re-installing if you don't think you'll lose anything important.
Gnome users? Anyone? I'm stuck at this point.

---

### Post by Touch.Code on 2006-07-30
Well, I only just installed earlier, so nothing on it yet. I just tried to get interent running first!

---

### Post by x64Jimbo on 2006-07-30
In that case, a re-install will almost certainly get you back to working. I'm not typically the kind of person who recommends a re-install for everything, especially in Linux when so many problems can be solved without one. I just don't know how to fix this particular problem.

---

### Post by Touch.Code on 2006-07-30
Thats ok! Well, it seems as if the driver I used may not be right, even though it came of the disc?

What should I do about that?

---

### Post by x64Jimbo on 2006-07-30
What's your card model and version?

---

### Post by Touch.Code on 2006-07-30
Belkin F5D9010

Thanks for your help by the way

---

### Post by x64Jimbo on 2006-07-30
Does it have a version number? Wifi card manufacturers have been notorious for changing chipsets between version numbers of the same model number.

---

### Post by x64Jimbo on 2006-07-30
It looks like that card can only be supported with NDISWrapper. Here's what you do:
Get ALL of the .sys and .inf files off that disc you have, and put them all in a directory on your hard disk. 
in a terminal:
sudo ndiswrapper -i <inffile.inf>
sudo modprobe ndiswrapper
ifconfig -a

Try that with different inf files if you have more than one. 
The inf file is only a file that tells the system how to install & use the sys file. If it doesn't find the sys file in the same directory, it won't work.

---

### Post by Touch.Code on 2006-07-30
Can you tell me how to get and install NDIS? I keep trying and failing!

---

### Post by x64Jimbo on 2006-07-30
ndiswrapper is what it's called. Open your package manager and type "ndis" it should come right up.

---

### Post by Touch.Code on 2006-07-30
OK XD! I will ask in a bit for more info!

---

### Post by Touch.Code on 2006-07-30
I have installed NDISWrapper, through Sypnatic Package Manager. Now I do the lines?

---

### Post by Touch.Code on 2006-07-30
I forgot to mention, that there is only 1 .inf file and thats the same one I used last time and it broke!

I have put in th following line:
```
sudo ndiswrapper -i rt61.inf
```

Error was returned as@
```
couldn't copy rt61.inf at usr/sbin/ndiswrapper line 135
```

---

### Post by x64Jimbo on 2006-07-30
Did you find those .sys files? Are they in that directory?

---

### Post by Touch.Code on 2006-07-30
Yes!

---

### Post by x64Jimbo on 2006-07-30
Ok, well you didn't mention it. Please try not to get upset. I'm doing the best I can. Are you doing these commands as root with sudo?

---

### Post by Touch.Code on 2006-07-30
Sorry..

What do you mean?

---

### Post by x64Jimbo on 2006-07-30
Sorry, I should have been more clear. Are you running the nidswrapper command as root by typing sudo in front of it?

---

### Post by Touch.Code on 2006-07-30
Yes! I just keep getting errors.

---

### Post by x64Jimbo on 2006-07-30
I googled your exact error and it brought me right back to this site.
[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)
Check that out and see if it helps.

---

### Post by Touch.Code on 2006-07-30
Would it work with my hardware?

---

### Post by Touch.Code on 2006-07-30
Ok.. Its flashing again. I havent used that link, its too complicated for me.

It says there is signal, but I cant connect to the interent or anything!

---

### Post by x64Jimbo on 2006-07-30
So it says that it has signal?
What security do you have on your wireless?

---

### Post by Touch.Code on 2006-07-31
None, that I know of!

---

### Post by x64Jimbo on 2006-07-31
So if you do this:
iwconfig
you should see an interface for your wireless. remember that name.
type this:
sudo dhclient <interface>
tell me the feedback you get.

---

