---
title: "Installing Kubuntu on a Lacie USB 2.0 external Drive"
date: 2005-10-30
forum: Apple PPC Users
---

### Post by vikingth0r on 2005-10-30
Alright, I have had some pretty good experiences using Slackware on PC's a few years back and I am interested in Installing Kubuntu on my external drive so I don't touch my internal drive on my Powerbook. I have 1.67Ghz Aluminum powerbook. I have looked around on this site to find some tutorials but I would like someone who has done this to list the steps as to what I need to do.

What I have tried so far is booting up from the cd and starting the installer and I had it partition the external HD (automatically) but when it installs yaboot, it fails. Now, after this step which is supposed to happen, the directions I have found were not quite clear to me as to what to do and also I do not know how I can get my laptop to be able to boot up from an external USB drive.

It would be awesome if someone with more knowledge on this subject could give me a hand.

Thanks
Christopher Ericson

---

### Post by vikingth0r on 2005-10-30
Ok, so after some more digging on the forums this is what I found to do:

#mkdir hd
#mount -t ext3 /dev/discs/disc1/part3 hd
#chroot hd
#mount proc
#mkofboot -b /dev/sda2 -o=usb1/disk@1
#pico /etc/yaboot.conf

with the following config:
ofboot=usb1/disk@1:
init-message="You know the drill\n\n&#8221;
partition=3
timeout=30
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
default=linux
image=/boot/vmlinux
label=linux
root=/dev/sda3
read-only
initrd=/boot/initrd.img
defaultos=linux
delay=10
enablecdboot 

and then #ybin -v --boot /dev/sda2 --config /etc/yaboot.conf

This is what I did on my external USB hard drive. Now, I had the kubuntu installer just erase and then partition my external hd however it wanted. Now when I go into the firmware and type: boot usb1/disk@1:yaboot it won't boot it

---

### Post by tonysathre on 2005-10-31
its probably in the BIOS to boot from USB, it doesnt look like u put a file system on your USB drive

---

### Post by beewer on 2005-11-03
[QUOTE=vikingth0r]Alright, I have had some pretty good experiences using Slackware on PC's a few years back and I am interested in Installing Kubuntu on my external drive so I don't touch my internal drive on my Powerbook. I have 1.67Ghz Aluminum powerbook. I have looked around on this site to find some tutorials but I would like someone who has done this to list the steps as to what I need to do.
[/QUOTE]

Hi.

I am also interested in this. I have an iBook and external usb2-drive. I would love to use Kubuntu on my iBook but I don't wan't to erase my hard drive and live cd/dvd does not seem to be ideal solution because I wan't to save my settings, bookmarks, files etc.

-B

---

### Post by brent.stephens on 2005-11-16
OK...we can do it without an initrd.  And its actually quite simple...once I found out how after weeks of trying.  Mac mini colocation pricing made it worthwhile ;)  FWIW, I just picked this thread over the 3 or so other ones addressing the same subject because its the one with the latest activity.

I was going to write it all out, but [this site](http://hansmi.ch/articles/boot-linux-from-firewire) explains the bulk of it.  There is one major mistake in it, however.  The [color=blue]ofdevice[/color] declaration should be **left empty** after [color=red]disk@0:[/color].  The partition is not needed, as it is already specified in the [color=blue]partition=[/color] declaration.  Everything else makes it pretty clear.

The next step he must have assumed we all knew.  Once the yaboot.conf is perfect, you have to run [color=red]mkofboot -v[/color].  Now pray.

For what its worth, I basically booted off the Server Install CD, set everything up up until the yaboot install, then dropped to a terminal, chrooted to /target, built kernel packages, installed them, and configured yaboot.  It now all works beautifully.

---

### Post by dwarf75 on 2005-11-21
Hmmm, been reading the whole lot.
I've got the feeling that I'm much more of a newby then you are... so i got a couple of problems.....

Would you mind actually typing it all out, so it can be used as a proper instruction.

That would be excellent.
In addition, is it possible to just put the new kernel on the net, or is it going to be too machine specific?


Cheers
Mike

---

### Post by dwarf75 on 2005-11-21
[QUOTE=brent.stephens]
[...] l, then dropped to a terminal, [...]
[/QUOTE]

which terminal? the shell on the installation disk or the terminal on the live disk?
[QUOTE=brent.stephens]
[...] configured yaboot [...]
[/QUOTE]
how?

 any help appreciated.

---

### Post by brent.stephens on 2005-11-21
[QUOTE=dwarf75]Hmmm, been reading the whole lot.
I've got the feeling that I'm much more of a newby then you are... so i got a couple of problems.....

Would you mind actually typing it all out, so it can be used as a proper instruction.

That would be excellent.
In addition, is it possible to just put the new kernel on the net, or is it going to be too machine specific?


Cheers
Mike[/QUOTE]

I can throw it up for you, but I make no guarantees.  I am actually currently having issues accessing the internal drive from my environment, altho it seems to access fine when booted to the CD.  This doesn't really matter much to me, as the Mac mini's internal drive wasn't going to be used anyway.

I will post the link when its done uploading to my current (soon-to-be-defunct) server.  That will probably be around 30 minutes from now.

The file is kernel.tbz2, its tar'd and bzip2'd.  It contains a folder called kernel-2.6.14.2 which has deb packages of everything going along with it.  Just cd to the dir and dpkg -i everything.

Again, no guarantees.  It is built for a Mac mini, and IDE may in fact be broken.

---

### Post by basscakes on 2005-11-24
I managed to get to the point where many have before me.  I've managed to get my Mac to find the bootstrap partition and yaboot from it.  However, yaboot fails for the expected reason (see the catch-22 thread that is on these boards).  Basically, the scsi module doesn't get loaded, so your firewire drive never shows up and it all goes to hell.

The solution is to custom compile a kernel with SCSI compiled in (not as a module).  I am an experienced redhat user and I develop on RH at work.  But I'm not so familiair with debian beyond hacking around on my Mac at home with fink.  Bottom line, I know I need to compile a custom kernel and install it.  

The key to success is to use the install CD and drop to a terminal (ctrl-option-f2) and follow the instructions that brent.stephens linked to under the "configuring yaboot" section.  You can set-up your yaboot.conf, run mkofboot, and rock.  Note: there is a bogus wiki page that gives incorrect instructions on how to attain the OpenFirmware (abbrevieated as of) path to your partition.  You must use the instructions in [http://hansmi.ch/articles/boot-linux-from-firewire](http://hansmi.ch/articles/boot-linux-from-firewire) (echo /proc/device-tree/pci*/firewire*/node*/sbp-2*).  

Conclusion for me: I don't know how to build the kernel and install it as brent describes.  I'm more than  happy to do so, and would much rather roll my own than use his compiled binaries.  Brent, can you provide us with a link to a HOWTO or some other resource.  I can't tell what state ubuntu is in when the attempt to install yaboot fails.  I ran into things like debootstrap, and so on, but I didn't make any progress.  There's not a lot of people out there who know how to build and compile the kernel at that weird juncture.  Share some gold?  Maybe I can trade you for some perl scripts or whatever.

Thanks
Steve

---

### Post by brent.stephens on 2005-11-24
Sorry, having severe issues with ISPConfig and had to reinstall everything.  Thats taken up a good bit of my time.

[http://brent.warehouse6.com/misc/kernel.tbz2](http://brent.warehouse6.com/misc/kernel.tbz2)

That should work.  They are deb packages.

---

### Post by basscakes on 2005-11-24
Hi Folks--

Thanks to brent.stephens posting of the pre-compiled debian kernel packages, I am writing this message to you from my Mac running Ubuntu off of a firewire drive.  I am setting up a blog to document the process.  check out  [http://macubuntu.blogspot.com/](http://macubuntu.blogspot.com/).  Please comment and I'll work on perfecting my instructions.  If any big dogs out there want to point me to some FAQs on the kernel building process for this specific hack...

---

### Post by brent.stephens on 2005-11-25
[QUOTE=basscakes]Hi Folks--

Thanks to brent.stephens posting of the pre-compiled debian kernel packages, I am writing this message to you from my Mac running Ubuntu off of a firewire drive.  I am setting up a blog to document the process.  check out  [http://macubuntu.blogspot.com/](http://macubuntu.blogspot.com/).  Please comment and I'll work on perfecting my instructions.  If any big dogs out there want to point me to some FAQs on the kernel building process for this specific hack...[/QUOTE]

The 'hack' isn't a kernel hack, but one for the bootloader.  The only thing the kernel needs is more time before it attempts to mount the root device.  Apparently, as I am not sure, this was introduced somewhere around the 2.6.11 kernel series.

The kernel building process is simply one of building the proper support for your hardware and making sure that SCSI Disk, Firewire, and SBP-2 support are built into the kernel instead of as modules.

Thank you for the blogspot, as **anything** is a much needed resource at this point.  Once my setup is complete and the mini is colocated, I should have some more time to add anything that I think might help.  I'm glad you got it running.

---

### Post by MMorbidfaithMM@gmail.com on 2005-12-10
I have been trying many sets of instructions that I have found, including those in the blogs and websites mentioned in this thread.  i am trying to accomplish the same thing with my firewire drive, and I cannot seem to figure it out.  I am a newbie at this stuff, can anyone tell me what I should do differently, or what i'm doing wrong.  Various steps do not work for me while following these instructions, particularly those involving changing directories and copying directories.

---

### Post by nulio on 2005-12-17
Hello,
I am a newbie as well. Is it possible to post a real step-by-step how to ?
By the way the link to the kernel is broken. Anyway if you use another computer e.g powermac g5 you will have to reconfigure your kernel or am i wrong ? If you have to, how do you configure it ?

---

### Post by nulio on 2005-12-17
... ok tried it 
Blocked here
"echo /proc/device-tree/pci*/firewire*/node*/sbp-2*"
Doesn't give me anything else than: echo /proc/device-tree/pci*/firewire*/node*/sbp-2*

And yeah anyway this: [http://brent.warehouse6.com/misc/kernel.tbz2](http://brent.warehouse6.com/misc/kernel.tbz2) is broken...

---

### Post by jlgoolsbee on 2006-02-06
I see no one's touched this thread in awhile, but...

I 've been going through this process, and tonight the link ([http://brent.warehouse6.com/misc/kernel.tbz2](http://brent.warehouse6.com/misc/kernel.tbz2)) worked, but then about 20 minutes later (when I actually went to download the file) the link was broken.

Anybody know if this file is hosted somewhere else?  Or if it was just moved?

If someone can point me to simple, easy to understand instructions to rolling my own kernel, I don't mind trying it, but I would consider myself a newbie on this stuff (especially rolling my own kernel).

Is it possible that Dapper Drake will have better support for installing/booting off an external firewire HD, and I've just missed it somewhere, and that's why this thread and link are dead?

---

### Post by brent.stephens on 2006-02-07
[QUOTE=jlgoolsbee]I see no one's touched this thread in awhile, but...

I 've been going through this process, and tonight the link ([http://brent.warehouse6.com/misc/kernel.tbz2](http://brent.warehouse6.com/misc/kernel.tbz2)) worked, but then about 20 minutes later (when I actually went to download the file) the link was broken.

Anybody know if this file is hosted somewhere else?  Or if it was just moved?

If someone can point me to simple, easy to understand instructions to rolling my own kernel, I don't mind trying it, but I would consider myself a newbie on this stuff (especially rolling my own kernel).

Is it possible that Dapper Drake will have better support for installing/booting off an external firewire HD, and I've just missed it somewhere, and that's why this thread and link are dead?[/QUOTE]


Change warehouse6 to liquid5th and it should work.  Sorry about that...lots of changes...

---

### Post by dwarf75 on 2006-02-18
I've tried it all yesterday and was partially successfull.
Here are the things from the blog that I had problems with and I think ultimately led to a non-booting kernel.

BTW, I'm using the Kubuntu 5.10 DVD, hence I am able to run it as a live CD and install from it. This is somewhat important as will become clear later on.

From the blog:

[COLOR="DarkRed"]Your install will crap out when it tries to install yaboot. Now the fun begins. Drop to a terminal by typing "alt-f2" (aka option-f2).
[/COLOR]
I actually continued installing without the bootloader until the point where it tells me to reboot. There, the "alt-f2" didn't work for me and I used the "Go back" option to enter the manual set-up. One of the last options allows you to execute the shell. I did just that.

[COLOR="DarkRed"]Type chroot /target[/COLOR]

works fine for me.

[COLOR="DarkRed"]Type "echo /proc/device-tree/pci*/firewire*/node*/sbp-2*"[/COLOR]
Does absolutely nothing, except as others have already said, it displays:" /proc/device-tree/pci*/firewire*/node*/sbp-2*".
So my idea was, as the openfirmware path seems to be hardware dependent, I can just run Kubuntu as live CD, drop to the terminal and enter above command.
That worked rather nicely, giving me back this:
[COLOR="Red"]/proc/device-tree/pci@f4000000/firewire@e/node@0030e000e000005c/sbp-2@000[/COLOR]
So far so good. As that means that I've aborted the earlier installation, I have to do it all over again.

[COLOR="DarkRed"]
Type "apt-get install wget".
[...]
cd into that dir, kernel-2.6.14.2 or something like that, mine is blown away now[/COLOR]

All of that works. BTW, Brent's link works again.

[COLOR="DarkRed"]type "dpkg -i *". you can ignore whatever warning messages safely[/COLOR]
not working. tells me that I need a file to do this with. Hence I think that the command is incomplete. But I have got no idea what it should be.


Now, here come to big problems:
1.) vi just won't work on my machine. It'll open but won't let me type.
2.) my OF path looks very different to the one discribed in the blog.

Solution 1.) 
I copied the yaboot config from the blog. Made my changes to it on another computer. Uploaded it to the web. changed directories to /etc. Deleted the original yaboot.conf and downloaded my amended file to the directory using "wget http:///....."

Solution 2.)
I truncated the OF path to fit the syntax shown in the blog. 
-> ofboot=fw/node@00d04b4a1905397c/sbp-2@c000/disk@0:2 
Hence, 
ofboot=/proc/device-tree/pci@f4000000/firewire@e/node@0030e000e000005c/sbp-2@000/disk@0:2
became[COLOR="SeaGreen"]
ofboot=fw/node@0030e000e000005c/sbp-2@000/disk@0:2[/COLOR]

And here it where assume I went wrong.
Can anyone shed any light on this? Also, you might notice, that in the blog, the last part of the ofboot sequence is:
/sbp-2@c000/disk@0:2 
while mine is
/sbp-2@000/disk@0:2 (without the c in 2@000/)

would that be the problem?


No following the blog.

I typed in
[COLOR="DarkRed"]mkofboot -v[/COLOR]
And it worked just fine.

Now restarting the computer and holding down the "option key", my mac recognises the external disk as a bootable linux disk!

However when I select the disk and boot, it blacks out and takes me back to the disk choice screen.

So, in summary, the major problems with the blog, that need improvement:
1.) the "echo /proc/..." command does bugger all to give you the OF Path
2.) "dpkg -i" is incomplete and does bugger all
3.) What do you do with the firmware path? Do you make it the same form as the one in the blog or do you use all of yours?

Hoping to here from anyone about this.

Cheers

---

### Post by Korolyuk15 on 2006-03-04
excuse me if i appear totally ignorant....but this step by step process and/or kernel are firewire specific, correct? so if my external Hard drive is USB 2.0, there is no point in trying these instructions without some modifications?

thanks for all the help guys

---

### Post by The Talking Yogurt on 2006-03-08
Hello to everyone, this is first post on the Ubuntu forums !

I plan to install some Linux distribution soon (maybe Ubuntu... ?) on an external Firewire HD but having no experience with OpenFirmware, I thought lurking in various forums first would be a good idea.

Regarding the following commands in succession:

```
chroot /target

echo "/proc/device-tree/pci*/firewire*/node*/sbp-2*"
```

They do not work because [COLOR="Blue"]/proc[/COLOR] is not mounted in the [COLOR="Green"]chroot[/COLOR] environment. It might work if you type the following:

```
chroot /target
[COLOR="Red"]mount -t proc proc /proc[/COLOR]
echo "/proc/device-tree/pci*/firewire*/node*/sbp-2*"
```

which mounts [COLOR="Blue"]/proc[/COLOR] so that the [COLOR="Green"]echo[/COLOR] command outputs something useful.


On to another problem,

> 1.) vi just won't work on my machine. It'll open but won't let me type.

I suppose (perhaps wrongly) you are not used to [COLOR="Green"]vi[/COLOR]; its use may seem awkward at first. Another editor choice would be [COLOR="Green"]nano[/COLOR] and I am almost sure it is available on the Ubuntu installation disk.

For the rest, I will have to try installing Ubuntu myself first :)

Cheers,

tty

---

### Post by Korolyuk15 on 2006-03-08
i am about to do exactly the same thing as soon as my firewire drive gets here in teh mail...please share your experience with us all

thanks

---

### Post by dwarf75 on 2006-03-18
talking yoghurt,
just tried another install with your edited proc  command
i.e.: 
mount -t proc.......

not working!

Any ideas?

Have you tried your install, I mean, has you're firewire drive arrived?

---

### Post by MalteL on 2006-10-08
I'm very interested in installing Ubuntu/PPC on a external HDD, too. Unfortunately, it seems that the kernel kindly built and uploaded by brent.stephens has disappeared. Is is possible for you to reupload it? Or are there others who still have it lying around?

Thanks in advance.

---

### Post by didg on 2006-10-09
Which Ubuntu version do you use? With Edgy the stock kernel and initrd work out of the box.

I don't know if the installer is ok though (I haven't used it for my install). 

Of course as opath is only for IDE and SCSI drives you have to manually configure yaboot.conf.

---

### Post by brent.stephens on 2006-10-21
I'm sorry that its taken so long to get this stuff back up.  I had a situation where I had to completely migrate all of mine and my clients stuff to my own personal Mac mini and then colocate it.  It wasn't fun.  But hey, now its a dual-core Intel mini ;)

Below is a link to a directory containing debs of the kernel image, kernel docs, kernel headers, and kernel source.  Hope it helps.  Enjoy :)

[http://brent.stephenscorp.com/ppc-kernel](http://brent.stephenscorp.com/ppc-kernel)

---

### Post by macman213 on 2006-11-29
I want to do the same... This is not working for me... can any body help???

---

