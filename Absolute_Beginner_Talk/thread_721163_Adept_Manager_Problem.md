---
title: "Adept Manager Problem"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by mikkko on 2008-03-11
as it said in my topic, my adept manager would not open.. 

i dont know why..

all i did was type 'sudo apt-get update' and the updater told me i have 3 new updates.. so i clicked on the little icon in the lower left part of the taskbar but the adept updater would not open, so i clicked kmenu>system>adept manager. it just loads but the window does not appear.. what should i do.. i need to find more updates using adept.. 

hoping for ur help guys.. thanks

---

### Post by wieman01 on 2008-03-11
Please start Adept from command line and post the terminal output if it still fails:
> sudo adept

---

### Post by hyper_ch on 2008-03-11
actully you should be using

```

kdesu adept

```

instead of

```

sudo adept

```

---

### Post by wieman01 on 2008-03-11
I never really got why people keep recommending this. I know there must be a reason, hyper_ch, but to me it makes little or even no difference. Any idea why? 'sudo' works perfectly fine.

---

### Post by mikkko on 2008-03-11
recommend what?


anyways, it gives me this output:

$ kdesu adept
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
sh:
adept: not found

---

### Post by wieman01 on 2008-03-11
Now please do:
> sudo apt-get install adept
And try again:
> kdesu adept

---

### Post by mikkko on 2008-03-11
$ sudo apt-get install adept
Reading package lists... Done
Building dependency tree
Reading state information... Done
adept is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


$ kdesu adept
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
sh:
adept: not found


i dont know what to do anymore.. will this be fixed still? :(:(:(

---

### Post by wieman01 on 2008-03-11
Please now try 'sudo' instead:
> sudo adept

_**EDIT:**_
I remember I have seen this issue before... just cannot put my finger on it right now.

---

### Post by hyper_ch on 2008-03-11
> **wieman01 said:**
> I never really got why people keep recommending this. I know there must be a reason, hyper_ch, but to me it makes little or even no difference. Any idea why? 'sudo' works perfectly fine.

Don't ask me for the technical details of it but gksu and kdesu should be used to start a gui program as root from the shell and sudo should be used to just run code as root in the shell...

Maybe someone can shed light on this - it's just what I learned from the forums here.

---

### Post by mikkko on 2008-03-11
$ sudo adept
sudo: adept: command not found


what is wrong with my adept? why isnt it functioning right?

---

### Post by wieman01 on 2008-03-11
When you type 'adept' in a terminal and press <tab> (= auto completion) is Adept listed at all? What other apps are listed?

I am not in front of my own computer, so I cannot test it myself.

---

### Post by mikkko on 2008-03-11
$ adept_
adept_batch      adept_manager    adept_updater
adept_installer  adept_notifier


this is what it says

---

### Post by wieman01 on 2008-03-11
> **hyper_ch said:**
> Don't ask me for the technical details of it but gksu and kdesu should be used to start a gui program as root from the shell and sudo should be used to just run code as root in the shell...

Maybe someone can shed light on this - it's just what I learned from the forums here.
Yeah... I guess so. I keep challenging it because nobody has really given me a reasonable explanation yet, even Aysiu's outline on his personal website isn't really satisfying.

---

### Post by wieman01 on 2008-03-11
Now do:
> kdesu adept_installer

---

### Post by mikkko on 2008-03-11
i tried typing kdesu adept_manager.. i got this...

$ kdesu adept_manager
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
Xlib: connection to ":0.0" refused by server
Xlib:
No protocol specified

adept_manager: cannot connect to X server :0.0

---

### Post by mikkko on 2008-03-11
> **wieman01 said:**
> Now do:

$ kdesu adept_installer
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
Xlib: connection to ":0.0" refused by server
Xlib:
No protocol specified

adept_installer: cannot connect to X server :0.0

---

### Post by wieman01 on 2008-03-11
What about:
> sudo adept_installer

---

### Post by hyper_ch on 2008-03-11
I dunno, I have the feeling something is seriously broken there...

I'd remove all of x11 and kde and reinstall the kubuntu-desktop.

---

### Post by mikkko on 2008-03-11
$ kdesu adept_installer
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
xauth: (argv):1: bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1: bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1: bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
Xlib: connection to ":0.0" refused by server
Xlib:
No protocol specified

adept_installer: cannot connect to X server :0.0

i do not know what could have caused this..

---

### Post by wieman01 on 2008-03-11
No, I mean 'sudo', don't use 'kdesu':
> sudo adept_installer

---

### Post by mikkko on 2008-03-11
the adept installer window loaded.. im gonna try sudo-ing the manager now.. i hope it wouldnt give any problems

---

### Post by wieman01 on 2008-03-11
So 'sudo' seems to work as opposed to 'kdesu'... strange. I have seen this before... let me think for a while. I think you need to remove a hidden folder in your home directory but I don't seem to recall which one it was.

---

### Post by mikkko on 2008-03-11
will this be resolved if i upgrade feisty to gutsy? coz i intend to do so in a couple of days when the cable guys install internet in my house.. :):lolflag:

---

### Post by wieman01 on 2008-03-11
Frankly I don't know... I am running out of ideas. Does 'sudo' work for you?

---

### Post by mikkko on 2008-03-11
sudo adept_manager opens adept manager

kdesu adept_manager doesnt

---

### Post by wieman01 on 2008-03-11
**mikkko:**

Is there a file like:
> /.kde/share/config/adept*
Or something similar?

---

### Post by bapoumba on 2008-03-11
To the OP: please post the output to (from your /home file):
```
ls -la .Xauth*
cat /etc/hosts
groups
gksudo -S -d gedit

```
Not running KDE, I'm not sure you can run kdesu with the same options:
```
kdesu -S -d kate
```

---

### Post by wieman01 on 2008-03-11
Thank you, Bapoumba. :-)

---

### Post by bapoumba on 2008-03-11
> **wieman01 said:**
> Thank you, Bapoumba. :-)
You're welcome :)

in addition to the OP, what is the output to:
```
update-manager
```

---

### Post by mikkko on 2008-03-11
the only files that start with A are


amarokrc
arkrc

---

### Post by wieman01 on 2008-03-11
What other files are there? Please also take a look at Bapoumba's posts. They might yield something as well.

---

### Post by mikkko on 2008-03-11
@bapoumba
i dont understand what to do.. sorry.. can u explain it again please?

---

### Post by mikkko on 2008-03-11
> **wieman01 said:**
> What other files are there? Please also take a look at Bapoumba's posts. They might yield something as well.

sir, is there any file that ill be looking for coz there seems to be a lot.. i will try bapo's posts after i install eclipse

---

### Post by wieman01 on 2008-03-11
No need to call me "sir". We are friends in here, you know.

Any files the resembles "adept"... Nothing?

Bapo's stuff will certainly shed some light on the issue. :-)

---

### Post by bapoumba on 2008-03-11
> **mikkko said:**
> @bapoumba
i dont understand what to do.. sorry.. can u explain it again please?

Just run the commands in a terminal and paste the whole output in here. As I do not really see what is wrong, these are basic verifications. I have to go for now, but I'll check back in here as soon as I can.

---

### Post by mikkko on 2008-03-11
oh ok.. sorry about that... anything that resembles adept... hold on...

uhm.. there is no file that links to adept..

anyhoo, can u explain how to do bapo's? i dont seem to understand how to do it.. :(

---

### Post by hyper_ch on 2008-03-11
> **wieman01 said:**
> No need to call me "sir".
... because it makes you feel old? ^^

---

### Post by mikkko on 2008-03-11
$ ls -la .Xauth*
-rw------- 1 mino mino 302 2008-03-11 15:17 .Xauthority
mino@:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 minomins

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
mino@:~$ groups
mino adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin p                                      owerdev admin
mino@:~$ gksudo -S -d gedit
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found

---

### Post by mikkko on 2008-03-11
$ kdesu -S -d kate
kdesu: Unknown option '-S'.
kdesu: Use --help to get a list of available command line options.

---

### Post by wieman01 on 2008-03-11
> **hyper_ch said:**
> ... because it makes you feel old? ^^
In fact, yes. Pretty much. ;-)

---

### Post by mikkko on 2008-03-11
> **wieman01 said:**
> In fact, yes. Pretty much. ;-)

my bad.. sorry about that

---

### Post by wieman01 on 2008-03-11
> **mikkko said:**
> my bad.. sorry about that
Don't worry, we're just kidding, mate.

---

### Post by mikkko on 2008-03-11
i think the only way to open my adept is to sudo it.. anyways, i got this other prob with my external HD..

the EHD has been partitioned and feisty cannot read it.. i mean when i plug it in, a windows pops up asking me what to do, and when i click open folder, it would not open.. and it the mounted volume icon on the desktop wont appear..

i tried other ehds(without partitions) and they work perfectly.. i have no other ehds with partitions though.. just one..

---

### Post by bapoumba on 2008-03-11
> **mikkko said:**
> $ kdesu -S -d kate
kdesu: Unknown option '-S'.
kdesu: Use --help to get a list of available command line options.

Okay, I looked at the man page, and indeed there is no sudo mode for kdesu, sorry. Then try:
```
kdesu -d kate
```

And please also paste the output to:
```
update-manager
```
Do you see the window open?

The other outputs were correct. Hmm.

---

### Post by wieman01 on 2008-03-11
Just to recap... 'sudo' works fine, 'kdesu' does not. Perhaps reinstalling 'kdesu' would help, no idea. I saw similar bugs on Launchpad and the consense seems to be that you have to remove 'kdesu' and install it once again.

---

