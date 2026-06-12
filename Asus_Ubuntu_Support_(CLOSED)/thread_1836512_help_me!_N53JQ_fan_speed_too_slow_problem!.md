---
title: "help me! N53JQ fan speed too slow problem!"
date: 2011-08-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jecelyin on 2011-08-31
As the fan speed is too slow, so when the weather is hot, heat a large notebook, but the fan speed below normal in Windows7, can effectively reduce the temperature.
I try [https://wiki.archlinux.org/index.php/Fan_Speed_Control]("https://wiki.archlinux.org/index.php/Fan_Speed_Control") above approach, but failed, and who can help me solve the problem of slow fan speed!

```

jecelyin@jecelyin-N53Jq:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +57.0°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +57.0°C  (high = +84.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +56.0°C  (high = +84.0°C, crit = +100.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +57.0°C  (high = +84.0°C, crit = +100.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +56.0°C  (high = +84.0°C, crit = +100.0°C)


```

```

jecelyin@jecelyin-N53Jq:~$ sudo pwmconfig
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

/usr/local/sbin/pwmconfig: There are no pwm-capable sensor modules installed


```

---

### Post by vprasu@gmail.com on 2011-09-21
I am also having the same problem with the same laptop. please anybody help...............

---

### Post by Novacaptain on 2011-10-14
same situation here (different model laptop tho).

proc/acpi has nothing on fans or thermal


I know for sure that the fans can spin a lot faster than this, because they always do a proper whirr during boot-up. Right now all my cores are around 83-95 degrees, (i'm 2 hours into a render) help?

ubuntu 11.04 64 bit dell studio laptop.

---

