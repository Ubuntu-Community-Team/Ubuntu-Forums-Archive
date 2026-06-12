---
title: "[SOLVED] Help me free my laptop from windows"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by tarek on 2007-07-13
Hello everyone,

After using Ubuntu (Linux) for a few months I can't stand Windows anymore. I have Ubuntu on my desktop but I still have Windows on my laptop.

I tried Ubuntu Feisty, dapper, Fedora and openSUSE but couldn't get the laptop to wakeup from the suspend or hibernate state. I know that the cause is the graphics card: ATI Xpress 200M and I tried many how-tos but they failed to work.

I formatted my hard drive 4 times last week trying distributions, I'm afraid of burning the thing. I don't even want the TV-out to work anymore, I'll be happy to get the system to function properly.

The CPU is AMD Turion 64. Is anybody out there who has the same card and has the suspend and hibernate working?

Any suggestions are appreciated .... I just wanna get rid of Windows.

Thanks!
Tarek

---

### Post by destructchaos on 2007-07-13
dumb sugestion, but if you want windoze off your box so badly, you could just not send it into suspend or hibernate until you find a workable solution.

---

### Post by tarek on 2007-07-13
> **destructchaos said:**
> dumb sugestion, but if you want windoze off your box so badly, you could just not send it into suspend or hibernate until you find a workable solution.

That's not gonna work :) I use my laptop in different places and starting up or shutting down the system "eats" the battery.

---

### Post by Amplidude on 2007-07-13
> couldn't get the laptop to wakeup from the suspend or hibernate state

But you could still boot up from scratch? I'm not being impertinent here, but what's so important about hibernate and suspend. I've never used them. Seriously, I'd never miss them. But to answer your question, try this thread [http://ubuntuforums.org/showthread.php?t=498300&goto=newpost](http://ubuntuforums.org/showthread.php?t=498300&goto=newpost)

---

### Post by stchman on 2007-07-13
> **tarek said:**
> Hello everyone,

After using Ubuntu (Linux) for a few months I can't stand Windows anymore. I have Ubuntu on my desktop but I still have Windows on my laptop.

I tried Ubuntu Feisty, dapper, Fedora and openSUSE but couldn't get the laptop to wakeup from the suspend or hibernate state. I know that the cause is the graphics card: ATI Xpress 200M and I tried many how-tos but they failed to work.

I formatted my hard drive 4 times last week trying distributions, I'm afraid of burning the thing. I don't even want the TV-out to work anymore, I'll be happy to get the system to function properly.

The CPU is AMD Turion 64. Is anybody out there who has the same card and has the suspend and hibernate working?

Any suggestions are appreciated .... I just wanna get rid of Windows.

Thanks!
Tarek

Sadly you have touched on an area that Ubuntu (and Linux in general) does have problems with?  My laptop will suspend and hibernate, but it is spotty and sometimes I cannot get it to wake up.  I have disabled those functions as they are a non factor for me.

From everything I have read XP is far better with suspend and hibernate than Ubuntu.

---

### Post by destructchaos on 2007-07-13
> **Amplidude said:**
> But you could still boot up from scratch? I'm not being impertinent here, but what's so important about hibernate and suspend. I've never used them. Seriously, I'd never miss them. But to answer your question, try this thread [http://ubuntuforums.org/showthread.php?t=498300&goto=newpost](http://ubuntuforums.org/showthread.php?t=498300&goto=newpost)

+1

i use kubuntu on my laptop and have never once suspended or hibernated it.  if you think the boot process is really that slow, go get a drink or a bag of chips, or something.  though, i've never really been comfortable with the concept or theory behind suspension/hibernation anyways.  i don't like the answers to all of the "what ifs".

---

### Post by sab0403 on 2007-07-13
> **tarek said:**
> Hello everyone,

After using Ubuntu (Linux) for a few months I can't stand Windows anymore. I have Ubuntu on my desktop but I still have Windows on my laptop.

I tried Ubuntu Feisty, dapper, Fedora and openSUSE but couldn't get the laptop to wakeup from the suspend or hibernate state. I know that the cause is the graphics card: ATI Xpress 200M and I tried many how-tos but they failed to work.

I formatted my hard drive 4 times last week trying distributions, I'm afraid of burning the thing. I don't even want the TV-out to work anymore, I'll be happy to get the system to function properly.

The CPU is AMD Turion 64. Is anybody out there who has the same card and has the suspend and hibernate working?

Any suggestions are appreciated .... I just wanna get rid of Windows.

Thanks!
Tarek

How is it that you know it's the graphics card that's the problem? Genuinly curious here...

Anyway, have you tried installing the latest ATI drivers?

---

### Post by tarek on 2007-07-13
Take it easy people! I use suspend/hibernate all the time since I use the laptop for a long periods of time without power and I don't have to close and save everything every time. I want to keep my battery alive as long as possible. Obviously rebooting is not the answer and not an option!

The problem is the ATI card because every time I install the drivers, from ATI website or open source, the problem starts. I searched online and found that this is a common problem with XPRESS.

I'm just asking if somebody got the card to work properly.

TK

---

### Post by Inxsible on 2007-07-13
Have you tried out uswsusp from the repos?

It seems to work for a lot of people. Not for me tho :(

```
sudo aptitude install uswsusp
```

Look at post # 19 and follow those instructions after you install uswsusp 

[http://ubuntuforums.org/showthread.php?t=194426&page=2](http://ubuntuforums.org/showthread.php?t=194426&page=2)

---

### Post by stchman on 2007-07-13
> **tarek said:**
> Take it easy people! I use suspend/hibernate all the time since I use the laptop for a long periods of time without power and I don't have to close and save everything every time. I want to keep my battery alive as long as possible. Obviously rebooting is not the answer and not an option!

The problem is the ATI card because every time I install the drivers, from ATI website or open source, the problem starts. I searched online and found that this is a common problem with XPRESS.

I'm just asking if somebody got the card to work properly.

TK

Have you tried the restricted ATI driver?  That works well with my laptop.

---

### Post by anewguy on 2007-07-13
Hi tarek! :)   Sorry I can't help with your problem as you did with mine, but I did want to say that I understand perfectly wanting to use hibernate - not only does it save your battery life but since you are "warm" booting when you wake up, you end up right back where you were without the hassles of starting everything up.

I have a cheap Gateway MX3215, and so far hibernate has been kind of spotty.  Without changing anything (that I KNOW of!:) ), I can hibernate one time and wake up fine, the next time it sort of wakes up but I can't do anything, other times it just doesn't wake up at all.  I've never really researched it, so I'll keep an eye on this post even though I just use a cheap IGP in my laptop.  I know the driver for my IGP has good points and bad points - some not so good.

Good luck!!:)

---

### Post by SyberKowboy on 2007-07-13
I have a new MSI whitebook that I put together and run a triple boot right now. Ubuntu seems to suspend just fine but will not hibernate at all. I never got into hibernation although many of my techy friends use it. Windoze is a lot better than Ubuntu when it comes to suspend/hibernate but the nightmares with stability are just not worth a little extra juice. <my two cents>

---

### Post by tarek on 2007-07-13
> **stchman said:**
> Have you tried the restricted ATI driver?  That works well with my laptop.

Hi, 

Yes I tried the restricted ATI driver but unfortunately it didn't work. 

I'm installing Kubuntu once again right now and this time I'm gonna try Inxsible's link.

I'll post an update once everything is installed.

Thanks everyone
TK

---

### Post by tarek on 2007-07-13
It seems that the new kernel 2.6.22 supports suspend and hibernate. I'm looking for a distro using the new kernel to test. If you know any please post it.

tk

---

### Post by tarek on 2007-07-15
> **anewguy said:**
> Hi tarek! :)   Sorry I can't help with your problem as you did with mine, but I did want to say that I understand perfectly wanting to use hibernate - not only does it save your battery life but since you are "warm" booting when you wake up, you end up right back where you were without the hassles of starting everything up.

I have a cheap Gateway MX3215, and so far hibernate has been kind of spotty.  Without changing anything (that I KNOW of!:) ), I can hibernate one time and wake up fine, the next time it sort of wakes up but I can't do anything, other times it just doesn't wake up at all.  I've never really researched it, so I'll keep an eye on this post even though I just use a cheap IGP in my laptop.  I know the driver for my IGP has good points and bad points - some not so good.

Good luck!!:)

Hi anewguy, I got the suspend and hibernate working :D 
Thanks to Inxsible, I followed the link you had and got the hibernate working.

Here's what I did:

I have AMD 64 but I installed FF 32 bit since flash and other things don't quite work yet.

1. Fresh install of Ubuntu 7.04.

2. Enable Restricted Drivers from the Administration menu to get TV-out + 3D working.

3. install uswsusp:
```
sudo aptitude install uswsusp
```

4. To get hibernate to work:

Edit /etc/acpi/hibernate.sh
```
sudo cp /etc/acpi/hibernate.sh /etc/acpi/hibernate_backup.sh_backup
sudo vi /etc/acpi/hibernate.sh

```

You'll get something like this:
```

blah blah ....

if [ -x /sbin/s2disk ]; then
DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
if [ -f /etc/usplash.conf ]; then
. /etc/usplash.conf
/sbin/s2disk -x "$xres" -y "$yres" $DEVICE
else
/sbin/s2disk $DEVICE
fi
else
echo -n "disk" >/sys/power/state
fi

blah blah ....

```

Replace it with:
```
if [ -x /sbin/s2disk ]; then
/sbin/s2disk
else
echo -n "disk" >/sys/power/state
fi
```

As described here: [http://ubuntuforums.org/showpost.php?p=2582225&postcount=19]("http://ubuntuforums.org/showpost.php?p=2582225&postcount=19") have a look to understand what and why.

5. suspend works just fine without changing anything.

6. when the pc wakes up from suspend (not hibernate) the wired network doesn't work even if you try to restart networking. The wireless network works though. To fix the problem:

Go to System > Preferences > Hardware info.

Find the network card and click on the advanced tab on the right hand side and find info.linux.driver, copy the value.

Edit /etc/default/acpi-support
```
sudo cp /etc/default/acpi-support /etc/default/acpi-support_backup
sudo vi /etc/default/acpi-support
```

Find: MODULES_WHITELIST="" and enter the value you have in info.linux.driver Mine like this:
```
MODULES_WHITELIST="8139too"
```

7. Done.

I got it working last night, so far so good. I had one problem where the laptop keyboard and mouse didn't work after the suspend but it only happened once, not sure what caused it yet.

Please let me know if you have other solutions. It's seems that every suspend something new happens so share your experiences.

Good Luck!

Tarek



**[COLOR="Red"]EDIT 1:[/COLOR]**

Also when I logout I get black screen and no keyboard or mouse/touchpad. To fix edit /etc/gdm/gdm.conf
```
sudo vi /etc/gdm/gdm.conf 
```

Find:  #AlwaysRestartServer=false (mine at line 97)
Remove # to uncomment and change false to true
```
AlwaysRestartServer=true
```

Restart X by pressing Control + Alt + Backspace
Done.



**[COLOR="Red"]EDIT 2:[/COLOR]**

Another update, I just got the keyboard/mouse problem fixed too. Just follow the instructions in this post:
[http://ubuntuforums.org/showpost.php?p=2690982&postcount=14]("http://ubuntuforums.org/showpost.php?p=2690982&postcount=14")

The fixes are out there but everywhere. I'm gonna do a clean 64 bit installation of FF and apply all the fixes then post a clean step by step tutorial.

If I encounter another problem/fix I'll update this post.

TK

---

### Post by RavanH on 2007-07-15
Thank Tarek, for your clear How-To :)

Sadly, in my case it didn't get hibernation or suspend working. It used to be like this: 
A. suspend did shut down the system (to suspended mode) but restarting resulted in an error indicating that resume failed and network down
B. hibernation did not shut down system, only brought me right back at login (the one that should be invoked at resume, not after reboot)

After following your instructions, the situation changed to this:
Both hibernation and suspend do not shut down system, only brings me right back at login as if I resumed the system.
EDIT: And networking now can only be restored by doing a 
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```


Any ideas what can be causing this? I'm using the buggy ATI drivers, would that be messing with S2D and S2R?

--ravan

---

### Post by tarek on 2007-07-15
I added another fix.

Ravan, I'm not sure why but did you restart after making the changes?

tk

---

### Post by RavanH on 2007-07-15
> **tarek said:**
> I added another fix.

Ravan, I'm not sure why but did you restart after making the changes?

tk

Yes, I did... Also the AlwaysRestartServer value (which I already had set to true) does not change anything...

---

### Post by ugm6hr on 2007-07-23
This takes a similar approach, but the script is a lot simpler.  It worked (to suspend - hibernate not tried) for my Acer Aspire 5051AWXMi (5050 derivative).

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by RavanH on 2007-07-23
> **ugm6hr said:**
> This takes a similar approach, but the script is a lot simpler.  It worked (to suspend - hibernate not tried) for my Acer Aspire 5051AWXMi (5050 derivative).

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

Thanks for the link! It seems to work for suspend2ram/sleep but not for suspend2disk/hibernate... And, ofcourse, it is s2d that i prefer :rolleyes:

---

