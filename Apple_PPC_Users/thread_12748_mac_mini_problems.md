---
title: "mac mini problems"
date: 2005-01-26
forum: Apple PPC Users
---

### Post by jstultz on 2005-01-26
I just got my mini yesterday and finally got it dualbooting w/ Ubuntu, and its great, but a few things still don't work.

Unfortunately out of the box X didn't work with my EN7100e LCD screen. I kept on getting "RADEON(0): FBIOPUT_VSCREENINFO: Invalid argument" errors. I finally managed to get it working by setting the resolution down from the native 1280x1024  to 1024x768, which works, but not very crisp on the LCD. 

Also there's no audio support, it seems.

Anyone have a clue how to resolve these issues?

thanks.
-john

---

### Post by jstultz on 2005-01-27
Problem solved! Using fbset, I manually set the framebuffer mode to "1280x1024-60" then I used "fbset -x" to generate a Mode Section for the Montior Section in /etc/x11/XF86Config-4. After that X came up in 1280x1024 without a problem.

---

### Post by Castaa on 2005-01-28
[QUOTE=jstultz]Problem solved! Using fbset, I manually set the framebuffer mode to "1280x1024-60" then I used "fbset -x" to generate a Mode Section for the Montior Section in /etc/x11/XF86Config-4. After that X came up in 1280x1024 without a problem.[/QUOTE]
 This is great.  This is the first post of someone actually running Linux on the new Mini Mac.  Keep us informed!

---

### Post by Huxley on 2005-01-29
Getting my mac mini next week.
No more fans.

---

### Post by mp3geek on 2005-01-29
I just loaded Ubuntu on my shiny new Mac Mini   :D   Everything is fine, except no sound :sad:   Anyone out there gotten sound to work? 

TIA, Mike

---

### Post by jstultz on 2005-02-04
Well, I've narrowed down to where the sound bombs out. 

The device reports itself as "AOAKeylargo" which in the current code uses the snapper mixer. Unfortunately we get all the way to snd_pmac_tumbler_init() where we do:
        tas_node = find_devices("deq");
        if (tas_node == NULL)
               return -ENODEV;
It seems the "deq" has something to do with the mixer, but I don't know.

I'm still hunting to see what is needed to make this work.

---

### Post by Buffalo Soldier on 2005-02-04
This could be a good start for HowTo: Installing Ubuntu on Mac Mini.

---

### Post by jstultz on 2005-02-04
Ohh! I got sound working! Looks like if you apply the attached patch, it uses the SCREAMER/AWACS mixer and everything is a go. ALSA is very laggy, but it works.
Definitly not a finished work, but its a start.

---

### Post by mp3geek on 2005-02-11
Could you elaborate on how to apply the patch for a newbie?  :grin: 

Thanks!

---

### Post by agravain on 2005-02-11
To manually apply the patch (just as easy in this case), 
just open the file linux/sound/ppc/pmac.c in an editor, 
and search for OAKeylargo. 
Where it says SNAPPER right below, you change to SCREAMER (in uppercase).
(In kernel 2.6.10 it's at line 967). 

Then you recompile your kernel, making sure you have set  CONFIG_SND_POWERMAC=y in your kernel config (or choose to enable powermac sound from the menus if you're using a GUI for configuring the kernel).

---

### Post by Castaa on 2005-02-11
This is the first time I've read sound working with a Mini and Ubuntu.  Great job.

---

### Post by jstultz on 2005-02-13
It should be mentioned that Owen from Yellowdog found that using the PMAC_AWACS instead of PMAC_SNAPPER worked without the whole-system stalls. It should be noted that this is not the correct solution, as the mixer doesn't work, but its better. Hopefully someone who knows the hardware will come up with a proper driver soon.

---

### Post by latrine on 2005-02-14
Hello... I am thinking of buying a mac. I am tired of windows problems, and even if I find ubuntu really great, I need something else... specially for the WAF (wife Acceptance Factor)

In my short search I found that MacOSX seems to be the optimal choice... specially in a mac mini for its price and bundled software... 

So I made my choice but when I get here... I find you guys installing Ubuntu on a mac mini...

What I would like know is simply... why?
1- Isn't MAcOSx really that great/different from windows?
2- IT is, but in a mini it has to be really scaled down  to have a good performance
3- I do it for the fun only :)

Thanxs

---

### Post by agravain on 2005-02-14
Suggestions for overcoming WaF with stereotype women;)

"Look how small and cute it is!"
"OS X looks and feels so much better than windows!"
"It looks nice enough to put in the living room"

plus

1- Isn't MAcOSx really that great/different from windows?
Sure is

2- IT is, but in a mini it has to be really scaled down *to have a good performance
It's not slow, if you're not playing 3D games

3- I do it for the fun only :)
It is fun

plus

You can have both ubuntu and mac os X installed at the same time, it's not hard.

---

### Post by josue on 2005-02-14
[QUOTE=latrine]Hello... I am thinking of buying a mac. I am tired of windows problems, and even if I find ubuntu really great, I need something else... specially for the WAF (wife Acceptance Factor)

In my short search I found that MacOSX seems to be the optimal choice... specially in a mac mini for its price and bundled software... 

So I made my choice but when I get here... I find you guys installing Ubuntu on a mac mini...

What I would like know is simply... why?
1- Isn't MAcOSx really that great/different from windows?
2- IT is, but in a mini it has to be really scaled down  to have a good performance
3- I do it for the fun only :)

Thanxs[/QUOTE]
 Well, it's just another computer.
I will use mine as a replacement for an old PC, but i'm not sure if i want to be 100% mac, so i'll just use the amazing hardware with an amazing OS: Ubuntu Linux.

---

### Post by toojays on 2005-02-15
I have a vague memory of seeing something about this on the debian powerpc list . . . IIRC the mini doesn't have a snapper mixer, it uses one of the others. The quick fix is to find the part of the kernel which is like "if KeyLargo then snapper mixer", and change it to use the correct mixer.

---

### Post by mac-mini-sweet-silence on 2005-02-15
Re: sound. AWACS was it? Might work...  :?

---

### Post by DJ_Max on 2005-02-17
Just for reference
[http://www.sowerbutts.com/linux-mac-mini/](http://www.sowerbutts.com/linux-mac-mini/)

---

### Post by timing on 2005-03-25
I added a bug report/feature request to the alsa-project bugzilla.
it's here:
[https://bugtrack.alsa-project.org/alsa-bug/login_page.php](https://bugtrack.alsa-project.org/alsa-bug/login_page.php) 

Log in as guest and search on the page for a bug report with the word "macmini". If we help tiwai (the developer who wants to fix the problem) as good as possible we could have sound on our macmini soon (i guess :-P)!

---

### Post by agravain on 2005-03-25
I'll help Tiwai fix it. I have wanted to fix this for a while :)

---

### Post by timing on 2005-03-25
so i guess you are perchrh ;-)

---

### Post by agravain on 2005-03-28
[QUOTE=timing]so i guess you are perchrh ;-)[/QUOTE]
right.

---

### Post by JaceMan on 2005-05-07
[QUOTE=agravain]To manually apply the patch (just as easy in this case), 
just open the file linux/sound/ppc/pmac.c in an editor, 
and search for OAKeylargo. 
Where it says SNAPPER right below, you change to SCREAMER (in uppercase).
(In kernel 2.6.10 it's at line 967). 

Then you recompile your kernel, making sure you have set  CONFIG_SND_POWERMAC=y in your kernel config (or choose to enable powermac sound from the menus if you're using a GUI for configuring the kernel).[/QUOTE]

Two things real quickly...

First, I cannot find a file: linux/sound/ppc/pmac.c on my system

Secondly, when you start talking about recompiling my kernel, I know what you mean, but I have no idea how it's done.

I don't own a Mac, but my brother-in-law does, and I've been trying to turn him into a Linux convert for a long time now.  He finally broke down and let me install Ubuntu as a dual boot on his Mac Mini, but the lack of sound is upsetting him.  Please help me get his system fully functional so we don't lose a new linux user.

Thanks.

---

### Post by agravain on 2005-05-07
[QUOTE=JaceMan]First, I cannot find a file: linux/sound/ppc/pmac.c on my system [/QUOTE]
The path is relative to the directory the linux-kernel is in. 
Check out /usr/src/linux .. 

[QUOTE=JaceMan]
Secondly, when you start talking about recompiling my kernel, I know what you mean, but I have no idea how it's done.
[/QUOTE]
Ok. Then maybe it's easier to download a precompiled version. 
Check out [http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/) for the necessary files and instructions.

Good luck :)

---

### Post by agravain on 2005-05-07
[QUOTE=timing]I added a bug report/feature request to the alsa-project bugzilla.
it's here:
[https://bugtrack.alsa-project.org/alsa-bug/login_page.php](https://bugtrack.alsa-project.org/alsa-bug/login_page.php) 

Log in as guest and search on the page for a bug report with the word "macmini". If we help tiwai (the developer who wants to fix the problem) as good as possible we could have sound on our macmini soon (i guess :-P)![/QUOTE]

Ok, consider it 'fixed'. 

Benjamin Herrenschmidt has made a driver for mac mini sound. It's included in kernel 2.6.12-rc4 and later. You need alsa-lib version 1.0.9rc3 or later too. You should use that driver, if possible, instead of the patch mentioned in this thread. The performance is much better.
Note that it will probably take some time before distros include alsa-lib 1.0.9+ and 2.6.12-rc4+, so depending on your skills compiling and installing stuff yourself, you might be stuck with the slomo patch for a while.

---

### Post by JaceMan on 2005-05-07
[QUOTE=agravain]The path is relative to the directory the linux-kernel is in. 
Check out /usr/src/linux .. [/QUOTE]

Ok, thanks for the explanation, much appreciated!

[QUOTE=agravain]Ok. Then maybe it's easier to download a precompiled version. 
Check out [http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/) for the necessary files and instructions.

Good luck :)[/QUOTE]

I had already visited that page before I posted here... it was due to what happened there that made me post here.

After, I followed his directions, not only did my brother-in-law not have sound, but we were unable to boot into Ubuntu at all.

So, I revisited [http://www.pw.org/~perchrh/](http://www.pw.org/~perchrh/) to obtain the gentleman's contact information.  I contacted him on MSN via Gaim and he told me that I had done everything right, except that I forgot to execute the command: sudo ybin

Of course, I new nothing about that command since he didn't have instructions for it on his instruction sheet.  He has since changed that, I'm guessing due in large part to my conversation with him, and his willingness to help people like me.

Anyway, here is the long and short of it.

I went back to my brother-in-law's house today with confidence that things would now work with the help of sudo ybin.

**So...**

I reinstalled Ubuntu.

Then I went to [http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/) and downloaded the kernel-image, kernel-headers, and kernel source.

I opened up my terminal and did the following.

sudo dpkg -i kernel-image-package-name.deb
sudo dpkg -i kernel-headers-package-name.deb
sudo dpkg -i kernel-source-package-name.deb 
sudo ybin

After I finished with the commands I decided to reboot and impress my brother-in-law with Linux sound on his new mac mini, **but instead** we were again unable to boot into Ubuntu.

When at the Yaboot Loader, we can boot into Mac OS X just fine, but Ubuntu is a no go.

Having been told that I did everything right, and my only failure was not executing the ybin command, and having done so this time I am incredibly confused now.

***What have I done wrong, and what do I try next?***

As always, please and thank you!  :smile:

**P.S. I'm using Hoary on his mac mini, not Warty if that matters.**

---

### Post by agravain on 2005-05-08
[QUOTE=JaceMan]... I forgot to execute the command: sudo ybin

Of course, I new nothing about that command since he didn't have instructions for it on his instruction sheet. 
[/QUOTE]
Ahem. It was always there, what's new is that I've repeated it with exclamation marks.
[QUOTE=JaceMan]
I reinstalled Ubuntu.
Then I went to [http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/) and downloaded the kernel-image, kernel-headers, and kernel source.

I opened up my terminal and did the following.

sudo dpkg -i kernel-image-package-name.deb
sudo dpkg -i kernel-headers-package-name.deb
sudo dpkg -i kernel-source-package-name.deb 
sudo ybin

After I finished with the commands I decided to reboot and impress my brother-in-law with Linux sound on his new mac mini, **but instead** we were again unable to boot into Ubuntu.

When at the Yaboot Loader, we can boot into Mac OS X just fine, but Ubuntu is a no go.

Having been told that I did everything right, and my only failure was not executing the ybin command, and having done so this time I am incredibly confused now.

***What have I done wrong, and what do I try next?***
[/QUOTE]
The procedure above worked for me and other people, so it's ok.
There has been some recent changes, though. I added the source and header packages, and upgraded to 2.6.11.8. 
Maybe there is some problem with 2.6.11.8.

When you're at the yaboot prompt, can you boot the system by typing 'old' <enter> ? If not, reinstall Ubuntu, else do so.
Then install the 2.6.11.7 image, available at 
[http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb](http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb)
and run ybin before rebooting.

I've changed the download link to point to the ..7 image in case there are problems with it.

Update: The 2.6.11.8 image was built without an initrd.img, I'm uploading it again, now with initrd.

---

### Post by JaceMan on 2005-05-08
**We met on MSN again, where agravain/perchrh and I were able to fix a TEMPORARY problem that probably only pertained to me.**

He was most helpful, and I trust/hope he doesn't mind me sharing this information.

**[COLOR=red]THANKS AGAIN!!![/color]**

---

### Post by JaceMan on 2005-05-08
[QUOTE=agravain]Ahem. It was always there, what's new is that I've repeated it with exclamation marks.

The procedure above worked for me and other people, so it's ok.
There has been some recent changes, though. I added the source and header packages, and upgraded to 2.6.11.8. 
Maybe there is some problem with 2.6.11.8.

When you're at the yaboot prompt, can you boot the system by typing 'old' <enter> ? If not, reinstall Ubuntu, else do so.
Then install the 2.6.11.7 image, available at 
[http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb](http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb)
and run ybin before rebooting.

I've changed the download link to point to the ..7 image in case there are problems with it.

Update: The 2.6.11.8 image was built without an initrd.img, I'm uploading it again, now with initrd.[/QUOTE]
 In regards to downloading the new kernel image link...

Forbidden

You don't have permission to access /~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.0.53 (FreeBSD) mod_ssl/2.0.53 OpenSSL/0.9.7d Server at [www.pvv.org](www.pvv.org) Port 80

---

### Post by agravain on 2005-05-09
Fixed the permissions. Sorry.

---

### Post by JaceMan on 2005-05-12
[QUOTE=agravain]Fixed the permissions. Sorry.[/QUOTE]
 Finally made it back over to my brother-in-law's house.  Sound is working.  Yay...  There are a ton of errors during the boot up process involving dmapper (blah, blah) that is above my head, but the end result is... **he has sound!**

Now, if i can get the volume control to work. :)

---

### Post by f992005 on 2005-07-18
JaceMan
  Could you please to re-write the procedure how to fix sound problem ?
   I'appreiated your help.
   
     f992005

---

### Post by agravain on 2005-07-20
[QUOTE=f992005]JaceMan
  Could you please to re-write the procedure how to fix sound problem ?
   I'appreiated your help.[/QUOTE]

Options are :
1. install a new kernel and a new alsa-lib version (recommended). 
Kernel version 2.6.12 or later and alsa 1.0.9 or later. Enable support for PMAC_TOONIE.
OR
2. patch existing kernel with patch found at [http://www.pvv.org/~perchrh/macmini](http://www.pvv.org/~perchrh/macmini)
OR 
3. download and install the new kernel at [http://www.pvv.org/~perchrh/macmini](http://www.pvv.org/~perchrh/macmini) 
(easiest)

Option 3 recipe:
Download [http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb](http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb)
run sudo dpkg -i kernel-image-2.6.11.7_1.2_powerpc.deb
run sudo ybin
Reboot. Sound should be working. Need to increase volume from 0.

---

### Post by f992005 on 2005-07-27
agravain
Thank you for your clearly instruction. Sound is working good. Now I can play video clips and mp3 music. :-P

---

### Post by XavierS on 2005-08-23
Agravain : Hope you'll excuse me for my bad english.

I updated my kernel with yours. But i have some errors on boot.

And it seems that i didn't have those before. Are aware of this ? Does it come from your kernel ?

Do I forgot to do something ?

NB : the sound works, mac mini also. But ...

---

### Post by agravain on 2005-08-23
[QUOTE=XavierS]I updated my kernel with yours. But i have some errors on boot.
And it seems that i didn't have those before. [/QUOTE]
What are the errors?
This is probably not new errors, but just ones that have been there all the time and are now shown 
because verbose startup (mesasges from bios) is enabled.

---

### Post by XavierS on 2005-08-23
I tried to do a capture but it didn't worK
It is something like that : 

ERROR : device dpt ...

Around 10 lines of diffrent error on devices

Then something about LVM, also 10 lines, identical line

How can i do a print screen for you ?

---

### Post by agravain on 2005-08-23
[QUOTE=XavierS]I tried to do a capture but it didn't worK
It is something like that : 
ERROR : device dpt ...
Around 10 lines of diffrent error on devices
Then something about LVM, also 10 lines, identical line
How can i do a print screen for you ?[/QUOTE]
Ok. I don't know what's causing this. If everything works for you, and you still want to find out what's causing the error messages you will have to find it out yourself.

---

### Post by XavierS on 2005-08-23
No problem

See U

---

### Post by XavierS on 2005-09-16
I hope that Breezy will correct all this

---

### Post by agravain on 2005-09-16
Breezy will correct all this if it comes with kernel 2.6.12 or newer, that has the driver. 
Alsa 1.09 or later is also needed, but that's in Breezy already.
Currently Breezy has kernel 2.6.11.9, which doesn't support the mac mini sound card.

---

### Post by XavierS on 2005-09-28
OK, but do you know how to update just the kernel ?

I mean, to use the kernel 2.6.12 with Hoary or Breezy.

---

### Post by agravain on 2005-09-28
Update: Ubuntu breezy now has kernel 2.6.12, which means it should support mac mini sound out of the box, no configuration/kernel change needed.

---

### Post by XavierS on 2005-09-30
That's good news.

Thanx for everything !

---

### Post by mfil on 2005-09-30
Hello everybody!
Sorry for my English, i'm from Russia... I very hope that you will understand it))

I have mac mini not long time, 3 monts, and I can't say that I am good know macintosh.
Today i've receive my ubuntu cds, try live cd and like it.

Tell me please, can I install ubuntu on my mac and not lose my mac os x and files?

---

