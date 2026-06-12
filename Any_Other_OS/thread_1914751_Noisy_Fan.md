---
title: "Noisy Fan"
date: 2012-01-25
forum: Any Other OS
---

### Post by NEQTAN on 2012-01-25
Problem: Noisy Fan, constantly running.
Possible Solution: Reduce fan speed, set temperatures so fan does not run constant.

                                                         > System:

laptop = HP Pavilion zv6000
cpu = AMD Athlon 64 processor 3500+
os = Linux Mint 12 (lisa)

Attempts:

Install lm-sensors
Run Command: sensors

Output:

acpitz-virtual-0
Adapter: Virtual device
temp1: +50.0°C (crit = +82.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp: +59.0°C

Install pwmconfig
Run Command: sudo pwmconfig

Output:

# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

Run Command: fancontrol

Output:

Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file
                     
     
 
All of my attempts have been with failure.

I have read multiple tutorials, manuals, and forum threads on the topic.  In hopes of finding some resolution, im asking this community for any  information they can lend. If anyone can help suggest how to control the  fan speed and fan on / off i would appreciate it.

Thank you in advance.

---

### Post by Perfect Storm on 2012-01-25
Moved to Other OS/Distro Talk.

---

### Post by mips on 2012-01-25
Oops, I'm asking a stupid question.

---

### Post by xyzzyman on 2012-01-25
That's a 5-6 year old notebook running a desktop processor. The fan is probably dirty and/or on its way out. The answer is to clean the fan and/or replace it before it completely dies. It looks like it might already be running on the warm side for that chip, but without knowing the CPU load at the time it's hard to say. You should idle in the 30's or low 40's at the worst with that processor. Also if I'm not mistaken, the fan in that isn't designed to ever be turned off even when working properly with it being a desktop CPU and all.

---

### Post by NEQTAN on 2012-01-25
xyzzyman,

Thanks for the response. I was thinking dust as well, or just plain old. Hehe. Ill clean it right way. 

I ran a diagnostic on the cpu, with the light duties i have been running has only reached 13%. 

While i have the machine open ill get a model number for the fan and get one ordered. 

So beyond that, your saying my endeavors to control the fan should be avoided?

Thank you again.

---

### Post by apoblepein on 2012-01-27
NEQTAN,

Here is a how-to reduce fan speed.

[http://www.muylinux.com/2011/06/16/controlar-el-uso-del-ventilador-en-ubuntu/]("http://www.muylinux.com/2011/06/16/controlar-el-uso-del-ventilador-en-ubuntu/")

Is spanish, but you´ll understand ;)

---

### Post by xyzzyman on 2012-01-27
@apoblepein I don't think that'll make a difference on his system due to lack of sensors on the mobo that report back to the OS. It wouldn't hurt to try though.

@NEQTAN How much experience do you have inside? If you're able to actually get at the fan, try to pull out as much gunk before blowing it out, and when you do make sure to try to blow it so it spins in the direction it normally does. You may find it cleans it enough that you are happy with it. Thing is if you suddenly don't hear it, then it's dead and should be turning off immediately. lol. So it's your call if you want to just replace it now. If you have the experience and some heat sink compound (or know someone who has some), replacing the heat sink compound on a system of that age can make a huge difference in CPU temps esp on a desktop chip like that. I have just a Core 2 Duo 2.53Ghz, and I replaced the OEM's CPU compound that was dry and flaky after 2 years with store-branded artic silver and dropped over 10degrees celcius on idle. I can't recommend anyone do it who hasn't before, unless you have some experience with electronics and can be smart about it but then even with any advice or walkthroughs your given it's still all in your hands if something went wrong.

Regarding adjusting the fan speed, I may be wrong but I don't think you're going to be able to control it via software on that model. I think it's all automated with no software connection outside of modifying the hard values in the BIOS. You definitely do not want to turn the fan off though. Unlike CPU's made for notebooks where some can turn the fan completely off when it's idle for a bit, that desktop CPU isn't designed for that plus it's working in a much more confined space.

---

