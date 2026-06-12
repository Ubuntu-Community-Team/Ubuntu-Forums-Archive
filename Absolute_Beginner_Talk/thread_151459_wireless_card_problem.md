---
title: "wireless card problem?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by boosted69 on 2006-03-27
I am tearing my hair out becuase i have read every post on broadcom wireless cards and i can't get Wlan to show up in network connections. I have tried everything and i do mean everything!  I am using a WPC54G ver.3  and the light turns on when i plug it in. The drivers appear to be installed correctly observed here:

chris@chris:~$ ndiswrapper -l
Installed ndis drivers:
lsbcmnds        driver present, hardware present
chris@chris:~$

but then this happens:



chris@chris:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
chris@chris:~$

i have edited all my conffiles to say radiostate 0 too and i still get the same message. i also get this error when i run dmesg:   (this is at the end of all the output) 

[4294836.150000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294836.207000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[4295370.284000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4295370.413000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'


PLease please help me out!

---

### Post by trent dillman on 2006-03-28
This is a bit much, but maybe you should try compiling from source?

First, get rid of the old ndiswrapper....

```

sudo apt-get remove ndiswrapper-utils
sudo mv /etc/ndiswrapper /etc/ndiswrapper.old

```

Then, get the source and install (assuming you have another net connection):

```

cd /opt/
sudo wget http://nchc.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.11.tar.gz
sudo tar zxvf ndiswrapper-1.11.tar.gz

```

If you have to d/l from another computer, d/l the source from ndiswrapper.sf.net, then copy it to your home directory:

```

cd /opt/
sudo tar zxvf ~/ndiswrapper-1.11.tar.gz

```

Now to compile:

```

cd ndiswrapper-1.11
sudo make install

```

Start the driver:

```

sudo modprobe ndiswrapper

```

Should be ok!

---

### Post by boosted69 on 2006-03-28
i couldnt get that command to work?

chris@chris:/opt/ndiswrapper-1.11$ sudo make install
sudo: make: command not found
chris@chris:/opt/ndiswrapper-1.11$

---

### Post by Titus A Duxass on 2006-03-28
editted to remove nonsense.

---

### Post by boosted69 on 2006-03-28
what nonsense?

---

### Post by boosted69 on 2006-03-28
i reinstalled ubuntu then went to synaptic to download ndiswrapper and it had an extra option under ndiswrapper. i installed them all, went throught the steps again and it worked?? strange. anyways, its showing up in network manager so i think i can take it from there. thanks for the response anyways trent!

---

