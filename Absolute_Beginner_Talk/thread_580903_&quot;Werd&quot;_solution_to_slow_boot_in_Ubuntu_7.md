---
title: "&quot;Werd&quot; solution to slow boot in Ubuntu 7.10"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by gaburko on 2007-10-19
Hi guys, firs post for me here.
So, I installed Ubuntu 7.10 yesterday on a relatively OK laptop - 2 Ghz, 2 GB RAM, X1300 128 MB Video. Aaaaanyway - what immediately striked me was the slow boot. 
since I have a dual-boot (Vista) I played a little with the menu.lst - I wanted Vista to be the default. However, the change that "did it" for me was the following:

original

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70[COLOR="Red"] ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]


```

now
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70
initrd		/boot/initrd.img-2.6.22-14-generic

```


simply remove "ro quiet splash" and "quiet"

dunno why, but it works - boots in about a minute -)

Cheers

---

### Post by ovitz on 2007-10-19
Great. That is a lot faster for me! Thanks!

---

### Post by Hedley on 2007-10-21
Brilliant! This solution took me from a six minute boot to a 45 second boot. Much better. 

Thanks,

HB

---

### Post by Alyx on 2007-10-21
wonderful solution! worked like a charm thanks. the slow boot was the only thing i could find that bothered me. but im happy now thanks! :guitar:

---

### Post by LeeAdkins on 2007-10-21
Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

---

### Post by Engmar on 2007-10-21
Thank you.

---

### Post by sugarland2k on 2007-10-23
VGA=791 sets up your xorg for something like this..


Screen   640x480     800x600     1024x768     1280x1024     1600x1200 
Colors  ---------------------------------------------------------------------- 
 256      | 769             771             773               775              796 
 32,768 | 784            787             790                793              797 
 65,536 | 785            788             791                794              798 
 16.8M  | 786            789             792                795              799 

Good work on this subject.

---

### Post by xyz on 2007-10-23
Strangely it doesn't make much difference for me. Too bad but thnx for sharing.

---

### Post by joao82 on 2007-10-28
I have this exact same problem and no loading bar, after I've installed Kubuntu 7.10 today. I'll give the second method a try.
*crosses fingers*

EDIT:
it worked!!!!! best thread of the year, make this one a sticky.
how could ubuntu programmers screw up a laptop boot so much.... and how did you know how to fix it? :) thanks

---

### Post by Crafty Kisses on 2007-10-28
Thanks!

---

### Post by Kilbe3 on 2007-11-01
Dude, U Rock, This Has Been Sending Me Insane!!!! 

T.o.p. T.h.r.e.a.d.

:-({|=

---

### Post by devilman on 2007-11-04
The second solution to this issue worked great for me also. Thanks so much. I almost gave up on 7.10.  :)

---

### Post by pordzio on 2007-11-06
If you still want some info:

"vga=791" sets the text console to 1024x768 and 16-bits color although it might not work with Gutsy, you should rather use "vga=0x318" instead (0x318 in hexadecimal numbers = 791 in decimal numbers)

---

### Post by rimoth on 2007-11-07
Second solution worked a treat....Many Thanks

---

### Post by boriquajake on 2007-11-07
OK, I have been having an issue or two with my lappy since installing Ubuntu the other day and as I have searched these forums I have come across apparent solutions to my problems. The only thing is I am a true "absolute beginner", and even some of the common knowledge is beyond me. For example, the pasted solutions to slow booting seem like exactly what I need but I don't understand how to implement them. Do I copy the whole thing and paste it into terminal? I think there is a shorthand that I am not understanding. If someone could direct me to a thread or a tutorial that will allow me to make use of the information offered here it would be great.

---

### Post by steveneddy on 2007-11-08
To get a good grip on what may be holding up your boot time, just install **bootchart** and look at the graphical log in /var/log/bootchart.

I had a boot time issue that i resolved with bootchart. Strangely enough. my issue was a difference in time between my BIOS and actual time. Somehow the system clock was way out of sync. I just manually reset everything and reboot a few times and bliss was at hand.

Here are my dealings with boot time issues.

[here]("http://ubuntuforums.org/showthread.php?t=571868") and [here]("http://ubuntuforums.org/showthread.php?t=566188")

:popcorn:

---

### Post by sports fan Matt on 2007-11-09
Ga,

Hi..Just want to ask (Maybe cause ive been dealing with this for a week now) I cant remember for the life of me where you got that imput from, forgive me alot going on..:) It seems like everytime i change or attempt it, it screws up and i end up dead and have to reinstall..which is a pain.

Steve:  I looked for that boot program and couldnt find it.  Is it in Synmpatics maybe cause I havent looked there yet...

---

### Post by sports fan Matt on 2007-11-09
update:

Removed "quiet" from the boot menu and hinestly can live with splash..

---

### Post by mikesmith36 on 2007-11-10
Thanks - 1st method speeds up boot but the second method speeds up boot AND gets the splash screen back.

Thanks for the effort - both of you.

An annoying problem is solved - great

Michael

---

### Post by Hans de Visser on 2007-11-11
> **LeeAdkins said:**
> Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

Thanks! :). Solved the problem for me. Got a Compaq Presario M2000 with 512 Mb RAM and 60 Gb disk.

---

### Post by hobo on 2007-11-11
Did no one else lose their WiFi when they made these changes? I did on a IBM t42. The only way to get it back is to remove all the changes. Then all is well with wifi but I am back to the slow boot again.

---

### Post by monckywrench on 2007-11-14
Parent post fix worked for me. THANK YOU.

I don't need a splash screen and prefer boot messages, so whenever I install on any other system I'll do the fix immediately..

---

### Post by wbloco on 2007-11-15
Ok. I am a begeiner. How I edit the menu.lst? I tried to edit with the text editor and gave an error telling me that I am not the owner of the file or dosent have permission to modifiy th file plase help

---

### Post by joao82 on 2007-11-16
> **wbloco said:**
> Ok. I am a begeiner. How I edit the menu.lst? I tried to edit with the text editor and gave an error telling me that I am not the owner of the file or dosent have permission to modifiy th file plase help

on the terminal type this:

sudo gedit /boot/grub/menu.lst

only if your text editor is gedit. then it will ask for your password and you can enter it, the file will open and be available for edit/save.

---

### Post by RedRogue on 2007-11-17
Many, many thanks for this easy and very helpful tip. Worked like a charm.

RedRogue

---

### Post by poscochubb on 2007-11-17
Thanks for that, my boot time has gone from 6 minutes to around 50 secs. Just installed Ubuntu on an old laptop to try it out and this has removed the main objection I had to learning more about it.

Apologies for hijacking this thread, but can anyone suggest some reading - either magazine or book?

Posco

---

### Post by n8makar on 2007-11-18
fantastic. ive actually had a lot of things i had to fix with ubuntu so far and this was on the list. worked like a charm (second solution that is) and now i can continue down the list :)!

---

### Post by wbloco on 2007-11-19
> **joao82 said:**
> on the terminal type this:

sudo gedit /boot/grub/menu.lst

only if your text editor is gedit. then it will ask for your password and you can enter it, the file will open and be available for edit/save.

Many thanks for your help. Now my notebook behaves like a Ferrari. Boot up time went down form 5 minutes to 40 seconds.  Ubuntu is great.

---

### Post by G. Cotgreave on 2007-11-19
> **LeeAdkins said:**
> Does the black Ubuntu loading splash screen work when you do that?

2) At the very end of the kernel line after  "splash" , add "vga=791" 

I started to work on the second method straight away but when i open menu.lst there is no ''splash'' written anywhere... this is the end of my file

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2de94552-f750-45a0-b3d3-205c4cfd1a62 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

What should i do??

---

### Post by question_chick on 2007-11-19
it's not the end of the file you need it's your main boot, that should be the one above recovery usually, 

basically the 7.10 kernal but not with recovery after it. 3rd line down should have splash at the end

---

### Post by crjackson on 2007-11-19
> **pordzio said:**
> If you still want some info:

"vga=791" sets the text console to 1024x768 and 16-bits color although it might not work with Gutsy, you should rather use "vga=0x318" instead (0x318 in hexadecimal numbers = 791 in decimal numbers)

The usplash and 791 fix work on 2 of my systems but won't work on my main system.  Why would using 0x318 be any better than passing 791?

---

### Post by bw44 on 2007-11-26
> **LeeAdkins said:**
> Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

Maybe you can help me.  My system does not boot slowly (it takes less than a minute), but I have never seen the "pretty" black Usplash screen, either with Feisty or after upgrading to Gutsy.  I don't see what I think you must mean by the "verbose" mode either (rapid low resolution display of many detail messages?). 

I followed your instructions above first with "vga=791" then with "vga=0x318" but as soon as the boot-up starts I get a message (something like) "You passed an undefined mode ... Enter mode number or scan" and a list of "Video adapter VESA VGA"  Row and Column settings like 80 X 24, and so on, to select from.  I don't have a clue, so I let it default by hitting space.  The system continues to boot up "normally" but still without the splash screen or verbose messages.

Maybe I don't fall in the category of "this only works if Usplash is broken."  What else might cause the Usplash screen not to display?  (I do get a brief "pixel map" effect with a partial display of the default desktop wallpaper shortly before the standard login page displays.) Here is the content of my usplash.conf file
```

# Usplash configuration file
xres=1024
yres=768
```
which is the resolution my screen usually runs at.

I'd like to see the Usplash screen at boot-up. Any suggestions as to what I should do?  (By the way, I cannot seem to get into verbose mode by entering CTRL F1 either)

Thanks.

---

### Post by philinux on 2007-11-26
Try installing startupmanager. Just be careful though, same warning as editing menu.lst.

The launcher appears under admin.

---

### Post by akiratheoni on 2007-11-26
I like the text only boot up because it actually tells you when fsck is checking a file system, with the graphical boot-up only, it just hangs when fsck is actually scanning a file system.

---

### Post by bw44 on 2007-11-26
> **philinux said:**
> Try installing startupmanager. Just be careful though, same warning as editing menu.lst.

The launcher appears under admin.

Thanks. I'm glad to have that tool in my kit.  Unfortunately, I didn't know quite what to ask it to do.

The "Show boot splash" box was already checked. So I changed the display resolution from 800X600 to 1024X768 and the color depth  to 24bits.  When I rebooted I got the message "You passed an undefined mode, etc," and there was still no splash screen and no verbose messages.

I'll try checking the box that says "Show text during boot" and reducing the color depth to 16, but I'm really just groping in the dark.

(Edit: Still got the message about passing the undefined mode number and no splash screen, but did get the verbose messages flashing past.)

Any other suggestions?

---

### Post by bw44 on 2007-11-26
> **akiratheoni said:**
> I like the text only boot up because it actually tells you when fsck is checking a file system, with the graphical boot-up only, it just hangs when fsck is actually scanning a file system.

That's a good point, but I'd at least like the option of the graphical boot-up.  Maybe after I've seen it just hang too often (assuming I can get it to work!) I'll turn it off.  At least Startup-Manger allows me to turn the text mode on and off.

Thanks for your input.

---

### Post by philinux on 2007-11-26
As long as it boots ok and the resolution is ok. Cant see anything wrong with trying a few settings out.

---

### Post by xpod on 2007-11-26
Speeds up my boot time from choosing the kernel in grub to login from 50 seconds down to around 40,on a 1.8Ghz machine with a gig of ram.:)

Just a note though guys...
> on the terminal type this:

sudo gedit /boot/grub/menu.lst

only if your text editor is gedit. then it will ask for your password and you can enter it, the file will open and be available for edit/save.

If your opening a graphical app with the relevant permissions like so then it`s generally advised to use "gksudo" instead of just "sudo".....
```
gksudo gedit /boot/grub/menu.lst
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Cheers

---

### Post by bw44 on 2007-11-26
> **philinux said:**
> As long as it boots ok and the resolution is ok. Cant see anything wrong with trying a few settings out.
Thanks, philinux, you were really helpful. And persistence paid off.  I did a re-install of usplash and usplash-theme-ubuntu and with the minimal resolution set using Startup-Manager (640X480 and 8-bit color depth) the Usplash screen is working fine now.

---

### Post by Salva con nome on 2007-11-27
> **Hedley said:**
> Brilliant! This solution took me from a six minute boot to a 45 second boot. Much better. 

Thanks,

HB

Six minute boot?!?!?! :(

PS: Hi everyone

---

### Post by bill93 on 2007-11-28
Sweet. The "longer" fix worked like a charm. Boots on a crappy old Dell C610 1.4 GHz 1GB RAM in <1 minute.

---

### Post by crjackson on 2007-11-28
Still nothing working for me... :confused:

---

### Post by somegirl on 2007-11-29
The first solution worked like a charm for me, thanks so much for posting it!

Also, I've got XP instead of Vista, so here's a case where it works just as well. For a while I was worried because when I'd boot in XP it'd boot faster than ubuntu, and thought that couldn't be right at all!

Now they take about the same amount of time on a 2Ghtz processor and 2Gigs of RAM. That's what really worried me, was even XP boots reasonably fast on this machine.

Anyway, thanks a bunch!

---

### Post by romojap on 2007-12-02
> **LeeAdkins said:**
> Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

I registered only to tell you, sir, that you are the greatest thing since sliced bread!

THANK YOU!

My boot time went from 3-4 minutes to 30 seconds.

---

### Post by Chang An on 2007-12-03
The 2nd longer method really messed up my pc.  Here is the message I get in recovery mode.

Kernel panic - not syncing : VFS unable to mount root fs on unknown - block.

How can I revert my settings back to before?  Someone please help.

---

### Post by GVaio on 2007-12-06
To a NOOB like me ... this thread was helpful.  Although what I was trying to accomplish was not directly related ... check this out: [http://ubuntuforums.org/showpost.php?p=3905665&postcount=3]("http://ubuntuforums.org/showpost.php?p=3905665&postcount=3")

And thank you all !

:) G.

---

### Post by nail33 on 2007-12-09
You sir, are a miracle worker. Thankyou so much. I upgraded from Feisty to Gutsy on my hp nc6000 and was about to reinstall Feisty because of the very slooooooooow boot up time and black screen. I'm a newbie when it comes to anything in terminal mode. I was able to follow your instructions and it worked great. This should be a "sticky" as I've read many complaints from other hp laptop users with just this problem. Thanks again!!!

---

### Post by pelle.henriksson on 2007-12-14
worked great, thanks!

---

### Post by u2buntu on 2007-12-17
I had problems editing menu.lst because I didn't have access to save that file. After googling around I found out you can edit it with Alt+F2, and then typing "gksudo gedit" without the ". You type the admin/root password and get a text editor with admin control. It may sound obvious, but it wasn't to me :/

As regards the first solution (removing the "ro quiet splash" and "quiet") it didn't make any change, except that the startup switched from a progressbar to text.

---

### Post by seventhc on 2007-12-17
has anyone tried all the methods? 'delete the lines', adding 'vga=791' and also the hex equivalent 'vga=0x318'. I'll probably try all 3 later but curious about other peoples results. Each machine might react differently to each method and I'd like to know if thats the case.

[edit for a question]
I tried with 791 and the hex but both seemed about the same. here is the line so I'm just asking if this is in the correct place.

```
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=9f4139dc-b54a-44cb-88cb-d0797d84d311 ro quiet splash vga=791
```
Also I have a duel boot bt3 and ubuntu. I actually had to delete the vga line in grub for bt3 to make the resolution correct. when it was in there i lost a few inches of screen space and couldnt get full resolution. took a few hours of messing with it to get it. I know editing the ubuntu portion wont affect bt3 but as far as boot times go will it matter??

---

### Post by Leion on 2007-12-20
I had slow boot as well as a blank screen on boot.
Thanks to a kind soul (willie_wang)for pointing me here
I managed to solve both my problems.

I have completed uninstalled usplash (I am fine with not looking at a splash screen on boot)
and removed the quiet lines in the grub menu.lst flie
now i am able to boot in less than a minute compared to 4 minutes last time

COOL!

Hope this can help anyone with the same issue

---

### Post by Tux.Ice on 2007-12-20
the black screen is because of hardware - driver misfunctions i think

correct me if im wrong but my bros laptop has same problem and mine is fine.

Brothers Laptop - Black Screen - Toshiba M70

My Laptop - No Black Screen - Toshiba A100 with a 120 gb hdd

---

### Post by jan quark on 2007-12-20
Bump and thanks for speeding up my boot time

---

### Post by Pinger05 on 2007-12-21
Thank you

---

### Post by Pogeymanz on 2007-12-21
I think my resolution is higher than 1024x700-whatever. Should I be using a different number than 791? I tried the fix and I think it's faster but the little bar doesn't grow on the splash screeen. My resolution, I think, is 1280x1024. Does that sound right for a laptop? I tried to check in Settings->Display Settings, but it just says "Default" with the other options being 800x600 and something lower than that.

---

### Post by kaichu on 2007-12-22
The "longer fix" didn't work on my laptop (HP Pavilion ze2000).
All it did was hang up on boot flashing caps lock. Couldn't even boot to
recovery mode.

So instead of waiting three minutes I ended up spending two hours downloading
the iso, burning it to disc and booting from that. Frustrating.

At least I was able to revert the configuration back to normal. I was afraid I would
have to install it from scratch again, configuring and installing wlan drivers again and
installing all the software again.

I think I'll live with slow boot for now, since this isn't my primary machine. Trying to solve this by trial and error and then booting from Live to get things back to normal seems too much of a hassle. There's bound to be an update somewhere along the line that'll fix this. Right?

---

### Post by kool_kat_os on 2007-12-22
Will this also get the splash screen back? If not how do I get the splash screen with the ubuntu logo and  an orange loading bar back?

---

### Post by Epic Plecostomus on 2007-12-22
:guitar:

HAIL HAIL HAIL!

My IBM Thinkpad R40 now boots in about 1 min 45 seconds as opposed to a seven-min boot!  All I did was remove the quiet lines as the OP suggested!  HURRAY!   

You guys are great.

---

### Post by indianethic on 2007-12-26
thnx for the solution.

---

### Post by Lukasz Tarkowski on 2007-12-26
Thank you so much it has worked great
Next remind us where the menu.lst file is listed what dir?
I had to go to irc chanell ofm ubuntu and I forgot again heh :p but it works fast now thnx to you :)

---

### Post by copycat on 2007-12-27
> **LeeAdkins said:**
> Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

Very nice.... keep up the good work!

---

### Post by Daniel Song on 2007-12-30
thanks, i will try this later, but thanks for sharing your information.

---

### Post by Kunks on 2007-12-30
I won't even bother to take a chance on either of these fixes as I don't want to have to do a re-install like a some have had to do as a result. I just hit Ctrl/Alt F1,F2, or F3 & after a momentary pause with a few text lines, it boots up rather quickly with my splash screen intact.... If i don't do anything it still will boot up( about 2-3 minutes) Don't know why, don't care, everything else works great.......

---

### Post by hotrod6657 on 2008-01-01
Good deal, thank you for that!!!

The both methods worked for me, the first one was a few seconds faster, but i'm not sure how consistantly my boot time really is.  

The second method also finally fixed the resolution of my progress bar upon loading!!!  it was always way too large, now... all better.

you all rock, thanks again!

hotrod

---

### Post by clayts450 on 2008-01-01
Regrettably, this solution killed my Ubuntu - if anyone can help I'd be grateful - see [here]("http://ubuntuforums.org/showthread.php?t=655529")

---

### Post by stuffelse on 2008-01-01
Reply to the first page fix by LeeAdkins, worked great for me! Boot speed went from 2+ minutes to about 30-40 seconds, and I got the boot splash!

---

### Post by Flying caveman on 2008-01-04
Thanks!  that worked for my brother's HP laptop. with the ATI xpress200M.  What happened to the thank you thingies???

---

### Post by clayts450 on 2008-01-04
Well after getting my T22 back to working order (see post above) after the second method trashed my Ubuntu (the same a couple of people got on here), I had a go at the first method. May have been a few seconds quicker, but nothing dramatic.

Mine never really took that long anyway - not bad for a 900Mhz, 384MB Thinkpad T22 really - around about a minute or 90 secs :)

Thanks for sharing the idea anyway - at least I learned a lot about Ubuntu when restoring my machine :)

---

### Post by ~LoKe on 2008-01-05
USplash is all bugged up, it shouldn't take that much longer to boot with it on.  But yes, removing the "quiet" and "splash" options speed up a boot dramatically.  I think I'm sitting at 16 seconds.

---

### Post by rmnstr on 2008-01-06
Worked for me too, thanks!

---

### Post by what4893 on 2008-01-07
The second method fixed me up. Thank you soooo much. I had just re-installed Feisty and this started happening. I had no idea what had changed because it ran great before. Took my boot time from 2:34 to 0:29. Thanks soooo much.   :popcorn:

---

### Post by robbieo11 on 2008-01-07
45 seconds

---

### Post by ubuntu-freak on 2008-01-09
Neither solution worked for me. If it didn't work for you try this.
 
Do you have a windows partition mounted? I realised when I enabled text mode that it was the filesystem check making usplash hang and timeout.
 
Enter this command in a terminal
 
sudo gedit /etc/fstab
 
Now go to the end of the line of your windows partition and change the 1 to a 0 and then close and save.
 
This will stop it being checked at boot and stop usplash hanging and timing out. Now and then you should check it with windows though incase there are errors. 
 
If you have weird behaviour by usplash on shutdown, suspend, reboot etc it is probably video card related.
 
Easy solution for me was to install this application 
 
sudo apt-get install startupmanager
 
Go to system>administration and launch it. Then change bitdepth to 16bit or just experiment until shutdown usplash works properly. Personally I use 1024x768 and 16bit colour.
 
Hope that works as well for you as it did for me.
 
Nathan

---

### Post by dutchcow on 2008-01-14
If you want a mix between verbose text and the graphical bootup and the speedup fix by adding the vga mode line; edit your /boot/grub/menu.lst and change the "defoptions" to something liek this:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash=verbose vga=791

```This will give you the progress bar and ubuntu logo with underneath it verbose messages of things being started, fsck running ,etc, etc. If the resolotion is too low try editing "/etc/usplash.conf" and change the resolution to a higher one, then run "sudo update-usplash-theme usplash-theme-ubuntu" and reboot.
Hope this helps anyone.

---

### Post by ubuntu-freak on 2008-01-14
> **dutchcow said:**
> If you want a mix between verbose text and the graphical bootup and the speedup fix by adding the vga mode line; edit your /boot/grub/menu.lst and change the "defoptions" to something liek this:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash=verbose vga=791

```This will give you the progress bar and ubuntu logo with underneath it verbose messages of things being started, fsck running ,etc, etc. If the resolotion is too low try editing "/etc/usplash.conf" and change the resolution to a higher one, then run "sudo update-usplash-theme usplash-theme-ubuntu" and reboot.
Hope this helps anyone.

 
Have you tried Startup Manager? Let's you do that with one click, and usplash acts more seemless with SUM installed. Great little app. 
 
Nathan

---

### Post by dutchcow on 2008-01-14
Havent tried startup manager yet, will give it a go. I'm quite comfy with using terminals myself, dont mind editing the odd text file here and there ;) Thansk for the tip tho!

---

### Post by ubuntu-freak on 2008-01-14
You can also change usplash with it, colours and set a grub password. Forgot to mention those.
 
Nathan

---

### Post by dutchcow on 2008-01-14
Given SUM a try, doesn't do much for me but might be very useful for less tech savvy people who don't want to use the terminals much. Also it didn't run from the menu as it wanted to use some sudo-to-root tool which isn't installed by default on my hardy, maybe it should use gksudo instead. Other than that a nice tool. Too bad the vga= string doesn't add any speed, my bootup time in text mode and with splash are there same, about 1 minute.

---

### Post by happyhamster on 2008-01-14
> **gaburko said:**
> 
simply remove "ro quiet splash" and "quiet"

dunno why, but it works - boots in about a minute -)

Cheers
Couldn't removing "ro" result in filesystem corruption, when fsck does its thing? Or perhaps it will prevent fsck being run at all? Either way, I think keeping the "ro" parameter is safest.

---

### Post by philinux on 2008-01-14
+1 for startupmanager fantastic little app.

---

### Post by ubuntu-freak on 2008-01-14
> **happyhamster said:**
> Couldn't removing "ro" result in filesystem corruption, when fsck does its thing? Or perhaps it will prevent fsck being run at all? Either way, I think keeping the "ro" parameter is safest.

Um that doesn't effect the filesystem check. Just stops Usplash showing.

Nathan

---

### Post by ubuntu-freak on 2008-01-14
> **dutchcow said:**
> Given SUM a try, doesn't do much for me but might be very useful for less tech savvy people who don't want to use the terminals much. Also it didn't run from the menu as it wanted to use some sudo-to-root tool which isn't installed by default on my hardy, maybe it should use gksudo instead. Other than that a nice tool. Too bad the vga= string doesn't add any speed, my bootup time in text mode and with splash are there same, about 1 minute.

It's like I said before though, it also makes the booting process quieter and more seemless. I've done little tests. I still don't know how it does it.

Nathan

---

### Post by GoKvallFarbror! on 2008-01-14
Thanks!!

---

### Post by ubuntu-freak on 2008-01-14
Are you a newbie Gok? Check out my multimedia how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Post your comments and results in that thread. 

Nathan

---

### Post by tqprvn on 2008-01-16
caution caution....newbie let loose at keyboard....10 days on Linux....

So I dug out the menu.lst thing from the OP to do this.  Deleted the required words.  Tried to save...got told that I dont have sufficient privileges (or somesuch) to edit and save the file.

How can?

---

### Post by seventhc on 2008-01-16
> **tqprvn said:**
> caution caution....newbie let loose at keyboard....10 days on Linux....

So I dug out the menu.lst thing from the OP to do this.  Deleted the required words.  Tried to save...got told that I dont have sufficient privileges (or somesuch) to edit and save the file.

How can?
try this ```
sudo gedit /boot/grub/menu.lst

```
:)

---

### Post by Drone4four on 2008-01-16
This is a useful thread.

---

### Post by jbobgray on 2008-01-16
thank you.
My system boot so much quicker. :)

---

### Post by tqprvn on 2008-01-16
> **seventhc said:**
> try this ```
sudo gedit /boot/grub/menu.lst

```
:)

thanks for this...pretty sure I just learned something.

Unfortunately this didnt speed up my start time...replaced my Ubuntu splash screen with lots of code, but that wasnt the slow part for me. 

Mine slows down after login, where it goes to that Ubuntubeige (TM) blank screen with only a mouse pointer on it, then takes a while to load my desktop.  Any ideas?  What is happening in the background there?

---

### Post by ubuntu-freak on 2008-01-16
> **tqprvn said:**
> thanks for this...pretty sure I just learned something.

Unfortunately this didnt speed up my start time...replaced my Ubuntu splash screen with lots of code, but that wasnt the slow part for me. 

Mine slows down after login, where it goes to that Ubuntubeige (TM) blank screen with only a mouse pointer on it, then takes a while to load my desktop.  Any ideas?  What is happening in the background there?

 
It's cos of compiz. GTK and compiz don't get along that great yet, especially starting together.
 
If you disabled effects it would speed up.
 
And forgot to install starupmanager. Much easier than editing by hand.

Nathan

---

### Post by skaldicpoet9 on 2008-01-17
*edit*

nvm, I read through the thread and found what I was looking for.

However, I do have one question: what is the difference between the two solutions given on here? One disables splash? Is that the login screen or something?

---

### Post by 2468_calvin on 2008-01-20
This solution worked well on my HP nc6000 and Ubuntu 7.10, down from 3 minutes 40 seconds to 95 seconds.  I tried the more involved method described after this original post, but unfortunately it did not improve the boot time.  For others NOOBs like me, you need to be in the terminal mode.  The file is "/boot/grub/menu.lst".  Once I changed to the "/boot/grub" folder, I used "sudo gedit menu.lst" to open the file and make my changes.

Thanks a lot to both people who posted these fixes. 

> **gaburko said:**
> Hi guys, firs post for me here.
So, I installed Ubuntu 7.10 yesterday on a relatively OK laptop - 2 Ghz, 2 GB RAM, X1300 128 MB Video. Aaaaanyway - what immediately striked me was the slow boot. 
since I have a dual-boot (Vista) I played a little with the menu.lst - I wanted Vista to be the default. However, the change that "did it" for me was the following:

original

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70[COLOR="Red"] ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]


```

now
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70
initrd		/boot/initrd.img-2.6.22-14-generic

```


simply remove "ro quiet splash" and "quiet"

dunno why, but it works - boots in about a minute -)

Cheers

---

### Post by ubuntu-freak on 2008-01-20
> **skaldicpoet9 said:**
> *edit*

nvm, I read through the thread and found what I was looking for.

However, I do have one question: what is the difference between the two solutions given on here? One disables splash? Is that the login screen or something?

 
Yeah the first solution disables usplash (Ubuntu loading screen).
 
You shouldn't have to do that though. Easier way to edit the various options is to 
 
**sudo apt-get install startupmanager** 
 
It gets installed into System>Administration. Keep the bit depth to 16bit or you might have distorted shutdown/restarts.
 
Nathan

---

### Post by birdsixone on 2008-01-26
What would I change my Xorg 'vga='  to for a 1280x800 resolution? vga=791 works but I cant view text if I switch to a virtual console by pressing ctrl+f1, I just get a blank screen.

---

### Post by ubuntu-freak on 2008-01-26
> **birdsixone said:**
> What would I change my Xorg 'vga='  to for a 1280x800 resolution? vga=791 works but I cant view text if I switch to a virtual console by pressing ctrl+f1, I just get a blank screen.

 
Xorg? You don't have to touch that. You can't see text cos it's setup to disable text and do a really quiet boot. You can install startupmanager and choose your res, and even show text on the usplash itself below the Ubuntu logo and name.
 
 Nathan

---

### Post by Paul86fxr on 2008-01-29
Fantastic fix, worked well!

Paul

---

### Post by Wobblybob on 2008-02-04
> **LeeAdkins said:**
> 

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

sudo gedit /boot/grub/menu.lst to add "vga=791" to menu file

then

sudo gedit /etc/usplash.conf to update usplash with my screen res 1280x800

re booted laptop and wow the boot up time is now back to Fiesty time, thanks LeeAdkins, great fix

---

### Post by ACGarib on 2008-02-04
I've got the same problem birdsixone has.  I when I do ctrl+alt+F1, I don't get anything anymore, just a blank screen with a blinking underscore line. I used to get a console.


How do I get that back?

I added the vga=791 line in menu.lst, changed the resolution in usplash.conf, and did: sudo update-initramfs -u -k <insert results from uname -r here>.

EDIT:

I followed the directions here: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/comments/161](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/comments/161)

but I omitted the "sudo dpkg-reconfigure console-setup" part because I didn't want to mess up my keyboard settings.

note: in the menu.lst, I added vga=0x365 at the end of the rootflags line instead of doing the defoptions thing.

---

### Post by tobydeemer on 2008-02-04
Hi all-

I had used the fix a while ago to remove the quiet splash lines, and it worked wonderfully while giving the verbose boot. And tonight I found the longer fix option that restored the boot splash screen and kept the speed. So good work guys.

One thing to keep in mind though is that any editing of the menu.lst file that you do will have to be redone after any kernel updates. I'm not sure about the conf file though. I would assume it's the same.

Does the Start Up Manager prevent that from having to be re-edited after a kernel update?

---

### Post by Frost1013 on 2008-02-05
Finally!! I don't have to wait 4 minutes to boot anymore.  Now, if I can only get dhcp to work...

Thank you :)

---

### Post by Frost1013 on 2008-02-05
Finally, I don't have to wait 4 minutes to boot anymore!!!  Now, if only I could get wireless under dhcp to work...

Many thanks!!!

---

### Post by gn2 on 2008-02-05
> **LeeAdkins said:**
>  add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. 

This might help explain it:
```


  VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits  640x480  800×600  [COLOR="Red"]1024×768[/COLOR]  1152×864  1280×1024  1600×1200
   256    8   vga=769  vga=771   vga=773   vga=353   vga=775    vga=796
 32000    ?   vga=784  vga=787   vga=790   vga= ?    vga=793    vga= ? 
 65000   [COLOR="Red"]16[/COLOR]   vga=785  vga=788   [COLOR="Red"]vga=791[/COLOR]   vga=355   vga=794    vga=798
 16.7M   24   vga=786  vga=789   vga=792   vga=795   vga=799


```

---

### Post by neolin on 2008-02-06
thank you so much for that menu.lst tip. worked on my celeron. the problem was that the loading bar during the splash screen would hang..then it would swithch to verbose mode saying that loading hardware drivers   [fail]............after that it would take a really long time to boot.....dunno why but ur tip solved the problem.....now the hardware drivers get   an [ok] for some reason...........had downloaded and installed ubuntu 6 time but with same result.....thought of giving it one last shot after reading ur tip....thanx a lot

---

### Post by Forrest Gumpp on 2008-02-06
Clearly, there is enormous interest in quick booting of Ubuntu.  I'm still too new to Ubuntu to have become irritated by booting slowness - maybe I have not yet experienced it - but thank you gaburko for the tip, I'm sure I'll get to using it.

Whilst reading posts to other topics on the forum I saw that one contributor had provided a link to APC Magazine's Windows Linux dual booting guide.  (On my doorstep, so to speak!)  The article contained this link:  [http://www.apcstart.com/3895/how_vista_screws_dual_booting_nirvana](http://www.apcstart.com/3895/how_vista_screws_dual_booting_nirvana)   

The article author, Declan Kennedy, writes:  "Since finding this, I've checked it out and even Windows XP can be simultaneously hibernated with Ubuntu on my notebook, meaning that I can always have a session of each ready.  Sheesh, Windows recovers ridiculously quickly from a hibernate, somewhere in the order of 10 seconds... I wonder if I'll ever shut it down again?".  The whole short article is well worth a read.

The article is only relevant to this topic inasmuch as it offers an alternative pathway for some users to gain rapid access to their (Ubuntu) desktop, something that over 15,000 Forum visitors have shown evident interest in on this thread alone.  What a ripper forum!  Thanks again, gaburko, but.....

A nitpick.  Can you edit "Werd" in the topic heading in the Forum index to "Weird"?  You were starting to raise my blood pressure with what I at first thought was the deliberatly mis-spelled name of a well known proprietary word processing application.  Visions of cross-platorm sabotage started coming to me!

---

### Post by vikasmk on 2008-02-07
How do i save the menu.lst file, after making changes .
it says i do not have permissions to do so.

---

### Post by El_Belgicano on 2008-02-07
did you open it with sudo?

---

### Post by philinux on 2008-02-07
> **vikasmk said:**
> How do i save the menu.lst file, after making changes .
it says i do not have permissions to do so.

gksudo gedit /boot/grub/menu.lst

---

### Post by Shackman on 2008-02-08
> **Wobblybob said:**
> sudo gedit /boot/grub/menu.lst to add "vga=791" to menu file

then

sudo gedit /etc/usplash.conf to update usplash with my screen res 1280x800

re booted laptop and wow the boot up time is now back to Fiesty time, thanks LeeAdkins, great fix

Thanks much to you wobbly bob and LeeAtkins.  My laptop is 1024x768 so I adjusted the usplash accordingly.  Works awesome! :)

---

### Post by moshuptrail on 2008-02-08
This is great!
BUT, a note of caution to all...
If you get a kernel update, the updater does not copy the kernel line parameters.  You will need to re-apply the vga=791 each time there is a kernel update.  I don't know about the usplash.conf file.  So keep a link to this post so you can look up the fix after the next kernel release! :)

---

### Post by philinux on 2008-02-08
If you have startupmanager installed the vga bit does not seem to get removed with a kernel update.

---

### Post by ubuntu-freak on 2008-02-08
> **moshuptrail said:**
> This is great!
BUT, a note of caution to all...
If you get a kernel update, the updater does not copy the kernel line parameters.  You will need to re-apply the vga=791 each time there is a kernel update.  I don't know about the usplash.conf file.  So keep a link to this post so you can look up the fix after the next kernel release! :)

 
If you're applying it to the def. options a bit further up in the menu.lst, doesn't it keep appying those options to each new kernel line?
 
I think they've fixed it lately anyway, the bug with usplash and the various settings. I always install startupmanager though.   

Note: SUM might cause a blank screen during your (every 30 mounts) disk check cos it does something to make the boot super smooth and quiet. Don't presume it's a hard lock crash and reboot.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-08
Have you noticed the above Phil?

---

### Post by vvvladut on 2008-02-09
I tried the second fix (fifth post in this thread), but via Startupmanager, after noticing that it adds exactly the same lines to the same files, plus rebuilds the boot image, so there is no need to bother doing all those yourselves. I think it did speed the pre-login screen boot sequence from about30 secs to 25, so not really significant, but there was something, so if your pre-login boot up takes 4 mins (as I've seen reported on tis thread) you should definitely try it.

However with me it's the post-login boot up that takes about 2 minutes, so much longer that the other one. Someone said it must be compiz trying to figure out how to start up all that eye candy...but I like eye candy, so I think I'm stuck with the longer boot up time...

---

### Post by vikasmk on 2008-02-09
used the werd solutin and it worked. thanx
   ps:      ubuntu  RULES!!!!:guitar:

---

### Post by jflynn4 on 2008-02-12
> **gaburko said:**
> Hi guys, firs post for me here.
So, I installed Ubuntu 7.10 yesterday on a relatively OK laptop - 2 Ghz, 2 GB RAM, X1300 128 MB Video. Aaaaanyway - what immediately striked me was the slow boot. 
since I have a dual-boot (Vista) I played a little with the menu.lst - I wanted Vista to be the default. However, the change that "did it" for me was the following:

original

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70[COLOR="Red"] ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]


```

now
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70
initrd		/boot/initrd.img-2.6.22-14-generic

```


simply remove "ro quiet splash" and "quiet"

dunno why, but it works - boots in about a minute -)

Cheers

THANK YOU!!!!   I'm NOW a fan of Ubuntu 7.10!!
Running an old HP Pavillion laptop 512mb ..... this fix works incredibly well.   Actually boots faster now than it did pre-Linux.

Again, THANK YOU!

---

### Post by Ohioan on 2008-02-14
This thread is incredible.  It needs to be sticky'd cause it's hard to find by searching.

---

### Post by gnicko on 2008-02-14
Well, here's the deal...

I tried this fix and now my machine won't boot.

Seems to run grub OK then begins to boot then hangs at "Waiting for root file system..." After about 5 minutes, it says "Done." then:

Check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/6e80.... [correct UUID]....  does not exist! Dropping to a shell!

then drops me to BusyBox with (initramfs) prompt....

If I check out /disk/by-uuid/ it shows the correct drive with the correct UUID.

Here's my question(s):

What exactly is (not) going on here? Iis this a "Grub" problem or a problem with the boot image?

Will "re-installing" Grub take care of this, or do I have to build a new boot image? Or should I do both?

If it is the boot image, what can I do to make sure that the "rebuilt" one isn't messed up in the same way?

Any help would surely appreciated!!


...OK, fixed the boot problem by copying an old boot.img over the top of the new one...back in business!!

My original problem is still there...long boot with no splash screen. Not really a big deal, but being a perfectionist, its bothering me.

---

### Post by hmmbe on 2008-02-18
thanks very much.

it improved my boot up time a lot. :-)

thanks again.

hmmbe

---

### Post by oddchild on 2008-02-24
BIG THANKS!!! I did that and changed "XP professional" to XP   "  poop" I think that helped it work better. Thanks very much for your help

---

### Post by arashiko28 on 2008-02-27
> **gaburko said:**
> Hi guys, firs post for me here.
So, I installed Ubuntu 7.10 yesterday on a relatively OK laptop - 2 Ghz, 2 GB RAM, X1300 128 MB Video. Aaaaanyway - what immediately striked me was the slow boot. 
since I have a dual-boot (Vista) I played a little with the menu.lst - I wanted Vista to be the default. However, the change that "did it" for me was the following:

original

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70[COLOR="Red"] ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]


```

now
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70
initrd		/boot/initrd.img-2.6.22-14-generic

```


simply remove "ro quiet splash" and "quiet"

dunno why, but it works - boots in about a minute -)

Cheers
 
Hi, I'm not a total noob but can't find the way to modify menu.lts please can you tell me? how to open it from terminal or anything that allows me to save the changes.

---

### Post by seventhc on 2008-02-27
> **arashiko28 said:**
> Hi, I'm not a total noob but can't find the way to modify menu.lts please can you tell me? how to open it from terminal or anything that allows me to save the changes.
sure, put this into the terminal
```
gksu gedit /boot/grub/menu.lst
```

:)

---

### Post by kool_kat_os on 2008-02-27
> **seventhc said:**
> sure, put this into the terminal
```
gksu gedit /boot/grub/menu.lst
```

:)

i did 

```
sudo gedit /boot/grub/menu.lst
```

it worked fine

---

### Post by seventhc on 2008-02-27
sudo will work, but your supposed to use gksu for gui application, sudo for terminal apps. so 
sudo vim
gksu gedit.
;)

---

### Post by Daplaya05 on 2008-03-01
i just do the su command and run terminal as root user, anyways thanks for this. now my xubuntu boots alot faster!

---

### Post by mahill on 2008-03-15
worked beautifully for me.  Thanks.

---

### Post by naptime on 2008-03-21
Thanks for the post.  I tried this solution on my Thinpad T41 running Gutsy to resolve my slow boot issue.  However, I did have to remove the "vga=791" addition to the kernel line.  With it on the line I booted quickly but never completed the logon (at least for 5 minutes when I gave up waiting for it).  Anyway, now it boots quickly and the logon completes quickly.  Nice tip.

---

### Post by rookie4evr on 2008-04-03
[PHP]gksu gedit /boot/grub/menu.lst[/PHP]

i typed this command in "Terminal" ....
it asked me for a password ... typed my password ....
then it took me to an program ... similer to "note pad" ....
nothing showing up though ??????

what do i do?????

---

### Post by dalewest on 2008-04-03
> **sugarland2k said:**
> VGA=791 sets up your xorg for something like this..


Screen   640x480     800x600     1024x768     1280x1024     1600x1200 
Colors  ---------------------------------------------------------------------- 
 256      | 769             771             773               775              796 
 32,768 | 784            787             790                793              797 
 65,536 | 785            788             791                794              798 
 16.8M  | 786            789             792                795              799 

Good work on this subject.
Thanks for the info... but what about those of us with widescreen displays?  I'm running @ 1280 x 800.

---

### Post by rookie4evr on 2008-04-04
Anyone!!!

---

### Post by rookie4evr on 2008-04-04
[PHP]gksu gedit /boot/grub/menu.lst  [/PHP]
[PHP]sudo gedit /boot/grub/menu.lst  [/PHP]

i tried both of these commands in "Terminal" ..both of them asked me for password ... typed it in ... and opened a word document or something ...
in these i don;t see anything .. just a blank document :confused::(:lolflag: HELP PLEASE

---

### Post by rookie4evr on 2008-04-04
hmmmmmm

---

### Post by philinux on 2008-04-04
I assume your pc boots up ok?

If I copy and paste that into mine I get the grub menu as normal.

---

### Post by rookie4evr on 2008-04-04
"I assume your pc boots up ok?

If I copy and paste that into mine I get the grub menu as normal."


well... When I choose ubuntu ..
I do one of the following ...
a) I get black screen for like 5 min and it boots into login screen .....
or 

b) I press "CTRL + ALT+ F6" ...to skip the splash screen to enter login screen ...:(

for some quite reason ... I been getting black screen from the start and my booting time it like 5 min or so ..... just want to figure out what is wrong with it ......

---

### Post by rookie4evr on 2008-04-04
I tried putting the same command code to ese, if the CD opens the menu ...:confused: :( 
CAN SOME PLEASE HELP ME WITH MY PROBLEM ....
I TRIED EVERYTHING .... CAN'T GET THIS TO WORK .....

---

### Post by naptime on 2008-04-05
Hmmmm, when I use your commands on my machine they each open up the menu.lst file for editing as they should.  I assume that when you say you "typed this command in "Terminal" " that you went to the Applications-Accessories menu and started a Terminal and in the subsequent terminal window typed in your command.  If not, then try doing it that way.  If you did do it that way then I suggest looking around your system a little from the Terminal.  You might try something like the following in the Terminal window:

cd /boot  # This should take you to the /boot directory
cd grub  # This should take you to the grub subdirectory (/boot/grub).
ls -l menu.lst  # This should list the directory entry for menu.lst to your Terminal window.
cat menu.lst  # This should rapidly list the contents of menu.lst to your Terminal window.

If all this works, then try your command "gksu gedit /boot/grub/menu.lst" again.

If one of these steps fails (including the gksu gedit command if you get that far) then post the results in a reply.  In your reply should paste the result of each step.

---

### Post by oarion7 on 2008-04-09
tried the first method in the thread, worked great!!! thanks

---

### Post by boofly on 2008-04-10
Had the same problem, Compaq Presario V2000 system with roughly 5 minute boot time. Removed the options from the boot params as specified, and my boot time is down to well under a minute now.  Thanks.

---

### Post by sayakb on 2008-04-10
If I remove "quiet" and "ro quiet splash", will I have a text mode boot, or will I see the usual usplash theme I selected?

---

### Post by orthopteroid on 2008-04-15
Has anyone noticed a boot speedup if they add 'noresume' to the kernel options in menu.lst?

As I understand it 'noresume' tells the kernel to not bother checking for a system 'resume image' - since I never do a hibernate or standby I've found it safe to add this option.

Originally, I was seeing 'fishy things' on my router during bootup, which 'noresume' was able address... Perhaps it was just me - but if anyone tries 'noresume' and they get mileage plz let me know - perhaps there it is only a ghost in my machine.

cheers,

john

---

### Post by dndrich on 2008-04-16
I had the same problem trying the 2nd solution in the thread, with the screen about the wrong parameters.  I downloaded startup manager from the repositories, and after a couple of different combinations tried with it, I hit on the right one.  Now the computer boots more quickly, and I get the splash screen.  So that worked for me.  The startup manager modifies grub, the kernal, and whatever else it does seamlessly.  So I recommend trying that folks.

---

### Post by fz43mw on 2008-04-18
Thankyou this made start go from upto 5 minutes to 45 seconds to login...

regards

---

### Post by vocalstud69 on 2008-04-19
Awesome!  This does work for me, cutting down boot time from four minutes to 27 seconds.  Thanks very much for your help.

---

### Post by kroustou on 2008-04-21
nice thanx!

---

### Post by SpinningAround on 2008-05-22
Does this work on 8.10 got a strange problem that I asked for help in this thread [http://ubuntuforums.org/showthread.php?t=794944](http://ubuntuforums.org/showthread.php?t=794944)

---

