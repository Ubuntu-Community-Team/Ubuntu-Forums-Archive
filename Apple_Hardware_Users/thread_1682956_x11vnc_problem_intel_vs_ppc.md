---
title: "x11vnc problem intel vs ppc"
date: 2011-02-06
forum: Apple Hardware Users
---

### Post by rezwits on 2011-02-06
Hi,

I have two clean installs of Ubuntu.  One install is a clean install of Ubuntu on an amd64 system, 10.04.  Then another clean install on a G4 ppc system of 10.04.  Immediately after install with no configurations, custom or otherwise, I proceeded to install x11vnc following these instructions:

[http://ubuntuforums.org/showthread.php?t=911887&page=1](http://ubuntuforums.org/showthread.php?t=911887&page=1)

I use my Remote Desktop Application 3.4 on my third Mac under 10.5.8.  I open up Remote Desktop Admin and connect to the Ubuntu amd64 via the VNC, they both show a status of VNC Available, the amd64 connects with no problem, but ppc can't connect.  I have checked for a firewall on the ppc and there isn't one present.

I did a complete re-install of the ppc and still the same "can't connect".

There has to be something different about the ppc install vs the x86 amd64 install...

The ppc just won't connect, but the amd64 will...

Any suggestions would be greatful...  Thanks and off to the SuperBowl

Laters...

---

### Post by krunge on 2011-02-07
Can you attach an x11vnc logfile (-o option) for the failing ppc case?

---

### Post by fremantle on 2011-02-08
what version of x11vnc are u using. i generally compile from source and it worked for me

---

### Post by rezwits on 2011-02-08
Here are my log files, they seem to be reporting a problem with the password file saying it can't be read.  In ran the same setup on another PPC G4 using Fedora 12, and same problem.

The first machine is boba a G4 running Ubuntu 10.04 PPC
The second machine is deathstar2 a Mac Pro running Ubuntu 10.04.1 amd64
The third added machine is dengar a G4 running Fedora 12 PPC

The ppc seem to be having problems with the .pass file being used...

[ATTACH]183049[/ATTACH]

[ATTACH]183048[/ATTACH]

[ATTACH]183050[/ATTACH]

I tried deleting the .pass file and re-creating it but that doesn't seem to work.  Thanks for your time in this matter.


A side note, I tried not using the x11vnc via startup and tried starting it from the command line using -nopw option with barebones commands and could not get one connection.

---

### Post by krunge on 2011-02-09
You don't seem to be being careful, i.e. "/etc/v11vnc.pass" one time and "/etc/x11vnc.pass" the two other times.

Of course if the file doesn't exist trying to read it will fail. Also if the user running x11vnc does not have the permissions to read the file it will fail (e.g. if /etc/x11vnc.pass is only readable by root, but x11vnc is run by some other user.)  I assume you know how to correct these.

I think you need to tell us exactly how you created those password files.

BTW, "-nopw" stands for "no password warning". So it just skips printing out a warning if you are not using a password; adding "-nopw" to the cmdline will have no effect besides skipping the warning.

I suggest trying without the '-rfbauth' option (i.e. no password protection.)  Paste into this thread the entire x11vnc cmd you use for that.  If that fails for you, include the -o logfile output for that case.

---

### Post by rezwits on 2011-02-09
Hi and thanks for helping me with this.

I setup the Fedora 12 PPC install just to check really quick if it was a PPC issue or not and I went too fast.  I changed the v11vnc.pass arg to what it should be x11vnc.pass and I can confirm that the Fedora 12 on PPC x11vnc works like it should.  That's why I tried it and was hoping it would work to narrow this down.

So it must be an Ubuntu PPC x11vnc problem...

I have tried:

x11vnc -safer -nopw -forever -display :0 -rfbport 5900 

and when I try to connect it sits in my Apple Remote Desktop window saying "Connection to "bobau32.codesetters.com" and sits there and the live log stops at:

cutbuffer_send: no send: uninitialized clients

then after a while:

Battling with something for -norepeat!! (0 resets left)

I have tried also different -rfbversion 3.3 from a tip from another thread that didn't work.

I don't know what this could be...  I will keep trying other things


I will get more detail in a bit...

here is a clear and concise line:

x11vnc -safer -forever -display :0 -rfbport 5900

the I try to connect and it sits and stop at:

cutbuffer_send: no send: uninitialized clients

then after a while:

Battling with something for -norepeat!! (1 resets left)

then I try:

x11vnc -safer -forever -o /tmp/x11vnc.log -display :0 -rfbport 5900

to send you a log... :)

can't send the log in here for some reason next post

---

### Post by rezwits on 2011-02-09
Log file for boba

[ATTACH]183060[/ATTACH]

Thanks again...

---

### Post by krunge on 2011-02-09
Try:

```

x11vnc -safer -forever -o /tmp/x11vnc.log -display :0 -rfbport 5900 -rfbversion 3.3

```
connect again and then attach the log file.

So does everything work fine if you use on MacOSX Chicken of the VNC or SSVNC as the viewer?

BTW, I can't see any reason for this to differ between Linux/ppc and Linux/amd64, etc.  So if you see a difference on Linux arch I think you are making some mistake and should look into that.

---

### Post by rezwits on 2011-02-09
HI again,

Well I tried the command line verbatim and chicken of the vnc disconnected instantly or refused I should say, the JollyVNC got connection closed, and the Apple Remote Desktop got connection failed

DISREGARD THIS LOG, I forgot to put a '-' in front of rfbport

here is the log...

[ATTACH]183102[/ATTACH]

I don't what say because it's really baffling.  The reason I say that is because I did a full format of the partition and then installed ubuntu then proceeded to the x11vnc lines so I could do a DD backup right after I got it setup.  I did the other two systems the same way except the Fedora 12 PPC, I setup that as ldap auth for user logins not the x11vnc, then it sat for a week and then did x11vnc yesterday posted the log then you corrected me then I fixed it then it worked.  It's just like ugh how can a clean install and the same instructions not work twice.  Because this is the 2nd clean install on this machine and immediate try... puzzling...

Thanks and 3.7 version didn't work either those along with 3.3 immediately refuse

oh I as a side note, I did enable thru the System -> Preferences -> Remote Desktop and turn that on that works no problem thru port 5900 ...

---

### Post by rezwits on 2011-02-09
Hate to reply to my own thread but that last log file was bogus...  This is accurate

I tried Apple Remote Desktop first 1 time, then JollyFastVNC 1 time, then Chicken the remaining times.  Chicken said Unknown authType 16777216

So I don't know, the command line used was:

x11vnc -safer -forever -o /tmp/x11vnc.log -display -rfbport 5900 -rfbversion 3.3

that is a copy from my terminal and pasted into here...

Thanks

---

### Post by rezwits on 2011-02-09
Forgot to attach log file again, I am just going to fast, this is just a crazy stumbling block in my whole setup :P  

[ATTACH]183111[/ATTACH]

damn

Chicken also reports with version 3.7 and 3.8 , The server closed the connection

As and addition to this, I tried another option adding -avahi, and the server shows up on my SHARED list on my mac for zero config items, and its says bobau32:0  I try to connect with the built in Screen Sharing app, and it sits and tries to continually connect till I cancel it...

strange

I also tried recreating the pass file, I gave it 775 perms and it didn't complain when trying to use the pass file.  Side note again Chicken and Jollyfast are using rfb 3.8, ARD and Screen Sharing app are using rfb 3.889

umm...

new note:

I tried building from source code but I couldn't find ppc linux source code, I found ppc darwin... bummer

the amd64 is running 0.9.9 the ppc is running 0.9.9-1

another note:

I have also tried connecting from my Mac Pro, and my laptop, in addition to dengar the G4 that has Fedora also installed but not running because it is running 10.5.8 Mac OS X, what I keep trying to connect from 192.168.1.120...

---

### Post by yahway666 on 2011-02-09
Have you tried using teamviewer instead? Teamviewer can connect different OSs easily. So for instance, windows to mac works just fine. Never tried it with linux before but it could be worth a shot.

Heres a link to teamviewer 
[http://www.teamviewer.com/en/index.aspx](http://www.teamviewer.com/en/index.aspx)

---

### Post by rezwits on 2011-02-09
I tried team viewer on windows but I didn't really like how it worked.  My environment is I have 16 different OS setups (x64, x86, ppc, etc) on 6 different triple boot machines some as VMs all of them are control-able from my 1 apple remote desktop window, all listed by there hostname, just for software development testing.  I don't really want to use team viewer just for this one simple case.  I tried using a default menu option under System -> Preferences -> Remote Desktop, and I can get that to work, but it has it's problems of having to auto-login, there is another option I could use but it has it's problems too, vnc4server...  

I just really love the simplicity of x11vnc ... it's how vnc apps should work...

Thanks

---

### Post by rezwits on 2011-02-10
Well I couldn't take it anymore.  So I went to:

[https://launchpad.net/ubuntu/+source/x11vnc/0.9.10-1](https://launchpad.net/ubuntu/+source/x11vnc/0.9.10-1)

and downloaded the original source installed the openssl and jpeg library and compiled/built it

I fired it up and on the first go it worked with pass file.

Then I setup the startup and it didn't work... doh... changed the the path to /usr/local/bin/x11vnc

then it worked on startup how it's supposed to...

oh well I guess this system is just weird...

strange...

Thanks for your help karl and others

I just can't spend anymore more days worrying about "the system being tarnish free" and not running the version that comes with the repository... it does bug me a little but I got it working with 0.9.10 so oh well

Thanks again

---

### Post by rezwits on 2011-02-10
New side note for karl if you come back...

How come in Fedora PPC/x86/x64 in my vnc app, doesn't matter which one, the screen size does not update and cannot be greater than 800 x 600.

But Ubuntu PPC/x86/amd64 in any of my vnc apps, the screen updates and can be any size... ??

wondering Please let me know I would love to solve this new problem.  I guess I should just over to Fedora Forums and post this :P

here is the new link...

[http://forums.fedoraforum.org/showthread.php?p=1442704#post1442704](http://forums.fedoraforum.org/showthread.php?p=1442704#post1442704)

Thanks

---

### Post by krunge on 2011-02-10
> **rezwits said:**
> 
then it worked on startup how it's supposed to...

oh well I guess this system is just weird...

strange...

Maybe your system is weird or maybe there is a build bug for ppc that you might want to report.

---

### Post by rezwits on 2011-02-10
I have another g4 same specs except different ram and hds, I can install ubuntu on it just to see but I don't know... we'll see in the future when I get a break...

I don't want to tear up the other G4 (1.25 dual) with Fedora on it...  cause my gut is telling me honestly the only thing is that the Ubuntu G4 has 2 ram chips that are different manufacturer, but it boots it sleeps it starts it stops...

I'll look into getting the other system Jango a G4 into using ubuntu.  But I feel like if I pulled HDs from Boba and put them in Jango how could it be different...??  Jango my other G4 , they are both G4 533 duals, that are basically the same model from apple except for guts (dvds, hds, ram, video cards) so I don't know...

future tests...but I think you might be right.

I am going to update my repositories to bleeding edge so I can sync up my Git version, have to anyway.  I think if get the bleeding edge version of x11vnc install (meerkat) via that repository it would work... just like it should again...  which will make it somewhat normal...

Thanks and if and after I do further investigating I will report the bug if it's the same on both systems...

---

### Post by krunge on 2011-02-11
> **rezwits said:**
> New side note for karl if you come back...

How come in Fedora PPC/x86/x64 in my vnc app, doesn't matter which one, the screen size does not update and cannot be greater than 800 x 600.

But Ubuntu PPC/x86/amd64 in any of my vnc apps, the screen updates and can be any size... ??

Please understand that in its basic operation x11vnc has no control over the X server's screen size.  x11vnc simply attaches to the existing X server process and exports the screen at whatever size it is.

So the 800x600 has nothing to do with x11vnc.  It has to do with your X server configuration (usually /etc/X11/xorg.conf)

I can't remember what you doing.  You are running an X server  on the physical graphics hardware, right?  Sometimes if a monitor is not attached to the graphics display hardware the display resolution will be a small, safe one.  These forums have some discussion on this ('x11vnc+headless')

(ASIDE: x11vnc has a '-create' mode where it will start up a virtual X server, Xvfb, (xvfb package) that is RAM-only.  This provides a multi user 'terminal services' mode of operation.  This is the only time x11vnc STARTS the X server, and the size can be set via -env FD_GEOM=WxHxD.  But I don't think you are doing this if I understand you correctly.)

---

### Post by rezwits on 2011-02-15
Thanks Karl,

I am not running headless, but I guess I could.  I am running in VMware using an actual hard drive partition as the boot drive and then sometimes using the same partition to boot natively if I need native speed and video.  All of my configurations are correct now though and everything is running great.  I use x11vnc for when I am native, and then VMware has a great built in VM guest os vnc for when I boot using VMware.

Thing is I can't beat the speed of the VMware VNC of the guest os, or the clarity...  So the native is native, x11vnc, I was trying to use x11vnc for all of my vnc connections.  The PPCs are always native tho and that is where the problem was, and why 0.9.8 was disconnecting on the on the PPC in Fedora and not disconnecting on the x86 in VM, because of that xorg issue, but when I went to x86 native I had to update that too to at least 0.9.9  because of your updated disconnect after login issue that was fixed with that release.  So, I went with 0.9.10 for all of them and they all work flawlessly.  I am curious as to why the Ubuntu-10.04-ppc-32 default x11vnc never worked but that can be fought some other day... :)

Laters...

---

