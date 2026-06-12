---
title: "Unable to boot to login screen"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by thecow on 2007-11-24
I recently tried to load on an add-on for pidgin which allows for secure communications.  I tried to run ./configure on it but it said that I needed various libraries, such as libotr, cairo, libjpg, libpng and such.  I downloaded all of the dependencies and eventualy got them all compiled and installed with 'make install' however at the very end my computer stopped opening up files so I tried to log out but  after I clicked log out my computer just hung for a while.  I restarted it manually, and it started up reasonably until it was about to go to the normal login screen.  The login screen never comes up, instead I get a black window with a spinning cursor.  I have no idea why the OS should be messed up by just installing these libraries.  I am not sure if the name libjpg and libpng are correct, but it was something similar to that.  I can only think that somehow installing these libraries over wrote some other library ubuntu uses and so now it won't display things properly.  THe problem with this theory is that it displays the ubuntu loading bar at bootup properly, it just never boots into the login screen.  

I can still get into the command line through grub.  But frankly I do not know enough to seriously tinker with it and try to figure out what to do. I read on a related thread that the command startx might have it boot into ubuntu however I have not been able to try that yet as I am not at home.  What I do now is just type 'exit' and it exits the command line and tries to boot into ubuntu normally but it of course hangs.
I also read in a thread to try this "sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx"

Does anyone have any suggestions?  I am at school right now as I need to work on a project, but I will be heading back in the near future to try and fix the problem.
Thank you

---

### Post by elctb on 2007-11-24
I would try to find out where linux is hanging. When ubuntu is booting up, as soon as you see the ubuntu logo and progress bar type "ctrl-alt-f1" to see what's going on. Make note of what's hanging or any error messages. It should be relatively easy to fix once you know what's wrong.

---

### Post by thecow on 2007-11-24
When I push alt-ctrl-F4 the last item it shows is "Running local boot scripts (/etc/rc.local)"  Also when I use startx it attempts to boot into the video screen then comes back to the command prompt.  I do not know what the error is however.

---

### Post by thecow on 2007-11-24
When the computer hangs with the spinning cursor, if I push alt-ctrl-f4 it takes me to the command prompt and asks me for my user name.  So I can login that way, but it is only a command line interface, when I try 'startx' it tells me it is already running.  So  really the only problem is the black screen with the spinning cursor right before the login screen.

---

### Post by elctb on 2007-11-24
OK. Try this once you login via the terminal:

. sudo pkill X
  This command will kill the X server that's already running.

. Then try startx again.

Post any error messages you get.

Also, just to make sure there's still room on your hard drive type the command "df" and make sure the partition mounted on root "/" is not full.

---

### Post by thecow on 2007-11-25
How do I tell what the error messages are?  When I am in the command line and type startx, it attempts to load into the X window system, but then goes to the familiar black background with spinning cursor page.  I have to hit ctr-alt-f4 to get back into the command line.  When I return it gives me messages but none have errors.  I get one warning near the top of the screen

"The XKEYBOARD keymap compiler (xkbcomp) reports:
>Warning:                Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                              Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server"

After this it gives me messages such as as "Synaptics DeviceInit called" and "finished PLL2" "Restore TV PLL"

Stuff like that until the end where it says 


"Synaptics DeviceOff called
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing"

And thats all it gives me, I cant scroll up the screen to see what the real errors are.  As I recall I think there is a log that stores the error messages but I cannot seem to remember the name or find it by searching.  I am studying in France at the moment so we probably have a 6-9 hour time difference, so I'll bump this in a while.

---

### Post by jingo811 on 2007-11-25
I don't know how to undo what you've done when doing the Pidgin thing but maybe you can solve it by re-installing the Desktop manager with this in Bash mode (text mode).

```
sudo apt-get install gdm ubuntu-desktop
```

You should see this after your Ubuntu has finished loading everything.  Then just login with your user/pass and do the above commands to install GDM and Desktop.
> 
Ubuntu 7.04 ubuntu tty1

ubuntu login:

---

### Post by thecow on 2007-11-25
I tried running that and this is what I get at the output
"Reading package lists... Done
Building dependency tree
Reading state information... Done
gdm is already the newest version.
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded"

Also I am at the library right now, and my laptop does not have internet access.  I don't know how to  use the wireless in a command line setting.

Also, I am using 7.10

---

### Post by jingo811 on 2007-11-25
Hmm....then you should try those commands when you have access at home.  Setting up wireless without GUI for a newbie is like climbing Mount Everest with nothing but Hawaii clothes and sandals.

The apt-get command requires Internet access.  Unless you have your Gutsy 7.10 CD at hand then you could probably do some trix  and install from the CD instead.
Also when you have Internet access with a UTP network cable or something like that.  First remove the Desktop then install again.

```
sudo apt-get remove gdm ubuntu-desktop
```
```
sudo apt-get install gdm ubuntu-desktop
```

---

### Post by thecow on 2007-11-25
Well, if I had internet access do you think it would download it?  It sounds like it wont do anything because I already have the newest versions.  Also do you think that ubuntu just automatically has me on the internet, I know there is an open wireless channel here.  

Do you have any other suggestions?  It would really help me out, Im working on a presentation, but these computers have open office 1.0 and the powerpoint aspect of it is real bad.  So Id appreciate of course being able to use my nice 1.3 at home.  Do you know how I can find out the actual error messages when I try the 'startx' command?

---

### Post by jingo811 on 2007-11-25
> **thecow said:**
> Well, if I had internet access do you think it would download it?  It sounds like it wont do anything because I already have the newest versions.  Also do you think that ubuntu just automatically has me on the internet, I know there is an open wireless channel here.  


Well you installed Pidgin through the Internet and I'm suspecting it messed up some dependencies for your Desktop and GDM.  Apt-get don't usually give much info if something is broken removing it and re-installing it only takes 1-3 minutes.  I would try it if I didn't know what the problem was.

Regarding connecting your wireless to your library did you have wireless access to your library before all this happened?  Either way plugging in a network cable to a router or modem is the easiest way I think.

> **thecow said:**
> 
Do you have any other suggestions?  It would really help me out, Im working on a presentation, but these computers have open office 1.0 and the powerpoint aspect of it is real bad.  So Id appreciate of course being able to use my nice 1.3 at home.  Do you know how I can find out the actual error messages when I try the 'startx' command?

Reading logs might be fun, but I'm not sure many ppl in here can give you much practical solutions with you pasting a long list of error logs.  Anyway if you need to pinpoint the logs here's a guide.
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

If you ask me it would be much quicker to work in Open Office 1.0 right now instead of trying to solve this.  Then convert things to 1.3 and adjust a little with your working PC at home.  You're wasting valuable time by waiting for answers to your wireless and login problem.  Me thinks.

---

### Post by thecow on 2007-11-25
Yea that sounds reasonable.  The only problem is that I use a proxy to connect to the internet at home.  However, I think when I last was using my computer I had the proxy turned off in the "Preferences->Network Proxy" Section.  So even if I plug my computer in, I am not sure it will connect to the internet.  Is there some way I can merely test to see if my computer is connected to the internet before I delete the Desktop manager?

---

### Post by jingo811 on 2007-11-25
If you already had wireless setup for Ubuntu you should see something in here.
> gara@sama:~$** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

gara@sama:~$ 


If you use UTP network cable to connect to a router via your Ethernet NIC you should get an ip address in the highlighted row.
> 
gara@sama:~$** ifconfig**
eth0      Link encap:Ethernet  HWaddr 30:10:7B:7E:91:1F  
       **   inet addr:192.168.0.5  **Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe89:210d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:104716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:125977154 (120.1 MiB)  TX bytes:5949960 (5.6 MiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


If no ip given to you try this.
> dhclient eth0


Ping the forums and press **Ctrl+C** after 5 pings or so to jump back to the terminal.
> 
gara@sama:~$ **ping ubuntuforums.org**
PING ubuntuforums.org (91.189.94.186) 56(84) bytes of data.
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=1 ttl=48 time=52.4 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=2 ttl=48 time=50.9 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=3 ttl=48 time=55.6 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=4 ttl=48 time=56.5 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=5 ttl=48 time=53.1 ms

--- ubuntuforums.org ping statistics ---
5 packets transmitted, 5 received, **0% packet loss**, time 4000ms
rtt min/avg/max/mdev = 50.995/53.750/56.546/2.069 ms
gara@sama:~$ 


---

### Post by thecow on 2007-11-25
Well I looked at the Xorg.0.log to try and find errors with the 'startx' command.
 
Obviously I canot post the whole thing, as it would be absurd, so just going through it I find the following things:

"(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24"
... so forth  until 0x32

"(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so"
(II)  GLX: Initialized DRI GL provider for screen 0
(II) RADEON(o): Setting screen physical size to 444 x 277"

these are the last lines

"enable montype: 2
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
disable montype: 2
(II) Radeon(0): RADEONRestoreMemMapREgisters() :
(II) RADEON(0): MC_FB_LOCATION  :  0xd7ffd000
(II) RADEON(0):  MC_AGP_LOCATION  : 0x003f0000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV"

So honestly it seems like its running fine until something shuts it down.  I can only assume what is shutting it down is when I push alt-ctrl-f4.  Which means it might be something not to do with the windows manager at all, but something that is stopping ubuntu from going into the login screen.  At that point I can't imagine what to do.

---

### Post by jingo811 on 2007-11-25
Sorry wrong number :)

---

### Post by thecow on 2007-11-25
Well I relieved a nearby computer of its ethernet cable and plugged it into my laptop.  When I run ifconfig I get this:

"eth1       Link encap:Ethernet   HWaddr 00:15:00:10:BC:EF
                UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                RX packets: 759 errors: 0 dropped: 0 overruns:0 frame:0
                TX packets:74 errors:0 dropped:0 overruns:0 carrier:1
                collisions:0 txqueuelen:1000
                RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)


eth1:avah Link encap: Ethernet   HWaddr 00:15:10:BC:EF
                 inet addr:169.254.7.225  Bcast: 169.254.255.255 Mask:255.255.0.0
                  UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
                  Interrupt:17 Base address:0x8000 Memory:fe9ff000-fe9ffff

lo             Link encap:Local loopback
                inet addr:127.0.0.1  Mask:255.0.0.0
                UP LOOPBACK RUNNING MTU:16436 Metric:1
                 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:0
               RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
"


When I try to run ping ubuntuforums.org it gives me "ping: unkown host ubuntuforums.org"

So I gather im not connected

---

### Post by jingo811 on 2007-11-25
Run this to obtain an ip address for your laptop.
```
sudo dhclient eth1
```

Then check again with this.
```
sudo ifconfig
```

---

### Post by thecow on 2007-11-25
Alright well Im back at home, and I got the laptop online.  So now I am going to try and delete, install those programs as you said earlier.  If that doesnt work is there any way just delete the entire graphical aspect of it and reinstall it?

---

### Post by thecow on 2007-11-25
Well I tried as you said, and when i restarted X using 'startx' it tried to load then crashed and went back into the command line mode.  It gave me a new error which is "getDrawableInfo failed to look up window"

---

### Post by jingo811 on 2007-11-25
Did you do it in this sequence?

[LIST]
[*]sudo apt-get remove gdm ubuntu-desktop
[*]sudo apt-get install gdm ubuntu-desktop
[*]startx
[/LIST]

Problems beyond this is out of my competence.
but maybe if you have a backup of your Xorg.conf file maybe you can overwrite the newest version with an older Xorg.conf backup.

Do this in terminal.  And paste the results!
gara@sama:~$ **cd /etc/X11**
gara@sama:/etc/X11$** ls | grep xorg**

---

### Post by thecow on 2007-11-25
Yea I did it in that order, I also tried it with xorg and gnome.  it said gnome wasnt installed so I tried to instsall it, but that still didnt do anything.

Anyways the output I get is
"xorg.conf
 xorg.conf~
 XORG.CONF.20071124203812
xorg.conf.20071124203925
xorg.conf.20071124204449
xorg.conf.fglrx-0
xorg.conf.original-0"

---

### Post by jingo811 on 2007-11-25
If I'm not mistaken this is GNOME.
sudo apt-get install gdm ubuntu-desktop

Anyhow I'm thinking this.  Take the oldest xorg.conf file in your system and cp that in order to overwrite your standard xorg.conf file.

> gara@sama:~$ **cd /etc/X11**
gara@sama:/etc/X11$ **ls -l | grep xorg**
-rw-r--r-- 1 root root  3534 2007-11-01 14:03 xorg.conf
-rw-r--r-- 1 root root  3425 2007-10-31 23:21 xorg.conf~
-rw-r--r-- 1 root root  3496 2007-10-31 23:19 xorg.conf.20071031231935
-rw-r--r-- 1 root root  3496 2007-10-31 23:13 xorg.conf_backup
gara@sama:/etc/X11$ 

I my case I would do something like this and then reboot the PC.  Use TAB to autocomplete filenames so you don't mistype any long file names.
```
sudo cp xorg.conf_backup xorg.conf
```
Then do this to restart your PC.
```
sudo init 6
```

See what happens.

---

### Post by thecow on 2007-11-25
I tried all the other xorg.conf files and none of them work.  Most of them give me errors telling me that the modules 'type1' and 'fglrx' do not exist.  fglrx is the driver for my video card, so how do I redownload this?

---

### Post by jingo811 on 2007-11-25
I've never used fglrx for my graphics so I don't know.  I hope you made a separate partition for your /home.  Because all I can think of at this stage is delete Ubuntu partition and Install it fresh again and then try to keep away from that Pidgin module you messed with earlier.

---

### Post by thecow on 2007-11-25
Ha I was thinking the same thing.  The problem is I need to get the files off the computer.  If there is someway to burn data cd's from the command line, which I assume there is, Ill just burn a copy of my files then load on a new version of linux.  Honestly I doubt Ill use Ubuntu again, but it was fun while it lasted.  I was thinking of trying Enlightenment as the windows manager to see how it is.

---

### Post by jingo811 on 2007-11-25
Then you better make a new thread asking about how to burn data CDs from terminal.  I think it will get noticed by ppl quicker that way.  Rather than having them read through all the problems discussed so far.  Good luck!

---

### Post by co0lingFir3 on 2007-12-26
Hey guys!
I have the same annoying problem as thecow. I wanted to compile gnomad2 myself and installed more or less the same libraries as thecow did.
The issue seems really to have their roots there...
Any updates on solving the problem?
greets

---

