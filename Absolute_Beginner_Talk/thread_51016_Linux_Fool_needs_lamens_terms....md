---
title: "Linux Fool needs lamens terms..."
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2005-07-22
[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)
^^ I need to use the above solution to solve the problem i have with my lucent win modem and connecting it to the internet.... Can anyone please put it into lamens terms how the hell i get lt_modem and lt_serial from Synaptic?

Please Help ASAP

Thanks,
~Kris~

---

### Post by az on 2005-07-22
They are in a package called "linux-restricted-modules"  Fire up synaptic package manager and install it.

---

### Post by KrisDwyer on 2005-07-22
[QUOTE=azz]They are in a package called "linux-restricted-modules"  Fire up synaptic package manager and install it.[/QUOTE]
 Ok, this might sound stupid but how do you start up Synaptic?

---

### Post by FLeiXiuS on 2005-07-22
Sure, but the directions are there but not so clear.  So I will give it my best to translate :-)

**Step 1:**
Lets add the modules to your /etc/modules list so that the module loads every boot.
```
sudo gedit /etc/modules
```
Add the following to the end of the file.
```

lt_serial
lt_modem

```

Save then exit.

**Step 2:**
You need a symbolic link created each time at boot for this device to load properly.  Since udev always chnages..lets make some simple modifications.
```
sudo gedit /etc/udev/rules.d/10-local.rules
```
Add the following then save and exit.
```
#ltmodem KERNEL="ttLTM0", SYMLINK="modem"
```
*Note: the 0 is a zero not an O.*

Almost done :-P

**Step 3:**
Since there's a bit of a problem with the 2.6 kernels as the wiki states.  You need to add a kernel boot parameter.  To do this you must edit your /boot/grub/menu.lst and include the option.
```
sudo gedit /boot/grub/menu.lst
```
Scroll till you find the title= lines.  Find the one that you use to boot and then locate the kernel line.  At the end of the kernel line you would want to add the following
```
pci=routeirq
```

Example...
```

title=Ubuntu 
kernel           /vmlinux-2.6 ro quiet splash **pci=routeirq**

```
Or something simular.  

Step 4:
Updating grub..voila.
```
sudo update-grub
```

**Step 5:**
Reboot and hopefully it works flawlessly.


Your welcome :-)

---

### Post by KrisDwyer on 2005-07-22
[QUOTE=FLeiXiuS]Sure, but the directions are there but not so clear.  So I will give it my best to translate :-)

**Step 1:**
Lets add the modules to your /etc/modules list so that the module loads every boot.
```
sudo gedit /etc/modules
```
Add the following to the end of the file.
```

lt_serial
lt_modem

```

Save then exit.

**Step 2:**
You need a symbolic link created each time at boot for this device to load properly.  Since udev always chnages..lets make some simple modifications.
```
sudo gedit /etc/udev/rules.d/10-local.rules
```
Add the following then save and exit.
```
#ltmodem KERNEL="ttLTM0", SYMLINK="modem"
```
*Note: the 0 is a zero not an O.*

Almost done :-P

**Step 3:**
Since there's a bit of a problem with the 2.6 kernels as the wiki states.  You need to add a kernel boot parameter.  To do this you must edit your /boot/grub/menu.lst and include the option.
```
sudo gedit /boot/grub/menu.lst
```
Scroll till you find the title= lines.  Find the one that you use to boot and then locate the kernel line.  At the end of the kernel line you would want to add the following
```
pci=routeirq
```

Example...
```

title=Ubuntu 
kernel           /vmlinux-2.6 ro quiet splash **pci=routeirq**

```
Or something simular.  

Step 4:
Updating grub..voila.
```
sudo update-grub
```

**Step 5:**
Reboot and hopefully it works flawlessly.


Your welcome :-)[/QUOTE]
 Thanks...

---

### Post by Knome_fan on 2005-07-22
And just in case you're still wondering about synaptic.
System -> System Administration -> Synaptic Package Manager will open synaptic. 
Once it's open, search for restricted. This will give you a list of various packages all called linux-restricted-modules-***.

Now you have to select the one that fits your kernel. If you have a standard install, this should be linux-restricted-modules-2.6.10-5-386. Select this package, then click apply and you should be good to go.

After it is installed, follow the great howto by FLeiXiuS.

Good luck!  :grin:

---

### Post by KrisDwyer on 2005-07-22
[QUOTE=Knome_fan]And just in case you're still wondering about synaptic.
System -> System Administration -> Synaptic Package Manager will open synaptic. 
Once it's open, search for restricted. This will give you a list of various packages all called linux-restricted-modules-***.

Now you have to select the one that fits your kernel. If you have a standard install, this should be linux-restricted-modules-2.6.10-5-386. Select this package, then click apply and you should be good to go.

After it is installed, follow the great howto by FLeiXiuS.

Good luck!  :grin:[/QUOTE]
 Ok, done that but now everytime i type sudo pon into the terminal... it dials then disconnects on me =( look at the screenie below.... that is what i typed in... please help...

[IMG]http://members.dodo.net.au/~kausten/INET.PNG[/IMG]

---

### Post by KrisDwyer on 2005-07-23
[QUOTE=Knome_fan]And just in case you're still wondering about synaptic.
System -> System Administration -> Synaptic Package Manager will open synaptic. 
Once it's open, search for restricted. This will give you a list of various packages all called linux-restricted-modules-***.

Now you have to select the one that fits your kernel. If you have a standard install, this should be linux-restricted-modules-2.6.10-5-386. Select this package, then click apply and you should be good to go.

After it is installed, follow the great howto by FLeiXiuS.

Good luck!  :grin:[/QUOTE]
 i was kinda hoping to get this problem solved asap... any takers?

---

### Post by strikeforce on 2005-07-23
Post what is says after you do it in /var/log/messages and paste that.  This will show you what the computer is doing.

You do that doing the following
$sudo tail /var/log/messages

That should spit out whats going on.

---

### Post by Knome_fan on 2005-07-23
I don't think it's disconnecting, pon is just starting a background process and then quits. To see what's actually going on, type plog, or sudo plog and to stop the connection poff would be the command you are looking for.

But again, I'd suggest to use the graphical tools available und System -> System Configuration -> Network

---

### Post by KrisDwyer on 2005-07-23
[QUOTE=Knome_fan]I don't think it's disconnecting, pon is just starting a background process and then quits. To see what's actually going on, type plog, or sudo plog and to stop the connection poff would be the command you are looking for.

But again, I'd suggest to use the graphical tools available und System -> System Configuration -> Network[/QUOTE]
 Ok password is right, number is right and username is right... however it wont connect???
Below is a screenie of what happened...
[IMG]http://members.dodo.net.au/~kausten/GAHINTER.PNG[/IMG]

---

### Post by KrisDwyer on 2005-07-23
please guys i need help ay.... can anyone help at all?

---

### Post by KrisDwyer on 2005-07-23
dw about it i realised it was the CHAP Protocol needed not PAP! Thanks, Kris

---

### Post by Ptero-4 on 2005-07-26
[QUOTE=KrisDwyer]dw about it i realised it was the CHAP Protocol needed not PAP! Thanks, Kris[/QUOTE]

Hi. I'm needing some help. I already followed the wiki (compiled the drivers from linmodems.org). I'm using the CHAP Protocol and pon to connect. The modem dials out but it hangs. Here's the contents of my /var/log/messages file.

```

Jul 25 16:18:16 localhost syslogd 1.4.1#16ubuntu6: restart.
Jul 25 16:20:54 localhost pppd[11477]: pppd 2.4.2 started by fanny, uid 1000
Jul 25 16:20:55 localhost chat[11488]: abort on (BUSY)
Jul 25 16:20:55 localhost chat[11488]: abort on (NO CARRIER)
Jul 25 16:20:55 localhost chat[11488]: abort on (VOICE)
Jul 25 16:20:55 localhost chat[11488]: abort on (NO DIALTONE)
Jul 25 16:20:55 localhost chat[11488]: abort on (NO DIAL TONE)
Jul 25 16:20:55 localhost chat[11488]: abort on (NO ANSWER)
Jul 25 16:20:55 localhost chat[11488]: abort on (DELAYED)
Jul 25 16:20:55 localhost chat[11488]: send (ATZ^M)
Jul 25 16:20:55 localhost chat[11488]: expect (OK)
Jul 25 16:20:55 localhost chat[11488]: ATZ^M^M
Jul 25 16:20:55 localhost chat[11488]: OK
Jul 25 16:20:55 localhost chat[11488]:  -- got it 
Jul 25 16:20:55 localhost chat[11488]: send (ATDT3555555^M)
Jul 25 16:20:55 localhost chat[11488]: expect (CONNECT)
Jul 25 16:20:55 localhost chat[11488]: ^M
Jul 25 16:21:40 localhost chat[11488]: alarm
Jul 25 16:21:40 localhost chat[11488]: Failed
Jul 25 16:21:42 localhost pppd[11477]: Exit.

```

---

