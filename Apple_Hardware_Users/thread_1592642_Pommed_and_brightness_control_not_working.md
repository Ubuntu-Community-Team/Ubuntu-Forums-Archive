---
title: "Pommed and brightness control not working"
date: 2010-10-10
forum: Apple Hardware Users
---

### Post by khronoslynx on 2010-10-10
I've installed Ubuntu 10.10 on my Macbook Pro 6,2 and try as I might can't change the brightness of my screen whatsoever. I cant use "echo 100> /sys/devices/virtual/backlight/nvidia_backlight/brightness" because the folder does not exist. Pommed, when run using "sudo pommed -d" complains with "Failed to access brightness node: No such file or directory".

I have the mbp-nvidia-bl driver installed *only* (removed nvidia-bli because I had seen in other threads that the two conflicted). I've tried searching the forums and the web but nothing is helping me so far. Biggest roadblock for me using ubuntu is having the headache of using a much to dim screen(or currently a much too bright screen) :/

Any help at all would be greatly appreciated.
Thanks!

Tim

---

### Post by khronoslynx on 2010-10-11
Also, I'm on 10.10 64-bit (in case that affects it)

---

### Post by zeroti on 2010-10-11
```
man fblevel
```

---

### Post by pantropik on 2010-10-11
I found that the newest mbp-nvidia-bl-dkms package broke backlight control for me, leaving me with two brightness options: 100% or off.

I'm successfully using a pommed I built myself and the mbp-nvidia-bl-dkms version 0.24 for Lucid off the Mactel PPA (with a manual hold to keep it from getting upgraded again). 

Using the 0.25 version of the module (either the Lucid or Maverick one) was a no-go for me. Fortunately, after it got auto-upgraded I found a copy of the older module in my apt cache and was able to downgrade. Soon as I got rid of the 0.25 module and rebooted everything was fine.

---

### Post by teejmya on 2010-10-11
I've dealt with this issue for a while, but finally found a tool that simplifies it.

```

sudo apt-get install nvclock

```

To change the brightness,
```

nvclock -S 100

```

This would set your brightness to 100 percent.

This works on my Macbook White Unibody Late 2009, let me know if all goes well.

---

### Post by khronoslynx on 2010-10-11
> **pantropik said:**
> I found that the newest mbp-nvidia-bl-dkms package broke backlight control for me, leaving me with two brightness options: 100% or off.

I'm successfully using a pommed I built myself and the mbp-nvidia-bl-dkms version 0.24 for Lucid off the Mactel PPA (with a manual hold to keep it from getting upgraded again). 

Using the 0.25 version of the module (either the Lucid or Maverick one) was a no-go for me. Fortunately, after it got auto-upgraded I found a copy of the older module in my apt cache and was able to downgrade. Soon as I got rid of the 0.25 module and rebooted everything was fine.

Which Pommed version are you using? Because even downgrading my mbp-nvidia-bl-dkms didnt change anything, pommed throws the same "Failed to access brightness node" shenanigan.

And nvclock doesn't support my video card yet, and warns that forcing it (using -f then -S) may be dangerous

---

### Post by khronoslynx on 2010-10-11
I reinstalled pommed and got this error after installation: "Starting Apple laptops hotkeys events handler: invoke-rc.d: initscript pommed, action "start" failed."

Any idea?

---

### Post by pantropik on 2010-10-11
I am using the 0.24 module from my other post and a pommed and customized /etc/pommed.conf from [here]("https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Keyboard").

---

### Post by khronoslynx on 2010-10-11
> **pantropik said:**
> I am using the 0.24 module from my other post and a pommed and customized /etc/pommed.conf from [here]("https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Keyboard").

I did that, and now when running "sudo pommed -d" when I use Fn+F2 it says 
Lcd stepping +1->1"

and Fn+F2 says
"Lcd stepping -1 -> 0"

yet my backlight doesnt change at all. I'm using both the mbp-nvidia-bl-dkms you linked and the pommed.conf. But while running pommed complains with "E:Not primary DBus name owner"

Sorry for being such a mess haha

---

### Post by _mario_ on 2010-10-12
> **pantropik said:**
> I found that the newest mbp-nvidia-bl-dkms package broke backlight control for me, leaving me with two brightness options: 100% or off.

Using the 0.25 version of the module (either the Lucid or Maverick one) was a no-go for me. Fortunately, after it got auto-upgraded I found a copy of the older module in my apt cache and was able to downgrade. Soon as I got rid of the 0.25 module and rebooted everything was fine.

actually version 0.25 of mbp-nvidia-bl changes the interface it uses. can you confirm that it definitely doesn't work, but 0.24.x did? which graphics driver are you using?

> **pantropik said:**
> 
I'm successfully using a pommed I built myself and the mbp-nvidia-bl-dkms version 0.24 for Lucid off the Mactel PPA (with a manual hold to keep it from getting upgraded again).

@op: pommed shouldn't be necessary just to change backlight. if the driver is loaded properly gnome-power-manager should just use it. you can verify this by echoing some value (0-15) to /sys/class/backlight/mbp_backlight/brightness.

ciao,
Mario

---

### Post by khronoslynx on 2010-10-12
@_mario_:
My driver must not be loaded correctly. Terminal tells me there is no such file or directory as "/sys/class/mbp_backlight/brightness"

Maybe thats the root of my problem. Any advice on checking if my driver is loaded correctly?]

**Edit**:
after looking through some older forum posts (From late 08/early 09) I saw a tip to try running
sudo rmmod mbp_nvidia_bl 
sudo modprobe mbp_nvidia_bl

cat /sys/class/backlight/mbp_backlight/brightness

in the terminal. Problem occurred when terminal returned **ERROR: Module mbp_nvidia_bl does not exist in /proc/modules**updated it back to the latest version, and am about to restart and see if I still get said errors
I just

**Edit 2:**
Still nothing. Same error occurs both with echo and rmmod

---

### Post by CalaverX11 on 2010-10-13
Same issue here. I am about to re-install Maverick (now that it's in official release) and try again. After updating the RC I was unable to regain brightness control; I hadn't tried the previously-mentioned steps yet, but I will if it's still broken.

---

### Post by khronoslynx on 2010-10-13
I now have the brightness keys to change the brightness "bar" but not the actual LCD brightness. Echoing values to /sys/class/mbp_backlight/brightness still produces the same error

---

### Post by wids on 2010-10-19
[https://bugs.launchpad.net/mactel-support/+bug/662420](https://bugs.launchpad.net/mactel-support/+bug/662420)

---

### Post by kokoklems on 2010-12-03
Hello,

I have maverick (2.6.35-23-generic) installed on my alu iMac 9,1, with a nVidia graphic card: GeForce 9400.

I am struggling for 2 weeks now because I can't decrease the brightness of my screen...
I installed mbp-nvivia-bl-dkms from mactel ppa, but I am not able to load the mbp_nvidia_bl module...

```

sudo modprobe mbp_nvidia_bl
FATAL: Error inserting mbp_nvidia_bl (/lib/modules/2.6.35-23-generic/updates/dkms/mbp_nvidia_bl.ko): No such device

```

Although, my /sys/class/backlight/ directory is empty...

What should I try next? ](*,)

Thank you very much guys for any help you can provide...

---

### Post by _mario_ on 2010-12-03
> **kokoklems said:**
> 
I have maverick (2.6.35-23-generic) installed on my alu iMac 9,1, with a nVidia graphic card: GeForce 9400.


the driver doesn't support iMac models and, hence, doesn't load. in fact, we don't know whether the driver works on this machine at all. i can provide a patched version, if you like to try.

ciao,
Mario

---

### Post by kokoklems on 2010-12-03
Indeed, I would like to give it a try if possible. Thank you for your help. Hope it will work...

---

### Post by _mario_ on 2010-12-10
> **kokoklems said:**
> Indeed, I would like to give it a try if possible. Thank you for your help. Hope it will work...

sorry, i almost forgot this thread. but if you still like to test, i attached a small program, that implements the same interfaces the driver uses. you can compile it like this:
```

$ gunzip apple-backlight.cpp.gz
$ c++ apple-backlight.cpp -o apple-backlight

```

then run:
```

$ sudo ./apple-backlight <OPTIONS>

```
where <OPTIONS> contains which interface to test (--nvidia should work) as well as --get or --set <VALUE>.

also, did you try to use the nvidia_bl driver? please note: installing both drivers is no problem, but mbp_nvidia_bl will not auto-load anymore (which doesn't matter since it doesn't support your machine anyway).

ciao,
Mario

---

### Post by pliz on 2011-01-05
Hi Mario, I have exactly the same problem as described in te current thread  after 10.10 install on macbook pro 6.2:
sudo modprobe mbp_nvidia_bl 
FATAL: Error inserting mbp_nvidia_bl (/lib/modules/2.6.35-24-generic/kernel/drivers/video/backlight/mbp_nvidia_bl.ko): No such device
and also with 
nvclock -Sf 10
Unable to shadow the video bios
It seems your card isn't officialy supported in NVClock yet.
The reason can be that your card is too new.
If you want to try it anyhow [DANGEROUS], use the option -f to force the setting(s).
NVClock will then assume your card is a 'normal', it might be dangerous on other cards.
Also please email the author the pci_id of the card for further investigation.
[Get that value using the -i option].

your tool does the job correctly. Is it integrated into ubuntu already, so the keyboard brightness control works? How do I merge it into my installation (everything is up to date now)?
Thanks!

---

### Post by cathy duncan on 2011-01-05
> **wids said:**
> [https://bugs.launchpad.net/mactel-support/+bug/662420](https://bugs.launchpad.net/mactel-support/+bug/662420)
 
Thanks for the link provided, I found it quite helpful for me as It carries few similar solutions that I required for myself.

---

### Post by tilarids on 2011-02-20
Mario, thanks for your tool! I wasn't able to make mbp_nvidia_bl module work and your tool works just fine.

P.S. I am using Gentoo with 2.6.37, MacBook Pro 6.2. I'm getting the same FATAL: Error inserting mbp_nvidia_bl  (/lib/modules/2.6.37-gentoo/kernel/drivers/video/backlight/mbp_nvidia_bl.ko):  No such device

---

### Post by _mario_ on 2011-02-21
> **tilarids said:**
> Mario, thanks for your tool! I wasn't able to make mbp_nvidia_bl module work and your tool works just fine.

P.S. I am using Gentoo with 2.6.37, MacBook Pro 6.2. I'm getting the same FATAL: Error inserting mbp_nvidia_bl  (/lib/modules/2.6.37-gentoo/kernel/drivers/video/backlight/mbp_nvidia_bl.ko):  No such device

Yepp. You'll have to use the mactel version, because the official version doesn't support your machine yet. (It always takes some time until the patches get accepted upstream.) On gentoo you can either compile it yourself or use dkms as well.

ciao,
Mario

---

### Post by mattywix on 2011-04-27
Hope no-one is offended by me asking on an Ubuntu forum but could anyone tell me how to get mbp_nvidia_bl working for Fedora14?

---

### Post by lordbyron820 on 2011-06-13
I'm now having this problem with Natty on my MacBook Pro 6.2. I tried Mario's cpp tool, which compiles and runs but always reports the brightness as 0.

```

$sudo ./apple-backlight -n -s 1
valid range: 0-15 (0xf)
setting brightness to: 1
current brightness is now: 0

```

Like some of the others posts in this thread, my folder /sys/class/backlight is empty:

```

$find /sys/ |grep backlight
/sys/class/backlight
$
```

nvclock reported that my graphics card isn't supported. I installed nvidia-bl-dkms from mactel, but I notice there is no mbp-nvidia-bl-dkms for Natty. Could that be the issue? Any ideas would be great and thanks for restarting the thread!

---

