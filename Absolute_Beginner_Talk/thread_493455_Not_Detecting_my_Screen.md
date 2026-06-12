---
title: "Not Detecting my Screen"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-05
I've tried reconfiguring my ATI video card but I can't figure out what I'm doing wrong. I used the 
> sudo dpkg-reconfigure xserver-xorg

and then I did

> sudo /etc/init.d/gdm start

then it says gnome is running,but after rebooting I get an error screen this time saying it cant detect my screen. Someone help?

---

### Post by Krosis on 2007-07-05
This is the guide I used that helped me out.  Give it a try.

[http://ubuntuforums.org/showthread.php?t=399913&highlight=feisty+on+dell](http://ubuntuforums.org/showthread.php?t=399913&highlight=feisty+on+dell)

Good luck.

---

### Post by snwbord2456 on 2007-07-05
On the first step of the guide when trying

> wget [http://www.mylittleubuntuguide.com/file/ati](http://www.mylittleubuntuguide.com/file/ati)

it says

"Resolving [www.mylittleubuntuguide.com...failed:](www.mylittleubuntuguide.com...failed:) Name or service not known.


I am on the forum on a different computer, my laptop has just the command prompt.

---

### Post by Krosis on 2007-07-05
Try plugging your Ethernet cable into your laptop and following that guide.

What I did was, I have to computer right beside one another, my Laptop and my Desktop.  My desktop does not have Wireless internet, so it always has an Ethernet cable attached.  My Laptop has a Wireless card built in, as I'm sure yours does.  I went to that guide on my Desktop, and THEN unplugged my Ethernet cable and plugged it in my laptop.  The guide was still loaded on my Desktop, and I could still scroll up and down, I just couldn't go anywhere else.  But I was able to follow the guide, and get everything else I needed on my Laptop also.

Maybe you can try something like that.

I'll be sure to check this post often.  I'm packing to leave out of town tomarrow, so I apologize if I'm slow in replying.

Hope I helped.

---

### Post by snwbord2456 on 2007-07-05
The internet connection isnt the problem as far as possible connections, I have a router and enough ethernet cables that I have both my laptop and my desktop wired but the link the in the guide did not work to download the file. Thats the issue that I had. Sorry for not being clear eough.

---

### Post by Krosis on 2007-07-05
Interesting.  I just used this guide a few hours ago when I re-installed Ubuntu so I know it works.

In your quote, you're missing a following "s" after the word file.  Not sure if you typed it correct on your laptop.

I just opened a Terminal and typed it in, this is what I got.

```

tim@tim-laptop:~$ wget http://www.mylittleubuntuguide.com/files/ati
--20:21:56--  http://www.mylittleubuntuguide.com/files/ati
           => `ati.1'
Resolving www.mylittleubuntuguide.com... 64.111.124.212
Connecting to www.mylittleubuntuguide.com|64.111.124.212|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 116 [text/plain]

100%[====================================>] 116           --.--K/s             

20:21:56 (8.42 MB/s) - `ati.1' saved [116/116]

```

So it **is** still working.

---

### Post by snwbord2456 on 2007-07-05
Wow, so I am stupid. It did download, but when after typing ./ati it said


> (EE) No devices detected

Fatal Server error:
no screen found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining

Sorry about that, feel a bit stupid.

---

### Post by Krosis on 2007-07-05
Everyone makes mistakes.  I remember the same thing happening to me.  I had to do the next step about the dell install, then go back and do the ATI file.

---

### Post by snwbord2456 on 2007-07-05
Thats what I'm doing now. Hope this works. If it does you're my new hero.

---

### Post by snwbord2456 on 2007-07-05
I'm looking ahead and it says to go into the install (cd install) directory and again type the same script command, how do I navigate to that directory?

---

### Post by avik on 2007-07-05
To **C**hange **D**irectories, use:

```
cd /path/to/dir
```

---

### Post by snwbord2456 on 2007-07-05
So I could go 
> cd /
dir
cd /cdrom

sorry for the step by step, i just dont want to mess this up

---

### Post by snwbord2456 on 2007-07-05
I feel really stupid. cd install would mean change directory to install, but when i do cd install, it says there is no such directory. Should I create one? Should it have been created by those files? or do i just run the ./dellinstall again?

---

### Post by Krosis on 2007-07-05
> **snwbord2456 said:**
> I feel really stupid. cd install would mean change directory to install, but when i do cd install, it says there is no such directory. Should I create one? Should it have been created by those files? or do i just run the ./dellinstall again?

You're correct.  Just run ./dellinstall again and continue on with the guide.

If it doesn't ask you about Wifi, it's alright, it didn't ask me either.  Once you get everything up and running let me know through this topic and I'll direct you to setting up your Wireless internet.

---

### Post by snwbord2456 on 2007-07-05
Awesome, thanks a lot. It's running the last part (with the wifi installer thing) now.

---

### Post by snwbord2456 on 2007-07-05
Graphics!!!! Its Amazing!!!

---

### Post by snwbord2456 on 2007-07-05
Now I'm running distro upgrades, what about the ati files do they need to be changed at all?

---

### Post by Krosis on 2007-07-05
Awesome!  Glad to help.  Here's the guide to get your Wifi up and running.

[http://ubuntuforums.org/showthread.php?t=297092&highlight=e1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=e1505)

Best of luck, and welcome to Ubuntu!

> **snwbord2456 said:**
> Now I'm running distro upgrades, what about the ati files do they need to be changed at all?

I didn't need to.

---

### Post by snwbord2456 on 2007-07-05
Thanks so much, and btw I'm replying to you on my laptop, now running linux.

---

### Post by Krosis on 2007-07-05
> **snwbord2456 said:**
> Thanks so much, and btw I'm replying to you on my laptop, now running linux.

Happy to help.  Good luck with everything that Linux has to offer.  :)  Don't be shy to ask for help about anything on the Forums, the Ubuntu Community is one of the best out there.

---

### Post by snwbord2456 on 2007-07-05
Final question, hopefully you're still on. 

when I get to

> Now we'll complile the Ndiswrapper program. In a terminal, go to the directory where you extracted ndiswrapper and execute the following:

Code:

sudo make uninstall



I get 
> make: *** No rule to make target `uninstall'.  Stop.


any ideas?

---

### Post by Krosis on 2007-07-06
> **snwbord2456 said:**
> Final question, hopefully you're still on. 

when I get to



I get 


any ideas?

Yeah. 

```

cd ndiswrapper-1.46

```

Then follow on.  You just needed to be in the correct directory.

---

### Post by snwbord2456 on 2007-07-06
So I got to :

sudo ndiswrapper -l

but then I get an invalid driver error. Any ideas?

---

### Post by Krosis on 2007-07-06
> **snwbord2456 said:**
> So I got to :

sudo ndiswrapper -l

but then I get an invalid driver error. Any ideas?

Did you change your directory?

After you unziped the R151517.exe, you should have changed your directory to DRIVER.

```

cd DRIVER

sudo ndiswrapper -i bcmwl5.inf

sudo ndiswrapper -l

```

**you should see a message that says driver present, hardware detected**

```

sudo ndiswrapper -m

sudo modprobe ndiswrapper

sudo echo ndiswrapper >> /etc/modules

```

**Your wifi light on your laptop should be illuminated, and you're all set!**

---

