---
title: "Where or how do you get chipset drivers?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Dominic02L on 2006-11-02
Hello, these are fantastic forums, and yes I am a newbie, but with your help I hope, one day, not to be...
I do not have the slighest idea how to install drivers on linux, my laptop is a dell inspiron and its graphics card is this one: [http://www.intel.com/products/chipsets/910gml/index.htm](http://www.intel.com/products/chipsets/910gml/index.htm)

I'd like to get my res set up right so i'm assuming i'd need to install the drivers for that chipset, but i don't know how.... please help me..

---

### Post by jpeddicord on 2006-11-02
You don't need to install any drivers, they come by default.

Try going to System > Prefrences > Screen Resolution.

Jacob

---

### Post by podunk on 2006-11-02
Intell has a page here:
[http://www.intellinuxgraphics.org/index.html](http://www.intellinuxgraphics.org/index.html)

but it looks sort of complex. If I were doing it I would give this a try first:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28Intel.29)

---

### Post by Dominic02L on 2006-11-02
> **jacobmp92 said:**
> You don't need to install any drivers, they come by default.

Try going to System > Prefrences > Screen Resolution.

Jacob

thanks jacob, but that only gives me the one option which is the wrong res for my screen unfortunately.


> **podunk said:**
> Intell has a page here:
[http://www.intellinuxgraphics.org/index.html](http://www.intellinuxgraphics.org/index.html)

but it looks sort of complex. If I were doing it I would give this a try first:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28Intel.29)

Sorry my knowledge is basic at best, what is it i am supposed to do?

---

### Post by devilsadvocate1987 on 2006-11-02
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

try doing that. It should work

---

### Post by Dominic02L on 2006-11-03
> **devilsadvocate1987 said:**
> [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

try doing that. It should work

Thank you too, my linux knowledge is none existent at this point, but i learn fast, so could you please explain what i should be doing?

---

### Post by PriceChild on 2006-11-03
The guide they have linked you to is pretty complete.

Where it tells you to enter code... put it into a terminal.

(Applications>Accessories>Terminal)

---

### Post by Dominic02L on 2006-11-03
> **PriceChild said:**
> The guide they have linked you to is pretty complete.

Where it tells you to enter code... put it into a terminal.

(Applications>Accessories>Terminal)

You guys are great, thanks for putting up with my stupidity...so I have opened the terminal, entered my password and typed 
"sudo apt-get install 915resolution"
I also tried changing the 915 to 910
"sudo apt-get install 910resolution"

but i'm getting this message:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 915resolution"

---

### Post by podunk on 2006-11-03
It sounds like you need to "Enable Extra Repositories" - a one time thing with instructions here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Also - it sounds like maybe you skipped 2 steps? Did you download and install "alien" and did you do the part that starts with "wget" above the 915 resolution section on the ubuntuguide?

---

### Post by Dominic02L on 2006-11-03
> **podunk said:**
> It sounds like you need to "Enable Extra Repositories" - a one time thing with instructions here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Also - it sounds like maybe you skipped 2 steps? Did you download and install "alien" and did you do the part that starts with "wget" above the 915 resolution section on the ubuntuguide?


Yes, I am an idiot, and somewhat threatened by this new system....well i get as far as "915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted"

and that is as far as i can go.

---

### Post by bodhi.zazen on 2006-11-03
You need to use "sudo"

```
sudo 915resolution [color=green]5c[/color] [color=red]1280 800[/color] [color=blue]24[/color]
```
[color=green]Mode to be changed[/color]
[color=red]Desired resolution[/color]
[color=blue]Desired color depth[/color]

Thus the Mode "5c" will be changed from the default resolution of 1920x1440 to the desired resolution of 1280x800 and a color depth of 24 bits.

I wrote a more dtaiiled how-to on this line:
[Monitor resolution](http://ubuntuforums.org/showthread.php?t=269052)

See the intel section near the bottom of my post.

---

### Post by Dominic02L on 2006-11-03
> **bodhi.zazen said:**
> You need to use "sudo"

```
sudo 915resolution [color=green]5c[/color] [color=red]1280 800[/color] [color=blue]24[/color]
```
[color=green]Mode to be changed[/color]
[color=red]Desired resolution[/color]
[color=blue]Desired color depth[/color]

Thus the Mode "5c" will be changed from the default resolution of 1920x1440 to the desired resolution of 1280x800 and a color depth of 24 bits.

I wrote a more dtaiiled how-to on this line:
[Monitor resolution](http://ubuntuforums.org/showthread.php?t=269052)

See the intel section near the bottom of my post.


Thank you all so much, as soon as I get back from shooting i'll try this out....its one step at a time but I'm learning. Thanks
bodhi.zazen, thanks a million.

---

### Post by Dominic02L on 2006-11-03
"dominic@Revolution:~$ sudo alien dri-I915-v1.1-20041217.i386.rpm
Warning: Skipping conversion of scripts in package dri-I915: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
dri-i915_v1.1-20041218_i386.deb generated
dominic@Revolution:~$ sudo dpkg -i dri-i915_v1.1-20041218_i386.deb
Selecting previously deselected package dri-i915.
(Reading database ... 88743 files and directories currently installed.)
Unpacking dri-i915 (from dri-i915_v1.1-20041218_i386.deb) ...
Setting up dri-i915 (v1.1-20041218) ...
dominic@Revolution:~$ sudo apt-get install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1kB of archives.
After unpacking 131kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe 915resolution 0.5.2-4ubuntu1 [15.1kB]
Fetched 15.1kB in 0s (37.2kB/s) 
Selecting previously deselected package 915resolution.
(Reading database ... 88748 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.2-4ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.2-4ubuntu1) ...
Starting 915resolution: Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 3c to resolution 1280x800 complete
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 4d to resolution 1280x800 complete
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 5c to resolution 1280x800 complete
915resolution.

dominic@Revolution:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel
dominic@Revolution:~$ sudo 915resolution 5c 1280 800 24
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 5c to resolution 1280x800 complete
dominic@Revolution:~$ sudo gedit /etc/rc.local"




god bloody dammit, that didn't work either, my res is stuck on 1024x768

---

### Post by bodhi.zazen on 2006-11-03
Looks good. Well what was that alien???

At any rate, REBOOT

---

### Post by Dominic02L on 2006-11-05
coooooool thanks guys, works fine ..... unfortunately i broke my broadband router :D so i'll be offline for a little while....but thanls a million for your help, all of you

---

