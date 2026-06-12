---
title: "fiesty too slow"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by romihim on 2007-07-11
firstly fiesty is taking a lot of time to boot up .
running too slow. nautilus takes at least 4-5 seconds to open .
same is the case with all the apps .
System monitor shows approx 100% usage for even small taks (even running system monitor sometime have  100% cpu usage)
windows xp works much faster than this with better graphics .........................
who says linux is fast :?:

---

### Post by ukripper on 2007-07-11
I do say and shout out loud, Linux is fast!

Sounds like you are running Feisty on IBM  x386 with 16MB RAM

---

### Post by rickycodie on 2007-07-11
can you post your system specs? if you have less then 256 ram then try damn small linux or puppy linux.
same if under a p2.

---

### Post by insomniacpyro on 2007-07-11
Are you running from the Live CD? If you are, this is why Fiesty is running slow. All the data you are trying to access has to come from your CD drive, which is horribly slow compared to your hard drive. If you install it on the other hand, you'll see the difference.

---

### Post by cybercur on 2007-07-11
As do I.  I find it odd that someone would come in here with the express intent of being flamed.  You don't provide any information on the computer you are running, or how you installed.  You just spout out stuff.  What was your question?

---

### Post by ukripper on 2007-07-11
Edit :
deleted

---

### Post by insane_alien on 2007-07-11
can you open up the system monitor and tell us what is using up all the cpu. then can you give us the specs of your computer.

if it is the former, we can probably help you.
if it is the latter then your hardware isn't good enough and you should try a lighter distro (fluxbuntu, puppylinux, Damn Small Linux etc.)

---

### Post by rickycodie on 2007-07-11
he's not going to post again. we've scared him off.

---

### Post by ukripper on 2007-07-11
Edit:

deleted again by me

---

### Post by Seisen on 2007-07-11
There is no need to be a jerk either, especially when somebody is a newb and they are asking a question.

---

### Post by ukripper on 2007-07-11
edit :
deleted

---

### Post by romihim on 2007-07-11
sry for the late reply ........i was just searching the ubuntu forums 
have not expected for such quick and angry replies

my comp specs .
P4 1.7ghz 
512 Mb ram
Running installed version of fiesty

---

### Post by Seisen on 2007-07-11
type **"top" **in the terminal and post what it says here.

---

### Post by romihim on 2007-07-11
@ukripper 
u r too emotional for linux 
I am just starting with linux ,not a geek like u r 
by ur comments u sound more like a jerk , in future plz refrain from using such kind of language 
i would have replied to the post if i had checked it before 

AND thanks Seisen

---

### Post by romihim on 2007-07-11
output of top command:-
----------------------------------------------------------------------------------------
 top - 20:18:20 up  4:47,  2 users,  load average: 0.81, 0.84, 1.07
Tasks: 101 total,   1 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.4%us,  5.0%sy,  0.0%ni, 85.5%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:    507864k total,   498772k used,     9092k free,     3404k buffers
Swap:   385520k total,   153224k used,   232296k free,    83092k cached

---

### Post by Seisen on 2007-07-11
It didn't list everything that was running? If it did post that.

---

### Post by romihim on 2007-07-11
top - 20:23:29 up  4:53,  2 users,  load average: 0.72, 0.82, 1.00
Tasks: 101 total,   4 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  3.3%sy,  0.0%ni, 86.4%id,  0.7%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    507864k total,   500412k used,     7452k free,     4772k buffers
Swap:   385520k total,   153224k used,   232296k free,    80472k cached
 Unknown command - try 'h' for help 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 4741 root      15   0  378m 101m 7856 R  6.3 20.4  17:53.50 Xorg                                                            
17470 himanshu  15   0 76328  17m  11m R  3.3  3.5   0:04.15 gnome-terminal                                                  
 9772 himanshu  15   0 11876 3960 3440 S  1.7  0.8   1:14.87 at-spi-registry                                                 
10567 himanshu  15   0  314m 131m  25m S  0.7 26.5  19:55.83 firefox-bin                                                     
 9847 himanshu  15   0 34368  20m 9216 S  0.3  4.1   1:16.07 geyes_applet2                                                   
16866 himanshu  15   0 83004  11m 4372 R  0.3  2.3   0:06.77 compiz.real                                                     
17498 himanshu  15   0  2316 1160  880 R  0.3  0.2   0:00.56 top                                                             
    1 root      18   0  2908 1768  480 S  0.0  0.3   0:01.62 init                                                            
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                     
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.42 events/0                                                        
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 khelper                                                         
    7 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                         
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.14 kblockd/0                                                       
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
  114 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod                                                         
  134 root      15   0     0    0    0 S  0.0  0.0   0:00.14 pdflush                                                         
  135 root      15   0     0    0    0 S  0.0  0.0   0:00.07 pdflush                                                         
  136 root      10  -5     0    0    0 S  0.0  0.0   0:01.40 kswapd0                                                         
  137 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
 1953 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
 1954 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
 2066 root      10  -5     0    0    0 S  0.0  0.0   0:03.48 ata/0                                                           
 2067 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
 2070 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
 2071 root      10  -5     0    0    0 S  0.0  0.0   0:10.64 scsi_eh_1                                                       
 2323 root      10  -5     0    0    0 S  0.0  0.0   0:05.00 kjournald                                                       
 2522 root      15  -4  2892  480  376 S  0.0  0.1   0:00.55 udevd                                                           
 3369 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused

---

### Post by kknd on 2007-07-11
Well, it is super fast here....

---

### Post by Alfdog on 2007-07-11
I have a similar machine

a p4 1.4ghz with 512ram (dell)

I too thought it was a little "slow" or "laggy" with both ubuntu and kubuntu.
I installed xubuntu on it and it runs better.  xubuntu just seems to be a better fit.
I also had an old scsi 10k rpm 9gb hard drive installed in the machine, then I just put an 80gb 7200rpm because their was no need for the scsi.  One thing is for sure, is that the bottleneck is definitely the processor.

good luck
alf

---

### Post by romihim on 2007-07-11
one more thing 
THERE HAS BEEN A SLIGHT INCREASE IN SPEED IN INSTALLED VERSION THAN LIVE CD 
BUT NOT MUCH AS EXPECTED 
ONLY A SLIGHT DIFFERENCE IN SPEED 

I AM DUAL BOOTING  WINXP AND UBUNTU FEISTY 
FEISTY IS INSTALLED ON EXTENDED PARTITION 
DOES HARD DISK PARTITION EFFECT THE SPEED 
SHOULD I POST MY HARD DISK  PARTITION STRUCTURE

---

### Post by romihim on 2007-07-11
So that mean its the max speed of ubuntu 
i have tried xubuntu on live cd and it does run faster but i prefer gnome(feisty)
Is not a way to tweak it to run faster ..........like stopping unnecessary processes 
like we do in XP ..........tweaking with registry 
and such kind of things

---

### Post by Seisen on 2007-07-11
[http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

There are other just google "speeding up Ubuntu"

---

### Post by romihim on 2007-07-11
thanks

---

### Post by rickycodie on 2007-07-11
you could try running

sudo apt-get autoclean

that might help, it's a directory cleaner.

thanks for giving us a second chance too, most of us are cool, but there's some d!cks.

---

### Post by moredhel on 2007-07-11
> @ukripper 
u r too emotional for linux 
I am just starting with linux ,not a geek like u r

firstly, you are new and are now saying who should and shouldn't use linux?

secondly you don't know if he is a geek, and while you are using text speech he is writing coherent sentences.


riiiiight.

But seriously, try out puppy linux, or zenwalk. Zenwalk I find feels much more like a full OS compared to puppy.

---

### Post by romihim on 2007-07-11
THIS IS WHAT I M GETTING

himanshu@himanshu-desktop:~$ sudo apt-get autoclean
Password:
Reading package lists... Done
Building dependency tree        
Reading state information... Done
himanshu@himanshu-desktop:~$ autoclean
bash: autoclean: command not found

---

### Post by orb9220 on 2007-07-11
> P4 1.7 Ghz , 512 Mb Ram 40 Gb hard disk ,**No Video Card** 

No Video card you mean you are using Onboard video of motherboard?
If so that is sharing your ram 512mb so for system you really only have 256mb-384mb or so.

Open a term and enter: ** lspci**  and post results here.

---

### Post by rickycodie on 2007-07-11
it must be 

sudo apt-get autoclean

as it affects your system, it must be sudo.

---

### Post by ukripper on 2007-07-11
Edit:

deleted by me

---

### Post by rickycodie on 2007-07-12
look your attitude is not condusive to a helpful environment. either stop or i'll report you ukripper. he was asking for help and you got offended, you didn't extend your understanding to his level, and see where he was at. the anger in here is generated by you. romihim, this is not a typical ubuntu user and he is not emulating the ubuntu spirit that we enjoy here so regularly. please do not base your experience on this thread. i will attest that these forums are a better place then demonstrated here.

---

### Post by twiceasworn on 2007-07-12
What are the specs of your video card?  I realize you said no video card, however there has to be something running the video for you to use the OS.  Is it onboard?  If it is, that is most likely the reason for the slowness.

---

### Post by rookshop on 2007-07-12
I just made the switch from XP and could not be happier. Even though I had a few problems that made me consider switching back, they were all sorted out thank to this great community.  :D

Oh, and I am using a 512MB RAM Lenovo R60 with 128MB shared video RAM and everything works fine. Much faster than XP.

---

### Post by romihim on 2007-07-12
Output of command lspci :-
---------------------------------------------------------------------------------------------
[I]himanshu@himanshu-desktop:~$  lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
01:01.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
himanshu@himanshu-desktop:~$ [/I]

---

### Post by romihim on 2007-07-12
In past couple of days i experimented a lot with ubuntu.searching the net ,trying all ur suggestions .Done quite a tweaking(especially with its look). Feeling  gr8 . 
Linux gives u so many options .

thanks guys

---

### Post by Big_Croc7 on 2007-07-12
Ubuntu should run fast on that hardware - I'm running it on an Athlon 850 and it works fine.  Have you enabled Compiz do you know?  That's the thing that gives you some fancy effects - it will really slow down your system, especailly without a dedicated graphics card.

---

### Post by romihim on 2007-07-12
compiz is enabled .

Thank u all guys for ur replys . Now i m getting used to ubuntu .doing some tweaks all the time .

its booting faster now:)

---

### Post by hackle577 on 2007-07-12
Yeah, all those Compiz effects will really bog down your box. Consider turning it off.

---

### Post by rickycodie on 2007-07-12
glad it's booting faster, i hope you love ubuntu, i do.

---

### Post by ukripper on 2007-07-12
> **rickycodie said:**
> look your attitude is not condusive to a helpful environment. either stop or i'll report you ukripper. he was asking for help and you got offended, you didn't extend your understanding to his level, and see where he was at. the anger in here is generated by you. romihim, this is not a typical ubuntu user and he is not emulating the ubuntu spirit that we enjoy here so regularly. please do not base your experience on this thread. i will attest that these forums are a better place then demonstrated here.

 I got offended certainly by the comparison which wasnt based on experience. For your information this wasnt anger, it was response to few windows  users who sometimes take linux for granted. You have no idea about ubuntu spirit. If you see how many users I have helped in forums you would be ashamed of yourself before telling me about ubuntu spirit. These forums are the best place to demonstrate ubuntu and linux spirit but if someone point finger at your something you consider dearly would you like it ? Would you say to him oh please insult my community and my family also as I am loving it? Shame on you mate for even bringing this up.

EDIT:

romihim, welldone mate I am so glad you are liking ubuntu. Apologies I didnt mean to be rude to you earlier and I have deleted my previous posts. It was just the comparison you made which I realised that I over-reacted thought you to be another troll. if you have any problems just don hesitate and post in forum or send me personal message I would be delighted to help you out. Sorry again for misunderstanding caused by me

---

### Post by ukripper on 2007-07-12
> **romihim said:**
> compiz is enabled .

Thank u all guys for ur replys . Now i m getting used to ubuntu .doing some tweaks all the time .

its booting faster now:)

Have you tried beryl yet?

---

### Post by rickycodie on 2007-07-12
@ ukripper
thank you.

---

### Post by romihim on 2007-07-13
> **ukripper said:**
> Have you tried beryl yet?

i did install beryl (with synaptic) but it kept on hanging ,really was not able to use it .So removed it .
Now only the default compiz(options which come with fiesty) r enabled .

---

### Post by ukripper on 2007-07-13
Compiz is still good and also take less resources. 

If you want something for monitoring there is a great light weight monitoring tool which gets forked to your desktop and monitors how you want it to - It is called Conky and takes very less resources.

here is little Howto for that if are interested -
[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky)

You can take ideas or even copy my conkyrc which i have posted on here - [http://ubuntuforums.org/showthread.php?t=281865&page=31](http://ubuntuforums.org/showthread.php?t=281865&page=31)

have fun

---

### Post by romihim on 2007-07-13
@ukripper
i installed conky using sudo apt-get conky
its running fine but probs :-
first as i have to run it using terminal (isnt der a direct way)
second its not as good looking as in ur deski. 
also its not transparent and i think in its current form its not that good to be used ...............

---

### Post by romihim on 2007-07-13
now experimenting with the script in .conkyrc .. 
when i run conky there's text written "MPD not responding" .
is it wat was making my system slow
and most of the time the cpu usage is quite high

---

### Post by Carlkiwi on 2007-07-13
When I first loaded Ubuntu I also found it to be very slow and clunky. However, once I loaded all the updates it gained speed and lost its clunkiness (I think thats a real word).

---

### Post by ukripper on 2007-07-13
try reinstalling conky following the guide I pointed earlier in the link.

Can you post screenshot after running conky so that i can see what exactly is happening with it.

Cheers

---

### Post by crimesaucer on 2007-07-13
Conky info: 

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)


This one is for custom .conkyrc files and screenshots of what they look like (EDIT- I guess it's already been linked): [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)



This is an easy guide for Compiz Fusion: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by crimesaucer on 2007-07-13
> **romihim said:**
> now experimenting with the script in .conkyrc .. 
when i run conky there's text written "MPD not responding" .
is it wat was making my system slow
and most of the time the cpu usage is quite high

You have a variable set displaying Music Player Daemon: [http://www.musicpd.org/](http://www.musicpd.org/)


...which you are not using probably.


If you read the Conky info links, especially the Conky Variables, you will be able to write your own .conkyrc...also, there are some good examples on the Ubuntu .conkyrc thread, and here also: [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by romihim on 2007-07-13
> **ukripper said:**
> try reinstalling conky following the guide I pointed earlier in the link.

Can you post screenshot after running conky so that i can see what exactly is happening with it.

Cheers

i m posting the screenshot of conky in its original form(i.e. with .conkyrc file which came with installation)

the only thing to notice here is "mpd not responding "

i have tried different conky cofig files and now have a better one

[[IMG]http://img58.imageshack.us/img58/7098/screenshotvr7.th.png[/IMG]](http://img58.imageshack.us/my.php?image=screenshotvr7.png)

---

### Post by romihim on 2007-07-13
[QUOTE=Carlkiwi;3014926]When I first loaded Ubuntu I also found it to be very slow and clunky. However, once I loaded all the updates it gained speed and lost its clunkiness (I think thats a real word).[/QUOTE

May be u r rite .
its running better with all the updates

---

### Post by romihim on 2007-07-13
> **ukripper said:**
> Compiz is still good and also take less resources. 

If you want something for monitoring there is a great light weight monitoring tool which gets forked to your desktop and monitors how you want it to - It is called Conky and takes very less resources.

here is little Howto for that if are interested -
[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky)

You can take ideas or even copy my conkyrc which i have posted on here - [http://ubuntuforums.org/showthread.php?t=281865&page=31](http://ubuntuforums.org/showthread.php?t=281865&page=31)

have fun


Could u plz mail me the wallpaper u used in ur deski . 
for the screen shot
[http://ubuntuforums.org/attachment.php?attachmentid=36646&d=1182980021](http://ubuntuforums.org/attachment.php?attachmentid=36646&d=1182980021)
and how did u get that vista looking panel . is it with some theme or any thing else .
i m bored with this rectangular panel .

---

### Post by crimesaucer on 2007-07-13
> **romihim said:**
> i m posting the screenshot of conky in its original form(i.e. with .conkyrc file which came with installation)

the only thing to notice here is "mpd not responding "

i have tried different conky cofig files and now have a better one

[[IMG]http://img58.imageshack.us/img58/7098/screenshotvr7.th.png[/IMG]](http://img58.imageshack.us/my.php?image=screenshotvr7.png)

mpd is Music Player Daemon.

Do you have Music Player Daemon installed?

If you read the 4 links I gave you, they all explain Conky and the .conkyrc....and they even give examples with screenshots.

---

### Post by crimesaucer on 2007-07-13
This also is a helpful link for Conky: [http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

but don't use 

```
${execi 60 wmctrl -a conky}
```

....it will conflict with the Beryl/Compiz window manager.


That guide may be a little old (it's for 1.4.2), but it's still good to learn somethings about Conky 1.4.5.


You also might want to try a different .conkyrc...one that doesn't use a separate window or mpd.

---

### Post by romihim on 2007-07-13
> **crimesaucer said:**
> mpd is Music Player Daemon.

Do you have Music Player Daemon installed?

If you read the 4 links I gave you, they all explain Conky and the .conkyrc....and they even give examples with screenshots.

thanks for the links .dey were gr8 .

I dont have MPD installed .

---

### Post by ukripper on 2007-07-13
> **romihim said:**
> Could u plz mail me the wallpaper u used in ur deski . 
for the screen shot
[http://ubuntuforums.org/attachment.php?attachmentid=36646&d=1182980021](http://ubuntuforums.org/attachment.php?attachmentid=36646&d=1182980021)
and how did u get that vista looking panel . is it with some theme or any thing else .
i m bored with this rectangular panel .

Here is wallpaper as attached below and yes, it is vista theme you can go to - [http://gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570](http://gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570)
for Linsta-not-Vista look.

---

### Post by crimesaucer on 2007-07-13
> **romihim said:**
> thanks for the links .dey were gr8 .

I dont have MPD installed .


Then if you check your .conkyrc, you will want to edit-out the lines of code that have any of these Variables in it:

```

mpd_artist 		 Artist in current MPD song must be enabled at compile
mpd_album 		Album in current MPD song
mpd_bar 	(height),(width) 	Bar of mpd's progress
mpd_bitrate 		Bitrate of current song
mpd_status 		Playing, stopped, et cetera.
mpd_title 		Title of current MPD song
mpd_vol 		MPD's volume
mpd_elapsed 		Song's elapsed time
mpd_length 		Song's length
mpd_percent 		Percent of song's progress
mpd_random 		Random status (On/Off)
mpd_repeat 		Repeat status (On/Off)
mpd_track 		Prints the MPD track field
mpd_name 		Prints the MPD name field
mpd_file 		Prints the file name of the current MPD song
mpd_smart 		Prints the song name in either the form "artist - title" or file name, depending on whats available

```


...I also suggest a completely different .conkyrc to start with.

---

### Post by ukripper on 2007-07-13
crimesaucer is right you would need to try different conkyrc which hasn´t got MPD try mine or someone else in the links given above.

---

### Post by crimesaucer on 2007-07-13
I'll also link you to these 2 pages that have Variable settings for your time and date:

[http://gentoo-wiki.com/index.php?title=MAN_strftime&printable=yes](http://gentoo-wiki.com/index.php?title=MAN_strftime&printable=yes)

[http://www.hmug.org/man/3/strftime.php](http://www.hmug.org/man/3/strftime.php)


....this way you can have the day of the week, or the month written out or abbreviated, plus you can have your time show in am/pm and in different ways.


have fun, I love writing my own .conkyrc, this is mine with a custom time/date: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22a.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22a.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22a-1.png[/IMG]

---

### Post by romihim on 2007-07-13
@UKRIPPER 
Using ur .conkyrc file . but der r some  prob with it :-
1) in terminal its constantly giving .signal.sh not found
2)I think u use wireless connection . i have a wired connection so it is not showing any internet connection speed

the message in the terminal :-

> Conky: statfs '/media/usbdisk': No such file or directory
Conky: statfs '/media/usbdisk': No such file or directory
connect: Connection refused
python: can't open file '/home/ash/.countdown.py': [Errno 2] No such file or directory
connect: Connection refused
sh: /home/ash/.signal.sh: not found
Conky: desktop window (1800059) is subwindow of root window (4d)
Conky: window type - override
Conky: drawing to created window (5200002)
Conky: failed to set up double buffer
Conky: drawing to single buffer
connect: Connection refused
connect: Connection refused
sh: /home/ash/.signal.sh: not found
connect: Connection refused
connect: Connection refused
mys deski:-
[[IMG]http://img146.imageshack.us/img146/8314/screenshot1ac9.th.png[/IMG]](http://img146.imageshack.us/my.php?image=screenshot1ac9.png)

---

### Post by ukripper on 2007-07-14
> **romihim said:**
> @UKRIPPER 
Using ur .conkyrc file . but der r some  prob with it :-
1) in terminal its constantly giving .signal.sh not found
2)I think u use wireless connection . i have a wired connection so it is not showing any internet connection speed

the message in the terminal :-


mys deski:-
[[IMG]http://img146.imageshack.us/img146/8314/screenshot1ac9.th.png[/IMG]](http://img146.imageshack.us/my.php?image=screenshot1ac9.png)

1)Completely get rid of that .signal.sh which is calling shell script, I wrote that script to make conky detect my wireless signal it is linked  to tthe shell  script stored in my home directory so thats why it wont work on yours. Just delete the whole line for .signal.sh

2)In conkyrc replace all entries from ath0 to eth0 that will detect your wired connection

3) Also I can see it is trying to detect your hdd temp for that you need to install hddtemp utility just type follwing command in terminal:
```
sudo apt-get install hddtemp
```
then conky will detect your hdd temperature which is coming up as N/A at the moment

---

