---
title: "Scanning..."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by IanBraby on 2008-02-09
Why does Linux have to be so arcane?

Why can't my transition from Windows be eased with simple installers rather than having to dive into the terminal to try and get things to work?

After carefully following the instructions from the Brother website I finally managed to get it to print... but the same cannot be said for scanning.

I have followed the instructions and used brsaneconfig2 to install the scanner but when I run Xsane I get the error: "Failed to open device 'brother2:net1;dev0': invalid argument."

What more must I do? There is no further instruction on the Brother website - they assume that their instructions should just work.

Frustrated!

Ian B:confused:

---

### Post by randy78 on 2008-02-09
> **IanBraby said:**
> Why does Linux have to be so arcane?

Why can't my transition from Windows be eased with simple installers rather than having to dive into the terminal to try and get things to work?

After carefully following the instructions from the Brother website I finally managed to get it to print... but the same cannot be said for scanning.

I have followed the instructions and used brsaneconfig2 to install the scanner but when I run Xsane I get the error: "Failed to open device 'brother2:net1;dev0': invalid argument."

What more must I do? There is no further instruction on the Brother website - they assume that their instructions should just work.

Frustrated!

Ian B:confused:

Ian,

I don't mean to sound crude, so don't take offense.
But you will have to realize sooner or later that Linux is much different than Windows and that most of those companies are locked into production agreements with Micro$haft, so they can't even consider making open source drivers available.

Ubuntu supports more different hardware configurations out of the box than ANY other type of OS, especially Windoze...

When I was using XP, I had to first set everything up, go find the correct soundcard and graphics drivers, update, and restart about a dozen times to get everything to work...

I understand your frustration, and I know firsthand that it's enough to make you want to tear your hair out, but trust me when I say that things DO GET BETTER if you take a step back, collect yourself and do some more searching.

I know that the command line seems different to you now, but once you get used to it and start working with it more, you probably won't even want to deal with GUI's anymore, since they are so limiting in what you are able to configure.

Start by giving us some more info on the make and model of your scanner or whatever device it is that you're having trouble with and we'll do our best to get you straightened out.

Just hang in there and go play some music, games or watch some movies for a while and jump back in when you're less stressed...
Trying to work while you're flustered will only compound the situation.

Take Care 
Randy

---

### Post by Rhubarb on 2008-02-09
It can indeed be tough getting linux-unfriendly hardware setup and working.
If you intend / are running a linux based OS (like ubuntu), it's best to buy hardware that is linux friendly.  That way hardware is as easy as plugging it in (and that's it).

---

### Post by IanBraby on 2008-02-09
Hi guys,

Thanks for responding so quickly!

OK - It's a Brother MFC-440CN and it's networked.

As I've already mentioned - I've persevered sufficiently to get it to print via the CUPS driver, so that's great - I can do these command lines, you see!

I've downloaded the SANE driver from the Brother site and carefully configured it, as per the instructions, but, as mentioned, XSane reports the error in my first post and I can't find any further assistance on the Brother site that seems relevant. Hence my post here!

Ian B

---

### Post by randy78 on 2008-02-09
Well, 
You definitely came to the right place.

I'll do some digging around to see what I can come up with, so forgive me if you don't hear back for a while.

In the meantime, don't be surprised if somebody else comes along with just the right info!

Take Care and Hang In There ;)

---

### Post by hyper_ch on 2008-02-09
also have a read at this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Paqman on 2008-02-09
> **randy78 said:**
> 
I know that the command line seems different to you now, but once you get used to it and start working with it more, you probably won't even want to deal with GUI's anymore

Er, I doubt that.

Unfortunately, IanBraby, the CLI is sometimes the easiest way to get broken things to work. Heck even Windows requires the use of the CLI (usually called the DOS prompt) for some things.

---

### Post by IanBraby on 2008-02-09
> **Paqman said:**
> Er, I doubt that.

Unfortunately, IanBraby, the CLI is sometimes the easiest way to get broken things to work. Heck even Windows requires the use of the CLI (usually called the DOS prompt) for some things.

Hi Paqman,

And I'm quite happy to dive in to the CLI - it's just that, having done so, I'm no further forward in getting the machine to be recognised by Xsane!

Regards,
Ian B
=====================
A Linux newbie but a computer user since the 80s!

---

### Post by mp035 on 2008-02-11
Hi all,
I fear that this problem may not be a simple one, I have the same problem, but I have successfully been using my brother MFC-640CW wirelessly networked via a router for a long time now, and all of a sudden it has stopped working,  Starting xsane from a terminal produces no output, but after about 30 minutes to an hour a dialog box pops up with the text:  
```
Failed to open device `brother2:net1;dev0': Invalid argument.
```

(I have them popping up everywhere as I'm writing this, from all the failed start attempts about 45min ago! )  

Any help is appreciated.




BTW IanBraby-  There's no question, Linux, even Ubuntu is harder to use than Windows.  I switched to Linux about 3years ago, and I'm only now starting to be as adept at Linux as I was with Windows.  It's a steep learning curve, 

I have 1 piece of advice that I found on a post that was invaluable to me:
> Don't switch to Linux cold turkey, or use the highly frustrating dual-boot scenario, find an old PC suitable for the distro, fork out the 20 bucks and buy a KVM switch and run Linux side by side with Windows until you can finally change all your needs to Linux.

I used this setup for about 2 years, you'll find after a while that you want to put MS on the old PC and use the newer hardware for Linux.  And in the 3 years I've been using Linux, it has improved leaps and bounds, and is still improving. 

All the best.
Mark.

---

### Post by mac71 on 2008-02-11
Hi,
It might be a stupid question, but did you read this on the FAQ?> [For Ubuntu Users (version 6.06 or later)]

1. Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor.
2. Add the following description to the file as below:

================= 
#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
LABEL="libsane_rules_end"
================= 

3. Restart the OS.

I couldnt get my brother printer/scanner to scan until i added these 3 lines.

---

### Post by mp035 on 2008-02-11
Hi MacWorld, 
The lines in the rules.d file are only for usb devices detected by sysfs, the problem is with networked scanners.

But just to be sure I just tried your suggestion, and restarted, still have the same syptoms.  I think the problem could be related to a recent update, because it used to work flawlessly.

Thanks for the suggestion though.:)

---

### Post by mp035 on 2008-02-11
Update:
I timed it with a stop watch, and xsane takes exactly 1 hour to return the error message, so this probably is viewed as a lock up by most users.  

Should there be a bug filed for this??

if so, ubuntu or xsane, or sane?

Does anyone know how to narrow down the failure?

---

### Post by leo1981 on 2008-05-26
I have the same problem with a Brother MFC-820CW.
Did you find a solution?

---

### Post by jbaerbock on 2008-05-27
Just because your printer has issues doesn't make Ubuntu arcane. My 3-in-1 HP printer I plugged in and withing 2 seconds ubuntu recognized and had it ready to work. And for scanning Xsane works perfectly. Jeee no terminal there....

If you do research well generaly you can do anything without the terminal. For every terminal program there is a simple GUI that does the same thing.

---

