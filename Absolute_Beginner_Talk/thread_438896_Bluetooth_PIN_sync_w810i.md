---
title: "Bluetooth PIN sync w810i"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-05-10
Hi there all, continuing issues with bluetooth PIN, have followed numerous guides but none seem to work thus far, if anyone can help with this situation that would be quality.

Sending files from my phone to my pc is no issue, the pc asks whether I will accept the file and then does so perfectly happily.

Syncing with my phone is a totally different beast. I have the multisync packages all installed, and set up, I can detect my phone via bluetooth but on clicking 'test connection' I run into issues.

On my phone it asks me whether I will accept the incoming connection etc, would I like to add the computer to my devices and then it asks for my PIN...

I put in 1234 and 0000 as they tend to be defaults, but to no avail, both just caused the connection to fail. I retried with 1234 having checked my hcid.conf which tells me:
```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        passkey "1234";


```
Which I presumed would work... but no luck again. Any ideas guys, cheers for your help,
Il

---

### Post by Inxsible on 2007-05-10
Hi..

I know this doesn't help you, but I have the exact same phone and I was wondering what bluetooth apps you were using?

I need to set up my bluetooth too !

---

### Post by jvc26 on 2007-05-10
How bizarre - it totally fixed itself after a reboot.

I am using the following bluetooth apps:
bluez-utils gnome-bluetooth multisync libmultisync-plugin-all (I presume that package also refers to the rest of the libmultisync packages - if not you can pick them up from synaptic)

Works fine for me now, just needed to reboot it and all worked fine

Il

---

### Post by Inxsible on 2007-05-10
Hey Illuvator,

I got all the packages installed. Should I just edit the hcid.conf file and add the password there, and I'll be good to go ?

Thanks again !

---

### Post by jvc26 on 2007-05-10
Sorry for taking a while to get back to you, what I did was I installed all those files, went into the hcid.conf to check that the passkey was 1234 (which it defaults to) then:

Set up the pairing in Multisync - turn on your device, set the multisync device 1 to be Ximian Evolution, then the second to be Irmc device, then search for bluetooth devices, once your w810i has been picked up, try to connect to it, if it refuses and basically denies all knowledge that the passkey is 1234, reboot the computer at this point, and then try again, after a reboot it worked fine for me, so it may well have been just that I was missing the setup or something - ah well, its working now. That will then sync your calendar with your phone, faff round with the settings to make sure it does what you want it to do and not to start deleting your entries or something (I'm always slightly nervous about something like that happening, but it doesnt it just seems to alert you to the errors (or at least its never happened in my extremely limited use of the setup)

And there you go that should work. To send files to your pc, you just send them via bluetooth with Bluetooth file sharing running from the accessories menu, and send them from the phone as you would to any bluetooth device. To put files to your phone, just right click, send to, obex push and select your phone

Hope that helps, apologies, I have very limited experience with this setup.
Il

---

### Post by Inxsible on 2007-05-11
When I try to connect my phone with my machine, it gives me the

"Entered passcode did not match passcode entered on the other device. Retry? "

on the phone. I checked the passcode in the /etc/bluetooth/hcid.conf file and it was set to 1234. I tried that and still no love :( 


I had connected my phone via bluetooth with my Vista and set a new password. I tried even that and still nothing.

Can someone help me out ?

---

### Post by stevenmansour on 2007-05-16
No love here either.

I can send / receive files using the bluetooth tool, but I can't set my laptop and phone (Nokia 7610) as a pair. My passkey is 1234, both in hcid.conf as well as bluez-pin in / out. 
```

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluez-pin;
	#pin_helper /usr/bin/bluepin;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
```

When I try to associate from the phone (create new pairing), it prompts me for the passkey (which I assume is still 1234), I enter it, but then it times out. I get no prompt on the laptop.

Same thing in Multisync, obviously: Add new device, detect -> it finds it. But test connection fails. :confused:

---

### Post by crucial123 on 2007-05-16
> **stevenmansour said:**
> No love here either.

I can send / receive files using the bluetooth tool, but I can't set my laptop and phone (Nokia 7610) as a pair. My passkey is 1234, both in hcid.conf as well as bluez-pin in / out. 
```

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluez-pin;
	#pin_helper /usr/bin/bluepin;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
```

When I try to associate from the phone (create new pairing), it prompts me for the passkey (which I assume is still 1234), I enter it, but then it times out. I get no prompt on the laptop.

Same thing in Multisync, obviously: Add new device, detect -> it finds it. But test connection fails. :confused:

With sony ericsson 810i
I am at this same spot exactly..
weird thing is that it worked yesterday for a while
yes my phone is charged and also my blutooth manager is set to "visable and connectable to other devices" 

if anyone is getting results let me know.

---

### Post by darkworld on 2007-05-21
Hi

I had no problems on a previous installation of Feisty. Re-installed and loaded bluetooth as before and now im getting what you guys were getting. HCId pass is default 1234 but its just no having it.

Can send files out to my Nokia N70 no probs just cant connect the other way because it doesnt like the default 1234???

Totally clueless! Help please.

---

### Post by darkworld on 2007-05-21
ok I have sorted this but I dont really understand the logic. If you seek to pair with PC from phone then you got no chance. If you right click a file in desktop then go send > via bluetooth your away. No pairing required. Same applies in opposite direction.

Only asks for password on pair request then declines no matter what. Thats the way it is for me.

---

### Post by rstana on 2007-05-22
try changing pairing mode to pairing auto;

restart bluetooth services by using
```

sudo /etc/init.d/bluetooth restart

```

and the try again to pair, initiate pairing from phone
that worked with my Sony Ericsson Z710i

---

