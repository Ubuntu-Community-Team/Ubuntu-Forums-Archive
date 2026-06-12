---
title: "Laptop getting too warm for tastes... help?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by ajcarson1 on 2008-03-09
I have read many threads on fan control using LM sensors but am not able to complete hardly any of them.

I use an Asus F3JP laptop which gets a little hot in vista (45idle/55-70load), however vista is able to kick the fan into high gear when the temps get into the 50's. 

In Ubuntu Gutsy the idle temp is between 50-55, and anytime I put the system under load it can jump straight up to 70 (then the fan finally kicks in). I would prefer that the system kick the fan in earlier, but I've read that it is only controlled through the bios.

I have done sensors detect, and the system only detected temperature sensors for my Core2duo processors. I don't get the option of fan control. When I run 

Sudo Pwmconfig

I get this message:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

I'm running the 2.6,14 kernel. Any ideas on how to get ubuntu to force the fan into higher gear based on temp? 

Thanks!

---

### Post by dcstar on 2008-03-10
> **ajcarson1 said:**
> I have read many threads on fan control using LM sensors but am not able to complete hardly any of them.

I use an Asus F3JP laptop which gets a little hot in vista (45idle/55-70load), however vista is able to kick the fan into high gear when the temps get into the 50's. 

In Ubuntu Gutsy the idle temp is between 50-55, and anytime I put the system under load it can jump straight up to 70 (then the fan finally kicks in). I would prefer that the system kick the fan in earlier, but I've read that it is only controlled through the bios.

I have done sensors detect, and the system only detected temperature sensors for my Core2duo processors. I don't get the option of fan control. When I run 

Sudo Pwmconfig

I get this message:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

I'm running the 2.6,14 kernel. Any ideas on how to get ubuntu to force the fan into higher gear based on temp? 

Thanks!

If it is new hardware then the current 7.10 kernel may not support it, you may be better off to wait until 8.04 is released in April and upgrade as it uses a later kernel with a lot more hardware support.

---

### Post by rstets on 2008-03-23
having the same issue with samsung r20

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

acpi -V shows something unbelieveble...

```
romko@klaptop:~$ acpi -V
     Battery 1: charging, 41%, 01:05:11 until charged
     Thermal 1: ok, 89.0 degrees C
     Thermal 2: ok, 27.0 degrees C
  AC Adapter 1: on-line

```

plus I get some "MP-BIOS ... IO-APIC" bug on startup...

tried upgrading to 8.04 with no luck on that issue either (though it's still an alpha release)


I guess all I have is just to wait. I really got used to kubuntu on my desktop pc, so I won't give it up on my laptop :guitar:

---

### Post by luvit on 2008-03-30
I SOLVED SHORT BATTERY LIFE, WARM PROCESSOR, AND RUNAWAY PROCESSES WITH THE 3  UTILITIES I OUTLINED!

My Short Battery Life problems are solved and I have as much control of ensuring maximum power saving using ubuntu tweak, and monitoring system activities.:)
It's easy installs direct from the webpages!
I have outlined these 3 packages in the tweaking section of my **[COLOR="RoyalBlue"][Ubuntu Blog]("http://www.yay4u.com/search/label/Tweaking")[/COLOR]**. ;)

My screen brightness and hard drive power saving settings wer optimal by default in Ubuntu.

---

### Post by lswest on 2008-03-30
just my $0.02 but i use powernowd (now comes pre-installed in Hardy i believe) for CPU scaling, and then use this command ```
sudo powernowd -vv -m 2
``` which is doubly verbose PASSIVE mode, meaning it steps up slowly, and only when cpu usage is at 80% at the step it's at.  Very useful.

---

