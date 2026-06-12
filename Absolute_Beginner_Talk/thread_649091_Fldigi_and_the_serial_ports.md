---
title: "Fldigi and the serial ports"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by KE6WX on 2007-12-24
I am using Umbutu 7.10
I have installed Fldigi and it works as far as receive is concerned
I cannot make the PTT go out to the interface (BTW this interface works, controlls,  on a windows xp machine with digipan and the Kenwood TS450S). I have an RS232 minitester in the serial cable from the linux machine and the control line states do not change in Linux. (They doi change in Windows xp)

I receive data on the screen but it will not transmit.

How do I examine the Serial (com) ports in Linux?

Where do I go from here.

Bill McFall, ke6wx in Las Vegas

---

### Post by pa3dsc on 2008-02-01
Hello Bill,

I use fldigi on Ubuntu 7.10
Installing a new system and have some troubles so looking for information I read your posting.
I use minicom to check the ttyS0 port.
apt-get install minicom
Then you have to set the /de/ttyS0 global
chmod 777 /dev/ttyS0  
In the setup up the minicom you can configure the /dev/ttyS0 in the minicom configuration.
Also set the port to 4800 N 2
So I check the connection to the set (Kenwood TS-50)
for instance the command  IF; results in the answer from the TS50
You can use the breakoutbox to check the blinking LEDS to see if ther is some 
bit transport.

73 martin pa3dsc

---

### Post by pa3dsc on 2008-02-01
And than when the communicatie is OK 
install hamlib from the site 
tar -zxvf hamlib.....gz 
./configure; make ; make check and than as root make install
or with the synaptic packet manager

rigctl -L 
list all the tranceivers commands etc.
look for your treanceiver to find out the model 
give the command    ( My TS850 is type 209)
rigctl -m209 -r/dev/ttyS0 -s4800 -C stop_bits=2
you can now communicate withe the tranceiver
f asking the frequency 
F 357500 set the frequency at 3.575 MHz
? gives all the commands
Next step is fldigi and configure hamlib.

73 martin pa3dsc

---

