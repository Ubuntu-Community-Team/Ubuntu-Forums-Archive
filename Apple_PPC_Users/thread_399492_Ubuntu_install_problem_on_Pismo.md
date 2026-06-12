---
title: "Ubuntu install problem on Pismo?"
date: 2007-04-02
forum: Apple PPC Users
---

### Post by Finnigan24 on 2007-04-02
First, Hello to the community.

I have never used linux before and wanted to give it a try. I chose Ubuntu because I have done a little research online and read that it was very friendly to new users. I also happened to notice that there are amateur radio applications available for use with it. I'm a ham.

Now, I have a 500mhz Pismo lying around and thought I'd try to make it dual boot Ubuntu/Panther.

The machine is a Pismo:
500mhz
128mb ram
pram battery appears to be dead
battery is dead
DVD drive seems to work fine
no Airport card
yo-yo power supply

So far I have used the Disk Utility to create 2 partitions:
1. Ubuntu 10gb
2. OSX 9gb

I installed Panther on the OSX partition.

I then booted from the Ubuntu CD (mailed to me from Ubuntu. I did NOT burn an .iso) using a "live" command at the prompt, or by just hitting "enter." I have no idea what the other options do. All seems to go well. Eventually I get a screen where there is a rectangular bar in the center and it says "Ubuntu" on the right side. In the bottom of the bar it seems to list things loading. The last thing I remember seeing is "nautilus," then the system seems to go into a long slow process of loading with nothing on the screen but a mouse pointer. This LITERALLY goes on for hours. The pointer IS responsive, but it's choppy.

One time a file manager window came up on screen on a black background. The mouse curser became what I assume is the linux version of a clock or pinwheel. It froze at that point.

A few things more:
When loading up, one message I noticed was that Linux couldn't access the system clock. I saw one thread that said this could be a problem starting up Ubuntu, BUT he already had Ubuntu installed and used a terminal window to fix the problem.

From reading threads here and there I see 128mb might be too little to run the "live cd." Is there a way to do an install otherwise? The instructions with the disk were to run live cd then double click the install icon.

I have a 10mb D-link wireless PCMCIA card I'd like to use if possible. Should I have it in the slot while installing Ubuntu?

Any help would be appreciated. I'd really like to take linux for a test spin, including downloading and using some programs.

---

### Post by grazie on 2007-04-02
Hello Finnigan24,

Welcome to the forum. Glad to see you're reading a few posts before adding your own.

Indeed, 128mb is not really enough to run the Desktop CD (Live CD), even though the website may state it is. I believe Dapper (6.06) use to make use of a swap partition if one existed (great for low ram machines) and Edgy (6.10) is supposed to, but I'm not so sure it does this successfully. It wouldn't take much to set up a swap and try it though.

If you have to get or download another cd, you may want to consider Xubuntu as 128mb isn't very much for running gnome (or OSX). The Alternate and Minimal CDs plus [other methods]("https://help.ubuntu.com/community/Installation") are available as alternative install options.

---

### Post by Finnigan24 on 2007-04-02
Thanks for the reply!

Well, In the long run, if all goes well,  I intend to build this laptop out all that I can. It will just have to be done a bit at a time.

I was hoping there would be a way to install (perhaps a command at the initial boot menu) without actually having to load the whole live CD session.

A couple more questions if you will:

If I booted using one of the other options to try and make it easier to load, would I be able to install?

How would I go about setting up a swap partition and get Ubuntu to use it?

---

### Post by Finnigan24 on 2007-04-02
I just found this in an older thread. Maybe this is what I need?

> Try resetting the PRAM (hold down command-option-P-R at boot and wait for chimes). Then try rebooting from the CD.

Try holding down the C key at boot to boot from the CD.

From in open firmware (hold down command-option-O-F at boot), run:

Code:
boot cd:,\install\yabootto boot directly from the CD. (I'm guessing that's the path to the yaboot bootloader on the CD; you can verify by mounting the CD on a working computer.)


---

### Post by dpny on 2007-04-02
Although not a direct response to your question, I would definitely recommend getting more RAM. I run Ubuntu on a Pismo and it's works pretty well, minus the usual PPC Linux issues.

---

### Post by andrewfortwayne on 2007-11-07
must set time due to dead pram battery, after u do the system should work fine.I read that if your system says the time is before 1970 then ubuntu wont boot right and you will get a blank screen

---

### Post by Tommy on 2007-11-08
> **andrewfortwayne said:**
> must set time due to dead pram battery, after u do the system should work fine.I read that if your system says the time is before 1970 then ubuntu wont boot right and you will get a blank screen

On my wallstreet I find I also have to reset the PMU any time I power it up (the PRAM battery and the main power battery have been dead for years now).

The command for resetting the PMU is inside the port door under the hinge. On my wallstreet it's shift-fn-ctrl-Power. (3 keys on the left plus the power button.) On mine the lights blink briefly and the fans spin up and down when it resets.

---

