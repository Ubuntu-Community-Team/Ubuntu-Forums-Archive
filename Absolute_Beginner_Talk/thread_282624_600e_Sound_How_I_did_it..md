---
title: "600e Sound How I did it."
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by clembone on 2006-10-23
Today is my first day with Ubuntu and I must say that I was impressed. Nice OS. 8) But I did beat my head on this one all day. Tried tons of stuff then combined a few things from 2 different sites to get this working.

To all the newbie’s that say they are afraid to mess with grub or any other file on your box please leave that at the door. If you are truly new then chances are you have no data on your box and thus reloading should not be of great importance.

Speaking of reloading I did start with a fresh load of Ubuntu 6.06.1 LTS (Dapper Drake) to get this working and thus that will be my recommendation to anyone trying this.

One small disclaimer this is "as is". This worked for me and I give no guarantee and or promise that it will for you. 

Here goes.
The 2 sites I used are:
[http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html")
&
[http://www.wlug.org.nz/ThinkpadNotes]("http://www.wlug.org.nz/ThinkpadNotes")

I will just list the steps in order and you can do additional reading on the sites if you need an explanation of the steps.

Add these lines to /etc/modules:
sound
ad1848
uart401
snd-cs4236

Blacklist the incorrect sound card in /etc/modprobe.d/blacklist. Add these lines to the bottom of the file as written below - with the xx's:
# IBM 600e Sound
blacklist snd-cs46xx
blacklist cs46xx

Add the following lines to the bottom of /etc/modprobe.d/alsa-base:
# IBM 600e Sound
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

:-k NOTE: When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'.

When using the kernel that came with Ubuntu 6.06 (dapper), I needed to boot the kernel without PNP? support. This is done by adding "pnpbios=off" to the kernel command line; the proper way to do this is to edit /boot/grub/menu.lst, and add pnpbios=off to the line that starts with

# kopt=root=...

and then running grub-update to get those options added to all the kernels that are installed. To run grub-update run the following commands from a terminal.

sudo -i
cd /sbin
./update-grub

You should also go into the BIOS menu (hold down F1 on power-on), and disable "fast boot". Fast boot means that you are using a PNP Operating System. This will prevent the BIOS from configuring the hardware.

Reboot and do not forget that there are 2 places that you must turn up the sound for it to work.

1. Hold down the Fn key and press PgUp repeatedly. You should hear beeps getting progressively louder.

2. On the speaker Icon in the panel.

Good Luck \\:D/

---

### Post by tripleee on 2006-10-28
Worked for me. Finally an instruction which worked! Thanks!

Question: Is there a particular reason you put the modprobe stuff in multiple files?

I was planning on creating just a /etc/modprobe.d/sound.600e.local instead of adding stuff to the alsa-base and blacklist files, just wondering if there's any technical reason not to do it that way? In general, I try to avoid editing files which were installed with the operating system if there's another way. That tends to make upgrades smoother and it's also clearer what I need to copy to another machine if there's ever a need.

Minor nits: On my system, the BIOS option is called "Quick Boot". Also what's with the multiple commands to update grub? A single sudo /sbin/update-grub should be enough, shouldn't it?

---

### Post by clembone on 2006-10-30
No and after pondering your statement about upgrades I think it is probably a better way of adding the module. I will try it. Thanks for the tip.

Question: When adding new files to the /etc/modprobe.d directory are there any special requirements for the new files? Is there a best practices naming convention or is it simply personal preference?

Riddle me this: nits = nitpicks?

My systems bios calls the Fast Boot option Quick Boot as well. Okay you got me I made a mistake. I will offer up this lame excuse. This post originally went in at about 2 or 3 am.

Yes a single command to update grub is sufficient. I read a post from one of the admins asking users to stop banging on new users because of their lack of Linux knowledge and the cli (Command Line Interface). The post also called for an attitude shift from the forum users to be clearer with post so that new users could understand the posts. After reading this I thought about how I should write my fix to the masses. I made the decision to try and educate the end users. The multiple commands shows that a user can set his privileges to admin with (sudo &#8211;i) change directory to the sbin directory with (cd \sbin) to find the update-grub executable to launch with (./update-grub). It was merely an attempt to do my part.

---

### Post by Adox on 2006-10-31
Hi, 
With Dapper on my thinkpad 600E I'd solve the sound problem but after the upgrade to Edge the sound broken.

This is what I get with the modprobe command. 

root@thin:~# modprobe --verbose snd-cs4236 port=0x530 cport=0x538 fm_port=0x388 irq=5 dma1=1 dma2=0
insmod /lib/modules/2.6.17-10-generic/kernel/sound/isa/cs423x/snd-cs4236.ko port=0x530 cport=0x538 fm_port=0x388 irq=5 dma1=1 dma2=0 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0 port= cport= fm_port= irq= dma1= dma2= isapnp=0 index=0 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.17-10-generic/kernel/sound/isa/cs423x/snd-cs4236.ko): Invalid argument

:shock: 

???? Why the arguments are duplicated? 
Anyone could help me?

Bye 
Adox

---

### Post by CCPhil on 2006-11-09
Hi

Nice write-up - happy its working for you - sorry to say, it didn't work for me.
Although I'm a bit of a 'newbie' when it comes to Ubuntu and its variants, I've used Linux/Unix for a while.
I'm using Xubuntu-edgy on the 600E - figured it'd be lighter and snappier than XP (which it seems to be).  The 600E is my wife's - and she's been complaining about its performance with XP - shame sound seems to be such a pain - if it were 15 years ago I could understand...

lspci reports the sound chip as a Crystal 4610/4611 and the default install detects it and loads the alsa cs46xx drivers but 'aplay -l' reports no soundcards found.

After trying suggestions from other posts (and removing the changes) and from this thread (including the bios change and updating the bios), 'aplay -l' still reports no soundcards found... ](*,) 

Anyone have further suggestions?

Thanks...

---

### Post by grumpymole on 2006-11-12
CCPhil,

The sound card is incorrectly detected as cs4610.  The step to blacklist this card is important to prevent this module from being loaded.  It should load the cs4236 module instead.  PM (this username at gmail.com) me if you still have a problem.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by king20878 on 2006-11-17
I can confirm that the instructions above work under Edgy.  If you are following the instructions above and still have trouble, I would recommend checking the quickboot option in the bios again and then initialize the bios.

Thanks for an excellent howto clembone!  :D

---

### Post by larryd85 on 2007-04-03
hey
thanks for this walkthrough
this is the only setup "guide" that i was able to understand

however becasue i didnt care about how messed up i made this computer i forgot what i have changed and stuff, and the sound still does not work

other options i have gone thru have involved downloading alsa drivers from the site, and installing them....... i had no idea how to install them so i did the steps leading up to that and added script to files i cant remember, and adding files here and not understanding this..... i was so confused....

so i am going to re-load ubuntu onto this POS and try it again...... hopefully it will work

now i have not tried to re-load ubuntu on here after i had put stuff on the HD.... is it possible to repair the OS without having to format..... (stupid question i know, andi havnt looked into it..... i just want to know if i have to back stuff up)

thanks again!
great instructions! too bad they didnt work for me...... yet!

---

