---
title: "Can't find installed program to execute"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by kli618 on 2007-07-24
I've installed a program from an rpm file by converting it to a deb file using the following commands:
$sudo alien -k ITvpnclient-4.6_JDS-2.i586.rpm
$sudo dpkg -i itvpnclient_4.6_JDS-2_i386.deb

I am having trouble finding how to run the program I've installed.  I have doubled clicked on the .deb file and it shows that it is installed.  It shows the following list of included files:
./
opt/
opt/local/
opt/local/bin/
opt/ITvpnclient/
opt/ITvpnclient/include/
opt/ITvpnclient/include/vpnapi.h
opt/ITvpnclient/lib/
opt/ITvpnclient/lib/libvpnapi.so
opt/ITvpnclient/bin/
opt/ITvpnclient/bin/cisco_cert_mgr
opt/ITvpnclient/bin/vpnclient
opt/ITvpnclient/bin/ipseclog
opt/ITvpnclient/bin/cvpnd
opt/ITvpnclient/docs/
opt/ITvpnclient/docs/properties.png
opt/ITvpnclient/docs/login.png
opt/ITvpnclient/docs/SunStart.html
etc/
etc/ITvpnclient/
etc/init.d/
etc/init.d/vpnclient_init
etc/CiscoSystemsVPNClient/
etc/CiscoSystemsVPNClient/vpnclient.ini
etc/CiscoSystemsVPNClient/license.rtf
etc/CiscoSystemsVPNClient/license.txt
etc/CiscoSystemsVPNClient/Profiles/
etc/CiscoSystemsVPNClient/Profiles/sfbay.pcf
etc/CiscoSystemsVPNClient/Profiles/prc.pcf
etc/CiscoSystemsVPNClient/Profiles/norway.pcf
etc/CiscoSystemsVPNClient/Profiles/india.pcf
etc/CiscoSystemsVPNClient/Profiles/holland.pcf
etc/CiscoSystemsVPNClient/Profiles/singapore.pcf
etc/CiscoSystemsVPNClient/Profiles/japan.pcf
etc/CiscoSystemsVPNClient/Profiles/uk.pcf
etc/CiscoSystemsVPNClient/Profiles/central.pcf
etc/CiscoSystemsVPNClient/Profiles/aus.pcf
etc/CiscoSystemsVPNClient/Profiles/east.pcf
usr/
usr/src/
usr/src/vpnclient-4.6/
usr/src/vpnclient-4.6/GenDefs.h
usr/src/vpnclient-4.6/Makefile
usr/src/vpnclient-4.6/linuxcniapi.c
usr/src/vpnclient-4.6/frag.h
usr/src/vpnclient-4.6/IPSecDrvOS_linux.c
usr/src/vpnclient-4.6/IPSecDrvOS_linux.h
usr/src/vpnclient-4.6/config.h
usr/src/vpnclient-4.6/interceptor.c
usr/src/vpnclient-4.6/vpnmod_build
usr/src/vpnclient-4.6/mtu.h
usr/src/vpnclient-4.6/linuxcniapi.h
usr/src/vpnclient-4.6/unixcniapi.h
usr/src/vpnclient-4.6/Cniapi.h
usr/src/vpnclient-4.6/linux_os.h
usr/src/vpnclient-4.6/driver_build.sh
usr/src/vpnclient-4.6/vpn_ioctl_linux.h
usr/src/vpnclient-4.6/IPSecDrvOSFunctions.h
usr/src/vpnclient-4.6/frag.c
usr/src/vpnclient-4.6/libdriver.so
usr/share/
usr/share/doc/
usr/share/doc/itvpnclient/
usr/share/doc/itvpnclient/changelog.Debian.gz
usr/share/doc/itvpnclient/copyright
opt/local/bin/cisco_cert_mgr
opt/local/bin/vpnclient
opt/local/bin/ipseclog
opt/local/bin/cvpnd
opt/cisco-vpnclient
etc/ITvpnclient/docs

Can anyone show me how to add this program to the applications menu or run this from the command-line?  I am new to Linux.

Thanks.

---

### Post by asmoore82 on 2007-07-24
the program's **binaries** ( or executable for ppl used to Win-speak )
have been installed in '/opt/local/bin' which is not in your PATH
a quick fix for your user only would be to add these lines to the end of your .bashrc file ...
```
PATH="$PATH:/opt/local/bin"
export PATH
```
then close and re-open the terminal for the change to take effect
-OR- for even more fun, reload the .bashrc file manually ...
```
~ $ source ~/.bashrc
```

---

### Post by kli618 on 2007-07-25
It worked...Thanks!

---

