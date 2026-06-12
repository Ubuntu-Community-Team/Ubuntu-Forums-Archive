---
title: "Is the mactel ppa repo version of macfanctld upgraded for 14.04?"
date: 2014-05-07
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-05-07
[http://ubuntuforums.org/showthread.php?t=1467062&page=11](http://ubuntuforums.org/showthread.php?t=1467062&page=11)

Folks:

Spent much of the afternoon yesterday trying to find a basic way to have the MBPro install of Xu 14.04 64 bit run cooler, and finally found the above thread from "swedish wings" . . . detailing his development of the "macfanctld" script.  I think in the past months this was recommended to me in a previous thread to deal with heat issues in LM16, but I couldn't find it; and it wasn't, still isn't clear to me how to best set the temp ranges, using it or other suggestions.  I finally actually started to read the Mactel FAQ as well . . . .

[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

So, found my way to this mactel support site, and seeing how to add this mactel ppa to sources list, and then scrolling down to macfanctld, I see older distros are listed, but no "trusty" version is mentioned . . . .

Will there be a trusty upgrade coming?  Does that matter, is it OK to use the latest version?  

And, at first it seemed like 14 was running cooler, but actually checking temps shows it's running warmer, so I need to fix this problem before I can use the MATE/Xub 14 system . . . please advise if macfanctld should be adjusted, or will be upgraded, to trusty--before installing it?

e.e.p.

---

### Post by MikeBraxner on 2014-05-09
I've been using macfanctld on my MBPr 10.1 since the 12.04 release without any issues, and I'm currently using the 13.04 version on 14.04 trusty with solid performance. Since, as far as I'm aware, there has been no move on further developments, I would suggest to just go ahead and use this older version ... it works just peachy for me.

If temperature is a concern for you, you will probably also want to take a look at using ***intel-p-state*** and ***thermald***. For a quick introduction, have a look at [http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html), and [https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues](https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues). 

I can only judge by my experience, but using *thermald* dropped my CPU temps under serious loads  (Mathematica plowing 6 out of 8 cores all out for days on end) from hitting 95-100 degrees down to a range of 70-80 degrees, which incidentally allowed macfanctld to slow my fans down from ~6000 rpm to ~4500 rpm. You pay for this with some minor loss of performance, you will likely never notice, but at least you stop frying your system ;-)

PS: Please note that in order for thermald to run properly it has to be able to get some decent sensor readings, i.e. you need lm_sensors and the coretemp module installed.

---

### Post by este.el.paz on 2014-05-09
> **MikeBraxner said:**
> I've been using macfanctld on my MBPr 10.1 since the 12.04 release without any issues, and I'm currently using the 13.04 version on 14.04 trusty with solid performance. Since, as far as I'm aware, there has been no move on further developments, I would suggest to just go ahead and use this older version ... it works just peachy for me.

If temperature is a concern for you, you will probably also want to take a look at using ***intel-p-state*** and ***thermald***. For a quick introduction, have a look at [http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html), and [https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues](https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues). 

I can only judge by my experience, but using *thermald* dropped my CPU temps under serious loads  (Mathematica plowing 6 out of 8 cores all out for days on end) from hitting 95-100 degrees down to a range of 70-80 degrees, which incidentally allowed macfanctld to slow my fans down from ~6000 rpm to ~4500 rpm. You pay for this with some minor loss of performance, you will likely never notice, but at least you stop frying your system ;-)

PS: Please note that in order for thermald to run properly it has to be able to get some decent sensor readings, i.e. you need lm_sensors and the coretemp module installed.

@MikeB:

Thanks very much for the reply and the added info, much appreciated . . . last night I read through your post on the rMBPro temp issues thread, seems pretty thorough and I have a better idea of the process now that I see the "mactel" repo ppa items . . . appreciate the thoughts on the thermald . . . I may get there, but my demands are not too excessive . . . no mathematica . . . sometimes chess or Go . . . can make the processor "think" warmly . . . .  So, thanks, I'll try to get this going in a day or two . . .

e.e.p.

---

### Post by este.el.paz on 2014-05-11
```
: Failed to fetch http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
-MacBookPro:~$ sudo apt-get install applesmc lm-sensors macfanctld coretemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package applesmc
E: Unable to locate package coretemp


```

The saga continues . . . inluded a small portion of the apt-get update data . . . when I tried to use the CLI to add the mactel repository it didn't show up in the /etc/apt/sources.list file, so I manually added it there by nano . . . actually same thing with MATE, didn't show up there, but in running update the MATE line shows up . . . so, I've tried a number of times to follow the Braxner instructions, once just starting with the applesmc, and other times with putting each of the other items as I did above . . . in this case it shows the two items as "not found" . . . but did not install the other items.  Yesterday I thought the wifi connect was bad, today at home, after this I ran an upgrade for 30+ packages and it went fine . . . some things working, some not . . . any thoughts about how to get some fan control going?

e.e.p.

---

### Post by MikeBraxner on 2014-05-11
The '404' says it all ... when you entered the ppa reference by hand, you made it specific to the **14.04 trusty** **release**, i.e. you used "http://.../dists/***trusty***/main/...", which does not exist, and thus can't be found. Simple enough to fix, though. If you follow the base URL [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/), you can see the available ppa versions (NB: *no "trusty"*). If you want to use an 'older' version instead, say raring, just adjust your URL accordingly.

However, just because you can't find a *specific* **ppa** release for a *specific* *distribution*, does not necessarily imply that there exists no viable, dist specific release version of what you're looking for ... people keep shunting stuff around between different ppa's, or someone just picks up a particular program, compiles it for a particular dist release, and generates a new ppa for it. 

It is always advisable to just search the Personal Package Archives for the *specific program* your interested in, e.g. [https://launchpad.net/ubuntu/+ppas?name_filter=macfanctld](https://launchpad.net/ubuntu/+ppas?name_filter=macfanctld), and then just to cobble through the individual ppa's to check if one has the dist release your looking for ... OK, so there really isn't one for macfanctld, but the point still worth making ;-)

In short, I would suggest using the 'raring' version from the “Mactel Support” team PPA ([https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)). You can check the available versions under technical details, where you'll also find the correct deb entries, signing keys and fingerprint, if you need them.

Hope this helps.

---

### Post by este.el.paz on 2014-05-11
@MikeB:

Thanks for the help . . . figured it was "operator error" . . . but like all self-made errors, we don't know when or how they are made . . . .  What is kind of odd is that trying to add it in by cli "add repository" brought similar errors?  Anyway, I like simple, so I'll try to adjust the sources.list to "raring" and try again . . . .

e.e.p.

---

### Post by MikeBraxner on 2014-05-11
cli ... add-apt-repository utilizes different specs, and tries to complete where needed ... i.e. appends your dist identifier (e.g. trusty) to the specification automatically unless implicitly prevented from doing so ... check the help, it's right there ;-)

---

### Post by este.el.paz on 2014-05-11
> **MikeBraxner said:**
> cli ... add-apt-repository utilizes different specs, and tries to complete where needed ... i.e. appends your dist identifier (e.g. trusty) to the specification automatically unless implicitly prevented from doing so ... check the help, it's right there ;-)

@Mike:

I do appreciate the response . . . I think I found LP help, but in looking at PPA help, doesn't seem to be showing me why I'm still failing . . . I opened the /etc/apt/sources.list file, and changed the "trusty" to "raring" saved and exited . . . ran update, and now **both** the LP trusty and raring are showing up . . . I looged out and even restarted, I ran "autoremove" . . . still running the attempt to install applesmc lm-sensors macfanctld coretemp returns the same response as with the trusty line item . . . .  My capacity is exceeded . . . I'll have to try to read up some more on this in the coming days . . . .  So far failure . . .sorry to say.

e.e.p.

---

### Post by MikeBraxner on 2014-05-12
Since apt cannot find what does not exist, 'both' *cannot* 'show up' ... sounds like you've still got a ghost entry in there somewhere that specifies a trusty version, which would be preferred by apt, since it matches your current system, and might therefore block the alternative entry, that actually works. Best I can think of is to remove all mention of mactel-support from apt, incl. sources.list and sources.list.d, key, etc. and start clean.

I ran through it, and with the proper deb entries in sources.list,...
```
deb [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) raring main
deb-src [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) raring main
```

apt-get updates fine, and finds the packages.

---

### Post by este.el.paz on 2014-05-12
> **MikeBraxner said:**
> Since apt cannot find what does not exist, 'both' *cannot* 'show up' ... sounds like you've still got a ghost entry in there somewhere that specifies a trusty version, which would be preferred by apt, since it matches your current system, and might therefore block the alternative entry, that actually works. Best I can think of is to remove all mention of mactel-support from apt, incl. sources.list and sources.list.d, key, etc. and start clean.
I ran through it, and with the proper deb entries in sources.list,...
```
deb [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) raring main
deb-src [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) raring main
```
apt-get updates fine, and finds the packages.

@MikeB:

Thanks so kindly for helping out . . . OK, "ghost entry" . . . don't know, I'm used to the Debian experience, where there was only one sources.list, and when you changed it, it was done . . . .  But, if you could, usually I'm just adding stuff and if something goes wrong I just do a total fresh install as my ultimate solution . . . so, to remove mactel-support more simply than total annihilation is it just "sudo apt-get rm mactel-support"??  and that will find all the items you mentioned and erase it??  I have removed apps using synaptics, but I don't know whether synaptics would do anything since in fact so far nothing from mactel is actually installed?  Right?  I'm sure there is something posted on the launchpad site about how to remove it, a bit pressed for time today . . . and since it's a "ghost" I don't know how to "ghost bust."

e.e.p.

Edit:  No worries, I found some stuff on google I could try out, or also see that it could be done in GUI using Software Center . . . might be easier going that way to remove . . . then I can try the re-install by CLI . . . sometime later, like tomorrow . . . .

---

### Post by MikeBraxner on 2014-05-12
Ghost entry ... all I meant was that you might have had *more than one* deb entry in your sources.list which uses the same mactel-support URL and specifies trusty as dist, which could happen if you tried to add the ppa *first* via gui or apt, and then, say, added *another* entry *by hand* in sources.list. 

Later amending the *hand-added* one---again by hand---to raring dist would of course ***not*** alter any other entry in sources.list, thus leaving a 'ghost' designating trusty as dist, which would implicitly overwrite your spec, since it matched your system. 

Alternatively, you might have changed the specification for the deb entry, but forgotten to change it for the deb-src entry. Anyway, just check for a duplicate mactel-support specification and get rid of them, leaving you with two deb entries for mactel-support/raring/main.

If you prefer GUI ... [Software Center/Muon Discover -> Sources -> Configure Sources]  OR  [Synaptics Package Manager -> Settings -> Repositories]. 
Under 'Other Software' just delete any *duplicate* mactel-support references, and make sure the two *remaining ones* (binary and src) are set to URL "http://ppa.launchpad.net/mactel-support/ppa/ubuntu", Dist "**raring**" and Components "Main".

Now **update** your sources, and you should be fine.

---

### Post by este.el.paz on 2014-05-12
> **MikeBraxner said:**
> Ghost entry ... all I meant was that you might have had *more than one* deb entry in your sources.list which uses the same mactel-support URL and specifies trusty as dist, which could happen if you tried to add the ppa *first* via gui or apt, and then, say, added *another* entry *by hand* in sources.list. 
Later amending the *hand-added* one---again by hand---to raring dist would of course ***not*** alter any other entry in sources.list, thus leaving a 'ghost' designating trusty as dist, which would implicitly overwrite your spec, since it matched your system. 
Alternatively, you might have changed the specification for the deb entry, but forgotten to change it for the deb-src entry. Anyway, just check for a duplicate mactel-support specification and get rid of them, leaving you with two deb entries for mactel-support/raring/main.
If you prefer GUI ... [Software Center/Muon Discover -> Sources -> Configure Sources]  OR  [Synaptics Package Manager -> Settings -> Repositories]. 
Under 'Other Software' just delete any *duplicate* mactel-support references, and make sure the two *remaining ones* (binary and src) are set to URL "http://ppa.launchpad.net/mactel-support/ppa/ubuntu", Dist "**raring**" and Components "Main".

Now **update** your sources, and you should be fine.

@Mike:  Thanks once again . . . I think one of the problems was/is that I didn't know that there is a "sources.list" and a "sources.list.d" file and perhaps it seems like the ".d" model is more important than the un .d model . . . and is probably why I didn't see the MATE repository in the regular "sources.list" file.  

I just used the Software Center approach . . . and indeed there were "two" or actually four lines there . . . two for "raring" and two for "trusty" . . . one of the trusty items was unchecked . . . so I removed the trusty items . . . and ran "sudo apt-get update" . . . so, I'm probably "good to go" . . . at work on an iffy wifi connect, I'll have to try the install macfanctld stuff tomorrow . . . .  I'll post back with the good news or the news of fresh disaster when I get there . . . .  : - )

e.e.p.

---

### Post by MikeBraxner on 2014-05-12
Oh happy days ... just keep smiling, mate.

---

### Post by este.el.paz on 2014-05-12
Indeed . . . I've only been messing w/linux for a couple years . . . still don't know the multiple paths to find and fix problems like I am in OSX.

e.e.p.

---

### Post by este.el.paz on 2014-05-13
@MikeB:

So, uh, it's 50% success and 50% fresh disaster???  Ran "update" and then ran "sudo apt-get install applesmc lm-sensors macfanctld coretemp" and got "E: Unable to locate package applesmc & second E with same thing for coretemp . . . .  So I ran a total apt-get upgrade and tried again . . . same thing.  So, then I tried to add the individual packages, starting with macfanctld . . . and that worked, same for lm-sensors . . . but again the applesmc and coretemp failed.  I ran "macfanctld -f" and it showed me similar numbers you had posted on the other thread on fancontrol . . . .  Pasting it in below; I saw where it said "found applesmc at /sys/devices" . . . even though it has not been installed?? So I tried the sudo tee suggestion . . . which seemed to do nothing, so I ctrl C'd out of it . . . .  And, the good news is that the fan is blowing more than it did before, it's hot here and the fan is cycling up and down as the computer is thinking I suppose . . . just can't seem to get apt to load applesmc and coretemp . . . .  So far my linux skills have not gotten to the hand download and extract and install file manually . . . perhaps I could try synaptic in a little while and see if it can do the job??  Anyway, fan is working and it isn't insanely loud . . .so I'm half-way there . . . .

e.e.p.

```
Running in foreground, log to stdout.
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    log_level: 0
Found applesmc at /sys/devices/platform/applesmc.768
Found 1 fan.
Found 13 sensors:
     1: TB0T - Battery TS_MAX Temp 
     2: TB1T - Battery TS1 Temp 
     3: TB2T - Battery TS2 Temp 
     4: TB3T - Battery Temp 
     5: TC0D - CPU 0 Die Temp 
     6: TC0F - ? 
     7: TC0P - CPU 0 Proximity Temp 
     8: TN0D - MCP Die 
     9: TN0P - MCP Proximity 
    10: TTF0 - ? 
    11: Th2H - Right Fin Stack Proximity Temp 
    12: Ts0P - Palm Rest Temp 
    13: Ts0S - ? 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual

sudo tee -a /etc/modules <<-EOF coretemp EOF
> sudo modprobe coretemp
> 
> ^C


```

---

### Post by MikeBraxner on 2014-05-14
First up: Great news that you're almost finished, and as for the hickups, they're partly my fault, if you used the 13.10 posting as more than a guide-line. As a reminder ...
> **MikeBraxner said:**
> [...] make sure you have access to Mactel's 'Support for Linux on Apple Machines' (*sudo add-apt-repository ppa:mactel-support/ppa*), and install **applesmc,** **lm-sensors** and **macfanctld**.

Start up **applesmc** (*sudo modprobe applesmc*) and install **lm-sensors** for easier access and monitoring of sensors, and **coretemp** to allow lm_sensors access to specific sensors, the rotation speed of the fan, and the GPU temperature (just clip coretemp to the end of /etc/modules and start it up) ...

```
sudo tee -a /etc/modules <<-EOF
    coretemp
EOF

sudo modprobe coretemp 

```

With the PPA-lack for 14.04 circumvented, some clarifications to help finish it all ...

***applesmc*** ... As a general tip, whenever *apt-get* spouts something like "*can't find ...*" it's more often than not a typo or an incomplete spec. To me, the simplest way to be sure that I've got it right, is to use a simple search, i.e. "***sudo apt-cache search applesmc***" which returns '**applesmc-dkms - Supplementary applesmc support**' ... in other words, you need to run "**sudo apt-get install applesmc-dkms**" to get applesmc. Incidentally, when *macfanctld -f* reported *"/sys/devices/platform/applesmc.768"* as found, it merely reported that a **device** of that name is known to your system ... what you install with *applesmc-dkms* (simplified) is the proper identification of the underlying hardware to the sensors you get to access and use via lm-sensors and macfanctld (see below).

***lmsensors*** ... While apt-get pulls the package in a basic configuration, you still need to *finalize the install* ([https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto), steps 2-4) by getting your system's sensors properly recognized via** sudo sensors-detect**  (just answer 'yes' to all detection requests), and append the required kernel modules (for the 10.1 MBPr that's coretemp) to */etc/modules* (which is what the *"sudo tee ..."* stuff was supposed to take care of), so go ahead and make sure that's in place. (Btw ... for the MBPr 10.1 */etc/modules* should also hold *hid_apple*.)

***coretemp*** ... After reading the Sensor Install HowTo it's probably a mute point, but I mention it anyway ... coretemp is not an independent package, but a kernel module that you merely have to get to start-up ... and that should be taken care of by now (reboot or the above Step 4).

Once you're done, run "***macfanctld -f***" again, and compare the output to what you posted, and you will see the differences immediately (2 fans instead of one, 43 sensors instead of 13, ...). 

Finally, adjust ***/etc/macfanctld.conf*** to your liking, as suggested in the 13.10 post, and you should be golden.

---

### Post by este.el.paz on 2014-05-14
> **MikeBraxner said:**
> 

***applesmc*** ... As a general tip, whenever *apt-get* spouts something like "*can't find ...*" it's more often than not a typo or an incomplete spec. To me, the simplest way to be sure that I've got it right, is to use a simple search, i.e. "***sudo apt-cache search applesmc***" which returns '**applesmc-dkms - Supplementary applesmc support**' ... in other words, you need to run "**sudo apt-get install applesmc-dkms**" to get applesmc. Incidentally, when *macfanctld -f* reported *"/sys/devices/platform/applesmc.768"* as found, it merely reported that a **device** of that name is known to your system ... what you install with *applesmc-dkms* (simplified) is the proper identification of the underlying hardware to the sensors you get to access and use via lm-sensors and macfanctld (see below).
***lmsensors*** ... While apt-get pulls the package in a basic configuration, you still need to *finalize the install* ([https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto), steps 2-4) by getting your system's sensors properly recognized via** sudo sensors-detect**  (just answer 'yes' to all detection requests), and append the required kernel modules (for the 10.1 MBPr that's coretemp) to */etc/modules* (which is what the *"sudo tee ..."* stuff was supposed to take care of), so go ahead and make sure that's in place. (Btw ... for the MBPr 10.1 */etc/modules* should also hold *hid_apple*.)
Finally, adjust ***/etc/macfanctld.conf*** to your liking, as suggested in the 13.10 post, and you should be golden.

@MikeB:

Again, the reply is appreciated, the devil is in the details . . . thanks for these, I'll look into the "SensorinstallHowto" link in a bit, but, I didn't get a chance to post back . . . trying to add applesmc by way of synaptic and software center . . . went no where . . . I then read thru the 13.10 thread or one of them and I saw that "applesmc-dkms" was mentioned . . . so I tried using that as well . . . did not succeed . . . .  I'll have to get back to this later today and see if I can find something . . . obviously if I could add "macfanctld" the ppa repo is OK, and I saw that applesmc is there in the list . . . seems weird, no?

e.e.p.
Edit:  I ran the "sensor-detect" series and answered yes . . . then at end it said to run "service kmod start" . . . which I did, brought some kind of error, tried "sudo service kmod start" and then I went for the "HowTo" "sudo service module-init-tools restart" . . . said, "unrecognized service" . . . and then I ran "sensors" ... seemed to show the same 13 as before . . . and then I ran "macfanctld -f" . . . seems the same . . . .  Do I need to log out or restart the system?  Keep in mind this is a laptop . .  does that have 4 fans?

 Code:

~$ service kmod start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.198" (uid=1000 pid=8555 comm="start kmod ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
-MacBookPro:~$ sudo service kmod start
kmod stop/waiting
-MacBookPro:~$ sudo service module-init-tools restart
module-init-tools: unrecognized service
-MacBookPro:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +55.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +53.0°C  (high = +105.0°C, crit = +105.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Left side  : 2007 RPM  (min = 2000 RPM, max = 5700 RPM)
TB0T:         +31.5°C  
TB1T:         +31.5°C  
TB2T:         +29.2°C  
TB3T:          +0.0°C  
TC0D:         +54.2°C  
TC0F:         +49.0°C  
TC0P:         +49.8°C  
TN0D:         +55.2°C  
TN0P:         +47.8°C  
TTF0:         +49.0°C  
Th2H:         +44.8°C  
Ts0P:         +30.5°C  
Ts0S:         +39.0°C  

-MacBookPro:~$ macfanctld -f
Running in foreground, log to stdout.
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    log_level: 0
Found applesmc at /sys/devices/platform/applesmc.768
Found 1 fan.
Found 13 sensors:
     1: TB0T - Battery TS_MAX Temp 
     2: TB1T - Battery TS1 Temp 
     3: TB2T - Battery TS2 Temp 
     4: TB3T - Battery Temp 
     5: TC0D - CPU 0 Die Temp 
     6: TC0F - ? 
     7: TC0P - CPU 0 Proximity Temp 
     8: TN0D - MCP Die 
     9: TN0P - MCP Proximity 
    10: TTF0 - ? 
    11: Th2H - Right Fin Stack Proximity Temp 
    12: Ts0P - Palm Rest Temp 
    13: Ts0S - ? 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual

---

### Post by MikeBraxner on 2014-05-15
Did you add coretemp to /ect/modules ... cause right now it looks as though your system only recognizes 2 cores? Did you install applesmc ... still seems to be missing, and with it the proper recognition of your sensors? You really need to get that install finished before you run your sensor detection. Anyway, a reboot/service restart should give you something in the neighborhood of ...
```
nat@nestor:~$ sensors
nouveau-pci-0100
Adapter: PCI adapter
temp1:            N/A  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +74.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +72.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +74.0°C  (high = +87.0°C, crit = +105.0°C)
Core 2:         +65.0°C  (high = +87.0°C, crit = +105.0°C)
Core 3:         +69.0°C  (high = +87.0°C, crit = +105.0°C)


applesmc-isa-0300
Adapter: ISA adapter
Left side  : 3611 RPM  (min = 3582 RPM, max = 5940 RPM)
Right side : 3619 RPM  (min = 3582 RPM, max = 5499 RPM)
TB0T:         +28.0°C  
TB1T:         +28.0°C  
TB2T:         +25.5°C  
TC0E:         +71.5°C  
TC0F:         +72.5°C  
TC0P:         +49.5°C  
TC1C:         +70.0°C  
TC2C:         +74.0°C  
TC3C:         +64.0°C  
TC4C:         +68.0°C  
TCGC:         +72.0°C  
TCSA:         +70.0°C  
TCTD:          +0.2°C  
TCXC:         +72.0°C  
TG0D:         +50.2°C  
TG0P:         +47.8°C  
TG1D:        -127.0°C  
TG1F:        -127.0°C  
TG1d:        -127.0°C  
TH0A:         +34.0°C  
TH0B:         +37.0°C  
TH0V:         +43.2°C                                                                                                  
TH0a:         +34.0°C                                                                                                  
TH0b:         +37.0°C                                                                                                  
                                                                                                                       
nat@nestor:~$ macfanctld -f                                                                                            
Running in foreground, log to stdout.                                                                                  
Using parameters:                                                                                                      
        temp_avg_floor: 45                                                                                             
        temp_avg_ceiling: 55                                                                                           
        temp_TC0P_floor: 35                                                                                            
        temp_TC0P_ceiling: 52                                                                                          
        temp_TG0P_floor: 40                                                                                            
        temp_TG0P_ceiling: 55                                                                                          
        fan_min: 2000                                                                                                  
        exclude: temp13_input temp17_input temp18_input temp19_input temp25_input temp32_input temp33_input temp34_input temp35_input                                                                                                         
        log_level: 0                                                                                                   
Found applesmc at /sys/devices/platform/applesmc.768                                                                   
Found 2 fans.                                                                                                          
Found 43 sensors:                                                                                                      
         1: TB0T - Battery TS_MAX Temp                                                                                 
         2: TB1T - Battery TS1 Temp                                                                                    
         3: TB2T - Battery TS2 Temp                                                                                    
         4: TC0E - ?                                                                                                   
         5: TC0F - ?                                                                                                   
         6: TC0P - CPU 0 Proximity Temp                                                                                
         7: TC1C - ?                                                                                                   
         8: TC2C - ?                                                                                                   
         9: TC3C - ?                                                                                                   
        10: TC4C - ?                                                                                                   
        11: TCGC - ?                                                                                                   
        12: TCSA - ?                                                                                                   
        13: TCTD - ?    ***EXCLUDED***                                                                                 
        14: TCXC - ?                                                                                                   
        15: TG0D - GPU Die - Digital                                                                                   
        16: TG0P - GPU 0 Proximity Temp                                                                                
        17: TG1D - ?    ***EXCLUDED***                                                                                 
        18: TG1F - ?    ***EXCLUDED***                                                                                 
        19: TG1d - ?    ***EXCLUDED***                                                                                 
        20: TH0A - ? 
        21: TH0B - ? 
        22: TH0V - ? 
        23: TH0a - ? 
        24: TH0b - ? 
        25: TH0c - ?    ***EXCLUDED***
        26: TH0x - ? 
        27: TM0P - ? 
        28: TM0S - ? 
        29: TMBS - ? 
        30: TP0P - ? 
        31: TPCD - ? 
        32: TS0D - ?    ***EXCLUDED***
        33: TS0P - ?    ***EXCLUDED***
        34: TS1D - ?    ***EXCLUDED***
        35: TS1P - ?    ***EXCLUDED***
        36: TW0P - ? 
        37: Ta0P - ? 
        38: TaSP - ? 
        39: Th1H - ? 
        40: Th2H - Right Fin Stack Proximity Temp 
        41: Ts0P - Palm Rest Temp 
        42: Ts0S - ? 
        43: Ts1S - ? 

```

... mind you, this is from a 15" MacBookPro 10.1 Retina (currently on a medium load with half the cores running a Mathematica sim, using thermald), so while your's should be similar in sensors (can only guess, you never specified what model your actually using, though I don't see the sensors listed for an NVidia), it may not be identical, and will certainly vary in values. 

But again, you really *need* to complete your install, or everything else is pretty much bubkes.

PS: You DID run the sensor-detect as sudo ... right?

---

### Post by este.el.paz on 2014-05-15
> **este.el.paz said:**
> @MikeB:
. . . trying to add applesmc by way of synaptic and software center . . . went no where . . . I then read thru the 13.10 thread or one of them and I saw that "applesmc-dkms" was mentioned . . . so I tried using that as well . . . did not succeed . . . .  I'll have to get back to this later today and see if I can find something . . . obviously if I could add "macfanctld" the ppa repo is OK, and I saw that applesmc is there in the list . . . seems weird, no?
e.e.p.
Edit:  I ran the "sensor-detect" series and answered yes . . . then at end it said to run "service kmod start" . . . which I did, brought some kind of error, tried "sudo service kmod start" and then I went for the "HowTo" "sudo service module-init-tools restart" . . . said, "unrecognized service" . . . and then I ran "sensors" ... seemed to show the same 13 as before . . . and then I ran "macfanctld -f" . . . seems the same . . . .  Do I need to log out or restart the system?  Keep in mind this is a laptop . .  does that have 4 fans?

 ```

~$ service kmod start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.198" (uid=1000 pid=8555 comm="start kmod ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
-MacBookPro:~$ sudo service kmod start
kmod stop/waiting
-MacBookPro:~$ sudo service module-init-tools restart
module-init-tools: unrecognized service
-MacBookPro:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +55.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +53.0°C  (high = +105.0°C, crit = +105.0°C)
applesmc-isa-0300
```

@Mike:  This is a '10 MBPro, 15" which I think is a "5,1"????  It's Core2Duo . . . so that would only show 2 cores I believe, so that part is OK . . . sensors might be the same, as in OSX Temp Monitor there are only a few numbers, perhaps 13.  
The problem seems to be the "applesmc-dkms"??? package, not showing up in apt, or synaptic, or software center . . .???  I also tried to "sudo nano macfanctld.conf"  file and it opened an empty page . . . .

The good news is that the fan(s) is blowing more often and seems to be keeping the temps more cool . . . but, I don't know if I'd try to push the activities . . . it would be "cool" if there was a way to get/find/install applesmc . . . and then try the "sensor -detect" process again?  I did restart the computer a couple times trying to fix a vanishing network manager . . . but what would the "service restart" look like? "sudo macfanctld service restart"??

On the "Did I run sensor detect as sudo?" . . . yes, but in looking at the "HowTo" it seemed to show some commands run as "su" . . . which I did not do, would that make a difference?  Can't remember if Ubuntu uses "su" to run Terminal as "root" . . . I haven't set up any other accounts other than admin . . . .  I'm kind of stymied on this no applesmc thing . . . .

e.e.p.

---

### Post by MikeBraxner on 2014-05-15
***applesmc-dkms*** ... if the ppa is working properly, and you **UPDATED** properly, then **sudo apt-get install applesmc-dkms** will install the driver just fine ... it does here. Please don't ***assume*** that the ppa is working ... CHECK ... and then CHECK AGAIN!!!!  While synaptics works here, if you have a problem, use the command line, that's what apt-get is for. If you prefer, you can of course always fallback on the source option (git clone [http://bitmath.org/git/applesmc-dkms.git](http://bitmath.org/git/applesmc-dkms.git)).

***macfanctld*** ... a demon restart, as mentioned in the 13.10 thread, is the standard ***sudo service macfanctld restart***. 

To keep an eye on the temps and the fan(s), as suggested in the 13.10 thread, just open a terminal and run ***watch sensors***, or have a look at some of the applets and plasmoids floating about for gnome and kde.

As to editing the config file ... judging by your command spec you did ***not*** try edit the existing configuration file, but instead tried to *create and edit* a file by the name *macfanctld.conf *in an unspecified directory, hence your then current working directory (possibly your home, possibly anywhere). Working non-gui, you really need to get used to the idea of being more specific, e.g. use the path spec if you want to access something. Here, it should read ***"sudo nano /etc/macfanctld.conf &"***. General tip, use the 'tab-completion' while you're typing in a terminal ... makes thing simpler, and ensures you implicitly check the correct path and file identity;-)

***sudo*** ... Unlike other distros, Ubuntu doesn't really let you use a true root account. Pretty much everything is supposed to be done via *"sudo ..."* calls. Put simply, while you *can* switch to root access, you're actively discouraged from doing so, in order to avoid major screw-ups ... some people agree with the concept, others think this 'pseudo-apple' garbage is just plain insulting.

---

### Post by este.el.paz on 2014-05-15
> **MikeBraxner said:**
> ***applesmc-dkms*** ... if the ppa is working properly, and you **UPDATED** properly, then **sudo apt-get install applesmc-dkms** will install the driver just fine ... it does here. Please don't ***assume*** that the ppa is working ... CHECK ... and then CHECK AGAIN!!!!  While synaptics works here, if you have a problem, use the command line, that's what apt-get is for. If you prefer, you can of course always fallback on the source option (git clone [http://bitmath.org/git/applesmc-dkms.git](http://bitmath.org/git/applesmc-dkms.git)).  As to editing the config file ... judging by your command spec you did ***not*** try edit the existing configuration file, but instead tried to *create and edit* a file by the name *macfanctld.conf *in an unspecified directory, hence your then current working directory (possibly your home, possibly anywhere). Working non-gui, you really need to get used to the idea of being more specific, e.g. use the path spec if you want to access something. Here, it should read ***"sudo nano /etc/macfanctld.conf &"***. General tip, use the 'tab-completion' while you're typing in a terminal ... makes thing simpler, and ensures you implicitly check the correct path and file identity;-)   @MB:  Sorry to be a bother, never really had any computer ed class post 40 years ago with the punch cards and the "basic" or "fortran"?? language . . . no time now to do a thorough job of it, linux is one of several hobbies . . . I can follow directions, but trying to piece this one together has been rougher than usual, the directions seem to be changing, etc . . . .  So, in terms of e.g., "checking and re-checking the ppa"???? if I looked at the software center "other sources" and the "mactel" item is listed there . . . ???  not enough checking?  Before apt-get was reporting coretemp & applesmc as not found, and nothing was installing . . . then after getting the "trusty" and "raring" thing straightened out, macfanctld installed . . . so, would that mean the ppa is "intermittently active"???  : - )    On the "creating the macfanctld.conf" file . . . yeah, I figured that's what I had done when it was empty . . . thanks for showing the suggested command adding the  [&] . . . I don't know too much about CLI commands . . . I don't know what a "tab completion" is . . . .  So, I may try to again see if the mactel ppa is showing up, and run "watch sensors" . . . and might be something to report back about???  e.e.p.

Edit:  I ran the "macfanctld.conf &" and then hit "tab" and it showed a drop down menu . . . nothing that seemed to be appropriate for a completing the string considering my limited knowledge, etc.  Also ran "watch sensors" and it shows the current data, it's not letting me copy it, but it's showing "coretemp-isa-0000" the two cores, and "applesmc-isa-0300" with the 13 sensors . . . .  Again, I ran "update" and the, how much easier could it get?  "sudo apt-get install applesmc-dkms" . . . and package not found was the return . . . .  Perhaps I'll try to manually add it . . . again, beyond my pay grade . . . I prefer using the "apt-get" approach . . . much simpler . . . .

Edit2: Later that same day, I tried to "pluma" the macfanctld.conf file . . . and again nothing . . . so, doing it the GUI way, I went to /etc and found the file sitting there, physically . . . but alone . . . I right-clicked it and opened it with pluma . . . and there it was . . . only thing missing is the "exclude" line . . . .  So, is it time to try that "coretemp EOF" series of commands?  I thought with running "sensors-detect" that all the modules were installed?  Even though the "kmod" command didn't seem to work . . . it's continuing to be odd that this file isn't opening in terminal, but is there????

# Config file for macfanctl daemon
#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       

fan_min: 2000

temp_avg_floor: 45
temp_avg_ceiling: 55

temp_TC0P_floor: 50
temp_TC0P_ceiling: 58

temp_TG0P_floor: 50
temp_TG0P_ceiling: 58

# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.

exclude:

# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors  

log_level: 0

---

### Post by MikeBraxner on 2014-05-16
***PPA*** ... If, and let me stress this again, ***IF*** the ppa is properly setup, then applesmc-dkms **will** install ... hence, there's something wrong with your ppa setup. 

If there are any glitches, then think it through logically. It might be a link to the wrong ppa, i.e. one that holds macfanctld, but not applesmc-dkms, or you may have linked to the valid ppa, 'accidentally' installed macfanctld early on, and subsequently deleted the ppa again (which is why applesmc-dkms cannot be found, but the *installed* version of macfanctld can). So first I would run a another update, just to be certain (***sudo apt-get update***), and try for applesmc-dkms once more. If that didn't work, I would suggest to re-check */etc/apt/sources.list* for the according entry, i.e. ...
```
deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu raring main 
deb-src http://ppa.launchpad.net/mactel-support/ppa/ubuntu raring main
```
... and make sure its the ONLY one for mactel-support, i.e. no version confusion, and/or overlap. This is what I mean by "don't assume ... check and re-check". Think it through, see where a glitch could have occurred, and just re-trace your steps. 

If, for whatever reason, this one does not work for you, there are at least two more ppa's in the personal package archive that hold applesmc-dkms, just watch out for the version [https://launchpad.net/ubuntu/+ppas?name_filter=applesmc-dkms](https://launchpad.net/ubuntu/+ppas?name_filter=applesmc-dkms). 

***tabbing*** ... This is simply a command completion. Try this, open a terminal, and type "more /etc/macf" and then hit the tab key. It works for known commands, pathways, file names ... one of the handier bits of the bash shell. 

***sensors*** ... "***watch sensors***" are actually two commands, the "***watch***" command gives a 2 second interval refresh of the "***sensors***" command, i.e. it updates/re-runs it every 2 seconds (have a look at the man page "***man watch***"). If you want a simple static version that easy to copy out of the terminal, just run "***sensors***" by itself. 

***exclude line*** ... In order to adjust ***/etc/macfanctld.conf*** exclude line, you need to know which sensors return readings, and which of them are/might be bogus. Run "***watch sensors***" and use some common sense. temp readings that are way below ambient temperature (0, -127, ...), or temps that would already have incinerated your system (283, 547,...) are obviously false, and have to be removed. Note down their ID's, say *TCTD*, or *TG1D*. Then run "***macfanctld -f***", run down the list of sensors and look for those IDs, and now note the according sensor number that macfanctld uses (e.g. 13 for TCTD, or 17 for TG1D). These are the numbers, separated by spaces, you can then add to the ***/etc/macfanctld.conf*** exclude line. Once again, read "***man macfanctld***".

---

### Post by este.el.paz on 2014-05-16
> **MikeBraxner said:**
> ***PPA*** ... If, and let me stress this again, ***IF*** the ppa is properly setup, then applesmc-dkms **will** install ... hence, there's something wrong with your ppa setup. 
just to be certain (***sudo apt-get update***), and try for applesmc-dkms once more. If that didn't work, I would suggest to re-check */etc/apt/sources.list* for the according entry, i.e. ...
```
deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu raring main 
deb-src http://ppa.launchpad.net/mactel-support/ppa/ubuntu raring main
```
... and make sure its the ONLY one for mactel-support, i.e. no version confusion, and/or overlap. This is what I mean by "don't assume ... check and re-check". Think it through, see where a glitch could have occurred, and just re-trace your steps. 

OK, thanks for the thoroughness and persistence very kind of you, and right anything is possible, I have checked that ppa, several times, so far it all looks right; possibly the "trusty" vibe is still hanging around making a problem . . . have to say this is the first time where, even with the exact instructions things are not happening . . . .  Couple points, after I had posted the 2nd edit here I got an error message that went on to detail some problems with "nano" and there was a "report this" window . . . that's when I switched to Pluma--so possibly in terms of reading the "macfanctld.conf" file, nano was glitchy??  And then after trying the apt-get update for like the tenth time I went to the repository and manually downloaded the applesmc-dkms tar.gz . . . and I extracted it to the Downloads file.  That's as far as I got; I'll have to read on Google how to install it and see if it works that way . . . .  

>  If, for whatever reason, this one does not work for you, there are at least two more ppa's in the personal package archive that hold applesmc-dkms, just watch out for the version [https://launchpad.net/ubuntu/+ppas?name_filter=applesmc-dkms](https://launchpad.net/ubuntu/+ppas?name_filter=applesmc-dkms). 

OK, thanks for that link, if the manual install goes wonky . . . as it might, I'll look into that . . . the fans are working as it is, just not adjusted in any way.

> 
***tabbing*** ... This is simply a command completion. Try this, open a terminal, and type "more /etc/macf" and then hit the tab key. It works for known commands, pathways, file names ... one of the handier bits of the bash shell. 
***sensors*** ... "***watch sensors***" are actually two commands, the "***watch***" command gives a 2 second interval refresh of the "***sensors***" command, i.e. it updates/re-runs it every 2 seconds (have a look at the man page "***man watch***"). If you want a simple static version that easy to copy out of the terminal, just run "***sensors***" by itself. 
***exclude line*** ... In order to adjust ***/etc/macfanctld.conf*** exclude line, you need to know which sensors return readings, and which of them are/might be bogus. Run "***watch sensors***" and use some common sense. temp readings that are way below ambient temperature (0, -127, ...), or temps that would already have incinerated your system (283, 547,...) are obviously false, and have to be removed. Note down their ID's, say *TCTD*, or *TG1D*. Then run "***macfanctld -f***", run down the list of sensors and look for those IDs, and now note the according sensor number that macfanctld uses (e.g. 13 for TCTD, or 17 for TG1D). These are the numbers, separated by spaces, you can then add to the ***/etc/macfanctld.conf*** exclude line. Once again, read "***man macfanctld***".

Thanks again for these definitions of terms . . . I did try them all out, thanks for the distinction on the "watch sensors" vs "sensors" on the copying aspect . . . and thanks for the "tab" . . . I did that, just not enough skilz to know which of those terms would be correct . . . .  Anyway, it'll be later today or tomorrow before I get a chance to look into installing the "applesmc" folder . . . by CLI . . . and after that I'll post back with news of success or again the fresh disaster . . . .

e.e.p.

---

### Post by MikeBraxner on 2014-05-16
***Hold it all ... ***I went through my stuff again, and found that I had actually the both, the **raring as well as the quantal **version of the ppa active --- what did I tell you: *check ... and check again* --- and wouldn't you know it, the mactel-support ppa holds applesmc-dkms **only** up to ***QUANTAL***. Ironically, this means that the above first option ...
> **MikeBraxner said:**
> If, and let me stress this again, ***IF*** the ppa is properly setup, then applesmc-dkms **will** install ... hence, there's something wrong with your ppa setup. 

If there are any glitches, then think it through logically. It might be a link to the wrong ppa, i.e. one that holds macfanctld, but not applesmc-dkms
was not only dead on right, but also somewhat prophetic ... you gotta love this kind'a stuff ;-)

So, just go ahead, and add that version to your repository sources with ...
```
deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu quantal main 
deb-src http://ppa.launchpad.net/mactel-support/ppa/ubuntu quantal main
```

That should resolve the whole applesmc-dkms fiasco. 

Sorry about that, mate.

---

### Post by este.el.paz on 2014-05-16
@Mike:

Indeed, you do have to love it, very funny . . . in a technical kind of way . . . .  But, thanks, obviously I've never gone through this ppa thing, so the details of it are unknown . . . clearly couldn't have done it without you.  Like I was saying, limited skilz, but if someone gives me the commands I can type them in, and generally it works . . . this one was just not dropping in . . . what is it, if you keep doing the same thing with expectation of different outcome??  : - )

Have to get to it tomorrow, been busy today . . . it's OK to leave the "raring" stuff?  And add the quantal to pick up the applesmc . . . ??  And then do I have to run the "sudo sensors-detect" process again?  Haven't had time to re-re-re-read through the thread here to catch all the details . . . but, this ***should*** get this closer to good news and away from the fresh disaster . . . .  : - )))


e.e.p.

---

### Post by MikeBraxner on 2014-05-17
*"... what is it, if you keep doing the same thing with expectation of different outcome??"* --- being ***reaaaaaaally*** *persistent ...* right?!

As to your questions: Leave the raring (macfanctld), add the quantal, install applesmc-dkms, reboot, re-run sensor-detect, check coretemp listed in /etc/modules, restart services/reboot, adjust /etc/macfanctld.conf (see earlier posts & man page)... that should take care of things.

---

### Post by este.el.paz on 2014-05-17
> **MikeBraxner said:**
> *"*

As to your questions: Leave the raring (macfanctld), add the quantal, install applesmc-dkms, reboot, re-run sensor-detect, check coretemp listed in /etc/modules, restart services/reboot, adjust /etc/macfanctld.conf (see earlier posts & man page)... that should take care of things.

@Mike:

So, did the "add the quantal" thing, and that went well, the "applesmc" install finally went through . . . rebooted, ran the sensor-detect . . . coretemp was there in /etc/modules . . . then I tried to check /etc/macfanctld.conf  using pluma, and nothing opens . . . at some point I modprobed coretemp and tried to follow the other thread suggestions to modprobe applesmc???  Rebooted a couple times . . . then I used the GUI to check the /etc/macfanctld.conf  file . . . still showing the 13 sensors, nothing is excluded . . . tried to edit the file in Pluma, nothing happened, then opened it in Mousepad, and I could change the numbers, just to follow the rMBPro temp thread to make the high end #'s more conservative . . . but, then would not save the changes . . . .  

So, I have finally gotten the applesmc-dkms installed . . . and generally the fans blow OK, but I wouldn't know if I need to adjust the "exclude sensors" #'s for the Nvidia card?  Just can't tell if things are at least running as they more or less should be . . . or if they need further attention, and then what would that be?

But, it seems closer . . . I'll have to try other stuff, "watch sensors"  or something?  But question is why is the /etc/macfanctld.conf file not opening in Terminal, or opening as empty, and why is the GUI Pluma file not editing?  These kind of questions . . . .

e.e.p.

Edit: ```
 sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +58.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +56.0°C  (high = +105.0°C, crit = +105.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Left side  : 1990 RPM  (min = 2000 RPM, max = 5700 RPM)
TB0T:         +34.8°C  
TB1T:         +34.8°C  
TB2T:         +32.5°C  
TB3T:          +0.0°C  
TC0D:         +57.8°C  
TC0F:         +52.8°C  
TC0P:         +52.8°C  
TN0D:         +58.5°C  
TN0P:         +51.0°C  
TTF0:         +49.0°C  
Th2H:         +47.8°C  
Ts0P:         +33.0°C  
Ts0S:         +41.8°C  


```

---

### Post by MikeBraxner on 2014-05-18
Your temps all look fine, except for TB3T, which essentially doesn't give you one, so that one should be excluded (man macfanctld). As to the un-editable macfanctld.conf, the answer is simple, and has been touched on before. 

Since macfanctld.conf lies in /etc, i.e. within a **system** directory (or in Ubuntu references, *outside* your home directory), you need root privilege to alter it. From a terminal, just use "***sudo nano /etc/macfanctld.conf &***" (or use the editor of your choice).

---

### Post by este.el.paz on 2014-05-18
> **MikeBraxner said:**
> Your temps all look fine, except for TB3T, which essentially doesn't give you one, so that one should be excluded (man macfanctld). As to the un-editable macfanctld.conf, the answer is simple, and has been touched on before. 

Since macfanctld.conf lies in /etc, i.e. within a **system** directory (or in Ubuntu references, *outside* your home directory), you need root privilege to alter it. From a terminal, just use "***sudo nano /etc/macfanctld.conf &***" (or use the editor of your choice).

@MikeB:

OK, great, looks like we're about out of the woods . . . so, I got it on the TB3T . . . since it's showing "0" it's obviously messing with the Temp averages . . . I'll look at the man . . . but, would that be something like "exclude: 4" ???  since it's the 4th one from the top??  No worries on that, but just a question in terms of the numbering . . . .

However, on the editing of macfanctld.conf . . . I have been using sudo and either nano or now pluma, or mousepad, but not the "&" . . . so I'll have to re-try that, my impression was from one of your previous posts that there would be something that would be **after** the "&" . . . and I had no idea what that would be . . . but this is looking like just the "&" . . . the only other time I've seen that is with some folks recommending  "sudo apt-get update && apt-get upgrade" . . . somethig like that, but not at the end . . . anyway, I'll try that in a few hours and hopefully that will finish this up . . . .  But, many thanks, it has been fun . . . an introduction to the wonderful world of ppa's.

e.e.p.

---

### Post by MikeBraxner on 2014-05-18
numbering ... discussed earlier; see ***exclude line*** comment above (2nd post, 3rd page)

***&*** at the end of a command merely means "run detached from shell", i.e. once its started it is independent of the shell.

---

### Post by este.el.paz on 2014-05-18
The oddness continues to be odd . . . trying to get the .conf file to open in Terminal . . . not working; read the manual and noticed it was using /etc/macfanctl.conf . . . but I was doing /etc/macfanctld.conf . . . so I tried that . . . it keeps showing this "[3] 2581" when I hit return . . . or if I try again it will do "[3]+ Stopped" and so on . . . .  I even tried "su" but it says authentication failed . . . I only have one account, haven't officially added myself to sudoers????  Obviously the file is "there" because I can open it in the GUI, but, it still isn't opening in Terminal . . . .  I'm flabbergasted . . . .  You can see that I'm trying different spellings and different place for "&" . . . doesn't seem to care.  When I do "watch sensors" the Terminal goes to that "page" showing the temps and I can "q" out of it, etc . . .  e.e.p.

```
~$ watch sensors
MacBookPro:~$ sudo pluma /etc/macfanctld.conf &
[1] 2553
MacBookPro:~$ sudo pluma /etc/macfanctld.conf&
[2] 2556

[1]+  Stopped                 sudo pluma /etc/macfanctld.conf
-MacBookPro:~$ man macfanctld

[2]+  Stopped                 sudo pluma /etc/macfanctld.conf
-MacBookPro:~$ sudo pluma /etc/macfanctl.conf&
[3] 2581
-MacBookPro:~$ sudo pluma /etc/macfanctl.conf &
[4] 2582

[3]+  Stopped                 sudo pluma /etc/macfanctl.conf
MacBookPro:~$ sudo nano /etc/macfanctld.conf &
[5] 2583

[4]+  Stopped                 sudo pluma /etc/macfanctl.conf
-MacBookPro:~$ sudo nano /etc/macfanctld.conf & 
[6] 2587

[5]+  Stopped                 sudo nano /etc/macfanctld.conf
MacBookPro:~$ man macfanctld

[6]+  Stopped                 sudo nano /etc/macfanctld.conf
-MacBookPro:~$ su
Password: 
su: Authentication failure
MacBookPro:~$ sudo mousepad /etc/macfanctl.conf &
[7] 2609


```

---

### Post by este.el.paz on 2014-05-18
OK, read the new post about the Mac 9,2 and went to the thermald page, saw the instructions showing "gksu gedit" so I tried that, and Terminal tells me "You don't have gksu" and how to add it, so I added it and tried again . . . and an admin password window opened telling me my system will be "modified" but nothing happened.  Then I went back to "sudo pluma /etc/macfanctl.conf &" and again it "stopped" . . . so I went back to plain old "sudo pluma /etc/macfanctl.conf" . . . with no "&" . . . and "boom" it opened . . . I added "4" to the "excluded" list . . . and saved it . . . .  In the "macfanctld -f" list it shows TB3T as "excluded" but over in "watch sensors" it's still there showing "0" . . .

Anyway, done deal . . . looking forward to hours of cool computing . . . thanks for the studious and thorough help . . . .

e.e.p.

Edit:  After going thru this process I went back to the mactel-support ppa and tried to look at other packages that might be helpful . . . particularly anything that might help with a "jumping cursor" issue where the only fix so far has been to disable "click to tap" on the touchpad . . . I'm wondering if installing any of the "xorg-xserver-synaptics" or the "multitouch" packages is necessary, or would that be redundant . . . have those packages been already updated in 14.04??  The packages list doesn't offer too much in terms of what they do, or whether they are needed in trusty . . . seems like you just have to know???

---

### Post by este.el.paz on 2014-05-21
> After going thru this process I went back to the mactel-support ppa and  tried to look at other packages that might be helpful . . . particularly  anything that might help with a "jumping cursor" issue where the only  fix so far has been to disable "click to tap" on the touchpad . . . I'm  wondering if installing any of the "xorg-xserver-synaptics" or the  "multitouch" packages is necessary, or would that be redundant . . .  have those packages been already updated in 14.04??  The packages list  doesn't offer too much in terms of what they do, or whether they are  needed in trusty . . . seems like you just have to know???

Hoping to get some further feedback on the other mactel-support ppa items . . . how can we tell if our computer needs the packages, or even, how can we tell what they do?  I guess apt/synaptic might show them if they are already installed?  Although neither of them showed macfanctl . . . I'd like to be able to have "tap to click" enabled again w/o having the problems of jumping cursor with data erasure, etc to contend with . . . .

e.e.p.

---

### Post by este.el.paz on 2014-05-23
> **este.el.paz said:**
> Hoping to get some further feedback on the other mactel-support ppa items . . . how can we tell if our computer needs the packages, or even, how can we tell what they do?  I guess apt/synaptic might show them if they are already installed?  Although neither of them showed macfanctl . . . I'd like to be able to have "tap to click" enabled again w/o having the problems of jumping cursor with data erasure, etc to contend with . . . .

e.e.p.

Can anybody give me some more info about the other mactel-support ppa items, whether or not the "xserver-synaptic" packages need to be installed or are already handled by 14.04?

Thanks,

e.e.p.

---

### Post by este.el.paz on 2014-05-29
> **este.el.paz said:**
> Can anybody give me some more info about the other mactel-support ppa items, whether or not the "xserver-synaptic" packages need to be installed or are already handled by 14.04?

Thanks,

e.e.p.

Yes, still hoping for some feedback on getting more details about the mactel ppa items . . . finding out what they do, or whether they are needed, etc.

e.

---

### Post by este.el.paz on 2014-06-06
> **este.el.paz said:**
> Hoping to get some further feedback on the other mactel-support ppa items . . . how can we tell if our computer needs the packages, or even, how can we tell what they do?  I guess apt/synaptic might show them if they are already installed?  Although neither of them showed macfanctl . . . I'd like to be able to have "tap to click" enabled again w/o having the problems of jumping cursor with data erasure, etc to contend with . . . .

e.e.p.

I'm still hoping to get some feedback on this extended question on the mactel ppa packages, as I mentioned the actual page just shows the available packages, but doesn't offer any information about what they do . . . or, like in the "xserver-synaptic" something package, whether that would help with fixing the dreaded jumping cursor phenomenon . . . is this package needed in 14.04 . . . all the questions that I've mentioned . . . .  Some further details on the mactel ppa or where to find them . . . .

e.e.p.

---

