---
title: "temporary freezes"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jakelute on 2008-02-05
Greetings!
I'm in the process of trying Ubuntu at the moment -- I have been using Windows XP, and, like so many others, I'm fed up with it. So far I'm delighted with Ubuntu (7.10) -- with the ease of use (for a beginner like me), the speed and responsiveness, and, of course, the philosophy behind Ubuntu. It's such a breath of fresh air! I have a dual boot system at the moment, because I want to be sure everything works in Ubuntu before getting rid of Windows -- I have two internal hard disks, and XP is installed on one, and Ubuntu on the other. I've also installed Ubuntu on my wife's laptop (Dell Inspiron 1100), where it works perfectly with no hitches at all (except for an easily fixable problem with the screen resolution). 

On my desktop computer, however, it's a different story. There are a number of things I haven't figured out yet (like playing DVDs, and networking with the laptop), but my chief area of concern is this: several times a day the system freezes temporarily, and then resumes as if nothing had happened. Usually the freezes last about 10 minutes. I can't find a pattern regarding what causes them. I think it's usually when I'm working quickly and doing a number of things at once (like, for instance, several tabs open in Firefox and perhaps copying some photos from one location to another at the same time). A similar problem (related?) is that playing music files is a little bit intermittent -- there are moments of silence sometimes rather than a continuous sound. Is it a memory thing? The other thing to point out is that after the freezes, the clock is wrong (slow by the number of minutes that the freeze lasted).

Presumably I should post my PC's vital statistics to help provide more informatoin -- forgive me, but what's the best place to find this information in Ubuntu, so that I can copy it an paste it into a post?

Sorry to be "green".

Many thanks in advance, and best wishes.

J.

---

### Post by emarkd on 2008-02-05
Don't be sorry.  You can get a listing of your hardware by running 

```
lshw
```

You may want to keep at Terminal window sitting open with 'top' running so maybe you can find out what process may be consuming your resources.

---

### Post by jakelute on 2008-02-05
Thank you very much!

Here it is:

 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 946MB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          size: 3400MHz
          capacity: 3400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
        *-ide:0
             description: IDE interface
             product: 437A Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: 4379 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   product: ST3120026A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 111GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom:0
                   product: CD-RW BCE4816IM
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
              *-cdrom:1
                   product: ASUS DRW-1608P3S
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-multimedia
             description: Audio device
             product: SB450 HDA Audio
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
           *-network
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:02:07.0
                logical name: eth0
                version: 10
                serial: 00:15:58:76:e0:c2
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.36 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

---

### Post by emarkd on 2008-02-05
Looks like you've got plenty of computer for Ubuntu.  Did you try that 'top' command?  You may find that something is using up lots of cycles.

---

### Post by upthelum on 2008-02-05
Does the Winblows setup freeze too. If so there could be a problem with a ram chip. I had freezes like you describe which were due to a faulty memory module but the system clock didn't change.

---

### Post by jakelute on 2008-02-05
I'm monitoring that now.
The browser (SeaMonkey at the moment) is using about 17 percent of memory (but this problem doesn't only happen when the web browser is open); otherwise, there doesn't seem to be much of anything going on.
Thanks,
J.

---

### Post by jakelute on 2008-02-05
In response to the question from upthelum: sorry, I should have said: I NEVER got crashes or freezes in Windows. So I think it's something to do with my Ubuntu installation. Perhaps I've configured something incorrectly? or some part of my system just doesn't like Ubuntu?

---

### Post by upthelum on 2008-02-05
Yeh probably the latter, no worries...

---

### Post by jakelute on 2008-02-06
any recommendations?
not sure where to go from here -- very keen to stick with Ubuntu, but can't afford to sit around for ten minutes everytime one of these freezes occurs....would love to find a way to resolve it.
Many thanks!

---

### Post by jakelute on 2008-02-06
Hi again.
Not having so far had any suggestions regarding this temporary freeze problem which I describe at the beginning of this thread, I've had another thought. When I boot up in Ubuntu, I always get an error message (see below). I wonder whether this has anything to do with my freeze problem as described above? What is this error message about, anyway? Can someone tell me? Many thanks!

Here's the message I get (the long numbers at the beginning are different every time):
34.564534] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
34.564581] PCI: Cannot allocate resource region 0 of device 0000:00:01.0

---

### Post by jakelute on 2008-03-06
Hello again,
A month later, I'm afraid I've found no way to solve this problem.
I still have a dual-boot system. I still like Ubuntu very much, and would very much like to make it my sole operating system, getting rid of windows altogether. But I've found no solution for this problem. I'm still getting numerous freezes every day -- everything freezes, the mouse is unresponsive, I can't do anything. Typically, after 5-10 minutes it wakes up again, and returns to normal -- but the clock in the upper right-hand corner is 5-10 minutes slow after the freeze. My level of knowledge and expertise is low, so I don't feel I can delve very deeply into this problem. Not having had any luck with this on the forum, I can only conclude that it's "one of those things".... Perhaps there's something on my system that doesn't "like" Ubuntu. Not sure what more I can do other than returning reluctantly to Windows, which will be painful and difficult having now discovered (thanks to Ubuntu) how much more fun things can be without Windows!
Any help very gratefully received. Many thanks, and
Best wishes.

---

### Post by jakelute on 2008-03-06
PS
I'd just like to add that this never happens to me in Windows with this computer. So I don't thnk it's likely to be faulty hardware.
thanks
By the way, this fault occurs both in 7.04 and in 7.10

---

### Post by jakelute on 2008-04-10
Hello again,

I've really enjoyed using Ubuntu (Gutsy) -- it's been an eye-opener for me, and I'd like more than anything to stay with it. In fact, on my wife's laptop (Dell Inspiron 1100), we WILL stay with it, because it's been absolutely trouble free in every way, and superior to Windows XP in every way.
However, on my PC (see all the previous posts in this thread please), I simply can't get rid of the temporary freeze problem, even after a couple of months of tinkering and trying various things. Several times a day, I get freezes, and then I just have to wait ten minutes or so for the computer to resume. Which it always does (but with the clock running ten minutes slow). 

Here is a summary of the facts:

1. This sometimes happens when running firefox, and sometimes when doing other things (such as viewing jpg files or downloading updates). The problem is NOT exclusive to Firefox.

2. I have no visual effects enabled at all.

3. I DO have a dual-boot system with Windows XP on a second internal HD, and I NEVER get crashes or freezes in XP (so I don't think it's hardware).

4. I've run memtest and get no errors at all.

5. I'm a beginner at this sort of stuff, so will unfortunately only understand simple instructions and suggestions. Sorry about that.

6. The problem happens in Hardy as well (I've updated to Hardy now to see if it's any better, and the identical problem still occurs).

7. Unfortunately there has so far been no solution to this problem, despite the kind messages from various forum members. I'm beginning to think my machine simply doesn't like Ubuntu or Ubuntu simply doesn't like my machine.

Anyway, I'm giving it one final try, and if this post doesn't result in success, I'll have to return to Windows XP (with a heavy heart, because I very much like Ubuntu, and I very much like the community, and would love to be part of it).

Then, maybe sometime in the future when this computer bites the dust, I can buy a new one which comes with Ubuntu pre-installed, to minimize the possibility of such problems in the future.

Thank you, and very best wishes,

jakelute

---

### Post by jakelute on 2008-04-12
One final thought occurs to me. Could the freeze problems have something to do with the fact that I'm on a dual boot system? If I removed Windows altogether, might the freezing problems go away?
I wonder whether anyone has had a similar experience.
Many thanks.

---

### Post by jakelute on 2008-04-19
One last observation before I give up:
I've tried removing all peripherals, and still get the problem.
I've tried with ATI proprietary driver and without, and get the problem in both cases.
I've tried every variable I can think of.
But there's a general pattern I've observed: the freezes happen with great frequency late in the day, when the computer has been on for quite a few hours. I rarely get freezes early in the day. Why would this be?
But I repeat: I never had crashes or freezes in Windows, so I don't see how it can be a hardware problem.
Many thanks!

---

### Post by unutbu on 2008-04-19
I once had a laptop that never ever froze, but once I installed a wireless network card, I started getting freezes at random moments about once every two days.

As an experiment, you might want to shut off your network interfaces, and see if the problem goes away. Then at least you might discover the part of the system which is causing the problem.

To shut of your network interfaces, you can do

```
sudo /etc/init.d/networking stop
```

I know you've said you've seen this problem even when Firefox is not running, but I think there are a number of programs (even ones that run in the background) which may try to connect to the internet without you knowing.

If you do determine that networking is the source of your problem, then maybe a different network card and different driver will allow you to avoid the problem. Or, before you do that, there may be different drivers you can try with your existing network card...

---

### Post by jakelute on 2008-04-20
Thank you very much for that reply. I'll try what you suggest. But before I do, can you just tell me the command for turning networking back on again?
Thanks.

---

### Post by unutbu on 2008-04-20
Ah. Good idea :)

Use this to start the network after a stop:
```
sudo /etc/init.d/networking start
```

If the network does not come up after a start, you sometimes might want to tell it to try again, in which case you use:
```
sudo /etc/init.d/networking restart
```

restart in simply a stop followed by a start.

Also, these commands are 'safe' in the sense that they leave no change on your machine that a reboot will not wipe away. Since your machine (presumably) activates the network upon boot, simply rebooting would restart the network too.

---

### Post by jakelute on 2008-04-20
Thank you very much for this, unutbu -- I tried it, and unfortunately I had another freeze within about an hour after turning off the network. So that is ruled out. Any other things I could try?
I've disconnected anything that was attached to my computer via usb, such as my scanner and cellphone and digital camera and so on. There's nothing left to disconnect really. Also, as I think I mentioned, I've tried both with and without the propietary ATI driver. (Without it the graphics don't work properly, unfortunately, and besides, the freezes still happen.)
I'd be enormously grateful for any further things I could try, because this system is so maddeningly close to working wonderfully! By the way, I've got rid of the dual boot now, because I wondered whether that might be the cause of the problem. But even after a fresh install of Ubuntu, with no traces left of the Windows installation, the problem is still occurring.
Oh, and by the way, the problem occurs equally in 7.04, 7.10 and 8.04 beta.
Thanks in advance for any further suggestions!
Best wishes.

---

### Post by unutbu on 2008-04-20
This is quite a puzzle. Unfortunately, I probably don't know enough to help you. However, on the off-chance that I can, here are a few hypotheses which, if we're *very* lucky, may point us toward the source of the problem:

**Hypothesis 1**: The freeze (delay) is caused by some background process. Check /var/log/messages to see if the background process is kind enough to leave a trail of complaints around the time of the freeze. Note the time of the next freeze. Wait until the machine unfreezes, then open /var/log/messages with

```
gksudo gedit /var/log/messages
```

Scroll down to the time of the freeze. Post the entries around that time here. 
[B]
Hypothesis 2[/B]: The freeze is somehow heat-related.
Supporting evidence: You've mentioned that the freezes tend to occur late in the day and when you are running a lot of processes.

Contra-indicator: the problem exihibits itself under Ubuntu but not under Windows. This suggests the problem isn't hardware related, but maybe there is some program running under Ubuntu that is monitoring the temperature and taking it upon itself to slow down all processes until the CPU cools down? I'm really grasping at straws here. 

Anyway, it would not hurt to blow a fan at the machine and see if you can avoid, delay, or diminish the frequency of the freezes. At least that might strengthen or weaken your belief in the heat-related hypothesis.

There is also a program you can install on the machine that can monitor/report the CPU temperature.

To install, these are the commands I used to get it to work:

```
sudo apt-get install lm-sensors
sudo sensors-detect  
```
(I just pressed return for YES to all questions, except the last which defaults to NO:
Do you want to add these lines to /etc/modules automatically? (yes/NO)yes
)

```
sudo modprobe it87    
sudo modprobe coretemp
```

The last two commands added the modules that were appropriate for my machine; yours may differ. Read the output of sensors-detect to determine which modules you should insert. 

Then you can find out the temp of the CPUs with
```

sensors
```

Or, open a terminal and run

```
watch sensors
```

This will run sensors every 2 seconds so you can see how the temperature changes over time and give you sense of what is a normal temperature.

If this ends up not being helpful, you can remove lm-sensors with

```
sudo apt-get remove lm-sensors
```

**Hypothesis 3**: The machine freezes when the CPU speed reaches a certain level. The command
```

cat /proc/cpuinfo | grep "cpu MHz"
```

will report the speed of your cpus.

To watch it change as you work, you could run:
```
watch "sensors && cat /proc/cpuinfo | grep \"cpu MHz\""
```

**Hypothesis 4**: The problem is quite low-level and this is exhibited by the fact that the BIOS hardware clock is freezing.

We can test whether the BIOS hardware clock is freezing by issuing the follow command after a freeze:
```

date && hwclock --show
```

date prints the system clock (updated by the linux kernel), hwclock prints the hardware clock. If date and hwclock show the same time after a freeze and they both show the wrong time (delayed by the length of the freeze) then the hardware clock must have frozen.

The hardware clock has its own battery and is supposed to keep time even when the machine is off. If it stops running that would be rather curious. I don't know what could cause that, but it would be interesting to know if that is happening.

**Hypothesis 5**: The problem is quite low-level and this is exhibited by the fact that the kernel does not respond to the soft-reboot key sequence. All commands suggested above are completely safe. The following suggestion -- to reboot -- should be safe, but you'll of course lose anything you were working on that wasn't saved before the freeze.
 
The key sequence below is a little safer that a power off/on. It at least tries to shutdown all process gracefully and unmount the filesystems so you are not left with orphaned inodes.

So, if you are willing to try this, next time the machine freezes, do a soft-reboot using Linux kernel commands:

```
Alt-SysRq-R
Alt-SysRq-E
Alt-SysRq-I
Alt-SysRq-S
Alt-SysRq-U
Alt-SysRq-B
```

Wait a few seconds between each command, because it takes a while to kill all processes and so forth.

Here is what each command does:

Alt-SysRq-R  turns off keyboard raw mode and sets it to XLATE
Alt-SysRq-E  send a SIGTERM to all processes, except for init.
Alt-SysRq-I  send a SIGKILL to all processes, except for init.
Alt-SysRq-S  will attempt to sync all mounted filesystems.
Alt-SysRq-U  will attempt to remount all mounted filesystems read-only.
Alt-SysRq-B  will immediately reboot the system without syncing or unmounting

If this works, then it means your kernel is still running. If it doesn't, it means the kernel is frozen. A frozen kernel would indicate that it is something in the kernel which is causing the freeze, perhaps a module. 

Along that line, it might be helpful if you post the output to

```
lsmod
```

Finally, here is a general purpose monitoring script which you can use to gather further information about the problem:

```
#!/usr/bin/perl
use strict;
use warnings;

my @cmd=(
    "ps axuww",
    "cat /proc/cpuinfo | grep \"cpu MHz\"",
    "sensors",
    );
my $file='monitor.out';
my $bak='monitor.out.bak';
my $last_time=time;
my $sec=2;
while (1) {
    my $cur_time=time;
    my $diff=$cur_time-$last_time;
    if ($diff > $sec+10) {
	die "There has been a freeze!";
    } else {
	$last_time=$cur_time;
	warn "diff: $diff\n";
    }
    if (-e $file) {
	my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,$atime,$mtime,$ctime,$blksize,$blocks)=stat($file);
	warn "size=$size";
	if ($size<10000) {
	    open(FILE,">>","$file") || die;
	} else {
	    rename($file,$bak);
	    open(FILE,">","$bak") || die;
	}
    } else {
	open(FILE,">","$file") || die;
    }


    foreach my $cmd (@cmd) {
	open(CMD, "$cmd |") || die;
	my ($sec,$min,$hour,$mday,$mon,$year,$wday,$yday,$isdst) = localtime;
	$year+=1900;
	$mon++;

	print FILE "$year-$mon-$mday $hour:$min:$sec % $cmd\n";
	while(<CMD>) {
	    print FILE;
	}
	close(CMD);
	print FILE "\n";
    }
    close(FILE);
    sleep($sec);
}

```
Save it in a file called monitor.pl. Make it executable

```
chmod 755 monitor.pl
```

Run it in the background:

```
monitor.pl &
```

It will create two files: monitor.out and monitor.out.bak. 
The program runs the commands 
```
ps axuww
cat /proc/cpuinfo | grep "cpu MHz"
sensors
```

every 2 seconds. The output is stored in monitor.out or monitor.out.bak. (It flip-flops the output, overwriting the older one so the files don't become huge.)
The program will stop when it detects a freeze -- when neither monitor.out nor monitor.out.bak gets written for more than 2 seconds.

Post the contents of monitor.out or monitor.out.bak (whichever is more recent) and hopefully it will contain something interesting.

---

### Post by Sinkingships7 on 2008-04-20
I've had this happen on a few Ubuntu installs as well, always on the same computer though. All it took was a reinstall of Ubuntu to fix the problem. It seems that Ubuntu does not always install correctly the first time. Always after the second re-installation, everything works perfectly.

---

### Post by jakelute on 2008-04-20
Big thanks both to unutbu and to sinkinships7 for those useful replies!

Sinkingships7: this is my third install, and the problem has been the same each time, so I'm not sure that reinstalling again is the answer.

Unutbu, I'm very grateful to you for taking so much time to send such a detailed and thoughtful list of things to try. It's going to take me a while to get through your suggestions (I'm pretty new to all of this, and they look slightly complicated!), but I WILL work my way through them, and I'll report back. But it may take me a few days.

It's nice to think that maybe we can crack this thing.

Many thanks again. Best wishes,

J

---

### Post by Sinkingships7 on 2008-04-20
Perhaps burn a new CD?

---

### Post by jakelute on 2008-04-21
In reply to Unutbu:
I've started looking into the things you suggested.

1. log messages: I've copied several below -- at the time of the freezes, one of two things appears in the message log: a) in numerous cases, there's nothing at all in the log at the time of the freeze or at the time of the spontaneous unfreeze; but b) in quite a few cases, where there was a message at the time of the freeze (or the unfreeze, to be more precise), there has been a message about the clocksource being unstable (see below). I have no idea what any of these things mean, and I'm hoping you might be able to help. Also, on those occasions where I got tired of waiting for an unfreeze to happen, and pressed the reset button, there is obviously a set of bootup messages. I've included some info from one of these (sorry this is a long post), because I'm curious about some of the things in it, and wonder whether they are relevant. Again, see below.

2. secondly, you mentioned heat: I take it back -- on closer observation, I don't think this is heat related -- I thought at one time that the problem was worse when the machine had been on for hours, but I don't think this is the case after all

3. thirdly, you mentioned that maybe it's freezing when the CPU speed reaches a certain level -- I haven't investigated this one yet -- will get back to you

4. fourth, you mentioned that the BIOS hardware clock may be freezing -- this is really weird -- I ran your test just now (shortly after a freeze): "date" shows a time which is about ten minutes slow, and "hwclock" shows a time which is about five minutes slow! Both are wrong. My  hardware clock was right earlier today! you say that the latter runs on a battery -- could there be something wrong with this battery? It does not appear to be keeping time very reliably!

5. I tried 
Alt-SysRq-R
Alt-SysRq-E
Alt-SysRq-I
Alt-SysRq-S
Alt-SysRq-U
Alt-SysRq-B
during a freeze, and nothing appeared to happen -- does this mean kernel is frozen?
You said I should post the output to "lsmod", which I'll do below. I haven't yet had time to implement the other longer monitoring script which you kindly provided.

Here, below, is some output. Thanks again!!!!

First of all, I mentioned that there's often no message during a freeze and unfreeze. But when there is, it usually includes something about the unstable clock. Here are several examples of this:

Apr 21 09:08:26 jake kernel: [  302.918660] sd 6:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
Apr 21 09:08:26 jake kernel: [  302.919056] sd 6:0:0:0: [sdb] Write Protect is off
Apr 21 09:08:26 jake kernel: [  302.919849] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 21 09:08:26 jake kernel: [  302.919855]  sdb: sdb1
Apr 21 09:08:26 jake kernel: [  302.928532] sd 6:0:0:0: [sdb] Attached SCSI disk
Apr 21 09:08:26 jake kernel: [  302.928589] sd 6:0:0:0: Attached scsi generic sg3 type 14
Apr 21 09:13:22 jake kernel: [  598.739057] Clocksource tsc unstable (delta = 253095255618 ns)
Apr 21 09:13:22 jake kernel: [  598.739805] Time: acpi_pm clocksource has been installed.
Apr 21 09:21:50 jake syslogd 1.5.0#1ubuntu1: restart.

another example:

Apr 21 10:03:08 jake -- MARK --
Apr 21 10:23:22 jake kernel: [ 2455.158616] Clocksource tsc unstable (delta = 65619961562 ns)
Apr 21 10:23:22 jake kernel: [ 2455.162926] Time: acpi_pm clocksource has been installed.
Apr 21 10:43:52 jake -- MARK --


again:

Apr 21 11:01:15 jake kernel: [   53.103060] hda-intel: Invalid position buffer, using LPIB read method instead.
Apr 21 11:10:21 jake kernel: [  598.737797] Clocksource tsc unstable (delta = 182875775084 ns)
Apr 21 11:10:21 jake kernel: [  598.741515] Time: acpi_pm clocksource has been installed.
Apr 21 11:10:21 jake kernel: [  598.758086] SysRq : Keyboard mode set to system default
Apr 21 11:10:21 jake exiting on signal 15
Apr 21 11:50:08 jake syslogd 1.5.0#1ubuntu1: restart.

another:

Apr 21 13:21:31 jake -- MARK --
Apr 21 13:38:07 jake kernel: [ 5834.895614] Clocksource tsc unstable (delta = 323383237004 ns)
Apr 21 13:38:07 jake kernel: [ 5834.900011] Time: acpi_pm clocksource has been installed.
Apr 21 13:39:58 jake kernel: [ 5945.941489] r8169: eth0: link up


Now, here's the output to "lsmod"

jake@jake:~$ lsmod
Module                  Size  Used by
binfmt_misc            12808  1
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0
acpi_cpufreq           10796  0
cpufreq_powersave       2688  0
cpufreq_stats           7104  0
cpufreq_ondemand        9740  2
cpufreq_userspace       5284  0
cpufreq_conservative     8712  0
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
dock                   11280  0
video                  19856  0
output                  4736  1 video
container               5632  0
sbs                    15112  0
sbshc                   7680  1 sbs
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  267780  10
af_packet              23812  2
ac                      6916  0
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         344600  3
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
fglrx                1555468  20
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0
i2c_piix4               9612  0
button                  9232  0
pci_hotplug            30880  1 shpchp
i2c_core               24832  1 i2c_piix4
soundcore               8800  1 snd
ati_agp                 9996  0
agpgart                34760  2 fglrx,ati_agp
evdev                  13056  3
pcspkr                  4224  0
psmouse                40336  0
ext3                  136712  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  3
atiixp                  5648  0 [permanent]
ide_core              113996  1 atiixp
ata_generic             8324  0
sata_sil               12296  2
ehci_hcd               37900  0
ohci1394               33584  0
r8169                  32900  0
floppy                 59588  0
ohci_hcd               25348  0
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0
usbcore               146028  3 ehci_hcd,ohci_hcd
pata_atiixp             8960  0
libata                159344  4 ata_generic,sata_sil,pata_acpi,pata_atiixp
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                16796  0
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 


Finally, in the very long list of messages when I hit the restart button, there are a couple which I want to ask you about, in case they are relevant. Again, this is all way over my head, but I'd just like to check.

1. is this something to worry about?
Apr 21 11:01:04 jake kernel: [   16.073738] Setting up standard PCI resources
Apr 21 11:01:04 jake kernel: [   16.076974] mtrr: your CPUs had inconsistent variable MTRR settings
Apr 21 11:01:04 jake kernel: [   16.076976] mtrr: probably your BIOS does not setup all CPUs.
Apr 21 11:01:04 jake kernel: [   16.076977] mtrr: corrected configuration.

2. what about this?
Apr 21 11:01:04 jake kernel: [   29.810619] Driver 'sd' needs updating - please use bus_type methods
and this?
Apr 21 11:01:04 jake kernel: [   29.810872]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
and this?
Apr 21 11:01:04 jake kernel: [   16.107327] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Apr 21 11:01:04 jake kernel: [   16.107330] PCI: Cannot allocate resource region 0 of device 0000:00:01.0


Thanks again for the help. I'm really sorry this is such a long post!

---

### Post by jakelute on 2008-04-22
A brief PS:
I've continued to monitor the freezing incidents, and I can confirm that the message about the "unstable clocksource" always comes at exactly the time that the computer wakes up again after a freeze -- here's an example:

Apr 21 10:23:22 jake kernel: [ 2455.158616] Clocksource tsc unstable (delta = 65619961562 ns)
Apr 21 10:23:22 jake kernel: [ 2455.162926] Time: acpi_pm clocksource has been installed.

Thanks. Looking forward to any help available!

---

### Post by unutbu on 2008-04-22
I've been googling "clocksource tsc unstable"
and come up with some semi-interesting pages. Still reading  through it.

In the meantime, would you please post
```

sudo cat /sys/devices/system/clocksource/clocksource0/available_clocksource 
sudo cat /proc/version
```

After a freeze:
```
sudo cat /sys/devices/system/clocksource/clocksource0/current_clocksource 

```
After a reboot, and before the first freeze:
```
sudo cat /sys/devices/system/clocksource/clocksource0/current_clocksource 

```

---

### Post by jakelute on 2008-04-22
Here is part one of my reply -- the other to follow

1.
jake@jake:~$ sudo cat /sys/devices/system/clocksource/clocksource0/available_clocksource
[sudo] password for jake: 
acpi_pm jiffies tsc 
jake@jake:~$ 

2.
jake@jake:~$ sudo cat /proc/version
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
jake@jake:~$

---

### Post by jakelute on 2008-04-22
part two of my reply (part three to follow)

this is straight after a crash and spontaneous recovery

jake@jake:~$ sudo cat /sys/devices/system/clocksource/clocksource0/current_clocksource
acpi_pm 
jake@jake:~$

---

### Post by jakelute on 2008-04-22
Here's the third and final part of my reply:
after a crash and reboot, and before the next crash:

jake@jake:~$ sudo cat /sys/devices/system/clocksource/clocksource0/current_clocksource
[sudo] password for jake: 
tsc 
jake@jake:~$

---

### Post by unutbu on 2008-04-22
The unstable clocksource message may be a red herring -- a complaint caused by the problem, but not itself the source of the problem. (All the web posts I've come across so far seem to indicate there are ways to avoid the unstable clocksource message (by disabling tsc, time stamp counter, (kernel option notsc) or setting the clocksource to acpi_pm (kernel option clocksource=acpi_pm)), but other people's freezing problem persists.

If setting the clocksource to acpi_pm was a fix, and the kernel does this itself after the first freeze, then why should you ever experience a second freeze?

However, I don't think there is any harm in trying, so if you agree, here's how to set the clocksource to acpi_pm at boot:

```
gksudo gedit /boot/grub/menu.lst
```

Go down to around line 130 where you'll see stanzas like this (Note your stanzas may look somewhat different, like 2.6.24-16 instead of 2.6.22-14.):

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Edit the line that begins with "kernel" by adding to the end "clocksource=acpi_pm":

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro clocksource=acpi_pm
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

You may also want to remove the words "quiet splash" if you see that. 
This will give you a more verbose boot message instead of the orange bar. 
I prefer it, but I can't say its very useful because the messages go by too quickly.

---

### Post by jakelute on 2008-04-22
Tremendous! Thanks. I'll try it. I suppose there's no great reason to be optimistic, because, as you say, it's probably a symptom rather than a cause, but I'll give it a try.
Before I do, could you tell me one thing? What does it actually mean "setting the clocksource to acpi_pm at boot"? It's Greek to me. And does doing this have implications I should be aware of?
I'll try it and report back.
Your help is immensely appreciated. I was on the verge of giving up a few days ago!

---

### Post by jakelute on 2008-04-22
I've run the command you suggest. When I scroll down to look for the stanza you mention, I get this:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I'm stuck now, because I'm not sure which of these many entries I'm supposed to edit. Or do I change them all?

---

### Post by unutbu on 2008-04-22
I'm really glad you check things out before you try them. It's extremely important that you understand what you are doing before you change your system, otherwise you may end up with a bigger problem than the one you are trying to fix.

Editing /boot/grub/menu.lst (I'm sorry, I should have warned you) is a little bit dangerous. If you do it wrong, your system may be unable to boot until you fix menu.lst. Generally, this just means boot from a Live CD and editing menu.lst. It's not really a big deal, but I can understand why people would feel anxious if their computer stops booting.

So, we are entering the territory where it is highly advisable to have a backup of all your data.

I don't know much about clocksource -- apparently there are various methods (tsc, acpi_pm, jiffies) which all try to do the same thing -- keep track of time based on estimations of the CPU speed and counting ticks of a crystal.

See [http://groups.google.com/group/comp.protocols.time.ntp/browse_thread/thread/d7bfff3883b321e9](http://groups.google.com/group/comp.protocols.time.ntp/browse_thread/thread/d7bfff3883b321e9)
Search for David Woolley's comments.

The linux kernel, your operating system, is by default choosing tsc to keep track of time. We can tell the kernel at boot-up that we want to use the acpi_pm method to keep track of time instead. That's what I meant by 
"setting the clocksource to acpi_pm at boot". 

So, to try acpi_pm (at boot), edit /boot/grub/menu.lst. Instead of editing a stanza as I said above, let's add a new stanza. That way, we can still boot the old way if necessary.

So just before the other stanzas, insert the following:

```
title Use acpi_pm
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro clocksource=acpi_pm
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```

Making this the first stanza will make it the default method of booting.

You may also be wondering where arcane kernel options like "clocksource=acpi_pm" come from. 
I found the above googling and reading other forum posts. But you can also learn more by reading 
[http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf](http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf)
Search for the word clocksource, for example.

---

### Post by jakelute on 2008-04-22
I did as you suggest -- added the new stanza.
Restarted at about 20:55:00.
Had another freeze  :(  at 21:01:29, which spontaneously recovered at about 21:05:00 -- I attach the log of events during that period. At the very bottom, you'll see the time of the freeze and recovery. What those entries mean, I've no idea! Please note, I was in the middle of printing this entire thread to pdf for safekeeping when the crash occured. I think there's something about pdf in the report below.

At precisely the time of the crash, it says 
Apr 22 21:01:30 jake kernel: [  641.139234] Clocksource tsc unstable (delta = 234325146668 ns)

That seems strange, as we changed the clocksource!

(question: is this important? Apr 22 20:55:25 jake kernel: [   18.730083] PCI: MSI quirk detected. MSI deactivated.

also: Apr 22 20:55:25 jake kernel: [   27.189002] Cannot allocate resource for EISA slot 4)


Apr 22 20:54:28 jake kernel: [  635.760119] [fglrx] interrupt source 10000000 successfully disabled!
Apr 22 20:54:28 jake kernel: [  635.760124] [fglrx] enable ID = 0x00000000
Apr 22 20:54:28 jake kernel: [  635.760127] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
Apr 22 20:54:29 jake kernel: [  636.789222] gdm[5165]: segfault at 10c04f78 eip b782a635 esp bfae1880 error 4
Apr 22 20:54:32 jake kernel: [  639.930003] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 22 20:54:33 jake exiting on signal 15
Apr 22 20:55:25 jake syslogd 1.5.0#1ubuntu1: restart.
Apr 22 20:55:25 jake kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 22 20:55:25 jake kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 22 20:55:25 jake kernel: Symbols match kernel version 2.6.24.
Apr 22 20:55:25 jake kernel: Loaded 23545 symbols from 83 modules.
Apr 22 20:55:25 jake kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 22 20:55:25 jake kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 22 20:55:25 jake kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Apr 22 20:55:25 jake kernel: [    0.000000] 62MB HIGHMEM available.
Apr 22 20:55:25 jake kernel: [    0.000000] 896MB LOWMEM available.
Apr 22 20:55:25 jake kernel: [    0.000000] found SMP MP-table at 000f4080
Apr 22 20:55:25 jake kernel: [    0.000000] Zone PFN ranges:
Apr 22 20:55:25 jake kernel: [    0.000000]   DMA             0 ->     4096
Apr 22 20:55:25 jake kernel: [    0.000000]   Normal       4096 ->   229376
Apr 22 20:55:25 jake kernel: [    0.000000]   HighMem    229376 ->   245488
Apr 22 20:55:25 jake kernel: [    0.000000] Movable zone start PFN for each node
Apr 22 20:55:25 jake kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 22 20:55:25 jake kernel: [    0.000000]     0:        0 ->   245488
Apr 22 20:55:25 jake kernel: [    0.000000] DMI 2.2 present.
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F87E0 checksum 0
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: RSDP 000F87E0, 0014 (r0 RS400 )
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: RSDT 3BEF3040, 0038 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: DSDT 3BEF3180, 416F (r1 RS400  AWRDACPI     1000 MSFT  100000E)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: FACS 3BEF0000, 0040
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: MCFG 3BEF7440, 003C (r1 RS400  AWRDACPI 42302E31 AWRD        0)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: APIC 3BEF7340, 0084 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: SSDT 3BEF74C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: SSDT 3BEF7950, 022A (r1  PmRef    CpuPm     3000 INTL 20041203)
Apr 22 20:55:25 jake kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 22 20:55:25 jake kernel: [    0.000000] Processor #0 15:6 APIC version 20
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 22 20:55:25 jake kernel: [    0.000000] Processor #1 15:6 APIC version 20
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Apr 22 20:55:25 jake kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 22 20:55:25 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr 22 20:55:25 jake kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 22 20:55:25 jake kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 22 20:55:25 jake kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:a4100000)
Apr 22 20:55:25 jake kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 22 20:55:25 jake kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Apr 22 20:55:25 jake kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Apr 22 20:55:25 jake kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243571
Apr 22 20:55:25 jake kernel: [    0.000000] Kernel command line: root=UUID=d5ca58d0-0c95-4ef7-bbf9-1e096847d371 ro clocksource=acpi_pm
Apr 22 20:55:25 jake kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 22 20:55:25 jake kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 22 20:55:25 jake kernel: [    0.000000] Initializing CPU#0
Apr 22 20:55:25 jake kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 22 20:55:25 jake kernel: [    0.000000] Detected 3399.951 MHz processor.
Apr 22 20:55:25 jake kernel: [   17.345531] Console: colour VGA+ 80x25
Apr 22 20:55:25 jake kernel: [   17.345536] console [tty0] enabled
Apr 22 20:55:25 jake kernel: [   17.349128] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 22 20:55:25 jake kernel: [   17.349837] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 22 20:55:25 jake kernel: [   17.371238] Memory: 961312k/981952k available (2157k kernel code, 20052k reserved, 998k data, 364k init, 64448k highmem)
Apr 22 20:55:25 jake kernel: [   17.371302] virtual kernel memory layout:
Apr 22 20:55:25 jake kernel: [   17.371303]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 22 20:55:25 jake kernel: [   17.371304]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 22 20:55:25 jake kernel: [   17.371305]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 22 20:55:25 jake kernel: [   17.371306]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 22 20:55:25 jake kernel: [   17.371307]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 22 20:55:25 jake kernel: [   17.371308]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 22 20:55:25 jake kernel: [   17.371309]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 22 20:55:25 jake kernel: [   17.371666] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 22 20:55:25 jake kernel: [   17.371786] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 22 20:55:25 jake kernel: [   17.451810] Calibrating delay using timer specific routine.. 6807.29 BogoMIPS (lpj=13614582)
Apr 22 20:55:25 jake kernel: [   17.451919] Security Framework initialized
Apr 22 20:55:25 jake kernel: [   17.451967] SELinux:  Disabled at boot.
Apr 22 20:55:25 jake kernel: [   17.452022] AppArmor: AppArmor initialized
Apr 22 20:55:25 jake kernel: [   17.452069] Failure registering capabilities with primary security module.
Apr 22 20:55:25 jake kernel: [   17.452122] Mount-cache hash table entries: 512
Apr 22 20:55:25 jake kernel: [   17.452284] monitor/mwait feature present.
Apr 22 20:55:25 jake kernel: [   17.452330] using mwait in idle threads.
Apr 22 20:55:25 jake kernel: [   17.452378] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 22 20:55:25 jake kernel: [   17.452460] CPU: L2 cache: 2048K
Apr 22 20:55:25 jake kernel: [   17.452505] CPU: Physical Processor ID: 0
Apr 22 20:55:25 jake kernel: [   17.452550] CPU: Processor Core ID: 0
Apr 22 20:55:25 jake kernel: [   17.452604] Compat vDSO mapped to ffffe000.
Apr 22 20:55:25 jake kernel: [   17.452661] Checking 'hlt' instruction... OK.
Apr 22 20:55:25 jake kernel: [   17.468263] SMP alternatives: switching to UP code
Apr 22 20:55:25 jake kernel: [   17.470019] Early unpacking initramfs... done
Apr 22 20:55:25 jake kernel: [   17.736311] ACPI: Core revision 20070126
Apr 22 20:55:25 jake kernel: [   17.736404] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 22 20:55:25 jake kernel: [   17.764223] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
Apr 22 20:55:25 jake kernel: [   17.764364] SMP alternatives: switching to SMP code
Apr 22 20:55:25 jake kernel: [   17.765177] Booting processor 1/1 eip 3000
Apr 22 20:55:25 jake kernel: [   17.775690] Initializing CPU#1
Apr 22 20:55:25 jake kernel: [   17.855549] Calibrating delay using timer specific routine.. 6799.84 BogoMIPS (lpj=13599680)
Apr 22 20:55:25 jake kernel: [   17.855564] monitor/mwait feature present.
Apr 22 20:55:25 jake kernel: [   17.855569] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 22 20:55:25 jake kernel: [   17.855571] CPU: L2 cache: 2048K
Apr 22 20:55:25 jake kernel: [   17.855573] CPU: Physical Processor ID: 0
Apr 22 20:55:25 jake kernel: [   17.855574] CPU: Processor Core ID: 1
Apr 22 20:55:25 jake kernel: [   17.856109] CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
Apr 22 20:55:25 jake kernel: [   17.856555] Total of 2 processors activated (13607.13 BogoMIPS).
Apr 22 20:55:25 jake kernel: [   17.856768] ENABLING IO-APIC IRQs
Apr 22 20:55:25 jake kernel: [   17.856996] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 22 20:55:25 jake kernel: [   18.003552] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 22 20:55:25 jake kernel: [   18.023640] Brought up 2 CPUs
Apr 22 20:55:25 jake kernel: [   18.023913] net_namespace: 64 bytes
Apr 22 20:55:25 jake kernel: [   18.023963] Booting paravirtualized kernel on bare hardware
Apr 22 20:55:25 jake kernel: [   18.024572] Time: 19:55:01  Date: 04/22/08
Apr 22 20:55:25 jake kernel: [   18.024639] NET: Registered protocol family 16
Apr 22 20:55:25 jake kernel: [   18.024892] EISA bus registered
Apr 22 20:55:25 jake kernel: [   18.024940] ACPI: bus type pci registered
Apr 22 20:55:25 jake kernel: [   18.027184] PCI: PCI BIOS revision 3.00 entry at 0xfb170, last bus=2
Apr 22 20:55:25 jake kernel: [   18.027232] PCI: Using configuration type 1
Apr 22 20:55:25 jake kernel: [   18.027276] Setting up standard PCI resources
Apr 22 20:55:25 jake kernel: [   18.030570] mtrr: your CPUs had inconsistent variable MTRR settings
Apr 22 20:55:25 jake kernel: [   18.030618] mtrr: probably your BIOS does not setup all CPUs.
Apr 22 20:55:25 jake kernel: [   18.030664] mtrr: corrected configuration.
Apr 22 20:55:25 jake kernel: [   18.036431] ACPI: Interpreter enabled
Apr 22 20:55:25 jake kernel: [   18.036478] ACPI: (supports S0 S1 S4 S5)
Apr 22 20:55:25 jake kernel: [   18.036679] ACPI: Using IOAPIC for interrupt routing
Apr 22 20:55:25 jake kernel: [   18.041146] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 22 20:55:25 jake kernel: [   18.042674] PCI: Transparent bridge - 0000:00:14.4
Apr 22 20:55:25 jake kernel: [   18.057598] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Apr 22 20:55:25 jake kernel: [   18.058141] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Apr 22 20:55:25 jake kernel: [   18.058680] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Apr 22 20:55:25 jake kernel: [   18.059220] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Apr 22 20:55:25 jake kernel: [   18.059778] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11)
Apr 22 20:55:25 jake kernel: [   18.060242] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Apr 22 20:55:25 jake kernel: [   18.060786] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
Apr 22 20:55:25 jake kernel: [   18.061251] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
Apr 22 20:55:25 jake kernel: [   18.061756] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 22 20:55:25 jake kernel: [   18.061835] pnp: PnP ACPI init
Apr 22 20:55:25 jake kernel: [   18.061885] ACPI: bus type pnp registered
Apr 22 20:55:25 jake kernel: [   18.064564] pnp: PnP ACPI: found 13 devices
Apr 22 20:55:25 jake kernel: [   18.064610] ACPI: ACPI bus type pnp unregistered
Apr 22 20:55:25 jake kernel: [   18.064658] PnPBIOS: Disabled by ACPI PNP
Apr 22 20:55:25 jake kernel: [   18.064939] PCI: Using ACPI for IRQ routing
Apr 22 20:55:25 jake kernel: [   18.064985] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 22 20:55:25 jake kernel: [   18.065044] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Apr 22 20:55:25 jake kernel: [   18.065093] PCI: Cannot allocate resource region 0 of device 0000:00:01.0
Apr 22 20:55:25 jake kernel: [   18.099426] NET: Registered protocol family 8
Apr 22 20:55:25 jake kernel: [   18.099476] NET: Registered protocol family 20
Apr 22 20:55:25 jake kernel: [   18.099592] AppArmor: AppArmor Filesystem Enabled
Apr 22 20:55:25 jake kernel: [   18.103420] Time: tsc clocksource has been installed.
Apr 22 20:55:25 jake kernel: [   18.111470] system 00:01: ioport range 0x140-0x15f has been reserved
Apr 22 20:55:25 jake kernel: [   18.111525] system 00:01: ioport range 0x228-0x22f has been reserved
Apr 22 20:55:25 jake kernel: [   18.111572] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Apr 22 20:55:25 jake kernel: [   18.111620] system 00:01: ioport range 0xc00-0xc01 has been reserved
Apr 22 20:55:25 jake kernel: [   18.111667] system 00:01: ioport range 0xc14-0xc14 has been reserved
Apr 22 20:55:25 jake kernel: [   18.111714] system 00:01: ioport range 0xc50-0xc52 has been reserved
Apr 22 20:55:25 jake kernel: [   18.111761] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Apr 22 20:55:25 jake kernel: [   18.111810] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Apr 22 20:55:25 jake kernel: [   18.111857] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Apr 22 20:55:25 jake kernel: [   18.111905] system 00:01: ioport range 0x4000-0x40fe has been reserved
Apr 22 20:55:25 jake kernel: [   18.111952] system 00:01: ioport range 0x4210-0x4217 has been reserved
Apr 22 20:55:25 jake kernel: [   18.112005] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Apr 22 20:55:25 jake kernel: [   18.112052] system 00:06: ioport range 0x220-0x225 has been reserved
Apr 22 20:55:25 jake kernel: [   18.112099] system 00:06: ioport range 0x40b-0x41a has been reserved
Apr 22 20:55:25 jake kernel: [   18.112147] system 00:06: ioport range 0x880-0x88f has been reserved
Apr 22 20:55:25 jake kernel: [   18.112201] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.112257] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
Apr 22 20:55:25 jake kernel: [   18.112305] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.112353] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.112401] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.112448] system 00:0c: iomem range 0x3bf00000-0x3bffffff has been reserved
Apr 22 20:55:25 jake kernel: [   18.112496] system 00:0c: iomem range 0x3bef0000-0x3befffff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.112549] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.112603] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.112650] system 00:0c: iomem range 0x100000-0x3beeffff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.113174] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.113227] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.113280] system 00:0c: iomem range 0xfff80000-0xfffeffff could not be reserved
Apr 22 20:55:25 jake kernel: [   18.143771] PCI: Bridge: 0000:00:01.0
Apr 22 20:55:25 jake kernel: [   18.143818]   IO window: e000-efff
Apr 22 20:55:25 jake kernel: [   18.143864]   MEM window: fde00000-fdefffff
Apr 22 20:55:25 jake kernel: [   18.143911]   PREFETCH window: d8000000-dfffffff
Apr 22 20:55:25 jake kernel: [   18.143959] PCI: Bridge: 0000:00:14.4
Apr 22 20:55:25 jake kernel: [   18.144005]   IO window: d000-dfff
Apr 22 20:55:25 jake kernel: [   18.144055]   MEM window: fdd00000-fddfffff
Apr 22 20:55:25 jake kernel: [   18.144103]   PREFETCH window: fdc00000-fdcfffff
Apr 22 20:55:25 jake kernel: [   18.144180] NET: Registered protocol family 2
Apr 22 20:55:25 jake kernel: [   18.147401] Time: acpi_pm clocksource has been installed.
Apr 22 20:55:25 jake kernel: [   18.183447] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 22 20:55:25 jake kernel: [   18.183825] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 22 20:55:25 jake kernel: [   18.184515] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 22 20:55:25 jake kernel: [   18.184951] TCP: Hash tables configured (established 131072 bind 65536)
Apr 22 20:55:25 jake kernel: [   18.184998] TCP reno registered
Apr 22 20:55:25 jake kernel: [   18.195503] checking if image is initramfs... it is
Apr 22 20:55:25 jake kernel: [   18.724826] Freeing initrd memory: 7430k freed
Apr 22 20:55:25 jake kernel: [   18.726044] audit: initializing netlink socket (disabled)
Apr 22 20:55:25 jake kernel: [   18.726117] audit(1208894101.208:1): initialized
Apr 22 20:55:25 jake kernel: [   18.726398] highmem bounce pool size: 64 pages
Apr 22 20:55:25 jake kernel: [   18.729501] VFS: Disk quotas dquot_6.5.1
Apr 22 20:55:25 jake kernel: [   18.729661] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 22 20:55:25 jake kernel: [   18.729867] io scheduler noop registered
Apr 22 20:55:25 jake kernel: [   18.729917] io scheduler anticipatory registered
Apr 22 20:55:25 jake kernel: [   18.729966] io scheduler deadline registered
Apr 22 20:55:25 jake kernel: [   18.730026] io scheduler cfq registered (default)
Apr 22 20:55:25 jake kernel: [   18.730083] PCI: MSI quirk detected. MSI deactivated.
Apr 22 20:55:25 jake kernel: [   26.776872] 0000:00:13.2 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Apr 22 20:55:25 jake kernel: [   26.777406] isapnp: Scanning for PnP cards...
Apr 22 20:55:25 jake kernel: [   27.128898] isapnp: No Plug & Play device found
Apr 22 20:55:25 jake kernel: [   27.175503] Real Time Clock Driver v1.12ac
Apr 22 20:55:25 jake kernel: [   27.175700] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 22 20:55:25 jake kernel: [   27.175934] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 22 20:55:25 jake kernel: [   27.176920] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 22 20:55:25 jake kernel: [   27.178234] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 22 20:55:25 jake kernel: [   27.178391] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 22 20:55:25 jake kernel: [   27.178603] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 22 20:55:25 jake kernel: [   27.179096] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 22 20:55:25 jake kernel: [   27.179152] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 22 20:55:25 jake kernel: [   27.188735] mice: PS/2 mouse device common for all mice
Apr 22 20:55:25 jake kernel: [   27.188934] EISA: Probing bus 0 at eisa.0
Apr 22 20:55:25 jake kernel: [   27.189002] Cannot allocate resource for EISA slot 4
Apr 22 20:55:25 jake kernel: [   27.189067] EISA: Detected 0 cards.
Apr 22 20:55:25 jake kernel: [   27.189115] cpuidle: using governor ladder
Apr 22 20:55:25 jake kernel: [   27.189160] cpuidle: using governor menu
Apr 22 20:55:25 jake kernel: [   27.189301] NET: Registered protocol family 1
Apr 22 20:55:25 jake kernel: [   27.189381] Using IPI No-Shortcut mode
Apr 22 20:55:25 jake kernel: [   27.189460] registered taskstats version 1
Apr 22 20:55:25 jake kernel: [   27.189613]   Magic number: 4:547:951
Apr 22 20:55:25 jake kernel: [   27.189692]   hash matches device ttya6
Apr 22 20:55:25 jake kernel: [   27.189939]   hash matches device tty8
Apr 22 20:55:25 jake kernel: [   27.190012] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 22 20:55:25 jake kernel: [   27.190058] EDD information not available.
Apr 22 20:55:25 jake kernel: [   27.190482] Freeing unused kernel memory: 364k freed
Apr 22 20:55:25 jake kernel: [   27.228541] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 22 20:55:25 jake kernel: [   27.385763] fuse init (API version 7.9)
Apr 22 20:55:25 jake kernel: [   27.401830] ACPI: Fan [FAN] (on)
Apr 22 20:55:25 jake kernel: [   27.408159] ACPI: SSDT 3BEF78C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
Apr 22 20:55:25 jake kernel: [   27.408443] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Apr 22 20:55:25 jake kernel: [   27.408579] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Apr 22 20:55:25 jake kernel: [   27.409978] ACPI: Thermal Zone [THRM] (40 C)
Apr 22 20:55:25 jake kernel: [   27.531628] SCSI subsystem initialized
Apr 22 20:55:25 jake kernel: [   27.559820] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 16
Apr 22 20:55:25 jake kernel: [   27.559990] ACPI: PCI interrupt for device 0000:00:11.0 disabled
Apr 22 20:55:25 jake kernel: [   27.560073] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
Apr 22 20:55:25 jake kernel: [   27.560195] ACPI: PCI interrupt for device 0000:00:12.0 disabled
Apr 22 20:55:25 jake kernel: [   27.560279] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
Apr 22 20:55:25 jake kernel: [   27.560398] ACPI: PCI interrupt for device 0000:00:14.1 disabled
Apr 22 20:55:25 jake kernel: [   27.570813] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 16
Apr 22 20:55:25 jake kernel: [   27.571620] scsi0 : sata_sil
Apr 22 20:55:25 jake kernel: [   27.572152] scsi1 : sata_sil
Apr 22 20:55:25 jake kernel: [   27.572378] ata1: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe080 irq 16
Apr 22 20:55:25 jake kernel: [   27.572427] ata2: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe0c0 irq 16
Apr 22 20:55:25 jake kernel: [   27.617185] usbcore: registered new interface driver usbfs
Apr 22 20:55:25 jake kernel: [   27.617294] usbcore: registered new interface driver hub
Apr 22 20:55:25 jake kernel: [   27.617727] usbcore: registered new device driver usb
Apr 22 20:55:25 jake kernel: [   27.815455] Floppy drive(s): fd0 is 1.44M
Apr 22 20:55:25 jake kernel: [   27.832978] FDC 0 is a post-1991 82077
Apr 22 20:55:25 jake kernel: [   27.884051] ata1: SATA link down (SStatus 0 SControl 310)
Apr 22 20:55:25 jake kernel: [   28.195839] ata2: SATA link down (SStatus 0 SControl 310)
Apr 22 20:55:25 jake kernel: [   28.196068] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
Apr 22 20:55:25 jake kernel: [   28.203951] scsi2 : sata_sil
Apr 22 20:55:25 jake kernel: [   28.204931] scsi3 : sata_sil
Apr 22 20:55:25 jake kernel: [   28.205135] ata3: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd080 irq 17
Apr 22 20:55:25 jake kernel: [   28.205185] ata4: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd0c0 irq 17
Apr 22 20:55:25 jake kernel: [   28.671473] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Apr 22 20:55:25 jake kernel: [   28.720094] ata3.00: ATA-7: ST3320620AS, 3.AAJ, max UDMA/133
Apr 22 20:55:25 jake kernel: [   28.720151] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr 22 20:55:25 jake kernel: [   28.786687] ata3.00: configured for UDMA/100
Apr 22 20:55:25 jake kernel: [   29.095129] ata4: SATA link down (SStatus 0 SControl 310)
Apr 22 20:55:25 jake kernel: [   29.095322] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
Apr 22 20:55:25 jake kernel: [   29.095710] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
Apr 22 20:55:25 jake kernel: [   29.095827] ohci_hcd 0000:00:13.0: OHCI Host Controller
Apr 22 20:55:25 jake kernel: [   29.096170] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Apr 22 20:55:25 jake kernel: [   29.096271] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfdffc000
Apr 22 20:55:25 jake kernel: [   29.156192] usb usb1: configuration #1 chosen from 1 choice
Apr 22 20:55:25 jake kernel: [   29.156269] hub 1-0:1.0: USB hub found
Apr 22 20:55:25 jake kernel: [   29.156324] hub 1-0:1.0: 4 ports detected
Apr 22 20:55:25 jake kernel: [   29.259122] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
Apr 22 20:55:25 jake kernel: [   29.259225] ohci_hcd 0000:00:13.1: OHCI Host Controller
Apr 22 20:55:25 jake kernel: [   29.259294] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Apr 22 20:55:25 jake kernel: [   29.259360] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfdffb000
Apr 22 20:55:25 jake kernel: [   29.319033] usb usb2: configuration #1 chosen from 1 choice
Apr 22 20:55:25 jake kernel: [   29.319104] hub 2-0:1.0: USB hub found
Apr 22 20:55:25 jake kernel: [   29.319157] hub 2-0:1.0: 4 ports detected
Apr 22 20:55:25 jake kernel: [   29.419031] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
Apr 22 20:55:25 jake kernel: [   29.419229] scsi4 : pata_atiixp
Apr 22 20:55:25 jake kernel: [   29.419323] scsi5 : pata_atiixp
Apr 22 20:55:25 jake kernel: [   29.420197] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
Apr 22 20:55:25 jake kernel: [   29.420246] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
Apr 22 20:55:25 jake kernel: [   30.058921] ata6.00: ATAPI: CD-RW BCE4816IM, VER 482S, max UDMA/33
Apr 22 20:55:25 jake kernel: [   30.058989] ata6.01: ATAPI: ASUS    DRW-1608P3S, 1.24, max UDMA/33
Apr 22 20:55:25 jake kernel: [   30.230776] ata6.00: configured for UDMA/33
Apr 22 20:55:25 jake kernel: [   30.402802] ata6.01: configured for UDMA/33
Apr 22 20:55:25 jake kernel: [   30.403226] scsi 5:0:0:0: CD-ROM            BTC      BCE4816IM        482S PQ: 0 ANSI: 5
Apr 22 20:55:25 jake kernel: [   30.409226] scsi 5:0:1:0: CD-ROM            ASUS     DRW-1608P3S      1.24 PQ: 0 ANSI: 5
Apr 22 20:55:25 jake kernel: [   30.409633] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
Apr 22 20:55:25 jake kernel: [   30.409732] ehci_hcd 0000:00:13.2: EHCI Host Controller
Apr 22 20:55:25 jake kernel: [   30.409802] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Apr 22 20:55:25 jake kernel: [   30.409905] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfdffa000
Apr 22 20:55:25 jake kernel: [   30.419109] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 22 20:55:25 jake kernel: [   30.419281] usb usb3: configuration #1 chosen from 1 choice
Apr 22 20:55:25 jake kernel: [   30.419350] hub 3-0:1.0: USB hub found
Apr 22 20:55:25 jake kernel: [   30.419400] hub 3-0:1.0: 8 ports detected
Apr 22 20:55:25 jake kernel: [   30.522403] r8169 Gigabit Ethernet driver 2.2LK loaded
Apr 22 20:55:25 jake kernel: [   30.522475] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 17
Apr 22 20:55:25 jake kernel: [   30.522843] eth0: RTL8110s at 0xf885a000, 00:15:58:76:e0:c2, XID 04000000 IRQ 17
Apr 22 20:55:25 jake kernel: [   30.533122] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
Apr 22 20:55:25 jake kernel: [   30.585992] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 22 20:55:25 jake kernel: [   30.593109] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 22 20:55:25 jake kernel: [   30.593176] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 22 20:55:25 jake kernel: [   30.600128] Driver 'sd' needs updating - please use bus_type methods
Apr 22 20:55:25 jake kernel: [   30.600268] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Apr 22 20:55:25 jake kernel: [   30.600330] sd 2:0:0:0: [sda] Write Protect is off
Apr 22 20:55:25 jake kernel: [   30.600868] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 20:55:25 jake kernel: [   30.600977] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Apr 22 20:55:25 jake kernel: [   30.601036] sd 2:0:0:0: [sda] Write Protect is off
Apr 22 20:55:25 jake kernel: [   30.601102] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 20:55:25 jake kernel: [   30.601158]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
Apr 22 20:55:25 jake kernel: [   30.637033]  sda5 >
Apr 22 20:55:25 jake kernel: [   30.637263] sd 2:0:0:0: [sda] Attached SCSI disk
Apr 22 20:55:25 jake kernel: [   30.642195] sd 2:0:0:0: Attached scsi generic sg0 type 0
Apr 22 20:55:25 jake kernel: [   30.642262] sr 5:0:0:0: Attached scsi generic sg1 type 5
Apr 22 20:55:25 jake kernel: [   30.642323] scsi 5:0:1:0: Attached scsi generic sg2 type 5
Apr 22 20:55:25 jake kernel: [   30.645160] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Apr 22 20:55:25 jake kernel: [   30.645210] Uniform CD-ROM driver Revision: 3.20
Apr 22 20:55:25 jake kernel: [   30.675636] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 22 20:55:25 jake kernel: [   30.901490] Attempting manual resume
Apr 22 20:55:25 jake kernel: [   30.957491] kjournald starting.  Commit interval 5 seconds
Apr 22 20:55:25 jake kernel: [   30.957499] EXT3-fs: mounted filesystem with ordered data mode.
Apr 22 20:55:25 jake kernel: [   37.548992] input: PC Speaker as /devices/platform/pcspkr/input/input2
Apr 22 20:55:25 jake kernel: [   37.667144] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 22 20:55:25 jake kernel: [   37.678035] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 22 20:55:25 jake kernel: [   37.798102] Linux agpgart interface v0.102
Apr 22 20:55:25 jake kernel: [   37.870379] input: Power Button (FF) as /devices/virtual/input/input3
Apr 22 20:55:25 jake kernel: [   37.929245] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Apr 22 20:55:25 jake kernel: [   37.943716] ACPI: Power Button (FF) [PWRF]
Apr 22 20:55:25 jake kernel: [   37.943846] input: Power Button (CM) as /devices/virtual/input/input4
Apr 22 20:55:25 jake kernel: [   37.993438] ACPI: Power Button (CM) [PWRB]
Apr 22 20:55:25 jake kernel: [   38.324481] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Apr 22 20:55:25 jake kernel: [   38.455356] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Apr 22 20:55:25 jake kernel: [   38.529552] r8169: eth0: link up
Apr 22 20:55:25 jake kernel: [   38.612977] [fglrx] Maximum main memory to use for locked dma buffers: 865 MBytes.
Apr 22 20:55:25 jake kernel: [   38.613090] [fglrx] ASYNCIO init succeed!
Apr 22 20:55:25 jake kernel: [   38.614481] [fglrx] PAT is enabled successfully!
Apr 22 20:55:25 jake kernel: [   38.630662] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Apr 22 20:55:25 jake kernel: [   38.881147] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
Apr 22 20:55:25 jake kernel: [   38.917315] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
Apr 22 20:55:25 jake kernel: [   39.869835] NET: Registered protocol family 17
Apr 22 20:55:25 jake kernel: [   39.895331] lp: driver loaded but no devices found
Apr 22 20:55:25 jake kernel: [   40.010860] Adding 2835432k swap on /dev/sda5.  Priority:-1 extents:1 across:2835432k
Apr 22 20:55:25 jake kernel: [   40.481670] EXT3 FS on sda1, internal journal
Apr 22 20:55:25 jake kernel: [   41.135088] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 22 20:55:25 jake kernel: [   41.449917] NET: Registered protocol family 10
Apr 22 20:55:25 jake kernel: [   41.450184] lo: Disabled Privacy Extensions
Apr 22 20:55:25 jake kernel: [   41.809109] No dock devices found.
Apr 22 20:55:26 jake kernel: [   43.650713] ppdev: user-space parallel port driver
Apr 22 20:55:27 jake kernel: [   44.104843] audit(1208894127.296:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5407 profile="/usr/sbin/cupsd" namespace="default"
Apr 22 20:55:27 jake kernel: [   44.153224] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Apr 22 20:55:27 jake kernel: [   44.153232] apm: disabled - APM is not SMP safe.
Apr 22 20:55:27 jake kernel: [   44.553175] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
Apr 22 20:55:28 jake kernel: [   45.265736] [fglrx] GART Table is not in FRAME_BUFFER range 
Apr 22 20:55:28 jake kernel: [   45.265748] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Apr 22 20:55:28 jake kernel: [   45.265754] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
Apr 22 20:55:28 jake kernel: [   45.490387] [fglrx] interrupt source 10000000 successfully enabled
Apr 22 20:55:28 jake kernel: [   45.490395] [fglrx] enable ID = 0x00000004
Apr 22 20:55:28 jake kernel: [   45.490403] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Apr 22 20:55:28 jake dhcdbd: Started up.
Apr 22 20:55:29 jake kernel: [   45.865780] Bluetooth: Core ver 2.11
Apr 22 20:55:29 jake kernel: [   45.865907] NET: Registered protocol family 31
Apr 22 20:55:29 jake kernel: [   45.865910] Bluetooth: HCI device and connection manager initialized
Apr 22 20:55:29 jake kernel: [   45.865914] Bluetooth: HCI socket layer initialized
Apr 22 20:55:29 jake kernel: [   46.078188] Bluetooth: L2CAP ver 2.9
Apr 22 20:55:29 jake kernel: [   46.078197] Bluetooth: L2CAP socket layer initialized
Apr 22 20:55:29 jake kernel: [   46.179305] Bluetooth: RFCOMM socket layer initialized
Apr 22 20:55:29 jake kernel: [   46.179322] Bluetooth: RFCOMM TTY layer initialized
Apr 22 20:55:29 jake kernel: [   46.179325] Bluetooth: RFCOMM ver 1.8
Apr 22 20:55:36 jake kernel: [   53.302887] hda-intel: Invalid position buffer, using LPIB read method instead.
Apr 22 20:55:38 jake kernel: [   55.801702] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x306f000a
Apr 22 20:59:16 jake kernel: [  273.587262] audit(1208894356.843:3): type=1503 operation="capable" name="dac_override" pid=6194 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Apr 22 20:59:16 jake kernel: [  273.587271] audit(1208894356.843:4): type=1503 operation="capable" name="dac_read_search" pid=6194 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Apr 22 21:00:33 jake kernel: [  350.323908] audit(1208894433.636:5): type=1503 operation="capable" name="dac_override" pid=6235 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Apr 22 21:00:33 jake kernel: [  350.323919] audit(1208894433.636:6): type=1503 operation="capable" name="dac_read_search" pid=6235 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Apr 22 21:01:30 jake kernel: [  641.139234] Clocksource tsc unstable (delta = 234325146668 ns)
Apr 22 21:01:54 jake kernel: [  665.408067] audit(1208894514.599:7): type=1503 operation="capable" name="dac_override" pid=6277 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Apr 22 21:01:54 jake kernel: [  665.408082] audit(1208894514.599:8): type=1503 operation="capable" name="dac_read_search" pid=6277 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Apr 22 21:02:42 jake kernel: [  712.940450] audit(1208894562.172:9): type=1503 operation="capable" name="dac_override" pid=6308 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Apr 22 21:02:42 jake kernel: [  712.940459] audit(1208894562.172:10): type=1503 operation="capable" name="dac_read_search" pid=6308 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"

---

### Post by unutbu on 2008-04-22
Here are a few more kernel options to try:
"clocksource=acpi_pm notsc noapic"
"acpi=off"

Minor improvement to make trying kernel options easier: You don't have to edit /boot/grub/menu.lst to try new kernel options! During a boot, watch for the GRUB message which gives you 3 seconds to press ESC. Press ESC. You'll be given a list of boot entries (You'll recognize these as the Title lines from your menu.lst). Use the arrow up/down keys to select a boot entry. Select the first entry, "Use acpi_pm". Press 'e' to edit that line. You'll see the stanza from menu.lst. Go to the kernel line and press 'e' again. Go to the end of that line and add the kernel options above. Press 'b' to boot. The additional kernel options will only be in effect for that single boot. If it works, you can edit menu.lst to make it permanent.

References:
[http://forums.fedoraforum.org/showthread.php?t=167879](http://forums.fedoraforum.org/showthread.php?t=167879) suggests using kernel options "clocksource=acpi_pm notsc noapic". (Also: according to jcliburn, "The MSI message is harmless and simply indicates that a Good Thing has happened: your hardware doesn't handle message signalled interrupts well, and the kernel has detected that condition and disabled them, switching to legacy interrupts instead.")

[http://ubuntuforums.org/archive/index.php/t-19536.html](http://ubuntuforums.org/archive/index.php/t-19536.html) suggests acpi=off.
[http://www.togaware.com/linux/survivor/ACPI_Kernel.html](http://www.togaware.com/linux/survivor/ACPI_Kernel.html) suggests acpi=off.

---

### Post by jakelute on 2008-04-23
Thank you. I will try the two new options, to see if they work any better.
Will report back!

---

### Post by jakelute on 2008-04-23
Tried option 1 -- replacing "clocksource=acpi_pm" with "clocksource=acpi_pm notsc noapic"

result: failure to boot up -- just an endless serious of error messages which are pretty much the same, saying something about "messages suppressed" and "general protection eip:b7f36b33 esp bf973284 error: 0"

pressed reset button

tried option 2 -- replacing "clocksource=acpi_pm" with "acpi=off"

result: no crashes so far, though it's too early to say for sure that there are not going to be any -- but, oddly enough, the other (undesirable result) is that there is no sound at all now on my system! I'll stick with it for awhile (long enough to be able to report for sure whether or not this has cured the freezing problem), but if you have any ideas about getting the sound back, I'd appreciate it!

Thanks.

---

### Post by jakelute on 2008-04-23
Hello again.

I'm still logged in with "acpi=off" replacing "clocksource=acpi_pm" --

I've been trying very hard to make it freeze or crash, and I can't! The freeze problem really does appear to have been cured by doing this. (Thank you unutbu for your enormous help and patience :) !!!)

However.....there's always a but: I've got no sound. When I try changing back to the way it was (with "clocksource=acpi_pm"), I immediately get my sound back.

Might there be a way to have both? (i.e., I'd love to have a freeze-free system AND sound as well)

Thanks again.

---

### Post by jakelute on 2008-04-23
Further update: still no crashes, but I've discovered another problem: besides having no sound, when "acpi=off", I can't shut down the computer! When I shut down, I get the message "make sure the message bus daemon is running!" (no idea what that means), and then "system halted" -- and that's it - computer carries on running, while showing that message. So to shut down, I have to go back in and replace acpi=off with clocksource=acpi_pm -- help!

---

### Post by unutbu on 2008-04-23
Perhaps try
"acpi=noirq"
"acpi=ht"
"acpi=strict"

I'm getting these from [http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf](http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf)

---

### Post by unutbu on 2008-04-23
[http://www.linuxforums.org/forum/peripherals-hardware/92255-acpi-off-disables-my-usb-mouse-2.html](http://www.linuxforums.org/forum/peripherals-hardware/92255-acpi-off-disables-my-usb-mouse-2.html)
is an interesting thread -- the problem was fixed by updating the BIOS. 

The command
```
sudo dd if=/dev/mem bs=32768 skip=31 count=1 | strings -n 10 | grep -i bios
```

will tell you what BIOS you are running. Please post the result.

---

### Post by jakelute on 2008-04-24
Hello unutbu,
Here's the information you asked me to post.
Meanwhile, a report on the results of your previous post (for which, thank you).
Result of acpi=noirq is still no sound.
Result of acpi=ht is still no sound.
Result of acpi=strict is entirely positive! There IS sound, the computer does shut down, and I can't make it freeze, try as I might.

However, maybe it's still a good idea to update the BIOS?

See below.

jake@jake:~$ sudo dd if=/dev/mem bs=32768 skip=31 count=1 | strings -n 10 | grep -i bios
[sudo] password for jake: 
1+0 records in
1+0 records out
32768 bytes (33 kB) copied, 0.000893868 s, 36.7 MB/s
$FBIOSI$410M01.01.F1.P.30.052906.594F1.410M01-GAR.13.RC4107MA-S2
IBM COMPATIBLE 486 BIOS COPYRIGHT Phoenix Technologies, Ltd
Phoenix - AwardBIOS v6.00PG
jake@jake:~$

---

### Post by unutbu on 2008-04-24
I am thrilled to hear acpi=strict seems to work!
Personally, I am a devotee of the "If it ain't broke, don't fix it" school of thought. (Lord knows I've managed to bungle a few things while doing so-called upgrades...) I don't see a clear advantage to upgrading the BIOS. In fact, the purpose of ACPI is to move functionality (hardware detection, power management) out of BIOS and into the operating system. (See [http://www.advogato.org/article/913.html](http://www.advogato.org/article/913.html)).

Moreover, acpi=strict tells the kernel to "make the ACPI layer be **less** tolerant of platforms that are not fully compliant with the ACPI specification." (Again, see [http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf](http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf))

Since this works for you, I interpret this to mean your hardware is in strict compliance with ACPI specs. That sounds good to me, and does not suggest using this kernel option impairs your system in any way.

I hope you enjoy your Ubuntu system!
Cheers, 
Unutbu.

---

### Post by jakelute on 2008-04-24
Dear Unutbu,

What can I say? Without your generous help, I'd never have got there!
So far it's all working fine, and I'm so pleased that it all worked out in the end. It was extraordinarily difficult (as you know from the long thread!) to get to the bottom of this problem, especially as I don't have much technical knowledge about Linux (nor, actually, do I know all that much about how computers work, in fact). I was ready to give up and go back to Windows, especially as there was a long period when my questions to the forum were going unnoticed.

I'm very grateful to the whole community for the help, and especially to you (wherever you are!). I hope I can give back something to the community as time goes on.

All best wishes,

Jakelute

---

### Post by jakelute on 2008-04-24
Alas, I spoke too soon!
I've had a couple of brief freezes in the last hour :( --
the first was followed by the usual message about tsc clocksource being unstable, and acpi_pm clocksource being installed. The second, curiously, didn't come with a message.
This is most disappointing. However, I'm convinced that it's better than it was. I was having dozens of freezes a day before......

---

### Post by jakelute on 2008-04-24
Should I go back to the idea of updating the BIOS? If so, how's it done?
Many thanks!

---

### Post by jakelute on 2008-04-25
25 April -- still with acpi=strict -- started the day with a freeze!
The problem is definitely not fixed!
The freeze was again followed by the message about tsc clock being unstable, and acpi_pm clock being started.
It occurs to me that if acpi=off is the only way to not have freezes, maybe we should (a) consider whether there's a way to make the sound work when acpi=off or (b) update the BIOS

---

### Post by jakelute on 2008-04-25
hi again -- a further update:
The problem with freezing when acpi=strict appears to be cumulative. In other words, I had a whole day where everything worked perfectly (using acpi=strict). But by the end of that day, I was getting a few freezes again. And this morning, when I log on with acpi=strict, it freezes immediately, and an unpleasant buzzing comes from my computer speakers! It's as if the problem builds up gradually until it's intolerable.

Unutbu, if you're still out there, and have a moment to give further advice, I'll be very grateful. Meanwhile I'll work using acpi=off and just make do without sound.

Thanks, and best wishes

---

### Post by unutbu on 2008-04-25
Hi Jakelute, I'm still here, thinking about what to do next. (Oh gods of ACPI, why didst thou rippest the sweet taste of victory from my mouth?)

Here are my reasons agaist upgrading the BIOS:
1) This BIOS worked with Windows to create a computer that did not freeze. Therefore, Window's ACPI knew how to work with your hardware. 
On the other hand, there may be a reason why Linux's ACPI does not work while Windows' did:
(See [Leaked Antitrust Memo: Bill Gates on Making ACPI Windows-specific]("http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf")) Still, there may be a way to get Linux's ACPI to work with your system that we just haven't tried yet.

2) Everything we've done so far can be backed out of. If a kernel option did not work, you are now an expert on changing kernel options to get your computer back to its prior state. If what we have been doing is rubbing lotion on a rash, upgrading the BIOS is like a heart transplant. 

In theory a BIOS upgrade can be backed out of too, *IF* the BIOS upgrade program gives you an option to save your current BIOS, *AND* the installation of the new BIOS goes smoothly. If something were to go wrong and your BIOS is left in a broken state, it may render your computer incapable of booting from CD or USB which may mean the computer can not be fixed in any way I'm familiar with. There may be a way to physically take out the BIOS and to reset it but this is way beyond what I'm comfortable helping you through.

3) There may be a way to fix the sound problem and the shutdown problem with more mundane Linux tools.

---

### Post by jakelute on 2008-04-25
OK, so maybe BIOS update should be considered as a last resort if all else fails.
Meanwhile, I'll do some Googling and see if I find anything useful.

---

### Post by jakelute on 2008-04-25
Here's an interesting one, but this person has exactly the opposite problem!
[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-gusty-intel-hda....no-sound-unless-acpioff-597705/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-gusty-intel-hda....no-sound-unless-acpioff-597705/)

---

### Post by unutbu on 2008-04-25
First, a question: With "acpi=noirq" or "acpi=ht" can the machine shutdown?

Second, to find out about audio hardware, please post the output to

```
aplay -l
cat /proc/asound/cards
lspci | grep -i audio
```

Third, it might be a good idea to start a new thread to ask about fixing the sound problem, and yet another to ask about the machine shutdown problem. The subject header 'temporary freezes' may not attract people who know a lot about fixing either of those problems. I'll still work on both (and find whatever new posts you make) but I'm no expert at any of this and would appreciate any help we can get.

---

### Post by jakelute on 2008-04-25
In reply to your first point:
acpi=noirq results in a successful shutdown
acpi=ht results in a halted system, just as with acpi=off

regarding those three lines of code you want me to post the output to: are they three separate commands, or do I copy all of that and paste it into terminal in one lump?

your third point: yes, I'll start two new threads -- good idea --

---

### Post by jakelute on 2008-04-25
PS

Here are some alternative commands I found while googling. Is it worth trying them?


acpi=power_off
acpi=force lapic
acpi=off apm=power_off
from [http://ubuntuforums.org/archive/index.php/t-359190.html](http://ubuntuforums.org/archive/index.php/t-359190.html)

acpi=force
from [http://www.mepislovers.org/forums/showthread.php?t=13084](http://www.mepislovers.org/forums/showthread.php?t=13084)

---

### Post by jakelute on 2008-04-25
jake@jake:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jake@jake:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfdff0000 irq 18
jake@jake:~$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
jake@jake:~$

---

### Post by jakelute on 2008-04-25
Sorry about the numerous posts -- I've been sending bits of information as and when they emerge. I think I've answered all three of your points now. I have not yet started the two new threads you suggested, because I'm waiting for the results of an experiment which I'm currently working on: I've put in acpi=force, and everything is working well. Shutdown is ok, sound is ok (except it's quite quiet, even when turned up very high, and this has been the case ever since I downloaded 8.04 Beta, so that's a seperate issue), and I can't make it crash! I won't say that the whole business is solved just yet, because I had a bad experience yesterday with acpi=strict -- there were no crashes for a whole day, but then they started coming thick and fast. So let's see how this goes. I've been on acpi=force all day with great success. I'll stick with that for another day or two before I come back and say that we've had success at last.

---

### Post by jakelute on 2008-04-25
Unfortunately I've had my first freeze with acpi=force -- it took a long time -- I never used to be able to go for a whole day without a single freeze. But I just had one which lasted about ten minutes. Message, which as usual came up at exactly the time of the unfreeze:
Apr 25 23:14:22 jake kernel: [20557.575172] Clocksource tsc unstable (delta = 318715645783 ns)
Apr 25 23:14:22 jake kernel: [20557.576632] Time: acpi_pm clocksource has been installed.

From having done some googling about other commands to try, I thought I might have a go with some of the others.

But so far, it's still the case that only acpi=off is freeze-free (and, even in the latter case, I can't be sure that it's freeze-free for all time). But, as we know, acpi=off is problematic because I'm getting no sound and can't power off.

---

### Post by jerrykenny on 2008-04-25
Jakelute . . . i do admire you your perseverance !

I'm much more blase about bios updates than Untbu, however i see his point, and hes definitely getting results.

Can you go into your bios (press del, or  f10)  make sure you have pnp OS set to yes . . . this will allow Ubuntu to take full control of hardware . . . 

There is a good set of BIOS setup instructions, on Debians website, theres no harm in going thru them.

If you're hung, you may try   ctrl-alt-f1   then logging in text mode . . . if you can do

sudo killall gdm

will quickly kill all the userspace nonsense . . . but wont cure hardware/ kernel issues. . . . . you can interrogate your system with the "top" command, . . . or "dmesg"  will tell you if its being a hardware issue . . . . 

If the terminal is stable, . . . . next time you might not want to kill gdm so quickly, . .. just run "top" and see whats using up yer processor / memorey

      Good Luck

---

### Post by jerrykenny on 2008-04-25
ps . . . in text mode, you can shut down yer pc with 

sudo halt

---

### Post by unutbu on 2008-04-26
I'm trying to organize what we know about the various kernel options. Is this correct?

```

		         No-freezes	 Sound		Can shutdown	
acpi=off		 Y	   	 N		N		
acpi=ht			 	   	 N		N		
acpi=strict		 N		 N (buzz)	Y		
acpi=noirq		 		   		Y               
acpi=power_off
acpi=force lapic
acpi=force		 N		 Y (quiet)	Y
acpi=off apm=power_off
```

---

### Post by jakelute on 2008-04-27
Sorry for the delay in replying to that one.
Here is an enlarged and more complete version of the table that you posted. Please note regarding sound that the quietness issue is true of 8.04 in general on my system. Once I downloaded 8.04, I found I had to turn the sound way up on my computer speakers, to a level which would have been intolerably high in 7.04 or 7.10. This is univerally true in all of these acpi options, and in the default 8.04 settings. There's some kind of volume issue on my system in 8.04 which is consistent and is therefore a seperate issue (a bug?).

I've retested everything, and here's what I get.

		         No-freezes	 Sound		Can shutdown	
acpi=off		 Y	   	 N		N		
acpi=ht			 	   	 N		N		
acpi=strict		 N		 Y	        Y		
acpi=noirq		 		 N  		Y               
acpi=power_off                           Y              Y
acpi=force lapic                         Y              Y
acpi=force		 N		 Y             	Y
acpi=off apm=power_off                   N              N


Looking at this, it's quite clear that I need to investigate acpi=power_off and acpi=force lapic. Both of these have potential. I'll try them each for a day, to see whether I get any freezes. 

Will report back. I guess we'll get there in the end. It's amazing that you've stuck with me on this!

---

### Post by jakelute on 2008-04-27
Sorry, the formatting didn't work! How do you do that?
My table isn't very clear, because the Ns and Ys are all scrunched together.
Obviously, in my table where there are only two letters (NN or YY or whatever), they refer to the second and third columns. Which is why I say I need to try out acpi=power_off and acpi=force lapic, because they both come out positive in columns two and three.

---

### Post by unutbu on 2008-04-27
Hi Jakelute. I'd like to see Ubuntu live up to the meaning of its name and what better way than to help others who seem likely to pass it on?

Furthermore, anyone willing to ditch Windows for a partially working Ubuntu system deserves all the support the Ubuntu community can offer.

Now then, to get the formatting, simply type your table, highlight it, then click the pound symbol (#) on the icon bar above the posting area. If you don't see the pound icon, look for a button which says Advanced mode, click on it and your icon bar should then have the pound icon.

Good luck with the further tests. I'll be interested to see how they turn out.

---

### Post by jakelute on 2008-04-28
Hi Unutbu (and hi Jerrykenny -- thanks for your posts) --
Well, I very much appreciate all the help and what you say about the philosophy of Ubuntu.
The thing that has kept me persevering is a) the fact that the alternative is to return to Windows, which I really really don't want to do, and b) the fact that it's a bit like waiting for a bus -- the longer you wait at the bus stop for a bus that's very very late, the more reluctant you are to leave the bus stop, in case it's just about to turn up.
However, having said all this, I'm on the verge of giving up and reinstalling Windows. As you know, I've been sticking this out for a very long time, and it's just not happening. Is my system really so unusual?

I'm willing to keep at it a little bit longer, but not very much longer.....

I can update yesterday's diagram now, to say that acpi=power_off and acpi=force lapic both lead quickly to freezes. So, they're no better than just using the default ordinary Ubuntu. I've gone back to acpi=off, which means there are no freezes happening, but there's also no sound and I can't power off.

And the latest thing (and possibly the last straw) is that suddenly I can't play DVDs. I just get an error message saying the source couldn't be read. I can view CDs with photos or other data on them, but I can't play DVDs all of a sudden, in any mode, with acpi=off or in the normal default Ubuntu.

Let me ask you something: would you go back to Windows at this stage if you were me, or would you keep trying? I'm really not sure. As I say, I'd love to avoid it if I possibly can.

Meanwhile, I'll start two new threads, explaining that the only mode which appears to work is acpi=off, and asking whether there's any way I can get the computer to shut down and to have sound in that mode.

What about this upgrading the BIOS thing....?

Thanks!

---

### Post by unutbu on 2008-04-28
Hi Jakelute. 

Your situation saddens me. You deserve better!
This doesn't happen to most linux users (as you've probably noticed, googling does not come up with many users with freezes like yours.)

What would I do in your situation?

Well, to be honest, I would keep trying to get some version of Linux working. (My comfort level with Linux and discomfort with Windows is just so great that I think I would go to just about any length to get a Linux system.)

First, if I were in your shoes, I would try running under kernel option "acpi=noirq" and see if I get any freezes there. At least under noirq you can still shutdown properly. Maybe the sound problem is not so hard to fix, and if (big if!) you get no freezes with noirq, then problem solved. 

If acip=noirq produces freezes, I'd then try acpi=ht, just to finish off the table. And who knows? We may get pleasantly surprised. Under this scenario we'd need to find a way to fix the shutdown problem too. I would wait a bit to see what responses you get from Ubuntuforums on these problems. I'm actually optimistic someone on this site can help you with the sound and shutdown problems because we get a lot of similar posts here that do get fixed.

Now if all of the above comes to naught, I think I would try burning other versions of Linux and just see if any of those fix my problem "out of the box". Another distribution may have a newer kernel with a newer version of ACPI...

If that doesn't work, and if you have the cash, the next easiest thing would be to sell your current hardware and get a new machine. The negative side is obvious -- you'll take a financial loss. The positive side is that you can guarantee yourself a machine that works well with Linux. Some companies like Dell ([http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWDAL&s=dhs]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWDAL&s=dhs"))
sell them with Linux pre-installed. 

Another option which comes to mind is posting a bug report at [http://bugzilla.kernel.org/enter_bug.cgi?product=ACPI](http://bugzilla.kernel.org/enter_bug.cgi?product=ACPI)
(Read [http://www.lesswatts.org/projects/acpi/bugzilla.php](http://www.lesswatts.org/projects/acpi/bugzilla.php)
first). The people who write the ACPI code read bugzilla, so if anyone can debug your situation, its  probably one of them.

The lesswatts.org link above recommends that you provide certain info when you post a message on bugzilla. Here are the commands you would need to produce the requested info:

```
cat /proc/version
cat /proc/interrupts
dmesg -s64000
lspci
sudo apt-get install acpidump
sudo acpidump
sudo dmidecode
```

I'm really sorry I couldn't be of more help.

---

### Post by jakelute on 2008-04-28
That is actually very useful!
I'll work my way through your suggestions one by one, and I will send occasional progress reports. I won't mark this solved, as it isn't!

Just one question -- other Linux distributions: if I ended up with one of them, would it really be feasible for someone like me (someone who doesn't know a great deal and who needs it simply to work in a relatively foolproof way)? Or, to put it another way, which distributions might be worth looking at?

But to start at the beginning, I'll try noirq and ht for freezes.....

Many thanks!

---

### Post by unutbu on 2008-04-29
Here is an attempt to get sound working and to fix the shutdown problem:

1) Edit /etc/modules by adding the following line at the bottom:

```
apm
```

2) Run gksudo gedit /etc/modprobe.d/power. Put the following line in the file.
```

options apm power_off=1 realmode_power_off=1
```

Save.

3) Reboot with the kernel option

```
acpi=off pci=noacpi 
```


pci=noacpi 
This, hopefully, will restore sound (and dvd?). It tells the kernel to "not use ACPI for IRQ routing or for PCI scanning." (See p108 of kernel-options-ch09.pdf) I think turning off ACPI disabled the computer's ability to detect hardware. Hopefully pci=noacpi will coax the kernel into using some non-ACPI method to detect hardware. (This was reported to work for a poster at [http://www.linuxforums.org/forum/redhat-fedora-linux-help/106986-acpi_power_off-called.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/106986-acpi_power_off-called.html).)


The editing of /etc/modules and /etc/modprobe.d/power comes from 
[http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)
This is an attempt at solving the shutdown problem.

---

### Post by jakelute on 2008-04-29
Thanks for this. Can't seem to get beyond step one. Am I doing something wrong? I go into terminal mode and type "/etc/modules" -- is that the right thing to do? 

Then I get 

jake@jake:~$ /etc/modules
bash: /etc/modules: Permission denied
jake@jake:~$ 


Thanks!

---

### Post by Jimmy9pints on 2008-04-29
> **jakelute said:**
> I wonder whether anyone has had a similar experience.
Many thanks.

Yes! I do. My computer regularly freezes up in exactly the way you have described.

---

### Post by jakelute on 2008-04-29
Hi Jimmy.
If you have the patience, I'd suggest you read through this thread (you'll need about an hour to spare though -- it's a thread of epic proportions), to find out what sorts of things I've been trying in order to solve this freezing problem. As you can see, it's not solved yet, but it is looking as though I'm heading in the right direction, thanks to the patience and generosity of various Community members who have been helping me.
Good luck!
The current problem is that I can get rid of the freezes, but then I find that I have to sacrifice my sound as well! But we're working on it! Watch this space.

---

### Post by Jimmy9pints on 2008-04-29
I will read the thread. I too am commited to Ubuntu - and much of what you've said about community and freedom from windows strikes a chord with me - but the freezing problems are REALLY annoying.

One line of enquiry is my graphics card - if I disable the effects, and/or disable the NVidia graphics driver - my computer doesn't freeze up.

---

### Post by jakelute on 2008-04-29
That sounds more straightforward -- I would suggest you start a new post (if you haven't done so) with a title something like "system freezes with NVidia graphics driver enabled -- help!"
I bet that can be swiftly rectified with the help of others who have had the same specific problem.

---

### Post by unutbu on 2008-04-29
Oops, sorry it wasn't clear.
Type 
```
gksudo gedit /etc/modules
```

/etc/modules is a file owned by root. So, you need "root privileges" to edit the file. gedit is the command which launches the text editor. gksudo is the command you tack on when you want to run a graphical program like gedit with root privileges.

---

### Post by jakelute on 2008-04-29
Thank you! I'll try it tonight.
Meanwhile, just to report that noirq freezes, but ht doesn't (at least not so far!).
Will report back on my findings.

---

### Post by jakelute on 2008-04-29
Hi Unutbu,

I have some results after running the procedures you outlined above.

First of all, I followed your instructions to the letter, and rebooted with acpi=off pci=noacpi -- result: still no sound, and still get an error when I put in a DVD, though I can read and write CDs as before. However, there was one success: shutdown now works. I've also tested it in acpi=ht, and it works there too.

So the latest situation is that the computer is now powering down correctly where it wasn't before, but we're no better off on the sound and DVD-reading side of things. So I'll post a new thread about sound, though I'm not quite sure what to say. I guess I'll try to outline briefly what the situation is.

Thanks for your help! Will keep this thread posted.

Meanwhile, if you were me and you were contemplating possibly trying a different brand of Linux, what would you be thinking about? Opensuse? Fedora? Mandriva?

---

### Post by unutbu on 2008-04-29
For the sound problem, would you please try this guide:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I think it would be a good starting point to better understand where the problem lies.

Also, I note that you posted the output to 

```
sudo lshw
lsmod
``` 

earlier in this thread -- presumably when sound and DVD were working. Would you post these again while running with kernel option acpi=off? I'm curious to see if there are any differences.

Now regarding other linux distros: I don't have a lot of experience with other distros, so I'm probably not a very good source for advice on this issue. If I were in your shoes I think I would try Fedora and openSUSE but I can't explain why -- I have no good reason for choosing those two.

Like many distros today they both offer Live CDs, so you can try them (to see if you get a freeze) without having to install. Actually, that begs the question, do you experience freezes with Ubuntu's Live CD?

A good place to go to research distros is [http://distrowatch.com/](http://distrowatch.com/).

I hope we can overcome the sound and DVD issues so you can stick with Ubuntu, as I think Ubuntu has a livelier support community than any other distro. In my opinion that's really the most important factor when choosing a distro (for novice to intermediate users). (My method of measuring liveliness is to visit a distro's forum (you can find the links at distrowatch.com) and look for the statistics on number of posts and number of members.)

---

### Post by jakelute on 2008-04-30
Hi Unutbu,

In answer to your last post, here's the output to sudo lshw and lsmod with kernel option acpi=off.

I will look at the sound troubleshooting pages you have recommended.

Regarding other distros, it will be a last resort. I'd much rather stay right here with Ubuntu! Thanks for the suggestions about possible distros to try.

Here's the output:

jake@jake:~$ sudo lshw
[sudo] password for jake: 
jake                      
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2
  *-core
       description: Motherboard
       product: RC4107MA-S2
       vendor: Foxconn
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (05/29/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          slot: Socket 775
          size: 3400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 5
          bus info: cpu@1
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          slot: Socket 775
          size: 3400MHz
          clock: 200MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci agp agp-2.0 normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: ST3320620AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5QF3EJ6C
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=10851084
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: d5ca58d0-0c95-4ef7-bbf9-1e096847d371
                   size: 295GiB
                   capacity: 295GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-04-17 22:33:34 filesystem=ext3 modified=2008-04-30 10:46:22 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-04-30 10:17:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   size: 2769MiB
                   capacity: 2769MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2768MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-cdrom:0
                description: CD-R/CD-RW writer
                product: BCE4816IM
                vendor: BTC
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 482S
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD-RAM writer
                product: DRW-1608P3S
                vendor: ASUS
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
           *-network
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:02:07.0
                logical name: eth0
                version: 10
                serial: 00:15:58:76:e0:c2
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.36 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s

lsmod on 30 April

jake@jake:~$ lsmod
Module                  Size  Used by
udf                    88612  0 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ipv6                  267780  16 
ppdev                  10372  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
apm                    22616  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
af_packet              23812  2 
snd_hda_intel         344728  5 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                1555468  20 
serio_raw               7940  0 
i2c_piix4               9612  0 
i2c_core               24832  1 i2c_piix4
soundcore               8800  1 snd
evdev                  13056  1 
ati_agp                 9996  0 
agpgart                34760  2 fglrx,ati_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
atiixp                  5648  0 [permanent]
ide_core              113996  1 atiixp
ata_generic             8324  0 
sata_sil               12296  2 
floppy                 59588  0 
ohci1394               33584  0 
pata_atiixp             8960  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
ehci_hcd               37900  0 
r8169                  32900  0 
ohci_hcd               25348  0 
libata                159344  4 ata_generic,sata_sil,pata_atiixp,pata_acpi
usbcore               146028  3 ehci_hcd,ohci_hcd
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 
jake@jake:~$

---

### Post by jakelute on 2008-04-30
Hi Unutbu,

Some developments:

I decided today to download a fresh 8.04 iso, which I did. And of course I verified the md5sum. After burning the CD, I also verified the integrity of the CD.

Then I reinstalled 8.04, completely fresh, repartitioning and taking over my entire disk drive.

Then I started using the new installation and had a freeze within minutes.

So I went through the entire epic thread that you and I have created, and put back in all the small changes and tweaks that you suggested over the last few days.

Now, interestingly enough, things are not great, but they are different!

For instance, in acpi-ht, it's no longer the case that I'm without sound. But the login music (little drum roll) plays when I get the login screen, and then continues to play ad infinitum in an infinite loop!

In acpi=ht pci=noacpi, I get just the same thing! An infinite loop of drums from the login screen. It's playing even now! (Though I've muted the sound.)

It's very odd -- where before I had no sound, I now have a continuous loop of sound which I can't figure out how to stop (other than muting the sound). Is this progress? I'm intrigued by the fact that I seem to have a different set of problems now. Still unable to play DVDs, though CDs are fine. Wondering whether there's actully something wrong with the DVD drive (I have two drives, one DVD and one CD only), though it worked in Windows.

Just for your information, I've redone all of the stuff you suggested, including the apm stuff you suggested yesterday. I'm currently running (so far without freezes) on acpi=off pci=noacpi.

The problem with the sound troubleshooting guide, as far as I can see (though I haven't studied it in detail yet -- that's next on my agenda!), is that it doesn't particularly deal with someone like me who has modified the kernel options.

Sadly, no replies at all to my post about the sound problem.

Where from here?

I guess I'll read carefully through the sound troubleshooting guide.

---

### Post by jakelute on 2008-04-30
Quick update just a few minutes later.
Since it was the login music which was infinitely repeating, I enabled automatic login, so that the login screen doesn't appear any more. Result: in acpi=off pci=noacpi we're back to no sound at all!

But....and this is really weird....I was just able to play a DVD (but with no sound) -- perhaps this reinforces my theory that the DVD drive is slightly defective.....

This is getting rather complicated. I'll be interested in any thoughts you might have.

---

### Post by jakelute on 2008-04-30
One more update:
I just did another test in acpi=off pci=noacpi -- I logged out which forces the login screen to reappear (even though I'd enabled automatic login). And lo and behold, I got the infitely repeating drum loop again, the login music over and over again. So I think I can say now that in acpi=off pci=noacpi, the only sound that works at all is the login music, and that works TOO well.
Is this a clue? If there is sound only before logging in, but not after (however defective that sound currently is), does this not tell us something about my own personal settings? (But what?)

---

### Post by unutbu on 2008-04-30
Wow, this is very strange and interesting.
I'll have to think about this for a while, but here are some quick thoughts.

1) Perhaps 8.04 has changed since the last time you downloaded it. If you have both 8.04 CDs, it would be interesting to compare their MD5sums but it's probably not that important so let's table that idea.

2) The problem with a very active forum community is that new posts get buried very quickly. If sound/hardware/acpi savvy readers aren't logged on when you post or don't click New Posts very soon after you post, it's likely to get lost in the shuffle. Let's combat that by holding all further conversation on the other thread.

---

### Post by pocketman on 2008-05-29
Thought I'd chime in here, as I have been having very much the same problem.  Actually, mine has been happening for several months now. I finally gave up using Ubuntu on this computer because of it, as the freezes made the computer completely unusable and I just didn't have the time to mess with it. I tried 7.10, 8.04, countless installs/video drivers/etc.

I would always freeze up, but then after a few minutes the lockup would cease and I could use it again until it happened again.  I then found the same thing in my logs as you had 'Clocksource tsc unstable' at about the time of the crash. However, I found this link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414"), which pointed me in the right direction. Right after the 'unstable' message in my logs, I found one saying that 'acpi_pm' was loaded as the clock source.  I added 'clocksource=acpi_pm' to my Grub kernel line .... and no lockups/freezes since. So maybe if you check which clocksource your kernel is loading after it comes back, you'll be able to modify your system in a similar way?

Now, I could be speaking too soon, as it looks like sometimes things appear that they work, and then don't. But I know that this is the longest I've gone without a lockup in a long time!  :guitar:


I am not sure whether it's related or not, but I was also getting a message that said something to the effect of 'MP-BIOS BUG: Timer not connected to IO-ACPI' or it may have said APIC, not sure. This message still appears, but I haven't had anymore lockups.

Quick Summary:

1. See what clocksource your kernel is loading after it unfreezes.
2. Try to change your clocksource in the grub menu to the same.
3. Hope for the best.

Hope this works for you...as I have been following this with some interest to see if someone found a resolution.  I hope this is it. I should also mention that sound as well as power down, etc. all work for me in this configuration.


Take Care!

---

### Post by d.kusummmanth@gmail.com on 2008-05-30
> **jakelute said:**
> One last observation before I give up:
I've tried removing all peripherals, and still get the problem.
I've tried with ATI proprietary driver and without, and get the problem in both cases.
I've tried every variable I can think of.
But there's a general pattern I've observed: the freezes happen with great frequency late in the day, when the computer has been on for quite a few hours. I rarely get freezes early in the day. Why would this be?
But I repeat: I never had crashes or freezes in Windows, so I don't see how it can be a hardware problem.
Many thanks!
i hv d exact same problem

---

### Post by d.kusummmanth@gmail.com on 2008-05-30
> **jakelute said:**
> Hello again,

I've really enjoyed using Ubuntu (Gutsy) -- it's been an eye-opener for me, and I'd like more than anything to stay with it. In fact, on my wife's laptop (Dell Inspiron 1100), we WILL stay with it, because it's been absolutely trouble free in every way, and superior to Windows XP in every way.
However, on my PC (see all the previous posts in this thread please), I simply can't get rid of the temporary freeze problem, even after a couple of months of tinkering and trying various things. Several times a day, I get freezes, and then I just have to wait ten minutes or so for the computer to resume. Which it always does (but with the clock running ten minutes slow). 

Here is a summary of the facts:

1. This sometimes happens when running firefox, and sometimes when doing other things (such as viewing jpg files or downloading updates). The problem is NOT exclusive to Firefox.

2. I have no visual effects enabled at all.

3. I DO have a dual-boot system with Windows XP on a second internal HD, and I NEVER get crashes or freezes in XP (so I don't think it's hardware).

4. I've run memtest and get no errors at all.

5. I'm a beginner at this sort of stuff, so will unfortunately only understand simple instructions and suggestions. Sorry about that.

6. The problem happens in Hardy as well (I've updated to Hardy now to see if it's any better, and the identical problem still occurs).

7. Unfortunately there has so far been no solution to this problem, despite the kind messages from various forum members. I'm beginning to think my machine simply doesn't like Ubuntu or Ubuntu simply doesn't like my machine.

Anyway, I'm giving it one final try, and if this post doesn't result in success, I'll have to return to Windows XP (with a heavy heart, because I very much like Ubuntu, and I very much like the community, and would love to be part of it).

Then, maybe sometime in the future when this computer bites the dust, I can buy a new one which comes with Ubuntu pre-installed, to minimize the possibility of such problems in the future.

Thank you, and very best wishes,

jakelute
i hv exact same problem
[PHP]WARNING: you should run this program as super-user.
eeee-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 510MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor ds_cpl cid xtpr
          configuration: id=0
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
           *-network
                description: Ethernet interface
                product: SiS900 PCI Fast Ethernet
                vendor: Silicon Integrated Systems [SiS]
                physical id: 7
                bus info: pci@0000:03:07.0
                logical name: eth0
                version: 02
                serial: 00:11:5b:53:95:e3
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.3 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S202J
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
[/PHP]

the way u listed out ur problems, connected so well to me, that I nearly cried out. I never felt so emotional in my 3 1/2 months at Ubuntu Forums, the way I felt when I was reading ur thread.

---

### Post by pocketman on 2008-05-30
Alas, I did speak too soon.  :(  It didn't stick.  However, I found another thread (this is beginning to get comical) [here]("http://ubuntuforums.org/showpost.php?p=4963984&postcount=24"), and tried the 'hires=off nohz=off irqpoll' along with 'clocksource=acpi_pm' and so far - fingers crossed - things are working okay.

I'll report back in a bit to see if this has held up or not.  I certainly hope so as I have spent so many hours trying to find a solution to this. And I know many other people have as well.  I feel a bit like I'm back in the Windows 98 days. :(

---

### Post by unutbu on 2008-05-30
pocketman and d.kusummmanth, I'm sorry to hear you've been experiencing this "temporary freezing" problem. I can only imagine it is very frustrating. 

You can find the rest of jakelute's temporary freeze saga here:
[http://ubuntuforums.org/showthread.php?t=774812](http://ubuntuforums.org/showthread.php?t=774812)

The short version is jakelute tried Mandriva and it worked -- no more temporary freezes. Last time he posted (about a week ago), he was trying Kubuntu -- also with no freezes. It sure would be nice if someone found a way to fix this under Ubuntu, and I hate to chase away Ubuntu users, but it would be cruel for me not to tell you.

---

### Post by pocketman on 2008-05-30
Well...unfortunately, "hires=off nohz=off irqpoll clocksource=acpi_pm" didn't work either. Then I installed compiz-switch, thinking it might be compiz...no dice.  I unchecked powernowd from the services menu, thinking maybe that had something to do with the 'clocksource tsc unstable' message, no dice.  

Interestingly enough though, I am no longer seeing the clocksource unstable messages in the log after a freeze.  :confused: But it's still freezing. This makes it harder to diagnose in my mind.  The freezing seems to be completely random.  I do seem to notice a cron job running near the time of freezes, but can't be sure that that is always the case. It is a cron job related to PHP, although I'm not sure what it's doing, or why it's there.

Here is the log message: CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

I am about at a loss. I would really like to stay with Ubuntu, but am not sure what the next step is, so I am currently downloading CentOS 5.  Since I run Cent on some of the web servers that I run, I guess it would make sense to have that on my primary box as well, however, I really like Ubuntu for a desktop distro, if only...

---

### Post by jakelute on 2008-06-14
Hi all -- sorry for the long delay. I've been away from my desk for awhile.
Just to add to what Unutbu said: I am still using Mandriva. It never freezes or crashes, and is working well for me. I would have preferred Ubuntu -- overall, I prefer it. But I had to give up.
Very interesting to learn that others are having experiences quite similar to mine. Good luck!
Best wishes,
Jake

---

### Post by unutbu on 2008-06-14
Hi Jake, thanks for the checking in! Glad to hear Mandriva never freezes. I really wonder what's the difference...

---

