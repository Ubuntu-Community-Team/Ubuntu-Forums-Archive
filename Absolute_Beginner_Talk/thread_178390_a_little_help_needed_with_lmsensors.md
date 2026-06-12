---
title: "a little help needed with lmsensors"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by Jeroen1000 on 2006-05-17
Hey everyone,

I've just installed ubuntu and lmsensors (using synoptic package manager)
Unfortunately I'm stuck now (but I can feel I'm close:D ).

The "problem' is this turtorial:

[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

If you take a look at the line numbered as number 2 :

*2. Run the mkdev.sh script in the lm-sensors source. It is extacted below:*

Where is this lm-sensors source? I can't seem to find out where ubuntu installs software.

Could someone point me to the right directory?

Many thanks!!

Jeroen

---

### Post by christhemonkey on 2006-05-17
duno wer it installs to, but try typing into a terminal
```
sudo updatedb
locate lm-sensors 
```
Will give you a list of locations.

Theres probably a better way using dpkg or apt, but thats what comes to mind.

---

### Post by Jeroen1000 on 2006-05-17
[QUOTE=christhemonkey]duno wer it installs to, but try typing into a terminal
```
sudo updatedb
locate lm-sensors 
```
Will give you a list of locations.

Theres probably a better way using dpkg or apt, but thats what comes to mind.[/QUOTE]

I'm getting a lot of locations but I THINK I know the right one (I've put it in bold):

list:


/etc/init.d/lm-sensors
/etc/rcS.d/S36lm-sensors
/var/lib/dpkg/info/lm-sensors.postinst
/var/lib/dpkg/info/lm-sensors.list
/var/lib/dpkg/info/lm-sensors.preinst
/var/lib/dpkg/info/lm-sensors.postrm
/var/lib/dpkg/info/lm-sensors.conffiles
/var/lib/dpkg/info/lm-sensors.md5sums
/var/cache/apt/archives/lm-sensors_1%3a2.9.2-5ubuntu3_i386.deb
/usr/share/doc/lm-sensors
/usr/share/doc/lm-sensors/copyright
/usr/share/doc/lm-sensors/doc
/usr/share/doc/lm-sensors/doc/fan-divisors
/usr/share/doc/lm-sensors/doc/Makefile
/usr/share/doc/lm-sensors/doc/mkpatch
/usr/share/doc/lm-sensors/doc/cvs
/usr/share/doc/lm-sensors/doc/busses
/usr/share/doc/lm-sensors/doc/busses/i2c-ali15x3.gz
/usr/share/doc/lm-sensors/doc/busses/i2c-ali1535
/usr/share/doc/lm-sensors/doc/busses/i2c-amd756
/usr/share/doc/lm-sensors/doc/busses/i2c-amd8111
/usr/share/doc/lm-sensors/doc/busses/i2c-hydra
/usr/share/doc/lm-sensors/doc/busses/i2c-i801
/usr/share/doc/lm-sensors/doc/busses/i2c-i810
/usr/share/doc/lm-sensors/doc/busses/i2c-ipmb
/usr/share/doc/lm-sensors/doc/busses/i2c-ipmi
/usr/share/doc/lm-sensors/doc/busses/i2c-nforce2
/usr/share/doc/lm-sensors/doc/busses/i2c-piix4
/usr/share/doc/lm-sensors/doc/busses/i2c-savage4
/usr/share/doc/lm-sensors/doc/busses/i2c-sis5595
/usr/share/doc/lm-sensors/doc/busses/i2c-sis630
/usr/share/doc/lm-sensors/doc/busses/i2c-sis645
/usr/share/doc/lm-sensors/doc/busses/i2c-tsunami
/usr/share/doc/lm-sensors/doc/busses/i2c-via
/usr/share/doc/lm-sensors/doc/busses/i2c-viapro
/usr/share/doc/lm-sensors/doc/busses/i2c-voodoo3
/usr/share/doc/lm-sensors/doc/busses/i2c-virtual.gz
/usr/share/doc/lm-sensors/doc/donations
/usr/share/doc/lm-sensors/doc/lm_sensors-FAQ.html
/usr/share/doc/lm-sensors/doc/fancontrol.txt
/usr/share/doc/lm-sensors/doc/temperature-sensors
/usr/share/doc/lm-sensors/doc/progs.gz
/usr/share/doc/lm-sensors/doc/modules
/usr/share/doc/lm-sensors/doc/chips
/usr/share/doc/lm-sensors/doc/chips/bmcsensors.gz
/usr/share/doc/lm-sensors/doc/chips/adm1021.gz
/usr/share/doc/lm-sensors/doc/chips/adm1025.gz
/usr/share/doc/lm-sensors/doc/chips/adm1024
/usr/share/doc/lm-sensors/doc/chips/adm1031.gz
/usr/share/doc/lm-sensors/doc/chips/adm9240.gz
/usr/share/doc/lm-sensors/doc/chips/bt869.gz
/usr/share/doc/lm-sensors/doc/chips/asb100
/usr/share/doc/lm-sensors/doc/chips/ddcmon.gz
/usr/share/doc/lm-sensors/doc/chips/it87.gz
/usr/share/doc/lm-sensors/doc/chips/ds1307
/usr/share/doc/lm-sensors/doc/chips/fscher.gz
/usr/share/doc/lm-sensors/doc/chips/fscpos.gz
/usr/share/doc/lm-sensors/doc/chips/fscscy.gz
/usr/share/doc/lm-sensors/doc/chips/gl518sm.gz
/usr/share/doc/lm-sensors/doc/chips/lm63.gz
/usr/share/doc/lm-sensors/doc/chips/lm78.gz
/usr/share/doc/lm-sensors/doc/chips/icspll
/usr/share/doc/lm-sensors/doc/chips/lm80.gz
/usr/share/doc/lm-sensors/doc/chips/lm75
/usr/share/doc/lm-sensors/doc/chips/lm83.gz
/usr/share/doc/lm-sensors/doc/chips/lm85.gz
/usr/share/doc/lm-sensors/doc/chips/lm87.gz
/usr/share/doc/lm-sensors/doc/chips/lm93.gz
/usr/share/doc/lm-sensors/doc/chips/lm92
/usr/share/doc/lm-sensors/doc/chips/ltc1710
/usr/share/doc/lm-sensors/doc/chips/matorb
/usr/share/doc/lm-sensors/doc/chips/max1619
/usr/share/doc/lm-sensors/doc/chips/pc87360.gz
/usr/share/doc/lm-sensors/doc/chips/mtp008
/usr/share/doc/lm-sensors/doc/chips/pca9540
/usr/share/doc/lm-sensors/doc/chips/pcf8574
/usr/share/doc/lm-sensors/doc/chips/saa1064
/usr/share/doc/lm-sensors/doc/chips/smartbatt
/usr/share/doc/lm-sensors/doc/chips/smbus-arp
/usr/share/doc/lm-sensors/doc/chips/smsc47m1
/usr/share/doc/lm-sensors/doc/chips/thmc50
/usr/share/doc/lm-sensors/doc/chips/vt1211
/usr/share/doc/lm-sensors/doc/chips/w83627hf
/usr/share/doc/lm-sensors/doc/chips/w83l785ts
/usr/share/doc/lm-sensors/doc/chips/mic74
/usr/share/doc/lm-sensors/doc/chips/MODPARMS.gz
/usr/share/doc/lm-sensors/doc/chips/SUMMARY.gz
/usr/share/doc/lm-sensors/doc/chips/adm1026.gz
/usr/share/doc/lm-sensors/doc/chips/ds1621.gz
/usr/share/doc/lm-sensors/doc/chips/eeprom.gz
/usr/share/doc/lm-sensors/doc/chips/gl520sm.gz
/usr/share/doc/lm-sensors/doc/chips/lm90.gz
/usr/share/doc/lm-sensors/doc/chips/max6650.gz
/usr/share/doc/lm-sensors/doc/chips/maxilife.gz
/usr/share/doc/lm-sensors/doc/chips/pcf8591.gz
/usr/share/doc/lm-sensors/doc/chips/sis5595.gz
/usr/share/doc/lm-sensors/doc/chips/via686a.gz
/usr/share/doc/lm-sensors/doc/chips/vt8231.gz
/usr/share/doc/lm-sensors/doc/chips/w83781d.gz
/usr/share/doc/lm-sensors/doc/chips/xeontemp.gz
/usr/share/doc/lm-sensors/doc/chips/w83792d.gz
/usr/share/doc/lm-sensors/doc/vid
/usr/share/doc/lm-sensors/doc/useful_addresses.html
/usr/share/doc/lm-sensors/doc/version-2
/usr/share/doc/lm-sensors/doc/version.texi
/usr/share/doc/lm-sensors/doc/developers
/usr/share/doc/lm-sensors/doc/developers/genpasswd.pl
/usr/share/doc/lm-sensors/doc/developers/design.gz
/usr/share/doc/lm-sensors/doc/developers/checklist
/usr/share/doc/lm-sensors/doc/developers/proc.gz
/usr/share/doc/lm-sensors/doc/developers/sysfs-interface
/usr/share/doc/lm-sensors/doc/developers/makefiles
/usr/share/doc/lm-sensors/doc/developers/sysctl
/usr/share/doc/lm-sensors/doc/developers/applications.gz
/usr/share/doc/lm-sensors/doc/developers/new_drivers.gz
/usr/share/doc/lm-sensors/doc/kernel
/usr/share/doc/lm-sensors/doc/kernel/proc_dir_entry.gz
/usr/share/doc/lm-sensors/doc/kernel/file_operations
/usr/share/doc/lm-sensors/doc/FAQ.gz
/usr/share/doc/lm-sensors/doc/lm_sensors-FAQ.texi.gz
/usr/share/doc/lm-sensors/changelog.gz
/usr/share/doc/lm-sensors/CONTRIBUTORS.gz
/usr/share/doc/lm-sensors/BACKGROUND
/usr/share/doc/lm-sensors/README.gz
/usr/share/doc/lm-sensors/TODO.gz
/usr/share/doc/lm-sensors/changelog.Debian.gz
/usr/share/doc/lm-sensors/examples
/usr/share/doc/lm-sensors/examples/maxilife
/usr/share/doc/lm-sensors/examples/maxilife/sysinfo.sh
/usr/share/doc/lm-sensors/examples/maxilife/writelcd.sh
/usr/share/doc/lm-sensors/examples/config
/usr/share/doc/lm-sensors/examples/config/grab_busses.sh
/usr/share/doc/lm-sensors/examples/daemon
/usr/share/doc/lm-sensors/examples/daemon/healthd.sh
/usr/share/doc/lm-sensors/examples/eeprom
/usr/share/doc/lm-sensors/examples/eeprom/decode-dimms.pl
/usr/share/doc/lm-sensors/examples/eeprom/decode-edid.pl
/usr/share/doc/lm-sensors/examples/eeprom/decode-vaio.pl
/usr/share/doc/lm-sensors/examples/eeprom/ddcmon.gz
/usr/share/doc/lm-sensors/examples/matorb
/usr/share/doc/lm-sensors/examples/matorb/displayit.pl
/usr/share/doc/lm-sensors/examples/hotplug
/usr/share/doc/lm-sensors/examples/hotplug/Makefile.p4b
/usr/share/doc/lm-sensors/examples/hotplug/Makefile
/usr/share/doc/lm-sensors/examples/hotplug/p4b_smbus.c.gz
/usr/share/doc/lm-sensors/examples/hotplug/README.p4b
/usr/share/doc/lm-sensors/examples/hotplug/README.gz
/usr/share/doc/lm-sensors/examples/hotplug/m7101.c.gz
/usr/share/doc/lm-sensors/examples/tellerstats
/usr/share/doc/lm-sensors/examples/tellerstats/gnuplotscript.tmpl
/usr/share/doc/lm-sensors/examples/tellerstats/gather.sh
/usr/share/doc/lm-sensors/examples/tellerstats/README
/usr/share/doc/lm-sensors/examples/tellerstats/tellerstats.conf
/usr/share/doc/lm-sensors/examples/tellerstats/index.shtml
/usr/share/doc/lm-sensors/examples/tellerstats/tellerstats.sh
/usr/share/doc/lm-sensors/examples/xeon
/usr/share/doc/lm-sensors/examples/xeon/decode-xeon.pl
/usr/share/doc/lm-sensors/README.thinkpad.gz
**/usr/share/lm-sensors**
/usr/share/lm-sensors/sensors.conf.eg

Can someone confirm?

---

### Post by christhemonkey on 2006-05-18
That is the directory most all of the stuff is installed to yes.

I think that howto is saying to run the script after getting the source.
Duno is not very well phrased!
But it cant hurt to try i suppose.
(it might for all i know, never done anything like this)

---

### Post by mcduck on 2006-05-18
The tutorial says it a bit strange way. It doesn't actually matter where you run the script. Just download it to your desktop and run there :)

---

