---
title: "Can't burn DVD in Ubuntu 7.04"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by zodmaner on 2007-05-19
> EDIT: For those of you who didn't want to read the whole thread, here is the brief summary of the problem and the current situation:

1. I can't burn CD/DVD using Ubuntu 7.04 (kernel 2.6.20.15)

2. Turning off DMA using command:
[quote] sudo hdparm -d0 -k1 /dev/cdrom
solves the problem.

3. But DMA is always enable when turn on the computer (so you have to disable it everytime before burning or use startup script to disable it (having tried this yet, on a to do list.)

4. With new kernel update (2.6.20.16), DMA is turn off when inserted a blank DVD disc (weather plus or minus). Burning still works when DMA is disabled but there are problem with DVD-RW sometimes fails to burn. Still trying to locate the sources of the problem. (DVD+R(W) seems to work fine.)

(I would also like to thanks Pragmatist for all the advises and wonderful links he gave, thanks a lot man :) )
[/quote]


Hi, sorry to created a new topic. But my old [thread]("http://ubuntuforums.org/showthread.php?t=447912") seems to die a long, silent death for quite sometime.

I'm currently trying to burn a DVD with Ubuntu 7.04. I have ASUS DRW-1608P DVD-recoder drive and every attempt to burn the disc have fail (using same data, same blank media). I try every burning program available (Graveman, Gnomebaker, Nero etc.) and all burning attempt have ended in failure.

Last night I try to enable the DMA of my drive, and was able to burn a DVD! But after that one success all subsequence attempts have failed.

I have read that a lot of people have this problem as well. Can anyone give me any update on the situation? And if you used to have this problem then how do you fix it? Thanks for all the help in advance guys. 

PS. I have attached an K3b error/debug file from my latest attempt to burn a DVD, hope it might be of some use.

---

### Post by zodmaner on 2007-05-19
Ok, I try burning a DVD again using Nero Linux Beta3. Got an error again so I attached the log file. Hope it will be of some help.

---

### Post by Pragmatist on 2007-05-19
> Hi, sorry to created a new topic. But my old [thread]("http://ubuntuforums.org/showthread.php?t=447912") seems to die a long, silent death for quite sometime.

One day ago is a "long, silent death"!!!!!  Please do not make multiple posts.  One day is nothing.  If your problem is obscure enough, you can easily wait weeks, months, or even never get a response!  Hopefully, however, we can solve your problem.

One other point about posting:  Put long output into a file and attach the file.  Pasting it all into a post makes everyone do a lot of scrolling!

Before getting Nero to work, have you tried using Nautilus to burn a simple DVD?

Where did you get Nero?  I don't see it in the repositories.  In order to help you, it would be useful to download and look at Nero's documentation.

---

### Post by zodmaner on 2007-05-19
Hi, sorry for being a little bit too hasty, but I'm a little bit frustrated after wasting 10+ DVD trying various programs & methods to try and get the drive to burn properly. Again sorry, won't let this happen again. :)

To answer your question: yes I tried to use Nautilus. I try burning a data DVD (don't know if this is simple DVD) total size of data is 4.1 GB (the same size and set of file I use in other program). Needless to say, it fails to burn properly. The program start to burn and then immediately display "finish writing" and then display the error message "input/output error". Sorry but I don't have the exact error message on my hand.

I download Nero Linux 3 beta from this [link]("http://www.nero.com/eng/nerolinux-prog.php?pak=16"). The MD5 checksum of the file I download is 
> 7d6768062e9fb9ccf7941934b526a4ff   
Which seems to match the one on the official Nero site.

---

### Post by Pragmatist on 2007-05-19
It is possible that you need to enable DMA each time (until you run something on startup to do it for you).  

Try enabling DMA again, just before burning the DVD.

Also, I would try to vary my experiments a little.  First, try using different data.  Second, use a small file (not 4GB).  Finally, you might want to try a DVD-RW since this will help to determine the problem (and it won't cost you so many DVD's!!).

My best guess, for now, is that the DMA is the problem.  It is very easy to add a small script that enables DMA every time you start your system.

---

### Post by zodmaner on 2007-05-20
Thanks for advices, Pragmatist. :)

I used to be able to durn a DVD after enable DMA using this command:

> sudo hdparm -d 1 /dev/hda

(I got it from K3b tips box.)

But after shutdown and restart my computer. It fails to burn DVD agin, despite the face that hdparm /dev/hda says that DMA is enable.

I don't think that this problem was relate to the program I was using to burn the disc (though I might be wrong.) But my first successful attempt was with Graveman.

Currently I've run out of blank DVD medium. When I get some more I'll try agin, after disable and re enable the DMA.

PS. That script sounds interesting, could you tell me more about it?

---

### Post by zodmaner on 2007-05-20
Update: Ok I still haven't got a new blank DVD yet, but I dig around and find an old verbatim CD-RW, perfect for experimenting with.

1st run: Erase using Graveman with DMA on (according to hdparm /dev/hda) went with no problem.

2nd run: Burn using 174 mb file (it was a movie file) using Graveman with DMA on at 24x. Burn success with no problem, video play fine.

3rd run: Erase using Graveman with DMA on. No problem

4th run: Burn with Nautilus, same data, full speed with DMA on, got an error saying that I should try again with lower speed. Try burning again with 20x burning speed. The burn was a success. Video play fine. Seems to be no problem.

5th run: Erase using Graveman with DMA off using this command: > sudo hdparm -d 0 /dev/hda No problem.

6th run: Try burning with Nautilus and Graveman with DMA off, same speed setting and same data set. Went with no problem. Video play just fine.

Looking good so far, I even thought I only got problem with DVD, as CD seems to burn fine.

That is until I restart the machine.

Before I restart, I enable DMA again by using this command: > sudo hdparm -d 1 /dev/hda

After restart, I run hdparm /dev/hda agin, just to make sure that DMA is enable. It say so (DMA =1).

Then I try burning again.

7th run: Erasing with Graveman with DMA on (as display by hdparm /dev/hda). Went fine.

8th run: Burn using Nautilus with same data file and same speed as before. **Fail!**. Got the same error as when trying to burn a DVD (the program start burning and before anything happen, display "finish writing" and end in failure.) I make sure that it was not a speed issue by trying with different speed (24x, 20x), all ended in failure.

9th run: Burn again using Nautilus this time after turning off DMA using command: > sudo hdparm -d 0 /dev/hda Guess what? It burns successfully.

Now I'm totally puzzle. What is happening here? Is this because DMA is disable even though hdparm says it is enable? (It says that DMA is enable (DMA =1) When I run hdparm /dev/hda after restart). 

Another interesting thing I noticed: After the 8th run (the failed burn after restart). I run hdparm /dev/hda and it says that DMA is **disable**! (DMA =0) despite the fact that I just check before burning that it is enable! So is it possible that, regardless of what hdparm /dev/hda says, that DMA is disable after every restart/shutdown?

Again remember I try this little experiment with CD-RW, I'll try again tomorrow with DVD-RW and sees what happens.

---

### Post by Pragmatist on 2007-05-20
A script is just a way to execute commands automatically.  A Bash script is a script written for the Bash shell (these are commonly called "shell scripts").  You can write scripts in many different computer languages (Python, Perl are some of the most common).  However, I'm only going to talk about shell scripts.

The simplest use of a script is to save typing!  For example, when I wanted to burn an ISO to make a bootable CD I was using a command called "cdrecord" which is a command-line tool.  When I got all the options right, the command looked like this:

```
cdrecord -v -eject -dao -pad -dev=/dev/hdc:1,5,0 speed=-1
```I don't want to remember this!!  So, I made a shell script:
> 
#!/bin/sh

cdrecord -v -eject -dao -pad -dev=/dev/hdc:1,5,0 speed=-1 $1;
exit;
There are two main things to notice.  First, every shell script begins with this line:
> #!/bin/shIt is this line which makes it a shell script rather than just some file.

Next, you see the command I described. 
> 
**cdrecord -v -eject -dao -pad -dev=/dev/hdc:1,5,0 speed=-1** $1**;**
 The only difference is there is a "$1" and the line ends with a semicolon ";"
You must end every command line with a **;**
This tells the shell that your command is finished

Don't worry about the **$1** right now.  I'll explain a little more about that later.
**exit;**  is probably not necessary, but it is also good practice to make sure you finish what you start.

Once I typed this,  I have to save the file and make it executable.  It is good to make a directory in your home directory called "bin" and put all your scripts there.  To make the file executable, I typed:
```
chmod a+x mycd
```To run this particular script, the usage is:  mycd <filename>  For example, say I downloaded an ubuntu ISO file and it is called ubuntu.iso:
```
mycd ubuntu.iso
```How does my script know that I want to burn the file called "ubuntu.iso" ??
That is what the **$1** is for.  In shell scripting, $0, $1, $2, ...  stand for places on the command line:
command   argument1    argument2    argument3  etc...etc....
When I typed in this code:
```
mycd ubuntu.iso
```"mycd" is $0  and "ubuntu.iso" is $1

This is how my script gets the users filename!  This is very useful here.  There are many details for advanced shell scripting.  This script here is a VERY basic script.  Its purpose is simple: save typing and to remember long commands.  To be honest, however, in this case using an "Alias" is probably more appropriate.  An alias is a feature of the shell that let's you give a different name to a command.  For example, you might like to use **ls -l** all the time.  So, to save typing, you can do something like this:
```
alias ll='ls -l'
```Now everytime you type: **ll** it means the same as **ls -l** and you save three keystrokes!  Take a look at your .bashrc file in your home directory

Another main purpose for a script is to make something automatic. Now saving typing isn't enough; we want to not type at all! Here, an alias won't help you. A classic example of making something automatic is when your system starts (these are called startup scripts).

BEFORE you do any of this, read these:

[https://wiki.ubuntu.com/InitScriptHumanDescriptions?highlight=%28init%29](https://wiki.ubuntu.com/InitScriptHumanDescriptions?highlight=%28init%29)
[https://help.ubuntu.com/community/InitScriptList](https://help.ubuntu.com/community/InitScriptList)
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
[https://help.ubuntu.com/community/SysvconfigHowTo](https://help.ubuntu.com/community/SysvconfigHowTo)

It was this kind of script I was referring to in my last post.  To enable DMA, you'd write a script something like this:
> 

#!/bin/sh

 sudo hdparm -d1 /dev/hdc;

How do we make it automatic?  We put startup scripts in special directory that is automatically read every time the system starts.  This directory is:  > /etc/init.dTake a look at some of the scripts in there (BUT DO NOT CHANGE THEM!!!).  These scripts are executed in a particular order.  That order is defined in the directories beginning with /etc/init.d/rc
These are the "runlevels".  Take a look at some of these.  They are only "links" to the files in /etc/init.d 
Why do it this way?  Because we want the scripts run in a particular order.  The links have names that all begin with either Knn or Snn where nn is a two-digit number.  K means kill and S means start.  When the directory is read, it is read in "alphanumeric" order.  So, K comes before S.  This is very clever as now things are stopped before others are started.  Within the K's or S's, the numbers also create order.

Whew!  What do we know so far?
1.) What a script is
2.) What a startup script is
3.) To put startup scripts in /etc/init.d
4.) Runlevels are directories containing links to scripts
5.) Runlevels are located in /etc and have names like rc0.d rc1.d rc2.d rcS.d
5.) Runlevels are used to ensure that scripts are run in a particular order.

Where do you put YOUR startup scripts??  Normally, you put them in runlevel S ('S' for Start).  This is directory /etc/rcS.d

---

### Post by Pragmatist on 2007-05-20
Why are you setting DMA on /dev/hda  Isn't /dev/hda your hard drive?  I always set DMA on my media drives (CD, DVD) which are typically at /dev/hdc or /dev/hdd

---

### Post by Pragmatist on 2007-05-20
Take a look at this:

[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by zodmaner on 2007-05-20
Wow! Thanks Pragmatist! That is one of the most easy to understand explanation of a script I have come across! :) I'll take a look at it and try to set up some startup script and see how it goes.

As for why I'm setting DMA on /dev/hda, well that is where my DVD-recorder is, according to K3b (see the screenshot attachment). BTW my harddrive is on /dev/sda (it use SCSI bus, apparently).

And trying to use hdparm on both /dev/hda and /dev/cdrom *seems* to indicate that they point to the same thing (though I maybe wrong):

> smith@smith-desktop:~$ hdparm /dev/hda

/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
smith@smith-desktop:~$ hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


with hdparm /dev/hdc result in error:

> smith@smith-desktop:~$ hdparm /dev/hdc
/dev/hdc: No such file or directory


Anyway, I'll get the DVD-RW tomorrow and try setting up the script and see how it goes. Again thanks for all the help, Pragmatist. I really appreciate it. :)

---

### Post by zodmaner on 2007-05-21
Hi there, after experimenting more with my CD-RW (still didn't get a chance to buy a DVD-RW yet). I think I nail the problem with burning CD-RW.

In short, when I turn off DMA with this command:

>  sudo hdparm -d0 -k1 /dev/hda

Using Nautilus, CD-RW burn just fine.

When I enable DMA using command:

>  sudo hdparm -d1 -k1 /dev/hda

Nautilus fails to burn (citing that I should use lower speed, but setting lower burn speed won't solve the problem).

Again, disable DMA fixes the problem and Nautilus burn just fine.

What makes me puzzle is that I used to be able to burn with DMA on, and that with DVD, turning on DMA help makes Graveman burn sucessful, once.

So, anyone have any thought on this? Not sure if this will fix the problem I have with burning DVD, I guess tomorrow we'll find out. :)

PS. Another thing I notices is that when the burn fails, if I check the DMA setting, it will shows that DMA is **off**! This happen every time DMA is turn on before the burn fails, it will always get disable after the failed burn.

PS-2. Another thing is that I have follow this [guide]("https://help.ubuntu.com/community/DMA") by edited my /etc/hdparm.conf file and insert the following line at the end of file:

> 
/dev/hdc {
dma = on
}


And the result was just like when I enable DMA using hdparm command, the CD-RW would just fail to burn.

---

### Post by Pragmatist on 2007-05-21
What happens if you use command-line tools to burn DVD/CD ?[  https://help.ubuntu.com/community/CdDvdBurning#head-6a74728bd8d6b3ed6992bea8a0ca21464eb5a60b]("https://help.ubuntu.com/community/CdDvdBurning#head-6a74728bd8d6b3ed6992bea8a0ca21464eb5a60b")

---

### Post by zodmaner on 2007-05-23
Hi guy(s), I finally got a DVD-RW and have done some testing on it. It turns out that, just like in the case of CD-RW, turning off DMA on the drive really *seems* to make it burns properly.

I test it with two media: a Sony DVD+RW and a Sony DVD-RW. Both burns fine with DMA off and got the same error with DMA on. I use Nautilus mainly for my test, but K3b seems to work fine. I also try burning with TDK DVD+R disc, which burns fine (except that in Nautilus the speed was limited to only 4.1x).

I haven't try burning using command line yet, will give the result when I try it out.

The strange thing I have noticed is that when the drive fail to burn when DMA is on, afterward when I check the DMA setting it'll appear as 'off', despite that it was enable before the burn and that I've not touch anything. 

Another strange phenomenal is that the DMA setting seems not to 'stick' when shutdown the computer, despite using the -k1 parameter. Every time I turn on the machine the DMA setting will automatically be set to on (and if burning a disc, will result in a failure). I check the hdparm.conf file to make sure that DMA is not set to turn on by default (all the line are mark with # at the first of the line) but still the DMA is turn on when I start up my computer even though I make sure that it is turn off before I shutdown using -d0 and -k1 parameters. Restarting the computer seems to keep the DMA setting fine.

So there you have it, burning CD/DVD seems to work fine now as long as I keep the DMA setting to **off**. Still it would be nice to know why DMA is casuing a problem and why I can't keep my DMA setting. I will try edit hdparm.conf file to set DMA to off and see if it will stick. (BTW, is no one experience the same problem as I did?)

Also, is it ok to burn CD/DVD with DMA off? Will it affect anything? I use DVD as my main archive, backup media and I need to have a reliable burning solution, else I risk losing or damaging data that I backup to the disc.

---

### Post by Pragmatist on 2007-05-23
> **zodmaner said:**
> 
Another strange phenomenal is that the DMA setting seems not to 'stick' when shutdown the computer...Restarting the computer seems to keep the DMA setting fine.


Please give us the output of these commands:

```
ls /etc/rc0.d
```
```
ls /etc/rc6.d
```

---

### Post by zodmaner on 2007-05-23
Here 
```

smith@smith-desktop:~$ ls /etc/rc0.d
K01gdm             K25hwclock.sh                       S20sendsigs
K01usplash         K50alsa-utils                       S30urandom
K19hplip           K99timidity                         S31umountnfs.sh
K20apport          README                              S40umountfs
K20nethack-common  S01linux-restricted-modules-common  S60umountroot
K20wesnoth-server  S15wpa-ifupdown                     S90halt

```

and here
```

smith@smith-desktop:~$ ls /etc/rc6.d
K01gdm             K25hwclock.sh                       S20sendsigs
K01usplash         K50alsa-utils                       S30urandom
K19hplip           K99timidity                         S31umountnfs.sh
K20apport          README                              S40umountfs
K20nethack-common  S01linux-restricted-modules-common  S60umountroot
K20wesnoth-server  S15wpa-ifupdown                     S90reboot


```

(Hey, what's Nethack and Wesnoth doing in there?)

---

### Post by Pragmatist on 2007-05-23
Just to make sure I'm understanding: 

1. You have **no problem **with DMA turned off.
2. When you start your computer, DMA is turned on.
3. When you restart your computer, DMA no change is made.

Your current goals are:

1.) Make sure that DMA is always off.
2.) Determine why DMA is getting turned on.

If this is all correct, then you already have a simple solution.  Just make a small script that will always make sure that DMA is turned off.

DMA is an optimization that allows the burning process to go faster.  It won't hurt anything to leave it off (although it will take longer to burn your discs).

To understand why DMA is getting turned on, you need to take a look at which scripts are started when Ubuntu begins.  For that you actually need to look at **/etc/rc2.d **directory. /etc/rc0.d is for shutdown and /etc/rc6.d is for reboot.  That is why I asked for them.  However, I should also have asked for /etc/init.d/rc2.d as that is most likely where DMA is getting turned on.  Take a look at this to know more:

[https://help.ubuntu.com/community/InitScriptList](https://help.ubuntu.com/community/InitScriptList)

---

### Post by zodmaner on 2007-05-29
Sorry for being absent for such a long time, I had a really hectic week.

Back to business, the new kernel update (v.2.6.20.16) didn't fix the DMA problem, I still had to turn it off before burning a CD/DVD just like in kernel v.2.6.20.1.5. The differences, is that DMA seems to automatically(?) turn itself off when I insert a blank DVD disc and that the burn speed on DVD-R(W) is slower, much much slower than when using DVD+R(W) disc. 

So there you have it, I haven't tried it on DVD-R(+R) disc yet, but so far things seems to be in working order, and if this 'automatic' self-disable DMA can be trust, then I might not need to mess with starting script at all. :)

Anyway, thanks for all the help, Pragmatist. I couldn't have done all this without you. I really, really appreciate your help. :D

UPDATE: Hm... Maybe I spoke too soon, it seems I have problem trying to get DVD-RW disc to burn properly (burn fail at 1x with DMA off). Will give an update once I have time to experiment with it some more.

UPDATE2: Okay, it seems that error with DVD-RW disc occurs when Nautilus tries to 'erase' (write over) the existence data on the disc. Turning off DMA didn't help. Formatted the disc using K3b first and then burn fixes the problem. Not sure why. Will try and get a DVD-R and see if it have the same problem. DVD+RW have no such trouble.

---

### Post by zodmaner on 2007-05-29
Ok, I can now confirm that DMA is turn off seemingly automatically on its own when I insert DVD+RW disc. (This strange behavior didn't exist back in kernel 2.6.20.15.) 

Strange... maybe kernel upgrade causes this? but on the plus side this mean that I can burn DVD without having to disable DMA using command line. :)

Seems to be the case with DVD-RW as well, but I still have trouble with DVD-RW refuses to burn.

---

