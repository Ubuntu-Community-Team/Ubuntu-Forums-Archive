---
title: "Warty: WPA/TTLS on iBook w/ Airport (not extreme)"
date: 2005-02-25
forum: Apple PPC Users
---

### Post by F_Athens on 2005-02-25
After using Ubuntu for some weeks, I must say I am impressed on how zippy it make s this ibook seem.  Most things run well (considering there is only 256MB of ram) and now I would like to connect to a WPA/TTLS wireless network.  I have tried wpa_supplicant and tried the  [wpa tutorial](http://www.ubuntulinux.org/wiki/WPAHowto) , but it seems that the airport is not supported (Error:   ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported).  
"xsupplicant" may be another option but beyond my ability to configure.  I am using Ubuntu Warty.  I would prefer a nice little gui to prompt for my TTLS username and pasword but I would be happy to have to put it in a configuration script as well as long as I could connect.  I don't need certificates enabled (I think) and I don't have to use any special keys to log in.

again, this is not a simple "get airport working thread" as the hardware is configured and can pick up other wireless networks, but more specifically getting TTLS authentication working on an ibook/airport combination.

Thank you for your help,

Francisco

---

### Post by mroth on 2005-03-06
I've also been unsuccessful in getting WPA-PSK to function in Linux on an Airport card. wpa_supplicant does appear to support the airport card, and on a PPC, ndiswrapper is not an option.

If anyone has any leads towards getting this one to work, it would be greatly appreciated, especially since more and more networks are switching to WPA instead of WEP.

---

### Post by F_Athens on 2005-03-06
[QUOTE=mroth]I've also been unsuccessful in getting WPA-PSK to function in Linux on an Airport card. wpa_supplicant does appear to support the airport card, and on a PPC, ndiswrapper is not an option.

If anyone has any leads towards getting this one to work, it would be greatly appreciated, especially since more and more networks are switching to WPA instead of WEP.[/QUOTE]

wow for I while I was beginning to think I was the only one!  

it seems that wpa_supplicant (from debian repositories) WOULD work but  the driver_hermes.c was not included in the compiled binary :P  of course you could compile your own wpa_supplicant IF you could find a copy of driver_hermes.c :P

we're not the only ones frustrated about this issue:

[http://lists.shmoo.com/pipermail/hostap/2005-March/009628.html](http://lists.shmoo.com/pipermail/hostap/2005-March/009628.html)
and
[http://www.netstumbler.org/archive/index.php/t-13950.html](http://www.netstumbler.org/archive/index.php/t-13950.html)

--------------------------------------------------------

UPDATE March 6, 2005:

The driver v7.22 located below has wpa_supplicant WITH the driver in hostap/wpa_supplicant included - tho there seems to be limited functionality (not usefull without xsupplicant for many forms of authentication) of this wpa_supplicant - when compiled and run it does not recognize many of the paramaters of the wpa_supplicant.conf :P

[http://www.agere.com/mobility/wireless_lan_drivers.html](http://www.agere.com/mobility/wireless_lan_drivers.html)

simply copying the  driver_hermes.c to the source folder of wpa_supplicant from the repositories also does not work after creating the .config file(even if you get the lib_ssl-dev as well as the opensll package)  the make also wants hcfcfg.h, hcf.h, hcfdef.h, and wireless/wl_if.h headers. Some of these are found in the hcf folder of the drivers but nothing in the wireless/ folder matches wl_if.h   so my search continues... 

YET ANOTHER gotcha:
[http://www.linuxforums.org/forum/viewtopic.php?t=20672](http://www.linuxforums.org/forum/viewtopic.php?t=20672)
seems like the above driver package is meant for 2.4 kernel and only supports Hermes II!!! 

<sarcasm>
will the fun ever end?
</sarcasm> 

I know -nearly- nothing of how to process this for my ubuntu install, being the linux noob that I am... but I'll keep trying...

now I hope my current driver supports WPA because otherwise I will have to make a new one.

heres some instructions for those slightly more savvy with doing so:
(see the bottom of)
[http://www.ee.surrey.ac.uk/Personal/G.Wilford/WiFi.html](http://www.ee.surrey.ac.uk/Personal/G.Wilford/WiFi.html)

looks like we are getting closer....

F

-------------------------------------------------------


somebody PLEASE find a way for us humble ibook folk to connect via WPA
at this point I'll be happy to use a usb solution if someone can document the functional hardware and software solution used.

---

### Post by F_Athens on 2005-03-07
UPDATE March 07,  2005:
ah ha! heres a how-to for updating the orinoco driver this should not only give us the ability to reset the WEP (required for some EAP operations) but also monitor mode as a bonus ;-) It would be NICE if the updated driver were INCLUDED with UBUNTU or at least available as an update in the repository.... notice if you type iwpriv <device> (where <device> is your wi-fi card, generally eth1 on an iBook with airport.) you dont see the reset options (thats where some of the problem lies, I'm sure)
I know it's for mandrake and a different laptop but compilation instructions will apply to us only changing where we get the kernel and pcmcia-cs pakages from.  Hopefully we wont have to deal with the wacky driver_hermes.c  from Agere mentioned on March 6th. 

[list]
[*][http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=398](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=398)


note: there also firmware issues that may complicate the issue. How can we upgrade/downgrade or even find out the current FW without using OSX?!


[*]The 2.6 patched driver from the article linked above, I will link here:
[http://www.nervous.it/download/wifi/orinoco-0.13e-SN-5.tar.bz2](http://www.nervous.it/download/wifi/orinoco-0.13e-SN-5.tar.bz2)


[*]Here's another orinoco driver link that seems to be updated further:
[http://www.tzi.de/~plasmahh/orinoco.html](http://www.tzi.de/~plasmahh/orinoco.html)


[*]now heres an article more specificaly about using an updated orinoco driver with xsupplicant:
[http://www.oreillynet.com/pub/wlg/4602](http://www.oreillynet.com/pub/wlg/4602)
note: the patches mentioned here seem to be arch specific to i386 :P
[/list] 


I'll give all this a try over the next few days.  I'm still considering which supplicant is better suited for EAP-TTLS... it looks like xsupplicant over wpa_supplicant... anyone care to make Gnome-Supplicant?!


F

---

### Post by F_Athens on 2005-03-16
UPDATE:
After installing OS X 10.3, updating to 10.3.8 , and updating the airport tools, the firmware for the airport was updated from 8.70 to 9.52.  I did this to confirm that the airport could indeed support 802.1x, which it does with OS X's builtin supplicant.   I also noticed that reinstalling OS X without updating reverts the airports firmware!  Creepy stuff!

After lurking in #ubuntu on irc.freenode.net, I ran into Seveas who was kind enough to post his working configs for EAP/TTLS with PAP, i'll give these a try soon. 
Note: this is for a system using a different HW setup, but should nonetheless help us. 
Note: the config disables certificates, which is a bit scary, but unless a way to download them from the server from within Ubuntu can be found, what else can we do? I was able to get certificates in OS X, but exporting was disabled :P

network:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto ath0
iface ath0 inet manual
pre-up ifconfig ath0 up
up /root/ssidselect
post-down ifconfig ath0 down
 
``` 

xsupplicant.conf
```

# This is an example configuration file for xsupplicant versions after 0.8b.

##########################################################################
#                              GLOBAL SECTION                            #
##########################################################################

# List of configured networks to keep in memory, expressed as a comma 
# seperated list or the keyword 'all'. For efficiency, keep only the 
# networks you use in this list and make sure that it includes your 
# default network.

#network_list = default, test1, test2
network_list = default, uva, Mobilander-Secure, VU-Campusnet

# Default network name to use when there is not an explicit match

#default_netname = my_defaults
default_netname = default

# When using the startup_command, first_auth_command, and reauth_command 
# directives, "%i" will be expanded to the interface name. This allows a 
# single network profile to work across different interfaces.

# The command to run when xsupplicant is first started.

#startup_command = <BEGIN_COMMAND>echo "xsupplicant startup"<END_COMMAND>

# The command to run when xsupplicant authenticates to a network for the
# first time.  This will usually be used to start a DHCP client process.

first_auth_command = <BEGIN_COMMAND>dhclient %i<END_COMMAND>

# The command to run when xsupplicant reauthenticates to a network.

#reauth_command = <BEGIN_COMMAND>echo "reauthenticated %i"<END_COMMAND>

# Where the supplicant should log to, (xsupplicant will create a new log 
# file on each invocation).
logfile = /var/log/xsupplicant.log

# The auth_period, held_period, and max_starts directives modify the 
# timers in the state machine. (Please reference the 802.1x spec for info
# on how they are used.) For most people, there is no reason to define 
# these values, as the defaults should work.

#auth_period = 30
#held_period = 30
#max_starts = 3

# Defining an interface in "allow_interfaces" will bypass the rules that
# xsupplicant uses to determine if an interface is valid.  For most people
# this setting shouldn't be needed.  It is useful for having xsupplicant
# attempt to authenticate on interfaces that don't appear to be true
# physical interfaces, (i.e. virtual interfaces such as eth0:1).

allow_interfaces = ath0

# Defining an interface in "deny_interfaces" will prevent xsupplicant from
# attempting to authenticate on a given interface.  This is useful if you
# know that you will never do 802.1x on a specific interface.  However,
# allows will take priority over denies, so defining the same interface in
# the allow_interfaces, and deny_interfaces will result in the interface
# being used.

deny_interfaces = eth0, sit0, lo

##########################################################################
#                             NETWORK SECTION                            #
##########################################################################

# the general format of the network section is a network name followed
# by a group of variables 

# network names may contain the following characters: a-z, A-Z, 0-9, '-', 
# '_', '\', and '/'. Those interested in having an SSID with ANY character
# in it can use the ssid tag within the network clause. Otherwise, your 
# ssid will be the name of the network.

## The default network is not a network itself. These values are the 
## default used for any network parameters not overridden in another 
## section. If it's not in your network configuration and not in your 
## default, it won't work!!

default  
{ 
  # The type of this network. wired or wireless, if this value is not set,
  # xsupplicant will attempt to determine if the interface is wired or
  # wireless.  In general, you should only need to define this when 
  # xsupplicant incorrectly identifies your network interface.
  #type = wireless

  # If this profile is forced to wired, this will not do anything. 
  # However, if the interface is forced, or detected to be wireless 
  # xsupplicant will take control of re/setting WEP keys when the machine 
  # first starts, and when it jumps to a different AP.  In general, you 
  # won't need to define, or set this value.
  #wireless_control = yes

  # Describes which EAP types this network will allow. The first type 
  # listed will be requested if the server tries to use something not in 
  # this list.
  #allow_types = eap_tls, eap_md5, eap_gtc, eap-otp
  allow_types = all

  # What to respond with when presented with an EAP Id Request. Typically,
  # this is the username for this network. Since this can be an arbitrary 
  # string, enclose within <BEGIN_ID> and <END_ID>
  identity = <BEGIN_ID>debian-user<END_ID>

  # Force xsupplicant to send it's packets to this destination MAC address.
  # In most cases, this isn't needed, and shouldn't be defined.
  #dest_mac = 00:aA:bB:cC:dD:eE

  ## Method-specific parameters are kept in the method 
  eap_tls {
      user_cert      = /etc/xsupplicant/tls/client.crt
      user_key       = /etc/xsupplicant/tls/client.key
      user_key_pass  = <BEGIN_PASS>password for key<END_PASS>
      root_cert      = /etc/xsupplicant/tls/ca.crt
      #root_dir      = /etc/xsupplicant/ca/
      crl_dir        = /etc/xsupplicant/tls
      chunk_size     = 1398
      random_file    = /etc/xsupplicant/tls/random

      # To enable TLS session resumption, you need to set the following
      # value to "yes".  By default, session resumption is disabled.
      #session_resume = yes
  }

  eap-md5 {
      username = <BEGIN_UNAME>testuser<END_UNAME>
      password = <BEGIN_PASS>testuserpass!<END_PASS>
  }

  eap-ttls {
      user_cert      = /etc/xsupplicant/tls/client.crt
      user_key       = /etc/xsupplicant/tls/client.key
      user_key_pass  = <BEGIN_PASS>password for key<END_PASS>
      root_cert      = /etc/xsupplicant/tls/ca.crt
      #root_dir      = /etc/xsupplicant/ca/
      crl_dir        = /etc/xsupplicant/tls
      chunk_size     = 1398
      random_file    = /etc/xsupplicant/tls/random
      
      # Verify the server certificate has this value in it's CN field.
      cncheck        = myradius.radius.com
      
      #session_resume = yes
      
      # Should it be an exact match?
      cnexact        = yes
      
      # phase2_type defines which phase2 to *actually* do. You MUST define
      # one of these.
      phase2_type = chap
      
      ## These are definitions for the different methods you might do at 
      ## phase2. only the one specified above will be used but it is valid
      ## to leave more than one here for convenience and easy switching.
      pap {
        username = <BEGIN_UNAME>papuser<END_UNAME>
        password = <BEGIN_PASS>pappasswd<END_PASS>
      }
      chap {
        username = <BEGIN_UNAME>chapuser<END_UNAME>
        password = <BEGIN_PASS>chappasswd<END_PASS>
      }
      mschap {
        username = <BEGIN_UNAME>mschapuser<END_UNAME>
        password = <BEGIN_PASS>mschappasswd<END_PASS>
      }
      mschapv2 {
        username = <BEGIN_UNAME>mschapv2user<END_UNAME>
        password = <BEGIN_PASS>mschapv2passwd<END_PASS>
      }
  }
 
  eap-leap {
      username = <BEGIN_UNAME>leapuser<END_UNAME>
      password = <BEGIN_PASS>leapuserpass!<END_PASS>
  }
  
  eap-mschapv2 {
      username = <BEGIN_UNAME>eapmschapv2user<END_UNAME>
      password = <BEGIN_PASS>eapmschapv2userpass!<END_PASS>
  }

  eap-peap {
      user_cert      = /etc/xsupplicant/tls/client.crt
      user_key       = /etc/xsupplicant/tls/client.key
      user_key_pass  = <BEGIN_PASS>password for key<END_PASS>
      root_cert      = /etc/xsupplicant/tls/ca.crt
      #root_dir      = /etc/xsupplicant/ca/
      crl_dir        = /etc/xsupplicant/tls
      chunk_size     = 1398
      random_file    = /etc/xsupplicant/tls/random
      
      # Verify the server certificate has this value in it's CN field.
      cncheck        = myradius.radius.com
      
      # Should it be an exact match?
      cnexact        = yes

      session_resume = yes

      # Currently 'all' is just mschapv2 If no allow_types is defined, all
      # is assumed. 
      #allow_types = eap_mschapv2
      allow_types = all # where all = MSCHAPv2, MD5, OTP, GTC, SIM

      # Right now you can do any of these methods in PEAP.
      eap-mschapv2 {
        username = <BEGIN_UNAME>phase2mschapv2<END_UNAME>
        password = <BEGIN_PASS>phase2mschapv2pass<END_PASS>
      }
  }

  eap-sim {

      # In order to obtain the IMSI from the SIM card, the password *MUST*
      # be defined here!  Otherwise, you need to specify your IMSI as the 
      # username below.
      username = <BEGIN_UNAME>simuser<END_UNAME>
      password = <BEGIN_PASS>simuserpass!<END_PASS>     
      auto_realm = yes
  }
}

# In this network definition, "test1" is the friendly name.  It can match
# the essid of the network, which means you won't have to set the "ssid"
# variable.  However, if it doesn't match, you need to set the "ssid"
# variable in order for the network to be detected correctly.
#test1
#{
#  type = wired
#  # You should not define this unless you have characters other than those
#  # specified above in the ssid of your network
#  ssid = <BEGIN_SSID>mvemjsnp<END_SSID>
#
#  allow_types = all
#  identity = <BEGIN_ID>Check this out- any char!#$<END_ID>
#
#}


#test2
#{
#  # You should not define this unless you have characters other than those 
#  # specified above in the ssid of your network
#  ssid = <BEGIN_SSID>up to 32 character ASCII string<END_SSID>
#  identity = <BEGIN_ID>testuser@testnet.com<END_ID>
#
#  allow_types = eap-tls
#  type = wireless
#}

#test3
#{
#  # You should not define this unless you have characters other than those 
#  # specified above in the ssid of your network
#  ssid = <BEGIN_SSID>foo-network!<END_SSID>
#
#  type = wired
#
#  identity= <BEGIN_ID>this will work too<END_ID>
#}

uva
{
	type = wireless
	wireless_control = yes
	allow_types = eap-ttls
	identity = <BEGIN_ID>0105848@uva.nl<END_ID>

	eap-ttls
	{
		root_cert = NONE
		phase2_type = pap
		pap
		{
			username = <BEGIN_UNAME>0105848@uva.nl<END_UNAME>
			password = <BEGIN_PASS><END_PASS>
		}
	}
}
Mobilander-Secure
{
	type = wireless
	wireless_control = yes
	allow_types = eap-ttls
	identity = <BEGIN_ID>0105848@uva.nl<END_ID>

	eap-ttls
	{
		root_cert = NONE
		phase2_type = pap
		pap
		{
			username = <BEGIN_UNAME>0105848@uva.nl<END_UNAME>
			password = <BEGIN_PASS><END_PASS>
		}
	}
}
VU-Campusnet
{
	type = wireless
	wireless_control = yes
	allow_types = eap-ttls
	identity = <BEGIN_ID>dkr210@vu.nl<END_ID>

	eap-ttls
	{
		root_cert = NONE
		phase2_type = pap
		pap
		{
			username = <BEGIN_UNAME>dkr210@vu.nl<END_UNAME>
			password = <BEGIN_PASS><END_PASS>
		}
	}
}

```


```

#!/bin/sh

IF=ath0

AUTH=NONE
for NET in `iwlist $IF scan 2>/dev/null | grep ESSID | cut -d '"' -f 2`
do
	if [[ $NET == "Kaarsemaker" ]];       then AUTH=WPA; iwconfig $IF essid $NET; fi
	if [[ $NET == "uva" ]];               then AUTH=X;   iwconfig $IF essid $NET; fi
	if [[ $NET == "Mobilander-Secure" ]]; then AUTH=X;   iwconfig $IF essid $NET; fi
	if [[ $NET == "VU-Campusnet" ]];      then AUTH=X;   iwconfig $IF essid $NET; fi
	if [[ $NET == "dekoning" ]];          then AUTH=WEP; iwconfig $IF essid $NET;
	                                                     iwconfig $IF key XXXXXXXXXX;
							     iwconfig $IF enc open; 
							     dhclient $IF; fi;
done

if [[ $AUTH == WPA ]]
then
	killall wpa_supplicant
	wpa_supplicant -wB -iath0 -c/etc/wpa_supplicant.conf
	sleep 5
	dhclient ath0
fi

exit 0

```

---

### Post by sniperd on 2005-03-22
Did you get this to work by any chance?

Im trying it on my ibook G3 and i will let you know if i get it working...
I dont care about stats or anything like that though.

---

### Post by todayalemon on 2007-06-12
any progress? any success? we have feisty now, at least...

---

### Post by catawalks on 2007-11-07
this is probably a lost cause by now....but did anyone get this to work? or WPA on an airport (not extreme) some other way? my house, my work, practically everwhere i use my laptop uses wpa...


I'm on feisty fawn and there doesn't seem to have any improvements with it. Maybe i should update to gutsy but idk if it will run well with 256mb and a 900mhz g3. anyways...if anyone has any news let me know.

---

### Post by stmiller on 2007-11-08
Hey catawalks:

Someone in this thread re-wrote the hemes driver which the airport original uses to work with WPA I on recent kernels. I have not tested this (so don't ask me :) ), but check out this thread:

[http://ubuntuforums.org/showthread.php?t=304217&page=6](http://ubuntuforums.org/showthread.php?t=304217&page=6)

---

