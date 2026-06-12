---
title: "Answering Machine"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by daacosta on 2006-03-23
Hello,

Could somebody post a set of instructions for setting up a answering machine?  I use dial up with a external modem (Z-modem)  I have speakers, a microphone, etc.  But I honestly have not been able to complete this project (I know that I need to install vgetty but quite honestly the information is too fragmented (I swear I have googled, looked at forums, etc.) and confusing)

If somebody has accomplished this and would be kind to share I would be gratefull forever.

Thanks!


-D-

---

### Post by Pragmatist on 2006-03-23
See if this works:
[http://www.vocpsystem.com/index.php](http://www.vocpsystem.com/index.php)

---

### Post by daacosta on 2006-03-24
[QUOTE=Pragmatist]See if this works:
[http://www.vocpsystem.com/index.php](http://www.vocpsystem.com/index.php)[/QUOTE]

Thanks... I am familiar with that website and many others... I have spent a lot of time reading wikis, looking at websites, etc. etc. but I haven't found a set of step by step instructions and quite honestly that is what I am looking for...

And... It is not the first time I install things like a firewall when I took the time to read firestarter's manual and go through it, or gppp when I wanted to install it on my box... Anyway, now I am sounding defensive... I will read the F..ing manual when I it is clear and if I can't find a clear manual I will ask for asistance as I am doing here...

---

### Post by Pragmatist on 2006-03-25
> .. I will read the F..ing manual when I it is clear and if I can't find a clear manual I will ask for asistance as I am doing here...

Asking for help is perfectly reasonable...that is why this forum exists :)

I have successfully used VOCP in the past and I'm sure, as long as you have the right equipment, that I could get you up and running.

So...lets start with the hardware...What brand and model (and chipset if you have it) modem?
How does it connect? (serial?)

---

### Post by daacosta on 2006-03-25
I have a external Z modem 56K V.92/V.90 Model 3048 (PC and Mac)

---

### Post by Pragmatist on 2006-03-25
I'm assuming Z Modem refers to Zoom Modem.  If that is true then you should be in great shape (works with Linux, voice capable).  I'm sure you have this, but for others, here is the link to Zoom's spec sheet:
[http://www.zoom.com/graphics/datasheets/dial_up/30481101.pdf](http://www.zoom.com/graphics/datasheets/dial_up/30481101.pdf)

Other hardware you'll need:
1.) working soundcard
2.) pair of speakers
3.) microphone
4.) one phone line and access to another phone for testing (cell phone, second line, friends phone, whatever).

Stage one: hardware
1.) connect modem to serial port.
2.) connect speakers
3.) mic not necessary yet
4.) plug phone-line from wall jack into modem's "line-in" jack
5.) plug telephone wire from modem's "line-out" jack to your telephone.
6.) Plug in the power of the modem
7.) Boot computer

Stage two: software
1.) go into synaptic: ```
sudo synaptic
```
2.) do a search with keyword: **mgetty**
3.) Click the box to the left of these packages, select 'install package' and press 'apply':
[B]mgetty
mgetty-pvftools
mgetty-voice
mgetty-docs[/B]

Let's start with that.  I'm digging out my external modem, which I got to work in the past, and I'm going to do this along with you.  My following post will present the next steps.

---

### Post by daacosta on 2006-03-25
Thanks man

[QUOTE=Pragmatist]I'm assuming Z Modem refers to Zoom Modem.  If that is true then you should be in great shape (works with Linux, voice capable).[/QUOTE]   

Yes, this is the modem.  I still have the box and when I purchased it I made sure about it being fully compatible with Linux

[QUOTE=Pragmatist]
Other hardware you'll need:
1.) working soundcard
2.) pair of speakers
3.) microphone
4.) one phone line and access to another phone for testing (cell phone, second line, friends phone, whatever).
[/QUOTE]

My soundcard works fine.  It is a Live-Theater 5.1 -- 5.1-CHANNEL PCI Sound Card
Speakers came with my computer Platinum JBL Series...
Microphone is embedded on the monitor and it works.
I have a phone line... The second phone line is also available from a friend...

[QUOTE=Pragmatist]
Stage one: hardware
1.) connect modem to serial port.
2.) connect speakers
3.) mic not necessary yet
4.) plug phone-line from wall jack into modem's "line-in" jack
5.) plug telephone wire from modem's "line-out" jack to your telephone.
6.) Plug in the power of the modem
7.) Boot computer
[/quote]

Everything is connected and the modem is working already.  Speakers and mic are already connected as well.  I have Ubuntu already connected to the Internet and I can dial-up easily...

[QUOTE=Pragmatist]
Stage two: software
1.) go into synaptic: ```
sudo synaptic
```
2.) do a search with keyword: **mgetty**
3.) Click the box to the left of these packages, select 'install package' and press 'apply':
[B]mgetty
mgetty-pvftools
mgetty-voice
mgetty-docs[/B]

Let's start with that.  I'm digging out my external modem, which I got to work in the past, and I'm going to do this along with you.  My following post will present the next steps.[/QUOTE]

Just finished doing this.

You know what? This should be part of a wiki... A real easy to understand wiki...

---

### Post by Pragmatist on 2006-03-25
> Originally Posted by: **daacosta**
Just finished doing this.
You know what? This should be part of a wiki... A real easy to understand wiki...

I agree 100%.  Well, once were finished, perhaps you'll contribute to the linux  community of volunteers by starting a wiki! :)  Just keep one more thing in mind before we begin.  This is an advanced project and while it can certainly be done, it is not simple or easy no matter what the instructions.

The steps, according to every site I consulted, as well as a book, are basically the same.  This part is easy, believe it or not:

**I. CONFIGURE VGETTY**
**A.** ***The voice.conf file***
Our key configuration file is **/etc/mgetty/voice.conf**

1. Read through this well-commented file (everybody recommends this).  

We are going to make at most 4 changes.  

Lets back it up first, so we can roll back the original if we want without having to remember what we changed:
```
sudo cp /etc/mgetty/voice.conf /etc/mgetty/voice.conf.BAK
```

open /etc/mgetty/voice.conf in an editor using sudo:
```
sudo gedit /etc/mgetty/voice.conf
```
 
2. Verify and/or make changes. All you have to do is make sure of 4 settings (hint: you could hit CTRL-F in gedit to do a simple find for these variables:

(a) **voice_dir** The directory where the messages, incoming and your greeting, are stored.  Default is /var/spool/voice  I left it this way. mine reads: **voice_dir /var/spool/voice**

(b) **rings**  The default is 3, and I left it that way.  In the past I believe the default was 5.  Use your judgement and set as you like.  I'm pretty sure it must be 2 at a minimum. mine reads: **rings 3**

(c) **voice_devices**   you must put your device file corresponding to your modem as the default is nothing (since everybody can be different there is no default).  Mine is on COM1 (first serial port) and so the device file is /dev/ttyS0  if it were COM2 it would be /dev/ttyS1 and so on. 
mine reads:  **[B]voice_devices** ttyS0[/B]

(d)**port ** This again refers to where your modem is connected. Mine is on COM1 (first serial port) so it is /dev/ttyS0  mine reads:
**port** ttyS0

**B.** ***The inittab file***:
Add vgetty to your /etc/inittab file so it can listen for calls all the time:

As usual, backup first:
```
sudo gedit /etc/inittab /etc/inittab.BAK
```

now open /etc/inittab with gedit:
```
sudo gedit /etc/inittab
```

There will be a list of lines that contain the term "respawn".  Put this line at the end of that list:
**S1:23:respawn:/usr/local/sbin/vgetty ttyS0 **

This assumes your modem is at ttyS0 if it isn't, put its location instead (so if your at the second serial port, COM2, put ttyS1 instead.

Save the file and exit gedit.

**C.** ***Record Your Greeting:***
Now for the fun part :)

1. with your mic turned on type this and record your greeting:
```
vm record standard.rmd 
```

2.Try playing your message over your sound card:
```
rmdtopvf standard.rmd | pvfspeed -s 8000 | pvftobasic > /dev/audio 
```

3. Try playing your message through your modem:
```
vm play standard.rmd
```

4. copy your message to the appropriate location:
```
cp standard.rmd /var/spool/voice/messages
```

Ok, this is far enough for now.  You could try calling your phone if you want to see if it works.  In my case I did a couple of things differently.  I have to go get a microphone.  Meanwhile, you can use wav files and then convert them with the pvf tools.  So, that is what I did.  However, it is better if the compression is 8000 khz whereas at present, the lowest I could make mine is 11000 khz.  This may or may not be the source of my problem.  Much more likely is the default modem settings.  By default, my modem is set for data.  Modems settings can be adjusted using "AT commands".  In working with a program called "minicom" I was able to determine much of my modem's capabilities.  I got the AT command set at my manufacturers website.  I was able to change the setting to voice, however, when the modem is reset when I exit the program.  I'm pretty sure that the way to fix this is to make some entries to the /etc/mgetty/mgetty.config file.  That is for tommorow! :)

This is part of the reason it was hard to find easy instructions for this subject.  One part is that this isn't that common a project.  Another is that much of the software is beta (which means unfinished documentation, less stability, and so on.  Because Linux makes stride through volunteers, the most popular projects get the most attention)  Finally, there is the fact that this particular project involves hardware that varies wildly.  This is no fault of linux.  There is, to my knowledge, no standardization of the AT command sets.  This is totally ridiculous and it means that one set of commands to your modem are going to be completely different in nature and syntax from the ones to my modem.

If you get a chance, do some research on google and your manufacturers website for documentation of its AT command set, or at least what chipset your modem has.  This may come in handy.

---

### Post by daacosta on 2006-03-26
Everything was good up to part A.

Then this:

> 
B. The inittab file:
Add vgetty to your /etc/inittab file so it can listen for calls all the time:

As usual, backup first:
Code:

```
sudo gedit /etc/inittab /etc/inittab.BAK
```



This must be wrong... It should be:

```
sudo cp /etc/inittab /etc/inittab.BAK
```

> 

now open /etc/inittab with gedit:
Code:

sudo gedit /etc/inittab



OK, thus far...

However, in the inittab file there are a lot of respawn entries.  I asume you refer to the one that reads:

```

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

```

In that case, wouldn't it be implied that I uncomment that line and enter the right modem port?

Please explain :mrgreen:

Rgds,


-D-

---

### Post by Pragmatist on 2006-03-26
Yes you were correct to deduce that I meant cp instead of gedit.

I'm glad you asked about the inittab since there were a couple of things I forgot to mention:

1.) You want to comment out any lines containing the word "mgetty".  So this line you mention: #T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3
You should keep it the way it is (where the first character is a #)  Any other lines that have the word "mgetty" (not "mingetty"  or "vgetty" or "agetty" exactly "mgetty") you comment out by placing a # at the head of the line.

There will be a series of lines like these:
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

After the last of these lines (which all have the phrase "respawn") you place this:

**S1:23:respawn:/usr/sbin/vgetty ttyS0 **

Please note: I made a mistake in my last post regarding the path to the vgetty program.  I left it as /usr/local/sbin/vgetty (which was the path used by the person whose website I was consulting).  I actually typed this mistaken path in myself and wondered at first why nothing was happening! :)

If you really want to be methodical, you can check for sure if your executable is located at /usr/sbin by just typing:
```
ls -l /usr/sbin/vgetty
```  Or, you could do as I did and use locate to find where the vgetty executable is:
```
sudo updatedb
```
```
locate vgetty 
```
Also, if you want to actually see if it all works, after you complete everything I explained, you need to type this first:

```
sudo init q
```

This has the system re-read the /etc/inittab file, which is necessary if you want it to recognize any changes you make to it without having to reboot.

---

### Post by daacosta on 2006-03-26
[QUOTE=Pragmatist]
I'm glad you asked about the inittab since there were a couple of things I forgot to mention:

1.) You want to comment out any lines containing the word "mgetty".  So this line you mention: #T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3
You should keep it the way it is (where the first character is a #)  
[/quote]

Question: You want me to remove the # sign in front of this line and correct the port for my modem as follows?

```
T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS0
```

[quote=Pragmatist]
Any other lines that have the word "mgetty" (not "mingetty"  or "vgetty" or "agetty" exactly "mgetty") you comment out by placing a # at the head of the line.

There will be a series of lines like these:
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

After the last of these lines (which all have the phrase "respawn") you place this:

**S1:23:respawn:/usr/sbin/vgetty ttyS0 **

[/quote]

So, you are asking me to include a # before the lines

```

#1:2345:respawn:/sbin/getty 38400 tty1
#2:23:respawn:/sbin/getty 38400 tty2
#3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

```

I will figure out the last part tomorrow :D

Please confirm that I am not mistaken in the steps I am going to take :mrgreen: {comenting, uncomenting, changing to tty0... I am already dizzy... Sorry}

And thanks for your time...

[QUOTE=Pragmatist]
Please note: I made a mistake in my last post regarding the path to the vgetty program.  I left it as /usr/local/sbin/vgetty (which was the path used by the person whose website I was consulting).  I actually typed this mistaken path in myself and wondered at first why nothing was happening! :)

If you really want to be methodical, you can check for sure if your executable is located at /usr/sbin by just typing:
```
ls -l /usr/sbin/vgetty
```  Or, you could do as I did and use locate to find where the vgetty executable is:
```
sudo updatedb
```
```
locate vgetty 
```
Also, if you want to actually see if it all works, after you complete everything I explained, you need to type this first:

```
sudo init q
```

This has the system re-read the /etc/inittab file, which is necessary if you want it to recognize any changes you make to it without having to reboot.[/QUOTE]

---

### Post by Pragmatist on 2006-03-26
Not sure how you came to your conclusions.  My directions were explicit:

Your first question: 
> Originally Posted by: **daacosta**
Question: You want me to remove the # sign in front of this line and correct the port for my modem as follows?

Answer: look in the quote of mine that you gave in your last post:
> Originally Posted by: **Pragmatist**
So **this line** you mention: **#T3:23:respawn:/sbin/*mgetty* -x0 -s 57600 ttyS3**
You should **keep it the way it is** (where the** first character is a #**) 

Your second question:
>  Originally Posted by: **daacosta**
So, you are asking me to include a # before the lines
#1:2345:respawn:/sbin/getty 38400 tty1
#2:23:respawn:/sbin/**getty** 38400 tty2
#3:23:respawn:/sbin/**getty** 38400 tty3
#4:23:respawn:/sbin/**getty** 38400 tty4
#5:23:respawn:/sbin/**getty** 38400 tty5
#6:23:respawn:/sbin/**getty** 38400 tty6


Answer: look in the quote of mine that you gave in your last post:
>  Originally Posted by: **Pragmatist**
You want to comment out any lines containing the word **"mgetty"**

> Originally Posted by: **daacosta**
...comenting, uncomenting, changing to tty0... I am already dizzy...

As I said before, this is an *advanced* project; it is not user-friendly.  Just reminding you since you seem to have an expectation that this should be easy.  
 
Let me know when you've completed my current instructions.  I'll wait until you're where I'm at before I proceed further.

---

### Post by daacosta on 2006-03-26
[QUOTE=Pragmatist]

As I said before, this is an *advanced* project; it is not user-friendly.  Just reminding you since you seem to have an expectation that this should be easy.  

[/QUOTE]

Oh no!  I wasn't expecting it to be easy :mrgreen:

Thanks for patience!

There was only one instance in which I found mgetty on my inittab file.  Namely the line

#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

Ergo, I don't have to do anything to the file in question if I understood correctly your instructions.  This is the way the file looks:

```

# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
S1:23:respawn:/usr/sbin/vgetty ttyS0


# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3


```

---

### Post by Pragmatist on 2006-03-27
Looks good. :)  So here is an overview of what you still need to do:

1.) record a message, test that it works, and put it in /var/spool/voice/messages

2.) type **init q** to make sure the vgetty program is running and listening for calls.

3.) Try it out!  Mine never works at this stage, but maybe yours will.

if necessary....4.) troubleshoot the modem

Obviously you should consult my earlier post for the exact details.

---

### Post by daacosta on 2006-03-27
Thanks Pragmatist.  I will try to complete the last part of the project tonight.

Rgds,

-D-

---

### Post by daacosta on 2006-03-29
[QUOTE=Pragmatist]Looks good. :)  So here is an overview of what you still need to do:

1.) record a message, test that it works, and put it in /var/spool/voice/messages

[/QUOTE]

:(  Hmmm... I don't know if I did this right but this was the output:

```

daacosta@ubuntu:~$ vm record standard.rmd
cannot open logfile /var/log/mgetty/mg_unknown.log: Permission denied
cannot log to /dev/console, disable logging: Permission denied
cannot open logfile /var/log/mgetty/vm.log: Permission denied
cannot log to /dev/console, disable logging: Permission denied
cannot open logfile /var/log/mgetty/vm.log: Permission denied
cannot log to /dev/console, disable logging: Permission denied
vm: could not open a voice modem device
daacosta@ubuntu:~$

```

Should I sudo it?  That is: sudo vm record standard.rmd

I unmuted the mic from the master volume control and increased its volume... This is with the alsa mixer, right?

Boy, do I feel like such an idiot!

:(

I haven't jumped to the rest of the instructions since I got stuck there :(

---

### Post by Pragmatist on 2006-03-29
Use sudo.  

Sorry I didn't suggest that, but I didn't follow that step (I used a digital recorder to produce a WAV file and then blah blah...not the best approach; I may still need to get a microphone...)

> Boy, do I feel like such an idiot! 
Welcome to Linux! :p
Seriously, I believe that we learn the most when going through the fire with projects such as these.  Hang in there!

---

### Post by patslap on 2006-09-27
I'm thinking of trying VOCP - but I have a conexant chipset internal winmodem and I'm running Dapper 64-bit. Is it worth trying with this setup, or should I invest in a serial modem?

---

### Post by Pragmatist on 2006-09-27
I don't know about your specific hardware, but when I last tried VOCP two years ago, I bought a serial modem.  In general, Linux works great with serial devices since no special drivers are usually needed.  As I undersand it, winmodems are notoriously difficult to use with Linux.

---

### Post by patslap on 2006-09-28
Maybe I'll get a serial modem then, as I'm still very much a noob! Any recommendations as to what chipset to go for? I've seen options for Intel, conexant, and Topic, in several different 56K serial modems.

Thanks.

---

### Post by Pragmatist on 2006-09-28
Check out the VOCP website.

[http://www.vocpsystem.com/install_modems.php?mode=function](http://www.vocpsystem.com/install_modems.php?mode=function)

They list several specific modems that are known to work.

---

### Post by Patb on 2006-10-18
Hi.  Sorry to be a bit thick but having set up my answering machine using the mgetty packages and tested it from another phone (seems to record okay), how do I actually listen to the recorded messages?  I've tried various combinations of "vm play [filename.rmd]" with a headset connected to either the computer (desktop) or the modem (external Diamond Voice 56E) but not a vestige of sound anywhere.  Any help/suggestions appreciated.  Cheers, Pat.

---

### Post by Patb on 2006-10-20
Hi. I'm still stuck. Can anyone tell me what is the 'normal' way to listen to recorded messages using mgetty/vgetty/vm?  Thanks, Pat.

---

### Post by Pragmatist on 2006-10-22
> **Patb said:**
> Hi. I'm still stuck. Can anyone tell me what is the 'normal' way to listen to recorded messages using mgetty/vgetty/vm?  Thanks, Pat.

My guess is that your modem isn't capturing voice yet.

Here is what I would do to make sure:

1.) Get or make a useable WAV file
2.) Convert the WAV file to a PVF (test this new PVF file if possible)
3.) Finally convert the PVF to an RMD file for testing
4.) Play the RMD file

The programs you use are: [B]wavtopvf  pvftormd
[/B]You could also test your RMD file by doing this all in reverse.  Use **rmdtopvf**  and then **pvftowav** and see if the WAV file sounds like anything.

If it all works, it means your problem isn't playing RMD files.  The problem probably is configuring your modem to capture voice.

My recollection, of using VOCP two years ago, is that there was alot of testing and trial and error and experimentation.  If you have a modem that is known to work, and you like hacking around, then stick with it.

---

### Post by Pragmatist on 2006-10-22
Check out this website:

[http://www.section6.net/wiki/index.php/Turning_Linux_into_an_Answering_Machine](http://www.section6.net/wiki/index.php/Turning_Linux_into_an_Answering_Machine)

It states you can also test your rmd file, using your sound card, by typing this:

```
rmdtopvf filename.rmd | pvfspeed -s 8000 | pvftobasic > /dev/audio
```

---

### Post by Patb on 2006-10-24
Thanks for the advice Pragmatist.  I was able to convert wav to pvf to rmd using pvftools but not able to play it.  The code for playing via the sound card worked like a charm, thanks.  

Just one other thing - I tried typing "vm devicetest" and got the following output:
```
Test Dialup Line, Int. Mic. and Int. Speaker: not supported by vm/vgetty-modemdriver
Test Dialup Line, Ext. Mic. and Ext. Speaker: not supported by vm/vgetty-modemdriver
Test Dialup Line and Local Handset: not supported by vm/vgetty-modemdriver
Test Dialup Line and Int. Speaker: not supported by vm/vgetty-modemdriver
Test Dialup Line and Ext. Speaker: not supported by vm/vgetty-modemdriver
Test Local Handset: OK
Test Int. Speaker: OK
Test Ext. Speaker: not supported by vm/vgetty-modemdriver
Test Int. Microphone: not supported by vm/vgetty-modemdriver
Test Ext. Microphone: OK
Test Dialup Line: OK
Test No Device: OK
```
From this, I would have at least expected it to play okay through the internal speaker using a command like:
```
vm play -d 6 filename.rmd
```
But I got nothing.  I'm still a bit confused but at least I can play messages through the sound card.

Cheers, Pat.

---

### Post by Pragmatist on 2006-10-24
Great!  So something works ;)

Please post/attach your **vocp.conf** file.

---

### Post by Patb on 2006-10-24
Thanks Pragmatist.  I have not installed VOCP so I don't have a vocp.conf file.  

I have successfully recorded a standard greeting message.  I found by the way that I got a better quality of sound by converting from a wav file using pvftools than I did by recording through the modem using vm record.  

And now thanks to your advice, I can play back via the sound card the messages which vgetty records, which is fine for my purposes.  

Next step is to write a reasonably user-friendly script for listening to the recorded messages one at a time.  I'm probably reinventing the vocp wheel here but anyway... :-? 

Cheers, Pat.

---

### Post by patslap on 2006-12-13
> 
Stage two: software
1.) go into synaptic: ```
sudo synaptic
```
2.) do a search with keyword: **mgetty**
3.) Click the box to the left of these packages, select 'install package' and press 'apply':
[B]mgetty
mgetty-pvftools
mgetty-voice
mgetty-docs[/B]

Let's start with that.  I'm digging out my external modem, which I got to work in the past, and I'm going to do this along with you.  My following post will present the next steps.

Hi

I'm trying this out for myself. I have acquired a U. S. Robotics serial modem and am using a minimal Xubuntu installation on an old 600Mhz Celeron PC.

Following the instructions above from post #6 by Pragmatist, I'm stuck already; when I search for 'mgetty' in synaptic I only get two results: 'mgetty' and 'mgetty-fax'. How do I get 'mgetty-pvftools', 'mgetty-voice', and 'mgetty-docs'?

Thank you.

---

### Post by beanni on 2007-02-15
This is really starting to turn into a great walk through pragmatist - thanks a bunch.  I am trying to do this myself, but having some problems and I am guessing it is becasuse I have an internal class 1 Lucent voice/fax/data modem.  I think this is a Linmodem (LT WinModem) and therefore is probably the reason why I am having troubles.  As you have probably already worked out I am a complete Newb.  I haven't tried to record a message yet, but after following all your steps and trying to call the modem it doesnt answer as it should.  Do you have any pointers on where I should go now.  

I would also like to set it up fax sending and retrieval.  Any tips?

---

### Post by Pragmatist on 2007-02-16
> **patslap said:**
> 
How do I get 'mgetty-pvftools', 'mgetty-voice', and 'mgetty-docs'?



Please post the contents of this file: 

 /etc/apt/sources.list

---

### Post by Pragmatist on 2007-02-16
> **beanni said:**
> I think this is a Linmodem (LT WinModem) and therefore is probably the reason why I am having troubles.  

I would tend to agree with you.  My advice is to use one of the modems listed in the database on the VOCP website.  Even better, use one of the modems they specifically recommend.

> **beanni said:**
> Do you have any pointers on where I should go now.  

As I said in post #21 in this thread:

Check out the VOCP website.

[http://www.vocpsystem.com/install_mo...?mode=function]("http://www.vocpsystem.com/install_modems.php?mode=function")

I would thoroughly examine all of the resources on the VOCP site.

> **beanni said:**
>  I would also like to set it up fax sending and retrieval.  Any tips?

After searching the VOCP website :), I see that you could also fax with VOCP:
[http://www.vocpsystem.com/fax_setup.php?mode=function](http://www.vocpsystem.com/fax_setup.php?mode=function)

If you don't want to use VOCP for faxing, see the wiki:
[https://help.ubuntu.com/community/DialupAndFax?highlight=%28fax%29](https://help.ubuntu.com/community/DialupAndFax?highlight=%28fax%29)

It also looks like they might make faxing even better in Feisty:
[https://help.ubuntu.com/community/DialupAndFax?highlight=%28fax%29](https://help.ubuntu.com/community/DialupAndFax?highlight=%28fax%29)

Also, you could search the forums using the keyword "fax" and search google linux: [www.google.com/linux](www.google.com/linux) 

Finally, check out my thread "How to Help Yourself":
[http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716)

In addition to my comments there are many other suggestions posted by other people that could help you not just solve this problem but many others as well.

---

### Post by patslap on 2007-03-07
> **Pragmatist said:**
> Please post the contents of this file: 

 /etc/apt/sources.list

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) Dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) Dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) Dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) Dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) Dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) Dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) Dapper free non-free

---

### Post by Pragmatist on 2007-03-07
There are two issues here, as I see it:

1. Why can't you find the mgetty packages in synaptic
2. How do you get the mgetty packages.

The second is much easier to solve as you can individually download the handful of mgetty packages that you need.  However, I think it is more fundamental to make sure you can get it through synaptic.  First, let us see what you have presently.

Try this:
```
sudo updatedb
```

and then post the results of this:
```
locate mgetty
```

Next, when you go into synaptic, how many packages does it say are available?  Click "All" in the left sidebar and then read the status bar at the bottom of the window.  Mine reads: >  20312 packages listed, 1820 installed, 0 broken, 0 to install/upgrade, 0 to remove

---

### Post by patslap on 2007-03-08
Ok - done the first two steps:

> **Pragmatist said:**
> There are two issues here, as I see it:

1. Why can't you find the mgetty packages in synaptic
2. How do you get the mgetty packages.

The second is much easier to solve as you can individually download the handful of mgetty packages that you need.  However, I think it is more fundamental to make sure you can get it through synaptic.  First, let us see what you have presently.

Try this:
```
sudo updatedb
```

and then post the results of this:
```
locate mgetty
```


pat@pat-desktop:~$ sudo updatedb
Password:
pat@pat-desktop:~$ locate mgetty
/var/lib/dpkg/info/mgetty.postinst
/var/lib/dpkg/info/mgetty.list
/var/lib/dpkg/info/mgetty.postrm
/var/lib/dpkg/info/mgetty.conffiles
/var/lib/dpkg/info/mgetty.md5sums
/var/lib/dpkg/info/mgetty-docs.postinst
/var/lib/dpkg/info/mgetty-docs.list
/var/lib/dpkg/info/mgetty-docs.preinst
/var/lib/dpkg/info/mgetty-docs.prerm
/var/lib/dpkg/info/mgetty-docs.md5sums
/var/lib/dpkg/info/mgetty-fax.config
/var/lib/dpkg/info/mgetty-fax.list
/var/lib/dpkg/info/mgetty-fax.templates
/var/lib/dpkg/info/mgetty-fax.postinst
/var/lib/dpkg/info/mgetty-fax.preinst
/var/lib/dpkg/info/mgetty-fax.prerm
/var/lib/dpkg/info/mgetty-fax.postrm
/var/lib/dpkg/info/mgetty-fax.conffiles
/var/lib/dpkg/info/mgetty-fax.md5sums
/var/lib/dpkg/info/mgetty-viewfax.postinst
/var/lib/dpkg/info/mgetty-viewfax.list
/var/lib/dpkg/info/mgetty-viewfax.postrm
/var/lib/dpkg/info/mgetty-viewfax.md5sums
/var/lib/dpkg/info/mgetty-voice.postinst
/var/lib/dpkg/info/mgetty-voice.list
/var/lib/dpkg/info/mgetty-voice.postrm
/var/lib/dpkg/info/mgetty-voice.md5sums
/var/log/mgetty
/var/log/mgetty/vm.log
/var/log/mgetty/fax
/var/log/mgetty/mg_unknown.log
/var/log/mgetty/mg_unknown.log.1
/var/log/mgetty/vg_ttyS0.log
/var/log/mgetty/vg_ttyS0.log.2.gz
/var/log/mgetty/mg_unknown.log.2.gz
/var/log/mgetty/vm.log.1
/var/log/mgetty/vg_ttyS0.log.1
/var/log/mgetty/vg_ttyS0.log.3.gz
/var/log/mgetty/vg_ttyS0.log.4.gz
/var/log/mgetty/vg_ttyS0.log.5.gz
/var/log/mgetty/vg_ttyS0.log.6.gz
/var/log/mgetty/vg_ttyS0.log.7.gz
/etc/init.d/mgetty-fax
/etc/logrotate.d/mgetty-fax
/etc/logrotate.d/mgetty
/etc/rc0.d/K20mgetty-fax
/etc/rc1.d/K20mgetty-fax
/etc/rc2.d/S20mgetty-fax
/etc/rc3.d/S20mgetty-fax
/etc/rc4.d/S20mgetty-fax
/etc/rc5.d/S20mgetty-fax
/etc/rc6.d/K20mgetty-fax
/etc/issue.mgetty
/etc/mgetty
/etc/mgetty/faxheader
/etc/mgetty/mgetty.config
/etc/mgetty/dialin.config
/etc/mgetty/login.config
/etc/mgetty/new_fax
/etc/mgetty/faxrunq.config
/etc/mgetty/sendfax.config
/etc/mgetty/voice.conf
/etc/mgetty/voice.conf.BAK
/sbin/mgetty
/usr/lib/mime/packages/mgetty-viewfax
/usr/lib/mgetty-fax
/usr/lib/mgetty-fax/faxq-helper
/usr/lib/mgetty-fax/cour25.pbm
/usr/lib/mgetty-fax/cour25n.pbm
/usr/share/doc/mgetty
/usr/share/doc/mgetty/changelog.Debian.gz
/usr/share/doc/mgetty/README.Debian
/usr/share/doc/mgetty/TODO.Debian
/usr/share/doc/mgetty/copyright
/usr/share/doc/mgetty/changelog.gz
/usr/share/doc/mgetty/README.callback
/usr/share/doc/mgetty/examples
/usr/share/doc/mgetty/examples/faxmemo
/usr/share/doc/mgetty/examples/fax
/usr/share/doc/mgetty/examples/inittab.DEBIAN
/usr/share/doc/mgetty/examples/answer_fax.sh
/usr/share/doc/mgetty/examples/coverpg-pl.ps
/usr/share/doc/mgetty/examples/coverpg.pbm
/usr/share/doc/mgetty/examples/coverpg.ps
/usr/share/doc/mgetty/examples/new_fax.NeXT
/usr/share/doc/mgetty/examples/faxview.th
/usr/share/doc/mgetty/examples/new_fax.mail
/usr/share/doc/mgetty/examples/new_fax.all
/usr/share/doc/mgetty/examples/new_fax.all/archive.module
/usr/share/doc/mgetty/examples/new_fax.all/INSTALL
/usr/share/doc/mgetty/examples/new_fax.all/delete.module
/usr/share/doc/mgetty/examples/new_fax.all/fax.module
/usr/share/doc/mgetty/examples/new_fax.all/faxlist
/usr/share/doc/mgetty/examples/new_fax.all/faxlist.dist
/usr/share/doc/mgetty/examples/new_fax.all/list.module
/usr/share/doc/mgetty/examples/new_fax.all/mail.module
/usr/share/doc/mgetty/examples/new_fax.all/new_fax
/usr/share/doc/mgetty/examples/new_fax.all/notify.module
/usr/share/doc/mgetty/examples/new_fax.all/print.module
/usr/share/doc/mgetty/examples/new_fax.all/write.module
/usr/share/doc/mgetty/examples/new_fax.all/README.gz
/usr/share/doc/mgetty/examples/new_fax.hpa
/usr/share/doc/mgetty/examples/new_fax.lj
/usr/share/doc/mgetty/examples/new_fax.vacation
/usr/share/doc/mgetty/examples/new_fax.mime1
/usr/share/doc/mgetty/examples/new_fax.mime3
/usr/share/doc/mgetty/examples/new_fax.pbm
/usr/share/doc/mgetty/examples/new_fax.th
/usr/share/doc/mgetty/examples/new_fax.tiff
/usr/share/doc/mgetty/examples/new_fax.mime4.gz
/usr/share/doc/mgetty/examples/printfax
/usr/share/doc/mgetty/examples/printfax.ps
/usr/share/doc/mgetty/voice
/usr/share/doc/mgetty/voice/Readme.Beginners
/usr/share/doc/mgetty/voice/examples
/usr/share/doc/mgetty/voice/examples/perl
/usr/share/doc/mgetty/voice/examples/perl/answering_machine.pl
/usr/share/doc/mgetty/voice/examples/perl/ChangeLog
/usr/share/doc/mgetty/voice/examples/perl/MANIFEST
/usr/share/doc/mgetty/voice/examples/perl/Makefile.PL
/usr/share/doc/mgetty/voice/examples/perl/README
/usr/share/doc/mgetty/voice/examples/perl/Vgetty.pm.gz
/usr/share/doc/mgetty/voice/examples/perl/callme.pl
/usr/share/doc/mgetty/voice/examples/scripts
/usr/share/doc/mgetty/voice/examples/scripts/convert_wav_to_rmd.sh
/usr/share/doc/mgetty/voice/examples/scripts/button.sh.gz
/usr/share/doc/mgetty/voice/examples/scripts/demo.pl.gz
/usr/share/doc/mgetty/voice/examples/scripts/dtmf.sh.gz
/usr/share/doc/mgetty/voice/examples/scripts/events.sh
/usr/share/doc/mgetty/voice/examples/scripts/demo.sh
/usr/share/doc/mgetty/voice/examples/scripts/speakdate.pl
/usr/share/doc/mgetty/voice/examples/scripts/faxback.sh
/usr/share/doc/mgetty/voice/examples/scripts/listen.sh
/usr/share/doc/mgetty/voice/examples/scripts/message.sh
/usr/share/doc/mgetty/voice/examples/scripts/new_voice.craig_southern
/usr/share/doc/mgetty/voice/examples/scripts/rsynth-0.9.linuxA.pch
/usr/share/doc/mgetty/voice/examples/scripts/speakdate.sh
/usr/share/doc/mgetty/voice/examples/scripts/vmtest.sh
/usr/share/doc/mgetty/voice/examples/scripts/Vgetty.sh.gz
/usr/share/doc/mgetty/voice/examples/scripts/Vgetty.sh.EXAMPLE.gz
/usr/share/doc/mgetty/voice/examples/scripts/dtmf_alpha.sh.gz
/usr/share/doc/mgetty/voice/NOTE
/usr/share/doc/mgetty/voice/compression_settings
/usr/share/doc/mgetty/voice/device_settings
/usr/share/doc/mgetty/voice/Readme.pvftools.gz
/usr/share/doc/mgetty/voice/Readme.voice_shell.gz
/usr/share/doc/mgetty/README.1st
/usr/share/doc/mgetty/FTP
/usr/share/doc/mgetty/README.viewfax
/usr/share/doc/mgetty/contrib
/usr/share/doc/mgetty/contrib/faxdvi2.perl.gz
/usr/share/doc/mgetty/contrib/next-login
/usr/share/doc/mgetty/contrib/next-login/Makefile
/usr/share/doc/mgetty/contrib/next-login/pathnames.h
/usr/share/doc/mgetty/contrib/next-login/setenv.c
/usr/share/doc/mgetty/contrib/next-login/README.gz
/usr/share/doc/mgetty/contrib/next-login/login.c.gz
/usr/share/doc/mgetty/contrib/ptylogin
/usr/share/doc/mgetty/contrib/ptylogin/ptylogin.c.gz
/usr/share/doc/mgetty/contrib/ptylogin/Makefile
/usr/share/doc/mgetty/contrib/ptylogin/TESTS
/usr/share/doc/mgetty/contrib/ptylogin/ptylogin.1
/usr/share/doc/mgetty/contrib/Makefile
/usr/share/doc/mgetty/contrib/3b1.gz
/usr/share/doc/mgetty/contrib/mgetty-to-flexfax.sh
/usr/share/doc/mgetty/contrib/faxdvi.config
/usr/share/doc/mgetty/contrib/g3tolj.c.gz
/usr/share/doc/mgetty/contrib/faxin.c
/usr/share/doc/mgetty/contrib/g3toxwd.c.gz
/usr/share/doc/mgetty/contrib/sun.readme
/usr/share/doc/mgetty/contrib/faxmail-smail
/usr/share/doc/mgetty/contrib/g3tops.c.gz
/usr/share/doc/mgetty/contrib/ttyenable.gz
/usr/share/doc/mgetty/contrib/g3tolj.1
/usr/share/doc/mgetty/contrib/g3toxwd.gz
/usr/share/doc/mgetty/contrib/g3toxwd.1
/usr/share/doc/mgetty/contrib/gs-security.fix
/usr/share/doc/mgetty/contrib/logparse.c
/usr/share/doc/mgetty/contrib/lp-fax
/usr/share/doc/mgetty/contrib/pbm2styl800.tar.gz
/usr/share/doc/mgetty/contrib/pbmscale.c
/usr/share/doc/mgetty/contrib/g3tolj.gz
/usr/share/doc/mgetty/contrib/pgx.c
/usr/share/doc/mgetty/contrib/readme.supra
/usr/share/doc/mgetty/contrib/scrts.c
/usr/share/doc/mgetty/contrib/tsfax-0.1.tgz
/usr/share/doc/mgetty/contrib/usr_gotcha.mail.gz
/usr/share/doc/mgetty/contrib/autoprint.sh
/usr/share/doc/mgetty/contrib/watchit.pl
/usr/share/doc/mgetty/contrib/README.gz
/usr/share/doc/mgetty/contrib/dvi-fax.gz
/usr/share/doc/mgetty/contrib/faxiobe.sh.gz
/usr/share/doc/mgetty/contrib/frame40ps.fix.gz
/usr/share/doc/mgetty/contrib/pbmsplit.c.gz
/usr/share/doc/mgetty/contrib/two-modems.gz
/usr/share/doc/mgetty/frontends
/usr/share/doc/mgetty/frontends/dialog
/usr/share/doc/mgetty/frontends/dialog/Makefile
/usr/share/doc/mgetty/frontends/dialog/xfaxq.in
/usr/share/doc/mgetty/frontends/dialog/xfaxq.1in
/usr/share/doc/mgetty/frontends/dialog/faxv2
/usr/share/doc/mgetty/frontends/dialog/faxv.in.gz
/usr/share/doc/mgetty/frontends/X11
/usr/share/doc/mgetty/frontends/X11/xforms.note.gz
/usr/share/doc/mgetty/frontends/X11/wosch.note
/usr/share/doc/mgetty/frontends/mail2fax
/usr/share/doc/mgetty/frontends/mail2fax/mail2fax.pl.gz
/usr/share/doc/mgetty/frontends/mail2fax/README.html
/usr/share/doc/mgetty/frontends/mail2fax/Test.Mail
/usr/share/doc/mgetty/frontends/mail2fax/WISHLIST
/usr/share/doc/mgetty/frontends/mail2fax/mail2fax.rc
/usr/share/doc/mgetty/frontends/mail2fax/README.gz
/usr/share/doc/mgetty/frontends/emacs
/usr/share/doc/mgetty/frontends/emacs/rs
/usr/share/doc/mgetty/frontends/emacs/rs/faxutil.el.gz
/usr/share/doc/mgetty/frontends/emacs/rs/ChangeLog
/usr/share/doc/mgetty/frontends/emacs/rs/README
/usr/share/doc/mgetty/frontends/emacs/rs/phone.el.gz
/usr/share/doc/mgetty/frontends/emacs/rs/sendfax.el.gz
/usr/share/doc/mgetty/frontends/emacs/faxmode10.ANN
/usr/share/doc/mgetty/frontends/emacs/faxmode11.ANN
/usr/share/doc/mgetty/frontends/faxmail
/usr/share/doc/mgetty/frontends/faxmail/aliases
/usr/share/doc/mgetty/frontends/faxmail/faxmail
/usr/share/doc/mgetty/frontends/voice
/usr/share/doc/mgetty/frontends/voice/fortytwo.README
/usr/share/doc/mgetty/frontends/voice/README
/usr/share/doc/mgetty/frontends/voice/am_tool.tar.gz
/usr/share/doc/mgetty/frontends/tcl
/usr/share/doc/mgetty/frontends/tcl/tkscanfax.txt
/usr/share/doc/mgetty/frontends/tcl/faxview-0.2
/usr/share/doc/mgetty/frontends/tcl/faxview-0.2/readline.tcl.gz
/usr/share/doc/mgetty/frontends/tcl/faxview-0.2/ChangeLog
/usr/share/doc/mgetty/frontends/tcl/faxview-0.2/INSTALL
/usr/share/doc/mgetty/frontends/tcl/faxview-0.2/faxview.man.gz
/usr/share/doc/mgetty/frontends/tcl/faxview-0.2/COPYING.gz
/usr/share/doc/mgetty/frontends/tcl/faxview-0.2/faxview.tcl.gz
/usr/share/doc/mgetty/frontends/tcl/README
/usr/share/doc/mgetty/frontends/mmdf-mail2fax
/usr/share/doc/mgetty/frontends/mmdf-mail2fax/faxgate.pl
/usr/share/doc/mgetty/frontends/mmdf-mail2fax/README.gz
/usr/share/doc/mgetty/frontends/network
/usr/share/doc/mgetty/frontends/network/README
/usr/share/doc/mgetty/frontends/perl-tk
/usr/share/doc/mgetty/frontends/perl-tk/faxman.doc
/usr/share/doc/mgetty/frontends/perl-tk/README
/usr/share/doc/mgetty/frontends/perl-tk/handle_commands.pl.gz
/usr/share/doc/mgetty/frontends/perl-tk/XYListbox.pm
/usr/share/doc/mgetty/frontends/perl-tk/xfax.pl.gz
/usr/share/doc/mgetty/frontends/perl-tk/Makefile
/usr/share/doc/mgetty/frontends/perl-tk/faxman.pl.gz
/usr/share/doc/mgetty/frontends/perl-tk/FileSelector.pm.gz
/usr/share/doc/mgetty/frontends/winword2
/usr/share/doc/mgetty/frontends/winword2/WinFaxServ.pl
/usr/share/doc/mgetty/frontends/winword2/README
/usr/share/doc/mgetty/frontends/winword2/ww6fax.macro
/usr/share/doc/mgetty/frontends/windows
/usr/share/doc/mgetty/frontends/windows/esemfax.txt
/usr/share/doc/mgetty/frontends/windows/README
/usr/share/doc/mgetty/frontends/windows/win+samba-2.txt.gz
/usr/share/doc/mgetty/frontends/windows/win+samba.txt
/usr/share/doc/mgetty/frontends/windows/lprfax.txt
/usr/share/doc/mgetty/frontends/winword
/usr/share/doc/mgetty/frontends/winword/mxfax10.zip
/usr/share/doc/mgetty/frontends/winword/README
/usr/share/doc/mgetty/frontends/winword/faxfilter.gz
/usr/share/doc/mgetty/frontends/xtexsh
/usr/share/doc/mgetty/frontends/xtexsh/xtexsh_fax.tgz
/usr/share/doc/mgetty/frontends/www
/usr/share/doc/mgetty/frontends/www/nph-vf-gif.in.gz
/usr/share/doc/mgetty/frontends/www/INSTALL.README
/usr/share/doc/mgetty/frontends/www/faxq-v.in
/usr/share/doc/mgetty/frontends/www/index-d.in
/usr/share/doc/mgetty/frontends/www/index-e.in
/usr/share/doc/mgetty/frontends/www/faxhists.in
/usr/share/doc/mgetty/frontends/www/Makefile
/usr/share/doc/mgetty/frontends/www/simplequant.pl
/usr/share/doc/mgetty/frontends/www/wwwsub.pl
/usr/share/doc/mgetty/frontends/www/TODO
/usr/share/doc/mgetty/frontends/www/wwwgui.cfg.in
/usr/share/doc/mgetty/frontends/www/README.gz
/usr/share/doc/mgetty/frontends/www/faxq.in.gz
/usr/share/doc/mgetty/frontends/www/faxhist.in.gz
/usr/share/doc/mgetty/frontends/www/viewfax.in.gz
/usr/share/doc/mgetty/frontends/www/faxsend.in.gz
/usr/share/doc/mgetty/frontends/Makefile
/usr/share/doc/mgetty/frontends/README
/usr/share/doc/mgetty/frontends/faxdvi-1.1.tar.gz
/usr/share/doc/mgetty/frontends/smail-direct.cfg
/usr/share/doc/mgetty/frontends/faxit.README.gz
/usr/share/doc/mgetty/frontends/gfax.README
/usr/share/doc/mgetty/frontends/faxpr.README
/usr/share/doc/mgetty/frontends/StarOffice.txt
/usr/share/doc/mgetty/frontends/fax-by-lpr.txt.gz
/usr/share/doc/mgetty/loginv2.txt
/usr/share/doc/mgetty/mgetty.texi.gz
/usr/share/doc/mgetty/modems.db.gz
/usr/share/doc/mgetty/ttyS-cua.txt
/usr/share/doc/mgetty/fhng-codes.gz
/usr/share/doc/mgetty/TODO.gz
/usr/share/doc/mgetty/win95.ppp
/usr/share/doc/mgetty/BUGS
/usr/share/doc/mgetty/scanner.txt.gz
/usr/share/doc/mgetty/THANKS
/usr/share/doc/mgetty/fax.magic
/usr/share/doc/mgetty/fax
/usr/share/doc/mgetty/fax/faxspool.rules.sample
/usr/share/doc/mgetty/secure_tty.txt.gz
/usr/share/doc/mgetty/changelog.voice.gz
/usr/share/doc/mgetty/voice.magic
/usr/share/doc/mgetty-docs
/usr/share/doc/mgetty-docs/changelog.Debian.gz
/usr/share/doc/mgetty-docs/copyright
/usr/share/doc/mgetty-fax
/usr/share/doc/mgetty-viewfax
/usr/share/doc/mgetty-viewfax/changelog.gz
/usr/share/doc/mgetty-viewfax/viewfax.tif
/usr/share/doc/mgetty-viewfax/copyright
/usr/share/doc/mgetty-viewfax/changelog.Debian.gz
/usr/share/doc/mgetty-voice
/usr/share/info/mgetty.info.gz
/usr/share/man/man1/mgetty-fax.1.gz
/usr/share/man/man4/mgettydefs.4.gz
/usr/share/man/man8/mgetty.8.gz
/usr/share/mgetty
/usr/share/mgetty/templates
/usr/share/mgetty/templates/etc
/usr/share/mgetty/templates/etc/dialin.config
/usr/share/mgetty/templates/etc/login.config
/usr/share/mgetty/templates/etc/mgetty.config
/usr/share/mgetty/templates/etc/faxrunq.config
/usr/share/mgetty/templates/etc/sendfax.config
/usr/share/mgetty/templates/etc/faxheader
/usr/share/mgetty/templates/etc/voice.conf

---

### Post by patslap on 2007-03-08
> Next, when you go into synaptic, how many packages does it say are available?  Click "All" in the left sidebar and then read the status bar at the bottom of the window.  Mine reads:

Synaptic reads: 2253 packages listed, 1664 installed, 0 broken, 0 to install/upgrade, 0 to remove

---

### Post by Pragmatist on 2007-03-08
> **patslap said:**
> Synaptic reads: 2253 packages listed, 1664 installed, 0 broken, 0 to install/upgrade, 0 to remove

Are you sure you pressed "All" on the left sidebar?  If you notice, I have ten times as many packages available to me! (~20,000 versus ~2000).  I'm using Edgy, but the number is similar in dapper (~18,000 sounds familiar).

We'll try this without Synaptic for the moment:

First:
```
sudo apt-get update
```

Then:
```
sudo apt-get install mgetty-pvftools
```

Post the information from your terminal.  Did it install the package?

---

### Post by patslap on 2007-03-09
Yep - I clicked on all. Here's a screenshot of synaptic (attached below).

I'll try the apt-get method instead....
.
.
.
.
OK - done that, but it didn't appear to be successful. Here's the ouput I got in the terminal:

```
pat@pat-desktop:~$ sudo apt-get update
Password:
Ign http://archive.canonical.com Dapper-commercial Release.gpg
Get: 1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://archive.canonical.com Dapper-commercial Release
Hit http://archive.canonical.com dapper-commercial Release
Ign http://archive.canonical.com Dapper-commercial/main Packages
Errhttp://archive.canonical.com Dapper-commercial/main Packages
  404 Not Found
Hit http://archive.canonical.com dapper-commercial/main Packages
Get: 2 http://gb.archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://security.ubuntu.com Dapper-security Release.gpg
Get: 3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Ign http://archive.ubuntu.com Dapper Release.gpg
Ign http://archive.ubuntu.com Dapper-updates Release.gpg
Hit http://gb.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com Dapper-security Release
Ign http://archive.ubuntu.com Dapper-backports Release.gpg
Ign http://archive.ubuntu.com Dapper Release
Get: 4 http://gb.archive.ubuntu.com dapper-updates/main Packages [133kB]
Hit http://security.ubuntu.com dapper-security Release
Ign http://archive.ubuntu.com Dapper-updates Release
Ign http://security.ubuntu.com Dapper-security/main Packages
Ign http://security.ubuntu.com Dapper-security/restricted Packages
Ign http://archive.ubuntu.com Dapper-backports Release
Ign http://security.ubuntu.com Dapper-security/main Sources
Ign http://security.ubuntu.com Dapper-security/restricted Sources
Ign http://security.ubuntu.com Dapper-security/universe Packages
Ign http://security.ubuntu.com Dapper-security/universe Sources
Ign http://archive.ubuntu.com Dapper/main Packages
Ign http://archive.ubuntu.com Dapper/restricted Packages
Ign http://archive.ubuntu.com Dapper/main Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com Dapper/restricted Sources
Ign http://archive.ubuntu.com Dapper/universe Packages
Ign http://archive.ubuntu.com Dapper/universe Sources
Ign http://archive.ubuntu.com Dapper/multiverse Packages
Ign http://archive.ubuntu.com Dapper/multiverse Sources
Ign http://archive.ubuntu.com Dapper-updates/main Packages
Ign http://archive.ubuntu.com Dapper-updates/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Errhttp://security.ubuntu.com Dapper-security/main Packages
  404 Not Found
Errhttp://security.ubuntu.com Dapper-security/restricted Packages
  404 Not Found
Ign http://archive.ubuntu.com Dapper-updates/main Sources
Errhttp://security.ubuntu.com Dapper-security/main Sources
  404 Not Found
Errhttp://security.ubuntu.com Dapper-security/restricted Sources
  404 Not Found
Errhttp://security.ubuntu.com Dapper-security/universe Packages
  404 Not Found
Errhttp://security.ubuntu.com Dapper-security/universe Sources
  404 Not Found
Ign http://archive.ubuntu.com Dapper-updates/restricted Sources
Ign http://archive.ubuntu.com Dapper-backports/main Packages
Ign http://archive.ubuntu.com Dapper-backports/restricted Packages
Ign http://archive.ubuntu.com Dapper-backports/universe Packages
Ign http://archive.ubuntu.com Dapper-backports/multiverse Packages
Errhttp://archive.ubuntu.com Dapper/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/universe Packages
Hit http://gb.archive.ubuntu.com dapper-updates/multiverse Packages
Get: 5 http://gb.archive.ubuntu.com dapper-updates/main Packages [133kB]
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/universe Packages
Hit http://gb.archive.ubuntu.com dapper-updates/multiverse Packages
Errhttp://archive.ubuntu.com Dapper/universe Sources
  404 Not Found [IP: 91.189.89.8 80]
99% [5 Packages bzip2 0] [Waiting for headers] [Connecting to packages.freecont
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Errhttp://gb.archive.ubuntu.com dapper-updates/main Packages
  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages - open (2 No such file or directory)
Errhttp://archive.ubuntu.com Dapper/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper/multiverse Sources
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-updates/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-updates/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-updates/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-updates/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-backports/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-backports/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-backports/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://archive.ubuntu.com Dapper-backports/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Errhttp://packages.freecontrib.org Dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 133kB in 2m0s (1105B/s)
Failed to fetch http://packages.freecontrib.org/plf/dists/Dapper/Release.gpg  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/Dapper-commercial/main/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.bz2  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages - open (2 No such file or directory)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Dapper-security/main/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Dapper-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Dapper-security/universe/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Dapper-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/main/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/restricted/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/main/source/Sources.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/restricted/source/Sources.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/universe/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/universe/source/Sources.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/main/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/restricted/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/universe/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/multiverse/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.89.8 80]
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.
pat@pat-desktop:~$ sudo apt-get install mgetty-pvftools
Reading package lists... Done
Building dependency tree... Done
Package mgetty-pvftools is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mgetty-pvftools has no installation candidate
pat@pat-desktop:~$
```

---

### Post by Pragmatist on 2007-03-09
These people seem to have the same problem:
[http://ubuntuforums.org/showthread.php?t=368942&page=2](http://ubuntuforums.org/showthread.php?t=368942&page=2)
[http://ubuntuforums.org/showthread.php?t=374424](http://ubuntuforums.org/showthread.php?t=374424)

It appears that your problem somehow has to do with your internet connection.  You might want to try some of the things suggested in the above threads.

If it were me, I would go through these instructions first, to be sure that my repositories are setup correctly:
[http://help.ubuntu.com/community/Repositories/Ubuntu](http://help.ubuntu.com/community/Repositories/Ubuntu)
[http://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto#head-565ca70308a00d15dd8bfdfa0b030f6f2d4041f0](http://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto#head-565ca70308a00d15dd8bfdfa0b030f6f2d4041f0)

---

### Post by patslap on 2007-03-20
Hooray! I managed to fix Synaptic using information on [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) particularly the troubleshooting section at the bottom of the page. Seems like a bug was present.

Thanks for the advice Pragmatist - I'm aware it was a little off-topic. :KS 

Now back on-topic: I will try your walkthrough now that I've d/l mgetty packages. Back soon....

---

### Post by patslap on 2007-06-07
Hi - I'm back!

I've downloaded Mgetty packages and followed steps in post #8, however, when I open up /etc/inittab with gedit there is no text in the file - it is completely blank. After a quick search in the forums it appears it has now been replaced by upstart. 

What should i do?

thanks,

patslap

---

### Post by patslap on 2007-06-22
bump!

---

### Post by Pragmatist on 2007-06-22
[https://answers.launchpad.net/upstart/+question/1984](https://answers.launchpad.net/upstart/+question/1984)

---

### Post by patslap on 2007-06-22
Thanks for replying.

So should I open up /etc/event.d/tty"com port where my modem is" and add ```
S1:23:respawn:/usr/local/sbin/vgetty ttyS0
``` below the line which says "Respawn"?

This is how /etc/event.d/tty1 currently looks:

```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1
```

Thought I should check as this appears a little different from the inittab route.

Thanks

---

### Post by JohnnyVW on 2007-10-27
I just ran into this.  Anyone know where/how you put 

```

S1:23:respawn:/usr/local/sbin/vgetty ttyS0

```

now that inittab is gone?

---

### Post by Pragmatist on 2007-10-28
> **JohnnyVW said:**
> I just ran into this.  Anyone know where/how you put 

```

S1:23:respawn:/usr/local/sbin/vgetty ttyS0

```now that inittab is gone?

This subject is unnecessarily complicated.  Apparently init has been replaced with upstart.  I read many pages and I am still confused!  Here is one thread that might help you:
[http://ubuntuforums.org/showthread.php?t=277507&highlight=inittab](http://ubuntuforums.org/showthread.php?t=277507&highlight=inittab)

I think you have two basic solutions:

1.) The right way is to use the files in /etc/event.d and create a file for ttyS0  I am not sure of the exact syntax, but you could probably figure it out by comparing the different tty files in /etc/event.d or by googling.

2.) Create your own /etc/inittab  I don't know if this would work, but I read that some people tried it.  I am using Feisty and I have a /etc/inittab file.

Good luck and let us know what happens.

---

