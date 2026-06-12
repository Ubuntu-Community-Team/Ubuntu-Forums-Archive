---
title: "Help with BASH- checking internet connection"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by phatdad on 2007-09-25
Finally I have Ubuntu up and running. It's been a while coming but I have a stable OS with no sudden X server problems or modem vanishing etc. I have a Sagem usb modem which is working fine with ueagle-atm.

I am trying to write a BASH script that will automate connection. So far, I have written a script, saved as an .sh file, which is called by a custom launcher on the panel. I want the script to launch the connection, then firestarter (I know- I'm an ex Windows man so I like to see it's there), then Firefox. 

Using
**export EDITOR=gedit && sudo visudo**
I have added
[B]dad ALL= NOPASSWD: /usr/sbin/firestarter
dad ALL= NOPASSWD: /usr/bin/pon[/B]
to the sudoers file to allow firestarter and pon to run without password

I have then written the script as
[B]#!/bin/bash
sudo pon ueagle-atm &
sleep 10
sudo firestarter &
firefox &
[/B] 
I have used sleep so firestarter doesn't say it can't start- ie firestarter starts after a 10 second delay, so the connection is established first. 
My question- 
Is there a way to make the bash script wait for the connection to be established before trying to start firestarter?

Thanks for looking, hope someone can help.

---

### Post by energiya on 2007-09-25
You can check for IP.
```

#!/bin/sh

# Define some colors first:
RED='\e[1;31m'
YELLOW='\e[1;33m'
CYAN='\e[1;36m'
NC='\e[0m'              # No Color

function FIP() {
	TEST=`/sbin/ifconfig ppp0 &> /dev/null`
	if [ $? -eq 0 ]; then
		MYIP="`/sbin/ifconfig ppp0 | awk '/inet/ { print $2 }' | sed -e s/addr://`"
	else
		TEST=`/sbin/ifconfig eth0 &> /dev/null`
		if [ $? -eq 0 ]; then
			MYIP="${CYAN}`/sbin/ifconfig eth0 | awk '/inet/ { print $2 }' | sed -e s/addr://`"
		else
			MYIP="${RED}ERROR"
		fi
	fi
	unset TEST
}

FIP
echo -e "My IP is: ${YELLOW}$MYIP${NC}"

```

I use this to check for my IP. I have an adsl conection so I only have ppp0 when I'm connected. If you don't know how to modify the script to suite you, post more specific info (ifconfig - with, without internet connection)

---

### Post by phatdad on 2007-09-25
Thanks for reply. 
With connection

edited out

Your script throws me completely- I am new to all this. Should I use that script after the pon command in my script- ie will it pause til connected and then go to the next line and load firestarter?

---

### Post by energiya on 2007-09-25
1. with and without are exactly the same ?!?!!?
2. when posting things like this replace your IP and MAC address

---

### Post by phatdad on 2007-09-25
I will try that again. Do I need to remove all the numbers that take the form *num.num.num.num* ? Not sure what my IP and MAC addresses look like I'm afraid. What's the danger?

---

### Post by energiya on 2007-09-25
> **phatdad said:**
> What's the danger?

IF your "lucky" you could get some hacking attempts. Better safe than sorry ;)

And the script:
```

#!/bin/sh
sudo pon ueagle-atm &

#--- Edit below ---
attempts=10
#--- Stop edit ---

nt=0
while true; do
	started=1
	ifconfig ppp0 &> /dev/null || { sleep 1; nt=$[ $nt + 1 ]; started=0; }
	[ $started = 1 ] && {
		sudo firestarter &
		break
	}
	[ $nt -eq $attempts ] && break
done

firefox &

```
I had so assume that when you don't have an internet connection you wont have ppp0 (thats how it is on my computer)
It will execute "sudo firestarter &" when the connection is active. It check this every 1 second. If you want to try more times than 10 edit the script .

---

### Post by phatdad on 2007-09-25
Thanks for the help, but I'm afraid firestarter starts up before the connection still. It could be because of the ppp0 setting. How can I tell if my set up will be checking for this?

---

### Post by energiya on 2007-09-25
Well, I had to assume what happens with ppp0. Try this:
> 
ifconfig
sudo ifconfig ppp0 down

unplug the modem
> 
sudo ifconfig ppp0 up

This should cut down your internet. Now compare the output of ifconfig with the one done before killing ppp0. I can't think of anything else.

---

### Post by phatdad on 2007-09-25
Thanks- I'll give it a try later. will post how it went.
Thanks for the time.

---

### Post by phatdad on 2007-09-26
Hello again

ifconfig for no connection returns 2 paragraphs relating to **eth0** and **lo**

ifconfig with connection returns 3 paragraphs relating to **eth0** and **lo** and **ppp0**

In both cases the **eth0** and the **lo** data is the same, except when connected the next to last line in the **lo** data now reads
RX bytes:1384 (1.3 KiB)  TX bytes:1384 (1.3 KiB)
(this compares to RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB) before connection)

The 3rd 'extra' paragraph when connected reads
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xx.xx.xx.xx P-t-P:xx.xx.xx.xx  Mask:xx.xx.xx.xx
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:61753 (60.3 KiB)  TX bytes:5051 (4.9 KiB)

Does this give you ant extra information?

thanks

---

